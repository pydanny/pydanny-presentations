=============
Code samples
=============

Executed and displayed here so I can cut-and-paste into Keynote.

Whitespace
==========

.. sourcecode:: python

    """ whitespace.py """
    from random import randrange
    
    def numberizer():
        # Generate a random number from 1 to 10.
        return randrange(1, 11)
        
    number = numberizer()
    if number > 5:
        print("This number is big!")
        
    class RandomNumberHolder(object):
        # Create and hold 20 random numbers using numberizer
        
        def __init__(self):
            self.numbers = [numberizer(x) for x in range(20)]
            
    random_numbers = RandomNumberHolder()
    
Zen of Python
=============

.. sourcecode:: python

    >>> import this
    The Zen of Python, by Tim Peters

    Beautiful is better than ugly.
    Explicit is better than implicit.
    Simple is better than complex.
    Complex is better than complicated.
    Flat is better than nested.
    Sparse is better than dense.
    Readability counts.
    Special cases aren't special enough to break the rules.
    Although practicality beats purity.
    Errors should never pass silently.
    Unless explicitly silenced.
    In the face of ambiguity, refuse the temptation to guess.
    There should be one-- and preferably only one --obvious way to do it.
    Although that way may not be obvious at first unless you're Dutch.
    Now is better than never.
    Although never is often better than *right* now.
    If the implementation is hard to explain, it's a bad idea.
    If the implementation is easy to explain, it may be a good idea.
    Namespaces are one honking great idea -- let's do more of those!


Strings
========

.. sourcecode:: python

    >>> foo = 'bar' # TODO: strike-out in slides
    >>> spam = 'eggs'
    
String methods
==============

.. sourcecode:: python
    
    >>> fun = 'spam and EGGS   '
    >>> dir(fun)
    ['__add__', '__class__', '__contains__', '__delattr__', '__doc__', '__eq__',   
     '__format__', '__ge__', '__getattribute__', '__getitem__', '__getnewargs__',
     '__getslice__', '__gt__', '__hash__', '__init__', '__le__', '__len__', '__lt__',
     '__mod__', '__mul__', '__ne__', '__new__', '__reduce__', '__reduce_ex__', 
     '__repr__', '__rmod__', '__rmul__', '__setattr__', '__sizeof__', '__str__',
     '__subclasshook__', '_formatter_field_name_split', '_formatter_parser',
     'capitalize', 'center', 'count', 'decode', 'encode', 'endswith', 'expandtabs',
     'find', 'format', 'index', 'isalnum', 'isalpha', 'isdigit', 'islower', 'isspace',
     'istitle', 'isupper', 'join', 'ljust', 'lower', 'lstrip', 'partition', 'replace',
     'rfind', 'rindex', 'rjust', 'rpartition', 'rsplit', 'rstrip', 'split',
     'splitlines', 'startswith', 'strip', 'swapcase', 'title', 'translate', 'upper',
     'zfill']
    >>> fun.strip()
    'spam and EGGS'
    >>> spam.title()
    'Spam And Eggs   '
    >>> fun.capitalize()
    'Spam and eggs   '
    >>> fun.index('3')
    3
    >>> len(fun)
    16
    >>> fun.__len__() # same as the len function
    16
    >>> help(fun)
    no Python documentation found for 'spam and EGGS   '
    >>> help(str)

Help Slide Part I
==================

code::

    Help on class str in module __builtin__:

    class str(basestring)
     |  str(object) -> string
     |  
     |  Return a nice string representation of the object.
     |  If the argument is a string, the return value is the same object.
     |  
     |  Method resolution order:
     |      str
     |      basestring
     |      object
     |  
     |  Methods defined here:
     |  
     |  __add__(...)
     |      x.__add__(y) <==> x+y
     |  
     |  __contains__(...)
     |      x.__contains__(y) <==> y in x

Help Slide Part II
==================

code::

     |  capitalize(...)
     |      S.capitalize() -> string
     |      
     |      Return a copy of the string S with only its first character
     |      capitalized.
     |  
     |  center(...)
     |      S.center(width[, fillchar]) -> string
     |      
     |      Return S centered in a string of length width. Padding is
     |      done using the specified fill character (default is a space)
     |  
     |  count(...)
     |      S.count(sub[, start[, end]]) -> int
     |      
     |      Return the number of non-overlapping occurrences of substring sub in
     |      string S[start:end].  Optional arguments start and end are interpreted
     |      as in slice notation.
     
Play with strings
=================

Strings are immutable

