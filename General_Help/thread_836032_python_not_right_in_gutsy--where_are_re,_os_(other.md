---
title: "python not right in gutsy--where are re, os (others?)"
date: 2008-06-21
forum: General Help
---

### Post by rbpember on 2008-06-21
OK, I got ubuntu fixed again and now for the question
that prompted me to delete python, break my gutsy installation,
and thrash for several hours :-({|= :

where in the heck are the standard python modules?

I was trying to configure my sound card via

asoundconf

and I got error messages from python:

-------------------------------------------------
%coot 10: asoundconf
'import site' failed; use -v for traceback
Traceback (most recent call last):
  File "/usr/bin/asoundconf", line 11, in <module>
    import sys, re, os.path
ImportError: No module named re
%coot 11: which asoundconf
/usr/bin/asoundconf
------------------------

I then just tried python directly:

-----------------
%coot 12: which python
/usr/bin/python
%coot 13: python
'import site' failed; use -v for traceback
Python 2.5.1 (r251:54863, Mar  7 2008, 04:10:12) 
[GCC 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import re
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named re
>>> import os
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ImportError: No module named os
>>> 
-----------------------------

Does anyone know how to get these modules? 

Since my earlier experience today showed python to be pretty central
to ubuntu, I think posting this here and not down in a more
specialized forum is appropriate.

---

### Post by VMC on 2008-06-21
I found this: "python setup.py install"

Better yet, here is the link: [http://docs.python.org/inst/inst.html](http://docs.python.org/inst/inst.html)
It describes it all.

---

### Post by geirha on 2008-06-21
The os and re modules are installed by the [python2.5-minimal](apt:python2.5-minimal) package. Try installing that one.

---

