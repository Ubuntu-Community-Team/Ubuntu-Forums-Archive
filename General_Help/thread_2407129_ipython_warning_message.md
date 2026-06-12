---
title: "ipython warning message"
date: 2018-11-30
forum: General Help
---

### Post by stable.os on 2018-11-30
When I try and execute 'ipython' from Linux shell by typing 'ipython' at the command prompt, it gives me the following message-[INDENT]   
Error processing line 1 of   /home/user_name/.local/lib/python3.6/site-packages/matplotlib-2.2.3-py3.6-nspkg.pth:
      Traceback (most recent call last):       File "/usr/lib/python3.6/site.py", line 174, in addpackage         exec(line)       File "", line 1, in        File "", line 568, in module_from_spec   AttributeError: 'NoneType' object has no attribute   'loader'
      Remainder of file ignored Python 3.6.7 (default, Oct 22 2018,   11:32:17)  Type 'copyright', 'credits' or 'license' for more   information IPython 6.4.0 -- An enhanced Interactive Python. Type '?'   for help.
 [/INDENT]

I also get the same message when trying to use updates with "sudo apt-get update" command.

$ sudo apt-get update

Hit:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease
Hit:2 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) bionic InRelease               
Ign:3 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease             
Hit:4 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) bionic-updates InRelease
Hit:5 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) bionic-backports InRelease
Hit:6 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release
Error processing line 1 of /home/user_name/.local/lib/python3.6/site-packages/matplotlib-2.2.3-py3.6-nspkg.pth:

  Traceback (most recent call last):
    File "/usr/lib/python3.6/site.py", line 174, in addpackage
      exec(line)
    File "<string>", line 1, in <module>
    File "<frozen importlib._bootstrap>", line 568, in module_from_spec
  AttributeError: 'NoneType' object has no attribute 'loader'

Remainder of file ignored
Reading package lists... Done



I have a Linux x86_64 Ubuntu OS [18.04] system. Any ideas as to why this is happening? And how to fix it?
  
Thanks!

---

### Post by salonitayal001 on 2019-11-03
Simple just delete it! ```
rm -R /home/user_name/.local/lib/python3.6/site-packages/matplotlib-2.2.3-py3.6-nspkg.pth
```

---

### Post by uRock on 2019-11-03
Back to sleep old thread.

---

