---
title: "uninstalling or removing python?"
date: 2007-04-24
forum: General Help
---

### Post by sievert on 2007-04-24
when trying to install a program, I kept getting an unmet dependency error telling me I had the wrong version of python. 
```
Depends: python (< 2.5) but 2.5.1~rc1-0ubuntu3 is to be installed
```

obviously I wasn't thinking straight, because I thought my python was out of date. 
Since there were no newer version of python in the repositories, I went to python.org, downloaded the latest version of python, and installed in manually using make install.

now I'm starting to realize that that was a mistake. Some programs have stopped working since I installed this version of python.
for example:
```
$ gmail-notify
Traceback (most recent call last):
  File "./notifier.py", line 4, in <module>
    import pygtk
ImportError: No module named pygtk
```

I get errors like these when I try to run certain programs that worked before.

I'm not sure what I have to do to return my system to normal. The only thing I can think of is uninstalling the version of python I manually installed. Unfortunately I did it with a makefile so I can't do it through Synaptic or apt-get. make uninstall isn't an option either.

any ideas?

---

### Post by sievert on 2007-04-25
nobody has any ideas?

in a similar post, someone suggested removing a manual install by deleting all the files coped by the makefile.  Is this safe? it seems like a bad idea to me.

---

