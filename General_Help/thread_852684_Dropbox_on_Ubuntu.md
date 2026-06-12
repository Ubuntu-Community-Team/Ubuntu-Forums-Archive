---
title: "Dropbox on Ubuntu"
date: 2008-07-07
forum: General Help
---

### Post by F1sh053 on 2008-07-07
Hello! This is my first time actually having to post to get help with Ubuntu. I have been running it for almost 6 months now with very low problems compared to my run with Vista and I love it!

As many of you know, a program called Dropbox is now in beta testing and I have been lucky enough to score an invite. I would love to use this program, but unfortunately I cannot install it on Ubuntu. Or rather, when installing it with Wine I get the following error in the logfile

Traceback (most recent call last):

  File "dropbox.py", line 3, in <module>

  File "zipextimporter.pyc", line 82, in load_module

  File "arch\__init__.pyc", line 4, in <module>

  File "zipextimporter.pyc", line 82, in load_module

  File "arch\win32\util.pyc", line 2, in <module>

  File "zipextimporter.pyc", line 98, in load_module

ImportError: MemoryLoadLibrary failed loading win32process.pyd


and thus I cannot open and use the program. I am curious if anyone has integrated Dropbox into Ubuntu or if anyone has ideas as to how Dropbox can be integrated into Ubuntu. 

Thanks!

---

### Post by The Spy on 2008-09-11
There is now a Linux version of Dropbox now. It can be downloaded at the Dropbox website, Getdropbox.com.
Dropbox is now public. You don't need a key to download it.

---

### Post by csmicfool on 2009-07-29
I am getting a very similar error with a different program for windows that is installed with wine.

"win32process.pyd" is missing.

Is there a win32process.pyd equivalent for linux?  Or some other type of workaround?

---

### Post by MichealH on 2009-07-29
I have the Linux version and you see when installed its the same as the windows one really you even get the thing in the notification area. Try it out at [http://www.getdropbox.com]("http://www.getdropbox.com/")!

Also when on page under Get Drop box there is a link called Linux** click it!**

---

