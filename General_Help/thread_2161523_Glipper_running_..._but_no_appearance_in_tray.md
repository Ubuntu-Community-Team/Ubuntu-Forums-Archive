---
title: "Glipper running ... but no appearance in tray"
date: 2013-07-11
forum: General Help
---

### Post by xigen on 2013-07-11
I installed Glipper, it appears to be running.  Unfortunately I do not see Glipper in my applets. 

I hit (super) + alt + rightclick   to bring up the menu to add applets and ... no Glipper in the applets selection.

Ubuntu 12.04  Gnome Classic

...............
meow@meowbaby:~$ ps aux | grep glipper
meow      2134  0.0  0.6 151876 17824 ?        Sl   22:44   0:00 /usr/bin/python /usr/bin/glipper
meow      2514  0.0  0.0   4384   808 pts/1    S+   22:47   0:00 grep --color=auto glipper

meow@meowbaby:~$ uname -a; lsb_release -a; apt-cache policy glipper
Linux meowbaby 3.3.6-030306-generic #201205121335 SMP Sat May 12 17:43:01 UTC 2012 i686 athlon i386 GNU/Linux
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.2 LTS
Release:	12.04
Codename:	precise
glipper:
  Installed: 2.3-1ubuntu0.1
  Candidate: 2.3-1ubuntu0.1
  Version table:
 *** 2.3-1ubuntu0.1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/universe i386 Packages
        100 /var/lib/dpkg/status
     2.3-1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/universe i386 Packages

meow@meowbaby:~$

---

### Post by ajgreeny on 2013-07-11
I can't help particularly with glipper, except to say that when I used it a long time ago (years, not months) it crashed pretty regularly so I started using parcellite instead, which seemed to be much more stable and useful.  It is in the standard repos.  I have not tried glipper since that time so can't comment on its stability now.

I did try gnome classic on 12.04 for a fairly long time, and used parcellite without problems, so it should work OK for you as well.

---

### Post by xigen on 2013-07-11
[ATTACH=CONFIG]244606[/ATTACH]Ug...

I just tried parcelite ... it did not launch.  I put an applet in the upper right hand screen boarder (see screenshot) and when I click the applet I get a brief flash and then no application. 

Then I tried Clipit ... it also did not launch

Suggestions?

---

### Post by xigen on 2013-07-11
Here is the output when I try clipit from the command line

meow@meowbaby:~$ clipit&
[1] 3592
meow@meowbaby:~$ 
** (clipit:3592): WARNING **: Binding '<Ctrl><Alt>H' failed!


** (clipit:3592): WARNING **: Binding '<Ctrl><Alt>A' failed!


** (clipit:3592): WARNING **: Binding '<Ctrl><Alt>P' failed!


** (clipit:3592): WARNING **: Binding '<Ctrl><Alt>F' failed!

---

### Post by xigen on 2013-07-12
I checked to see if clipper is running somehow and getting my input.  The clipit history file has plenty of stuff.  Unfortunately, I am having a difficult time getting clipper into the panel on my Ubuntu 12.04 / Gnome classic instillation. 

meow@meowbaby:~$ cat ~/.local/share/clipit/history

0[http://www.youtube.com/watch?v=CFf7dlewJus&hl=eny](http://www.youtube.com/watch?v=CFf7dlewJus&hl=eny) &#65533;:	
The 25 Most Failed States On Earth

---

### Post by Toz on 2013-07-12
*Removed duplicate post.*

---

