---
title: "Shell Scripts in linux"
date: 2008-01-27
forum: General Help
---

### Post by TBOL3 on 2008-01-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/openldap2.2/+bug/120834](https://bugs.launchpad.net/ubuntu/+source/openldap2.2/+bug/120834) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have a GM965/GL960 graphics card.  And it has a few problems in ubuntu  When I start up blender, it likes to crash.  I found the bug for this on launchpad.  It is a simple change to my Xorg.conf file.  After making the change, blender worked fine.  However, none of my 3d games now work.  But i can switch between the two xorg.conf files and restart X to get what I want.  The only problem is that this takes time.  i want to double click on an icon, type in my pasword, logout-login again.  And use the file.  So I'm thinking a shell script would be good for this (actually I'm thinking I would need two, but one might work).  I've done some scripting in windows, but nothing in ubuntu.  So could any of you help me?  Do I just type in the commands in a .sh?

Thank you.

---

### Post by TBOL3 on 2008-01-27
Well, I think I have them, but I would really like to get them checked before I use them.

To switch to blender mode:
cd /etc/X11
sudo mv xorg.conf xorg.conf.backup
sudo mv xorg.conf.backup2 xorg.conf

And to switch out of blender mode:
cd /etc/X11
sudo mv xorg.conf xorg.conf.backup2
sudo mv xorg.conf.backup xorg.conf

---

### Post by p_quarles on 2008-01-27
The syntax for shell scripts is pretty simple. The first line needs to be something like this:
```
#! /bin/bash
```
You can replace "bash" with whichever shell you need, but that will be fine for this one.

Then, write whatever commands you want the script to run in successive lines. E.g:
```
mv /etc/X11/xorg.conf /etc/X11/xorg.alt2
mv /etc/X11/xorg.alt1 /etc/X11/xorg.conf
/etc/init.d/gdm restart
```
Just be careful, of course, when automating the manipulation of xorg.conf!

---

### Post by TBOL3 on 2008-01-27
Thank you.

So what does #! bin/bach mean?

---

### Post by p_quarles on 2008-01-27
It's #! /bin/bash, and it's the path the shell that you want to use to execute the commands that follow.

---

