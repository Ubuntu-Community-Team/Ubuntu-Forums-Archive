---
title: "Making a .pyc"
date: 2006-10-19
forum: General Help
---

### Post by gorded on 2006-10-19
I've heard that .pyc files starts up faster than .py files, i was wondering what i need to do to make a .py file into a .pyc

Thanks

---

### Post by meng on 2006-10-19
Python automatically creates a .pyc file once you run a .py file.

---

### Post by gorded on 2006-10-19
Ok i shall tell the whole story, I use urk and an irc client and when i run 
Python urk.py all of the .py in the urk folders get there own happy .pyc files. urk.py is however leftout of this. Is there any reason that urk might be removing its .pyc or would simply not make one.

---

### Post by po0f on 2006-10-19
gorded,

It's because of the difference in the way the files are used.  urk.py is considered a "script" I guess you could say.  The other Python files are considered "modules", because they are somehow used in urk.py, either by direct import or an imported file importing them.  Python byte-compiles modules, and puts the resulting bytecode from file foo.py into a file foo.pyc.

Programs that are run via `python script.py` are interpreted by Python and byte-compiled in memory.  Once the program is in memory, there should be no speed difference between the script and an already compiled Python module in terms of execution speed, just the difference in the time it takes to load the script and byte-compile it when it is first run.

The simple answer is that you can compile a Python script into Python bytecode, but I haven't found a reason to yet (so I don't know how to either).  IMO Python is fast enough, and once the program is loaded it doesn't make a difference anyway.

---