sourcecode:: python

    >>> a = "Daniel"
    >>> b = "Adam"
    >>> c = "Greenfeld"
    >>> a + b + c
    'DanielAdamGreenfeld'
    >>> "{0} {1} {2}".format(a, b, c)
    'Daniel Adam Greenfeld'
    >>> "{first} {middle} {last}".format(first=a, middle=b, last=c)
    'Daniel Adam Greenfeld'
    >>> lst = [a,b,c]
    >>> lst
    ['Daniel', 'Adam', 'Greenfeld']
    >>> " ".join(lst)
    'I like Python'
    
Diving into lists
=================

.. sourcecode:: python 

    lst = [1,2,3,4,5,"Python", [1,2,3,4]]
    
Sets dominate
===============

.. sourcecode:: python 

    >>> lst = [1,1,1,1,1,2,2,2,3,3,3,3,3,3]
    >>> s = set(lst)
    >>> s
    set([1,2,3])

How is this useful? What about counting unique words in a paragraph?

    >>> address = """Four score and seven years ago our fathers brought forth on this continent a new nation..."""
    >>> for r in [',','.','-']:
    ...     address = address.replace(r,'')
    >>> words = address.split(' ')
    >>> len(words)
    278
    >>> unique_words = set(words)
    >>> len(unique_words)
    143

List Comprehension
====================

.. sourcecode:: python

    >>> items = [x for x in range(20)]
    >>> items
    [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19]
    >>> [x for x in range(20) if x % 2]
    [1, 3, 5, 7, 9, 11, 13, 15, 17, 19]
    >>> # Fizzbuzz solved using Python's List Comprehension
    >>> lst = [(x, 'Fizz', 'Buzz', 'FizzBuzz') \ 
    ...     [(not x % 3) | (not x % 5) << 1] for x in range(20)]
    >>> for x in lst: print(x)
    FizzBuzz
    1
    2
    Fizz
    4
    Buzz
    Fizz
    7
    8
    Fizz
    Buzz
    11
    Fizz
    13
    14
    FizzBuzz
    16
    17
    Fizz
    19
    
    
    
Generator Expressions
=====================

.. sourcecode:: python

    >>> items = (x for x in range(20))
    >>> items
    <generator object <genexpr> at 0x100721460>
    
In Python, a generator can be thought of as an iterator that contains a frozen stack frame. Whenever the iterator's next() method is called, Python resumes the frozen frame, which executes normally until the next yield statement is reached. The generator's frame is then frozen again, and the yielded value is returned to the caller.

.. sourcecode:: python

    # loop way
    wwwlog = open("access-log")
    total = 0
    for line in wwwlog:
        bytestr = line.rsplit(None,1)[1]
        if bytestr != '-':
            total += int(bytestr)
    print "Total", total
    
.. sourcecode:: python    

    # generator expressions way
    wwwlog     = open("access-log")
    bytecolumn = (line.rsplit(None,1)[1] for line in wwwlog)
    bytes      = (int(x) for x in bytecolumn if x != '-')
    print "Total", sum(bytes)

Pygments
=========

First get the pygments code::

    pip install pygments

Then run this simple 'recursive' program:

.. sourcecode:: python

    from pygments import highlight
    from pygments.lexers import get_lexer_by_name
    from pygments.formatters import HtmlFormatter

    if __name__ == '__main__':
        code = open("pygments_demo.py", "rw").read()
        lexer = get_lexer_by_name("python", stripall=True)
        formatter = HtmlFormatter(linenos=False, cssclass="source")
        css = HtmlFormatter().get_style_defs('.source')
        highlighted_code = highlight(code, lexer, formatter)        
        page = """
            <html>
                <head><style>{css}</style></head>
                <body>{highlighted_code}</body>
            </html>
            """.format(css=css, highlighted_code=highlighted_code)
        print(page)

Now run the program and check the results::

    python pygments_demo.py > text.html
    open text.html
    
Isolate Environments
=====================

code::

    $ curl https://raw.github.com/pypa/pip/master/contrib/get-pip.py | python
    $ pip install virtualenv
    $ virtualenv my_env
    $ source my_env/bin/activate
    (my_env) $ 
    
More code::

    (my_env) $ pip install django==1.3.1
    (my_env) $ pip install requests==0.9.1
    (my_env) $ pip install mongoengine==0.5.2
    (my_env) $ pip install celery==2.4.6
    (my_env) $ pip freeze
    celery==2.4.6
    django==1.3.1
    mongoengine==0.5.2
    requests==0.9.1
    (my_env) $ pip freeze > requirements.txt
    ...
    (another_env) $ pip install -r requirements.txt

Persist SQL 
====================

