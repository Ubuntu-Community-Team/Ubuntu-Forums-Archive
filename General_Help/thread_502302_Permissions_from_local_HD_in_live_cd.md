---
title: "Permissions from local HD in live cd"
date: 2007-07-16
forum: General Help
---

### Post by xadloki on 2007-07-16
My Ubuntu installation got messed up after I physically removed my second HD, what happens is th machine boots but after GRUB it goes to the terminal and doesn't load the GUI, it complains something about fdisk check... fail... blah blah... 
I try to edit the fstab but it seems no commands work and always complains "not installed" exapmle:
apt is not installed, you can install it using apt-get install.
Well I'm tired of messing around with no success and I'll take this chance to install Xubuntu to see if it's better with my hardware. But I need to get my bookmarks from my home partition in /home/.mozilla, I launched the Kubuntu live cd and mounted the drives and using Konqueror I found the correct folder only I don't have permission to read it. I then tried going through the terminal and same thing happens, no permission to read... (i tried sudo, gksudo... none works) how can I get the permission to see this folder?
Also I suppose doing a reinstall and not formatting the Home partition would not change the fac that I have no permission to view that folder?
please help.

---

### Post by splintercellguy on 2007-07-16
Perhaps you should edit your fstab in recovery mode.

---

### Post by xadloki on 2007-07-16
oops nevermind, I just figured it out, I used sudo chown -R ubuntu:ubuntu /media/hd1

---

### Post by aysiu on 2007-07-16
Alt-F2 ```
kdesu konqueror
``` should give you permission.

---

### Post by xadloki on 2007-07-16
i tried recovery mode but it does the same thing, goes to terminal and complains that nothing is installed

---

### Post by aysiu on 2007-07-16
> **xadloki said:**
> oops nevermind, I just figured it out, I used sudo chown -R ubuntu:ubuntu /media/hd1
Oh, no! That's going to screw things up. The system files are supposed to belong to root in order for them to function properly...

I don't think there's a repair ownership function, though.

---

### Post by splintercellguy on 2007-07-16
You could try using the LiveCD to edit fstab.

---

### Post by xadloki on 2007-07-16
i tried to edit the fstab and I can do it but I don't really know what is wrong, I can't put the old drive back since it's erased. I've only been using linux exclusively now for about 2 months and I don't really know how to deal with problems.

---

### Post by xadloki on 2007-07-16
The only guess I can make is that the boot flag was changed after I removed the drive, I tried using gparted in the live cd to flag it back but didn't affect anything...

---

