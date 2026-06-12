---
title: "amsn not working"
date: 2007-07-05
forum: General Help
---

### Post by Portable_Jim on 2007-07-05
I had aMSN working fine a couple of days ago. I then tried to do something with aptitude and it started removing all my programs / packages starting with the a's. I then stopped aptitude and reinstalled the programs that were uninstalled. That seemed to have no effect until I started up amsn. It closed immediately (not even the window showed up). So I ran the command in the terminal. I got ```
Segmentation fault
```. I tried using the Ubuntu package but to no avail. After searching google I decided to install from source. After getting ```
./configure
``` to work with ```
./configure --with-tcl=/usr/lib/tcl8.4 --with-tk=/usr/lib/tk8.4 --enable-debug
```it then came up with an error about TkCximage.

I have installed tk8.5 tk8.5-dev tcl8.5 tcl8.5-dev and have had no sucess

Can anybody help me.
Thanks in advance.

---

### Post by DagMan on 2007-07-06
try 
```
sudo apt-get build-dep amsn
```
and then maybe you can build it
I had troubles with amsn recently and it was the program itself wanting to download somehing extra apparently having to do with using the new windows live protocol over the msn messenger one... I think.  It failed.  I found the fix on the automatix forum but can't remember what it was.  Perhaps it's the same issue.

---

