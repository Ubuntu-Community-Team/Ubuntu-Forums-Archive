---
title: "I've broken something, get strange gdbm error"
date: 2015-11-06
forum: General Help
---

### Post by wilson-eric-n on 2015-11-06
I'm getting a very puzzling error at my terminal. It happens when I type something that is not a command or installed program. It looks like this:

```

my@my_machine:~$ a # or anything else that is not an installed program or bash command
Traceback (most recent call last):
  File "/usr/lib/python3.5/dbm/gnu.py", line 4, in <module>
    from _gdbm import *
ImportError: No module named '_gdbm'


During handling of the above exception, another exception occurred:


Traceback (most recent call last):
  File "/usr/lib/python3/dist-packages/CommandNotFound/CommandNotFound.py", line 7, in <module>
    import dbm.gnu as gdbm
  File "/usr/lib/python3.5/dbm/gnu.py", line 6, in <module>
    raise ImportError(str(msg) + ', please install the python3-gdbm package')
ImportError: No module named '_gdbm', please install the python3-gdbm package


During handling of the above exception, another exception occurred:


Traceback (most recent call last):
  File "/usr/lib/command-not-found", line 27, in <module>
    from CommandNotFound.util import crash_guard
  File "/usr/lib/python3/dist-packages/CommandNotFound/__init__.py", line 3, in <module>
    from CommandNotFound.CommandNotFound import CommandNotFound
  File "/usr/lib/python3/dist-packages/CommandNotFound/CommandNotFound.py", line 9, in <module>
    import gdbm
ImportError: No module named 'gdbm'

```

This is really strange to me. I've tried installing ```
python3-gdbm package
``` but it tells me that I already have it.

So what did I do?
[LIST=1]
[*]Recently upgraded from Python 3.4 to Python 3.5. That seemed to work fine ... mostly (more on that later)
[*]Upgraded to Node 4.2.1 from 0.12
[*]In an effort to upgrade ember-cli did ```
bower cache clean
```
[*]Upgraded to the latest versions of npm and bower
[/LIST]

With my Python upgrade, I was having some trouble with virtualenv and virtualenvwrapper. I can't create a virtual environment for python 3, it always puts python 2 in it, but I don't know that this is related a all.

Please help me diagnose this, I currently have no understanding of why an unknown command would try to invoke anything with python.

---

### Post by ian-weisser on 2015-11-07
The unknown command is properly invoking command-not-found.
Command-not-found is tying to load a database (one assumes to look for possible matching commands), and failing.

I would try reinstalling python3-gdbm and command-not-found.
If that doesn't work, please file a bug report against command-not-found.

---