.. sourcecode:: python

    from datetime import datetime

    from django.contrib.auth.models import User
    from django.db import models
    from django.utils.translation import ugettext_lazy as _
    
    class Post(models.Model):
    
        author = models.ForeignKey(User)
        title = models.CharField(_('Title'), max_length=100)
        content = models.TextField(_("Content"))
        pub_date = models.DateTimeField(_("Publication date"))
        
    class Comment(models.Model):
        post = models.ForeignKey(Post)
        name = models.CharField(_('Title'), max_length=100)
        content = models.TextField(_("Content"))
        
Persist NoSQL
=============

.. sourcecode:: python

    from django.utils.translation import ugettext_lazy as _

    import mongoengine as me
    
    class User(me.Document):
        email = me.StringField(_('email'), required=True)
        first_name = me.StringField(_('first name'), max_length=30)
        last_name = me.StringField(_('last name'), max_length=30)    
        
    class Post(me.Document):
        title = me.StringField(_('title'), max_length=100, required=True)
        author = me.ReferenceField(User)
        content = me.StringField(_('content'))
        pub_date = me.DateTimeField(_("Publication date"))

    class Comment(me.EmbeddedDocument):
        name = me.StringField(_('name'), max_length=100)    
        content = me.StringField(_('content'))
                
Message Queues
===============

dependencies::

    celery
    requests

tasks.py:

.. sourcecode:: python

    import logging
    import requests
    from celery import task
    
    from products.models import Product
    
    logger = logging.getLogger('products.tasks')
    
    @task
    def confirm_all_images():
    
        for product in Product.objects.all():
            response = request.get(product.medium_image.url)
            if response.status_code != 200:
                msg = "Product {0} missing image".format(product.id)
                logging.warning(msg)

Shell:

.. sourcecode:: python

    >>> from products.tasks import confirm_all_images
    >>> result = confirm_all_images.delay()
    >>> result.ready()
    False
    >>> result.ready()
    True
    
Exception Handling
===================

.. sourcecode:: python

    >>> import logging
    >>> logger = logging.getlogger()
    >>>
    >>> class CustomTypeError(Exception):
    ...     pass
        
    >>> try:
    ...     a = 1 + "Error"
    >>> except TypeError as e:
    ...     raise CustomTypeError(e)
    >>> except Exception as e:
    ...     logger.error(e)
        
    Traceback (most recent call last):
      File "<stdin>", line 4, in <module>
    __main__.CustomTypeError: unsupported operand type(s) for +: 'int' and 'str'
        
Generators
============

.. sourcecode:: python

    >>> def countdown(n):
    ...     print("Counting down from {0}".format(n))
    ...     while n > 0:
    ...        yield n
    ...        n -= 1
            
    >>> x = countdown(10)
    >>> x
    <generator object at 0x58490>
    >>> x.next()
    Counting down from 10
    10
    >>> x.next()
    9
    >>> x.next()
    8
    >>> x.next()
    7

* http://www.dabeaz.com/generators/Generators.pdf

Do things with Strings
========================

.. sourcecode:: python

    >>> scale = 'Southern California Linux Expo'
    >>> scale[0]
    'S'
    >>> scale[0:8]
    'Southern'
    >>> scale[:-11]
    'Southern California Linux'
    >>> scale[0:8] = 'Northern'
    Traceback (most recent call last):
      File "<input>", line 1, in <module>
    TypeError: 'str' object does not support item assignment    
    >>> scale.replace('Southern California','SoCal')
    'SoCal Linux Expo'
    >>> scale 
    'Southern California Linux Expo'
    >>> s = scale.replace('Southern California','SoCal')
    >>> s
    'SoCal California Linux Expo'
    >>> scale.startswith('Windows')
    False
    >>> scale.endswith('Windows')
    False
    >>> scale.startswith('Southern')
    True
    >>> 'Windows' in scale
    False
    >>> 'Linux' in scale
    True
    
Basics
========

.. sourcecode:: python

    >>> x, y, z = 5, 10, 15
    >>> 5 < 10
    True
    >>> 5 > 10
    False
    >>> True == False
    False
    >>> (5 == x) or (10 == x)
    True
    >>> (5 == x) and (10 == x)
    False
    >>> x + y - z
    0    
    >>> 10 * 5
    50
    >>> 10 / 5
    2
    >>> 10 + 5
    15
    >>> 10 ** 2
    100 
    
Dictionaries
============

Python dictionaries are mutable key/value stores. 

