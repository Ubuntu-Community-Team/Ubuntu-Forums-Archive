---
title: "Opening Root User?"
date: 2007-12-14
forum: General Help
---

### Post by teamalpha on 2007-12-14
So, I have an :mad:Acer:mad: laptop with Ubuntu 7.10 on it, and i found a way to use the pre-provided keyboard shortcut to increase the volume, but when I tried to change the file required to do this, it says I do not have permissions, and I must be root user. I change my root password, restart and log on, and it says you can not log on as root. Does anyone have a clue as to how to get into root user to change this file?

Thanks!:)

---

### Post by cmnorton on 2007-12-14
Whoever installed Ubuntu is considered the Administrator. So, if you installed it, use your password. If you did not install it, then you need to log in as that person and add yourself to the sudo list.
[http://ubuntuforums.org/showthread.php?t=162867](http://ubuntuforums.org/showthread.php?t=162867)

---

### Post by rouge568 on 2007-12-14
In the terminal, you can either type ```
 sudo gedit (FILE) 
```
or ```
su -s
``` which will let you use any command thereafter as root.
Hope this helps!
eidt: use your own password for the first one and the root password for the second. If it doesn't work, try filp-flopping them.

---

### Post by Joshua on 2007-12-14
I'm not sure how experienced you are, but here are several links that will explain some of the stuff that has been mentioned:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Using_gksu_vs._sudo]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#Using_gksu_vs._sudo")
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_switch_to_root_user_in_Console_mode]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_switch_to_root_user_in_Console_mode")
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_allow_more_sudoers]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_allow_more_sudoers")
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_change_files.2Ffolders_permissions]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_change_files.2Ffolders_permissions")

Probably the best method I've used for what I think you are describing is described at:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_open_files_as_root_user_via_right_click]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_open_files_as_root_user_via_right_click")

When I don't use that, I will sometimes do:
```
gksudo nautilus
```
That should open a new file browsing window where you can navigate and open files as the root user.

Edit: Oh yeah, it is also possible to enable the root login.  That is also described somewhere at the ubuntuguide.org website, but there are many other ways that will allow you to edit those files.  I've never felt it necessary to enable the root login, mostly because you can add the right-click option to open files as the root user.  It is very convenient once you have it set up.

---

### Post by teamalpha on 2007-12-14
Thanks all, but do I need Nautilus for this? i am not sure if I have Nautilus or Gnome, or does it make any difference?

---

### Post by PmDematagoda on 2007-12-14
Nautilus is the File Manager which is used on top of GNOME which is the Desktop Environment itself. So you have to use Nautilus:).

---

### Post by teamalpha on 2007-12-22
Ok, i am not sure if i have nautilus though, how can i check.
in my previous install, it showed nautilus at boot, but now, it just skips to desktop, does this mean i have no nautilus?

---

### Post by bodhi.zazen on 2007-12-22
> **teamalpha said:**
> Ok, i am not sure if i have nautilus though, how can i check.
in my previous install, it showed nautilus at boot, but now, it just skips to desktop, does this mean i have no nautilus?

You should use sudo at the command line.

To become root on the command line use 

sudo -i

NOT su

For graphical applications use gksu (kdesu fo rKDE)

so for nautilus :

```
gksu nautilus
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

	gksudo : [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

