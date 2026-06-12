---
title: "My viewing packages is not responding"
date: 2015-02-04
forum: General Help
---

### Post by mohsin525 on 2015-02-04
hello,
I am using ubuntu 12.04, after i installed python, I can't access my viewing packages like salomemecca won't start, paraFoam does not work, paraview opens up but does not respond, matplotlib.pyplot won't work. Can you help me out. I just executed matplotlib in the command prompt and it gave me this error
 
import matplotlib.pyplot as plt
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/pymodules/python2.7/matplotlib/__init__.py", line 132, in <module>
    import sys, os, tempfile
  File "/usr/lib/python2.7/tempfile.py", line 34, in <module>
    from random import Random as _Random
  File "random.py", line 1
    ;; This buffer is for notes you don't want to save, and for Lisp evaluation.
    ^
SyntaxError: invalid syntax
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/apport_python_hook.py", line 66, in apport_excepthook
    from apport.fileutils import likely_packaged, get_recent_crashes
  File "/usr/lib/python2.7/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.7/dist-packages/apport/report.py", line 12, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os
  File "/usr/lib/python2.7/tempfile.py", line 34, in <module>
    from random import Random as _Random
  File "random.py", line 1
    ;; This buffer is for notes you don't want to save, and for Lisp evaluation.
    ^
SyntaxError: invalid syntax


Original exception was:
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/pymodules/python2.7/matplotlib/__init__.py", line 132, in <module>
    import sys, os, tempfile
  File "/usr/lib/python2.7/tempfile.py", line 34, in <module>
    from random import Random as _Random
  File "random.py", line 1
    ;; This buffer is for notes you don't want to save, and for Lisp evaluation.
    ^
SyntaxError: invalid syntax
>>> import matplotlib.pyplot as plt
KeyboardInterrupt
>>> 
muhsin@muhsin-HP-ProBook-4530s:~$ clear


muhsin@muhsin-HP-ProBook-4530s:~$ python
Python 2.7.3 (default, Feb 27 2014, 20:00:17) 
[GCC 4.6.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import matplotlib.pyplot as plt
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/pymodules/python2.7/matplotlib/__init__.py", line 132, in <module>
    import sys, os, tempfile
  File "/usr/lib/python2.7/tempfile.py", line 34, in <module>
    from random import Random as _Random
  File "random.py", line 1
    ;; This buffer is for notes you don't want to save, and for Lisp evaluation.
    ^
SyntaxError: invalid syntax
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/apport_python_hook.py", line 66, in apport_excepthook
    from apport.fileutils import likely_packaged, get_recent_crashes
  File "/usr/lib/python2.7/dist-packages/apport/__init__.py", line 1, in <module>
    from apport.report import Report
  File "/usr/lib/python2.7/dist-packages/apport/report.py", line 12, in <module>
    import subprocess, tempfile, os.path, urllib, re, pwd, grp, os
  File "/usr/lib/python2.7/tempfile.py", line 34, in <module>
    from random import Random as _Random
  File "random.py", line 1
    ;; This buffer is for notes you don't want to save, and for Lisp evaluation.
    ^
SyntaxError: invalid syntax


Original exception was:
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/pymodules/python2.7/matplotlib/__init__.py", line 132, in <module>
    import sys, os, tempfile
  File "/usr/lib/python2.7/tempfile.py", line 34, in <module>
    from random import Random as _Random
  File "random.py", line 1
    ;; This buffer is for notes you don't want to save, and for Lisp evaluation.
    ^
SyntaxError: invalid syntax
>>>

---

### Post by Peptid on 2015-02-05
Hi,

I am just confused. Doesn't Python come within Ubuntu, why/what did you install? 

Also, where did you entered matplotlib command, in iPython environment? I think I might help if you be more specific with what you did.

---

### Post by Holger_Gehrke on 2015-02-05
> **mohsin525 said:**
> 
```

Original exception was:
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/pymodules/python2.7/matplotlib/__init__.py", line 132, in <module>
    import sys, os, tempfile
  File "/usr/lib/python2.7/tempfile.py", line 34, in <module>
    from random import Random as _Random
  File "random.py", line 1
    ;; This buffer is for notes you don't want to save, and for Lisp evaluation.
    ^
SyntaxError: invalid syntax

```


Looks to me like you somehow managed to save an emacs scratch buffer into '/usr/lib/python2.7/random.py'. That file is part of the package 'python2.7-minimal'. You might want to reinstall that.

---

