---
title: "Question about Python version"
date: 2013-07-15
forum: General Help
---

### Post by vasa1 on 2013-07-15
This is what I see on a fully updated Lubuntu 13.04 (with quite some extra software installed):

```
[09:01 AM] ~ $ python2
Python 2.7.4 (default, Apr 19 2013, 18:32:33) 
[GCC 4.7.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 
[09:01 AM] ~ $ python3
Python 3.3.1 (default, Apr 17 2013, 22:32:14) 
[GCC 4.7.3] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> 
[09:01 AM] ~ $ python
Python 2.7.4 (default, Apr 19 2013, 18:32:33) 
[GCC 4.7.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 


```

Does that mean that the default is Python 2.74 and not Python 3.3.1? Why do I have two Python versions?

I mentioned that I have installed additional software packages in case that explains why I see two Python versions but then why does the third command show Python 2 and not Python 3?

---

### Post by oldfred on 2013-07-15
They are in the process of converting all the python code in Ubuntu to python3, but will still offer python2 as many users have not converted yet.
Currently I have both python2 & python3 in my 12.04, but I have to install the current version of python3 to have it and specify python3 if I want to run that version.
It is just the link from python is to python2 currently. 
In some future version python will link to python3, and then to run python2 you will have to be explicit.

---

### Post by vasa1 on 2013-07-16
Thanks, that solved my question.

---

### Post by sanderj on 2013-07-16
Please note that python2 is a different language than python3; code written for python2 does not run with pyhon3.

'python' defaults to python2 as most code is python2 style.

---

### Post by oldfred on 2013-07-16
Its not a different language but there were major changes that made parts of the code incompatible. The latest 2.7 made some of the differences less as it would work with both the old & new. There are some tools to highlight differences from 2.7 to new 3, but some changes cannot just be done with an editor.  
I found the change to the print  to need () as the biggest changes as the simple programs I wrote had few if any of the other changes.

---

