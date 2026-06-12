---
title: "Python 2.5 - using the &quot;tabulate&quot; recipe"
date: 2007-08-11
forum: General Help
---

### Post by trilobite on 2007-08-11
Hi all - 

  I'm wanting to do a small public-domain crosstab app using Python 2.5.  What I have in mind is something which reads in a csv file (using Python's built-in csv module) and does a crosstab of it.  

In the Python docs (in the "itertools" section), there's an example of a recipe called "tabulate" - it uses another function called "imap".  Here they are -  ( by the way, I've just noticed that posting has mucked-up the layout of the code, removing the very-important whitespace at the left-hand-side of the code.  Here's a link to the imap page - 
[http://docs.python.org/lib/itertools-functions.html](http://docs.python.org/lib/itertools-functions.html)

.... and here's a link to the "tabulate" code - 
[http://docs.python.org/lib/itertools-recipes.html](http://docs.python.org/lib/itertools-recipes.html) 


def imap(function, *iterables):
         iterables = map(iter, iterables)
         while True:
             args = [i.next() for i in iterables]
             if function is None:
                 yield tuple(args)
             else:
                 yield function(*args)

def tabulate(function):
    "Return function(0), function(1), ..."
    return imap(function, count())

Now, I've searched on the 'net to try to find an example of this "tabulate" being used. No luck.  ( One problem, which the docs *don't* clarify, is - what can tabulate be *used on*?  Lists? Tuples? )   

All I need is an example which shows tabulate being used with whatever kind of data-structure it can use, whether that be a list or whatever.  So, I'm hoping that there may be a Python guru or two around who's able to help out... :-)  Very many thanks in advance - bye for now - 
 - trilobite

---

### Post by apetresc on 2007-08-11
> **trilobite said:**
> 
All I need is an example which shows tabulate being used with whatever kind of data-structure it can use, whether that be a list or whatever.  So, I'm hoping that there may be a Python guru or two around who's able to help out... :-)  Very many thanks in advance - bye for now - 
 - trilobite
It's not used on data structures, it's used on functions. It's a little piece of functional programming in Python :) What a beautiful language...

Here's a little example I whipped up to demonstrate:
```
adrian@rootbeer:~$ python
Python 2.5.1 (r251:54863, May  2 2007, 16:56:35)
[GCC 4.1.2 (Ubuntu 4.1.2-0ubuntu4)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> from itertools import imap, count
>>> def tabulate(function):
...     return imap(function,count())
...
>>> def sq(x):
...     return x*x
...
>>> sq_iter = tabulate(sq)
>>> sq_iter.next()
0
>>> sq_iter.next()
1
>>> sq_iter.next()
4
>>> sq_iter.next()
9
>>> sq_iter.next()
16
>>> sq_iter.next()
25
>>>
```
If you've ever done functional programming before, this'll be familiar to you. If you've only done procedural and object-oriented, this may need some explaining, so let me know :)

Also, for future reference, we have an entire forum for programming questions: [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

### Post by trilobite on 2007-08-11
> **AdrianP said:**
> It's not used on data structures, it's used on functions. It's a little piece of functional programming in Python :) What a beautiful language...

Here's a little example I whipped up to demonstrate:
```
adrian@rootbeer:~$ python
Python 2.5.1 (r251:54863, May  2 2007, 16:56:35)
[GCC 4.1.2 (Ubuntu 4.1.2-0ubuntu4)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> from itertools import imap, count
>>> def tabulate(function):
...     return imap(function,count())
...
>>> def sq(x):
...     return x*x
...
>>> sq_iter = tabulate(sq)
>>> sq_iter.next()
0
>>> sq_iter.next()
1
>>> sq_iter.next()
4
>>> sq_iter.next()
9
>>> sq_iter.next()
16
>>> sq_iter.next()
25
>>>
```
If you've ever done functional programming before, this'll be familiar to you. If you've only done procedural and object-oriented, this may need some explaining, so let me know :)

Also, for future reference, we have an entire forum for programming questions: [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

Hi - thanks very much, AdrianP!  This is great!  
  I have to admit that I didn't see the programming forum - should have looked harder... :-P   
  I'm just getting into functional programming via Haskell - that's an amazing language.  Makes the ol' head spin a bit, but  I love the elegance of it.  
 Thanks again - bye for now - 
- trilobite

---

