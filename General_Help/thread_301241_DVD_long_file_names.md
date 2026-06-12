---
title: "DVD long file names"
date: 2006-11-16
forum: General Help
---

### Post by complexgeek on 2006-11-16
Hi.
I just installed Xubuntu (well, it started as Kubuntu but I installed the xubuntu-desktop package and switched the default window manager), and have run into a confusing problem. If I try to access files on a DVD-R, the filenames are all cut off at 25 characters, plus a "." and 3 letter extension, as well as having the case stripped. For example, "Stargate SG1 9x12 - Collateral Damage.avi" is displayed as "stargate sg1 - collat.avi". This happens both in a terminal window, and a file manager window.

The line for the DVD drive in my fstab is:
/dev/hdc   /media/cdrom0   udf,iso9660 user,noauto   0   0

Can anyone help?

---

### Post by complexgeek on 2006-11-16
OK, it seems to only be happening with DVD-Rs burned from Mac OS X, not discs burned in Windows. So could it be something related to the fle system on the discs? The same discs displayed filenames correctly under Windows.

---

### Post by computx on 2006-11-17
Yes it could be related to the file system used. 
see the link below for limitations of different cd/dvd file systems.
[http://disktype.sourceforge.net/doc/ch03s11.html](http://disktype.sourceforge.net/doc/ch03s11.html)

---

### Post by Pausanias on 2007-07-14
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/44233](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/44233) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				There is a workaround for the problem. 

```

sudo gedit /etc/fstab

```

Find the line that contains the words ```
udf,iso9660
``` Delete that phrase and replace with ```
auto
```. Then reboot

This bug has been around for over a year, and is described in the launchbad bug report above.

---

