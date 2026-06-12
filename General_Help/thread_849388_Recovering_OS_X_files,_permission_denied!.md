---
title: "Recovering OS X files, permission denied!"
date: 2008-07-04
forum: General Help
---

### Post by Wafflesrevenge on 2008-07-04
So to start this off I did find a thread in the archives that describe my problem, read it [here]("http://ubuntuforums.org/showthread.php?t=293306").

I have mounted my OS X harddrive, I can get to the directory I need to access but am having 'permission denied' problems. 

Here's what I can figure out, all of these files are written for access by user '501' but there is no user '501'...should I create a new user and call it 501? (useradd or adduser?) 

Also, at some point won't I need to input my OS X password or are the files not encrypted?

Thanks in advance for the help!

---

### Post by Habbit on 2008-07-04
501 is the user ID of your user under Mac OS X. Since your Ubuntu system does not have an user with UID=501, it shows you the UID instead of the name. You have several options:[list=1][*]As root, change the owner of the whole tree to you, so that you are able to access the files. This is not recommended if you want to put your Mac partition to work again or if you want to preserve ownership/permissions information, as they will be botched. If you want to follow this path, do "sudo chown youLinuxUser: -R /media/MacOsXPartition"[*]Create an user with UID=501 in your system. Might cause some trouble later because UIDs < 1000 are by convention reserved to system (daemon) accounts on Debian/Ubuntu. If you want to go this way, do "sudo adduser --uid 501 newUserName".[/list]

---

### Post by Wafflesrevenge on 2008-07-04
I'm trying to go with option two as I can't restore OS X back to leopard...I enter that command but get an error

sudo: uid 999 does not exist in the passwd file!

Could this error be cause by running off a live CD?

---

### Post by Wafflesrevenge on 2008-07-04
tried chown'ing the directory, no luck...I'm starting to think the problem is that I'm running a live cd

---

### Post by aysiu on 2008-07-04
Press Alt-F2 and type ```
gksudo nautilus
``` and you should be able to access the files. You can read them and copy them, but you probably can't change them, since Linux cannot reliably write to HFS+ (Mac's filesystem).

---

### Post by Wafflesrevenge on 2008-07-04
gksudo nautilus did it...now here's the $20 question, why did that work?

---

### Post by lukjad on 2008-07-04
Because you became root, the overall owner of all the files. If you need to be a Captain to order around a Lieutenant, a General certainly can. ;)
Now, where's my $20? Canadian Funds please!

---