.. sourcecode:: python

    >>> data = {
           'name':'Daniel Greenfeld',
           'nickname':'pydanny',
           'states_lived':['CA','KS','MD','NJ','VA','AD'],
           'fiancee':'Audrey Roy'
           }
    >>> data['name']
    'Daniel Greenfeld'
    >>> data['nickname'] = 'audreyr'
    >>> data['nickname']
    'audreyr'
    >>> data['nickname'] = 'pydanny'    
    >>> data.keys()
    ['fiancee', 'nickname', 'name', 'states_lived']
    >>> data.get('fiancee')
    'Audrey Roy'
    >>> data.get('fiance')
    None
    >>> data.pop('fiancee')
    'Audreyr'
    >>> data
    {'nickname': 'pydanny', 'name': 'Daniel Greenfeld', 'states_lived': ['CA', 'KS', 'MD', 'NJ', 'VA']}
    >>> data['fiancee'] = 'Audrey Roy'
    >>> data
    {'fiancee': 'Audrey Roy', 'nickname': 'pydanny', 'name': 'Daniel Greenfeld', 'states_lived': ['CA', 'KS', 'MD', 'NJ', 'VA', 'AD']}
    
Work with JSON
==============

.. sourcecode:: python

    >>> import json
    
    >>> data = {
        'name':'Daniel Greenfeld',
        'nickname':'pydanny',
        'states_lived':['CA','KS','MD','NJ','VA','AD'],
        'fiancee':'Audrey Roy'
        }
    >>> type(data)
    <type 'dict'>
    >>> payload = json.dumps(data)
    >>> payload
    '{"fiancee": "Audrey Roy", "nickname": "pydanny", "name": "Daniel Greenfeld", "states_lived": ["CA", "KS", "MD", "NJ", "VA", "AD"]}'
    >>> type(payload)
    <type 'str'>
    >>> restored = json.loads(payload)
    >>> restored
    <type 'dict'>
    >>> restored
    {u'fiancee': u'Audrey Roy', u'nickname': u'pydanny', u'name': u'Daniel Greenfeld', u'states_lived': [u'CA', u'KS', u'MD', u'NJ', u'VA', u'AD'
    ]}
    
Object-Oriented Programming
============================

.. sourcecode:: python

    class Animal(object):
        def __init__(self, name):    # Constructor of the class
            self.name = name
        def talk(self):              # Abstract method, defined by convention only
            raise NotImplementedError("Subclass must implement abstract method")
 
    class Cat(Animal):
        def talk(self):
            return 'Meow!'
 
    class Dog(Animal):
        def talk(self):
            return 'Woof! Woof!'
 
    animals = [Cat('Missy'),
               Cat('Mr. Mistoffelees'),
               Dog('Lassie')]
 
    for animal in animals:
        print animal.name + ': ' + animal.talk()

output::

    Missy: Meow!
    Mr. Mistoffelees: Meow!
    Lassie: Woof! Woof!

* http://en.wikipedia.org/wiki/Polymorphism_in_object-oriented_programming#Examples

REPL
====

example::

    $ python
    Python 2.7.1+ (r271:86832, Apr 11 2011, 18:13:53) 
    [GCC 4.5.2] on linux2
    Type "help", "copyright", "credits" or "license" for more information.
    
python:

.. sourcecode:: python

    >>> 3 + 4
    7
    >>> a = 5 * 10
    >>> a
    50
    >>> def add(a, b):
    ...     return a + b
    ... 
    >>> add(3,4)
    7
    >>> add('Py','thon')
    'Python'
    >>> for x in 'Python':
    ...     print x
    ... 
    P
    y
    t
    h
    o
    n
    >>>
    
Serve the Web
==============

.. sourcecode:: python

    from flask import Flask
    app = Flask(__name__)

    @app.route("/")
    def hello():
        return "Hello World!"

    if __name__ == "__main__":
        app.run()
        
PyMongo
========

.. sourcecode:: python

    >>> import pymongo
    >>> connection = pymongo.Connection("localhost", 27017)
    >>> db.name
    u'test'
    >>> db.my_collection
    Collection(Database(Connection('localhost', 27017), u'test'), u'my_collection')
    >>> db.my_collection.save({"x": 10})
    ObjectId('4aba15ebe23f6b53b0000000')
    >>> db.my_collection.save({"x": 8})
    ObjectId('4aba160ee23f6b543e000000')
    >>> db.my_collection.save({"x": 11})
    ObjectId('4aba160ee23f6b543e000002')
    >>> db.my_collection.find_one()
    {u'x': 10, u'_id': ObjectId('4aba15ebe23f6b53b0000000')}
    >>> for item in db.my_collection.find():
    ...     print item["x"]
    ...
    10
    8
    11
    >>> db.my_collection.create_index("x")
    u'x_1'
    >>> [item["x"] for item in db.my_collection.find().limit(2).skip(1)]
    [8, 11]