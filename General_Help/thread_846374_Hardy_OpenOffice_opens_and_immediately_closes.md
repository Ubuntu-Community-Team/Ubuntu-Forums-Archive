---
title: "Hardy OpenOffice opens and immediately closes"
date: 2008-07-01
forum: General Help
---

### Post by DChamp on 2008-07-01
First, I'm a complete noob, but I'm slowly learning.

Now then, I have Hardy 8.0.4 all patched, but just recently, (probably after one of the "patches", if I go to open any of the OpenOffice applications, it opens and quickly closes before the interface completely comes up. No error, just closes.

If I take an existing document and double click on it, it works fine.
OpenOffice is version 2.4.1
I'm running in a VMWare Workstation window on an HP Laptop. This worked fine recently.
Only changes I made to Hardy was to update to FireFox 3 a few weeks ago and I can't remember if I was able to open any of the apps afterwards. I do know though, that from Evolution I can't click on a link and have it automatically open a webpage.

One other thing, I can create a new user and OpenOffice works fine for them. For me (installer of the patches) though, no luck.

Any help would be appreciated (with complete steps to fix please.. noob, remember!)

Dave/DChamp

---

### Post by kuja on 2008-07-01
Try deleting your ~/.openoffice.org2 directory.

---

### Post by DChamp on 2008-07-01
Tried and did nothing to help.

---

### Post by DChamp on 2008-07-03
I found the answer on another forum. Someone was nice enough to show me how to fix it without reinstalling OpenOffice at all.

---

### Post by Midahed on 2008-08-01
> **DChamp said:**
> I found the answer on another forum. Someone was nice enough to show me how to fix it without reinstalling OpenOffice at all.

Any chance of a clue as to what the solution actually was, or a link to it? :)

I have an almost identical problem and, so far, haven't managed to find a solution....

Thanks,

Mike

---

### Post by michael_1234 on 2008-08-01
...(in case the original poster does not post the answer) .... it sounds like  the shortcut just pointed to the older version of the software, which may have been removed upon an update.  That is, possibly it's just the shortcut (or menu item or whatever) that is bad.  I'm just totally guessing, of course.

Check the menu editor:  System > Preferences > Main Menu

Right-click the icon / entry / whatever for: OpenOffice.org Word Processor, etc, and see what actual program is being used.  Eg: ooffice -writer %U

Also, see if it'll start from the terminal: 
$ which ooffice
/usr/bin/ooffice

$ ooffice  -writer
[I]  (does office start?)
[/I]
If it's a shell script, you can look at it. If it's a link, see where it points to.

1$ ls -l /usr/bin/soffice 
lrwxrwxrwx 1 root root 33 Jul  2 23:03 /usr/bin/soffice -> ../lib/openoffice/program/soffice

$ file /usr/bin/ooffice 
/usr/bin/ooffice: POSIX shell script text executable

[I](don't run "more" on a binary file!  but a shell script is ok to view)
[/I]
$ more /usr/bin/ooffice 
#!/bin/sh
/usr/lib/openoffice/program/soffice  "$@"

*Ok... ooffice actually runs */usr/lib/openoffice/program/[I]soffice...
[/I]
$ file /usr/lib/openoffice/program/soffice*
/usr/lib/openoffice/program/soffice:     POSIX shell script text executable
/usr/lib/openoffice/program/soffice.bin: ELF 32-bit LSB executable, Intel ...


$ /usr/lib/openoffice/program/soffice.bin  -h
OpenOffice.org 2.4  680m17(Build:9310)

...again, I'm just guessing, but if the disconnect starts at the menu-item / shortcut, then just trace your way from there all the way back to the executable.

(hey, original poster...!  if you find an answer, then please post it!!  "Never mind, I found an answer elsewhere." isn't terribly helpful to others who have the same problem... at least post a link to the  other thread.)

thanks,
-m

---

### Post by Midahed on 2008-08-02
Thanks for your detailed response but, following a bit more research, it looks like I'm dealing with an entirely separate problem that's caused by the version of xorg (7.3) that's part of the Ubuntu 8.04 Hardy distribution.

Googling for a while eventually led me [[COLOR="Blue"]here[/COLOR]](http://communities.vmware.com/thread/104635).

---

