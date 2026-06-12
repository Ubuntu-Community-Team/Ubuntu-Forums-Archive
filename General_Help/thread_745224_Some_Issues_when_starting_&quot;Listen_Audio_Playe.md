---
title: "Some Issues when starting &quot;Listen Audio Player&quot;"
date: 2008-04-04
forum: General Help
---

### Post by Vedanta on 2008-04-04
Hi, 

This is my first post on this Forum, i switched from windows to Ubuntu (Gutsy Gibbon 7.10, using compiz fusion and Gnome) and, after some weeks of learning because i don't wanted to use the defaults, am really satisfied with it.  

So now the problem: 

I've downloaded the "Listen Audio Player" and compiled it (i hope thats right) with "./configure" (by that he showed me some dependencies that I've installed afterwards). After that i did "make" and "make install". After some time of troubleshooting it was done. When i want to start it now this message occurs and the starting ends: 


** (listen.py:5422): WARNING **: Irregular conf file line(1):
# this file contains quirks

** (listen.py:5422): WARNING **: Irregular conf file line(1):
# list prgname that need to be ignored below

** (listen.py:5422): WARNING **: Irregular conf file line(1):
#

** (listen.py:5422): WARNING **: Irregular conf file line(0):

Traceback (most recent call last):
  File "/usr/lib/listen/listen.py", line 66, in <module>
    import utils, const, stock, config
  File "/usr/lib/listen/utils.py", line 33, in <module>
    import stock
  File "/usr/lib/listen/stock.py", line 78, in <module>
    import const
  File "/usr/lib/listen/const.py", line 116
SyntaxError: Non-ASCII character '\xc3' in file /usr/lib/listen/const.py on line 117, but no encoding declared; see [http://www.python.org/peps/pep-0263.html](http://www.python.org/peps/pep-0263.html) for details


I've really searched the whole web for an post like this (I think this is the first time i couldn't google something) but you can imagine that "listen" is a bad word in google and it wasn't nice what i've found with that errormessage. Also the link in the error doesn't say anything to me, don't know what to do with this information. 
 
I hope someone can help, thanks.

---

### Post by davey.moore on 2008-07-11
Have you found a solution to this?
I came across your post because Im having the same problem at the moment.

I hope you can help...

---

