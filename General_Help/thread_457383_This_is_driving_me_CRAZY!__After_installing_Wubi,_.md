---
title: "This is driving me CRAZY!  After installing Wubi, I boot STRAIGHT INTO WINDOWS!"
date: 2007-05-28
forum: General Help
---

### Post by bishoyhanna on 2007-05-28
There's no boot screen option!  I install Wubi, reboot, and it goes straight to XP!  There's no screen that allows me to load into Ubuntu!

I'm on a Dell laptop  (Inspiron e1505) and this is driving me nuts.  Can someone please help?  I can't find anything online about it.  

The installation went fine and said "restart  now."  I selected it, restarted, and nothing,  Right back into XP.  Tried reinstalling and the same thing happened.  I loaded Wubi onto my only hard drive.

---

### Post by ago on 2007-05-28
check c:\boot.ini if there is an entry for ubuntu

---

### Post by bishoyhanna on 2007-05-28
[operating systems]
c:\grldr="Ubuntu"
[boot loader]
timeout=15


That's what it says.  I'm assuming that's the correct entry.


Thanks for the quick reply, by the way.  I really appreciate it man.

(Please keep helping me so I can resolve this!)

---

### Post by bishoyhanna on 2007-05-28
Should I change the timeout value to something else?

---

### Post by ago on 2007-05-28
If there is no "windows" in there it means we edited the wrong  boot.ini

Do you have any other boot.ini laying around on other partitions?

---

### Post by bishoyhanna on 2007-05-28
The only other partition on my PC is "D:" which is a backup partition and is EMPTY.  Where else could a boot file be located?  And what could it be called?

---

### Post by ago on 2007-05-28
is there no "windows" inside your boot.ini?

You can use control panel > system > advanced > Startup and Recovery

---

### Post by bishoyhanna on 2007-05-28
> **ago said:**
> is there no "windows" inside your boot.ini?

You can use control panel > system > advanced > Startup and Recovery


I went there, and when I press 'edit' I see the following:


[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(4)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(4)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect

Hm...

Where could this file be located?  What should I put into it?  This isn't that boot.ini file that wubi created, which has nothing about windows in it.

---

### Post by bishoyhanna on 2007-05-28
It IS in D:!  When I look in D, there is nothing, but I can see that the file is in D because when I modify it and close it, it says the directory is in D.  I have view hidden files on but I still don't see anything.

What should I put into the file and then save it?

---

### Post by ago on 2007-05-28
append

c:\grldr="Ubuntu"

and set timeout to 10 or something. Then copy c:\grldr to d:\

---

### Post by rustybutt on 2007-05-28
> **bishoyhanna said:**
> There's no boot screen option!  I install Wubi, reboot, and it goes straight to XP!  There's no screen that allows me to load into Ubuntu!

I'm on a Dell laptop  (Inspiron e1505) and this is driving me nuts.  Can someone please help?  I can't find anything online about it.  

The installation went fine and said "restart  now."  I selected it, restarted, and nothing,  Right back into XP.  Tried reinstalling and the same thing happened.  I loaded Wubi onto my only hard drive.


I assume you're trying to dual boot?  I had this experience in setting up my IBM Thinkpad to dual boot.  This is not a simple process, but quite doable.

First you have to realize that your whole install right now is toast.  

Reboot your machine with the Ubuntu install CD, but do NOT install Ubuntu just yet.    If you're using the Ubuntu desktop install CD, open up a terminal window and do:

sudo bash

This will give you a root shell.  You want to manually partition your hard disk with fdisk.  Something like:

fdisk /dev/hda

You want to create 3 partitions at least.   The 1st partition will be your Windows partition.  The 2nd partition should be your swap partition and the 3rd partition is where you put Ubuntu.  

***IMPORTANT!!!***

***IMPORTANT!!!***

When you make the 1st partition, be sure to begin it at cylinder #1, not cylinder #0!  The reason for this is that when you later do your Ubuntu install, it wants to write out the boot block and /boot onto /dev/hda, which begins at partition #0, and will step on Windows badly.  If you really want to be paranoid, being partition #1 at cylinder 2 or 3.  Just don't begin it at partition 0!

Make sure you change the partition type for the first partition to be HPFS/NTFS, which is type ID 7.  While you're still in fdisk, after you've carved out the partitions you want, use the "t" option to identify partition #1 as ID 7.

If you plan to use vmware server, you might want to create more partitions to be used as drive space for your VM's, but that's a different subject.

Once you've made the changes to the partition mapping, you then reset the machine and boot off of your Windows CD.    Install Windows on parition #1, leaving all of the other partitions alone.

After you've finished with all of your Windows install stuff, patching, updating, yadda, yadda, then you're ready to install Ubuntu.

Instead of booting off the Ubuntu desktop install CD, you want to install off the Alternate Install CD. This is CRITICAL!   Install off of that CD and use the now defined partitions.   Partition #2 is your swap partition and partition #3 is your Ubuntu install partition.  If you use the Desktop CD, you'll wipe out everything and it will step on your Windows install as well.

Once you've install Ubuntu and reboot, grub will come up and give you a choice of what operating system to boot from, including Windows.

Have fun!

rustybutt

---

