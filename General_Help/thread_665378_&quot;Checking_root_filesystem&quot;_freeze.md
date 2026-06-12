---
title: "&quot;Checking root filesystem&quot; freeze"
date: 2008-01-12
forum: General Help
---

### Post by Shkristensen on 2008-01-12
After using Ubuntu for only a few days my system has started freezing during boot. 
When the stall happens it is always at almost the same percentage: 71-something percent (it can be 71.1 or 71.2...).  It looks like this:
[IMG]http://lh6.google.com/SHkristensen/R4i8uRmw9EI/AAAAAAAABJA/Qq-vqlwmqKE/DSCF1075.JPG?imgmax=912[/IMG]

The same thing happens whether I boot to the graphical system or in text-mode.  

I found the bug: [https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/124773](https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/124773)
but i can't use the help there, since I dont have a live CD and I can't disconnects the harddisk since it is internal in the laptop. 

If anybody has an idea as to what I can do from grub I would be delighted.

---

### Post by lgambett on 2008-01-12
Start the system in recovery mode, then edit /etc/fstab, ie from the terminal input
sudo nano /etc/fstab.
You will find one or more rows like that;
UID=506cf0c3-c464-4dc7-accb-82478aa2abe7 /home ext3 defaults 0 1
change the 1 at the end with 0. This will disable the fsck check at startup.
Obviously is only a temporary workaround !

---

### Post by Shkristensen on 2008-01-12
Thanks for the fast respond, but one of my problems is that I can't boot recovery mode either, since that also includes mounting the drive in question. 

Is there a way of doing something similar trough GRUB?

---

### Post by Shkristensen on 2008-01-14
Solved it using the fix suggested above, but through windows!!! (Using [Ext2IFS]("http://fs-driver.org/")) 
I have never fixed anything through Windows before, but I'm glad I didn't remove it!!

---

### Post by lgambett on 2008-01-16
That was a good solution ! You could have also booted your machine with a Live CD (Knoppix is perfect).

---

