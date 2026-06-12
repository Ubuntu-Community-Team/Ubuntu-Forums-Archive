---
title: "Error during boot"
date: 2006-10-15
forum: General Help
---

### Post by sylint on 2006-10-15
I've searched these forums and haven't found a solution to the problem. If there is already a similar or the same problem then sorry for reposting.

So basically when i start up my computer it does the usual checks on the splash screen but then comes up with this..

```

*Checking root file system...
/dev/hda1 contains a file system with errors, check forced.
Error reading block 163909 (Attempt to read block from filesytem resulted in sort read) while doing inode scan.

/dev/hda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
     (i.e., without -a or -p options)

*An automatic file system check of the root filesystem failed.
*A manual fsck must be performed, then the system rebooted.
*This fsck can be performed in maintenance mode.
*Please note that the root filesystem is currently mounted read-only.
*The fsck should only be performed while the root filesystem is
*mounted read-only. However, the command to remount it read-write
*is:
*   # mount -n -o remount, rw /
(or type Contorl-D to continue): eenance shell, press CONTROL-D

```

So thats what comes up, if anyone can help out thanks in advance.

---

### Post by wuhaa on 2006-10-15
Hi,

Try this:

press CONTROL-D to enter maintenance mode

You may be asked to enter the super user password.

Then do a file system check by entering these commands one at a time
(if system is installed on /)
```

umount /     [COLOR="SeaGreen"]<--- to un-mount the file system[/COLOR]
fsck -y /    [COLOR="SeaGreen"]<--- to do a file system check[/COLOR]
exit         [COLOR="SeaGreen"]<--- to exit when everyting is done![/COLOR]
```

The system should reboot without any issue

---

### Post by sylint on 2006-10-15
Hey thanks alot, it rebooted fine.

During the fsck -y process it came up with I/0 errors. But any idea what or why it didnt start in the first place?

---

### Post by wuhaa on 2006-10-15
As far as I know, those errors can be caused by bad sectors on hard disk surface.

Sometimes they come up when the system is forcefully shut down (like a hard reboot or power loss).

---

### Post by ndeertrack on 2007-05-08
> **wuhaa said:**
> Hi,

Try this:

press CONTROL-D to enter maintenance mode

You may be asked to enter the super user password.

Then do a file system check by entering these commands one at a time
(if system is installed on /)
```

umount /     [COLOR="SeaGreen"]<--- to un-mount the file system[/COLOR]
fsck -y /    [COLOR="SeaGreen"]<--- to do a file system check[/COLOR]
exit         [COLOR="SeaGreen"]<--- to exit when everyting is done![/COLOR]
```

The system should reboot without any issue

I am having this exact problem with ubuntu.

What is meant by, "if system is installed on /?"  What should I be dismounting?  hda1?  I'm a linux super noob and I just want my computer to run again :(.  Thanks for any help.

---

### Post by ndeertrack on 2007-05-09
Well shucks!  I figured it out with the advice already given!  Thanks.

---

### Post by edoardotosca on 2007-06-14
I had the same problem just today.
Fortunately i have resolved the problem quickly, reading the alert message printed.

Anyway i have a question.
ubuntu is normally installed with a single user that can get superuser privileges using SUDO.

In this case, you have to put the root password.. but if you have not a superuser  with his own password??

Have ideas?

PS. Firstly i've tried with my usual password but i could not login..

thanks to everybody!

---

### Post by berkayonen on 2007-09-07
> **wuhaa said:**
> Hi,

Try this:

press CONTROL-D to enter maintenance mode

You may be asked to enter the super user password.

Then do a file system check by entering these commands one at a time
(if system is installed on /)
```

umount /     [COLOR="SeaGreen"]<--- to un-mount the file system[/COLOR]
fsck -y /    [COLOR="SeaGreen"]<--- to do a file system check[/COLOR]
exit         [COLOR="SeaGreen"]<--- to exit when everyting is done![/COLOR]
```

The system should reboot without any issue



press CONTROL-D to enter maintenance mode


where can i press ctrl+d at the os choose screen or another place

---

