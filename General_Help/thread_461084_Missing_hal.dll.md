---
title: "Missing hal.dll"
date: 2007-06-01
forum: General Help
---

### Post by cpatgs on 2007-06-01
After installing WUBI and restarting my computer I cannot load Ubuntu because of the grub problem that has been discussed already and I was going to fix until I tried to load in windows and I got the message:

<windows root>/system32/hal.dll The file is missing.  Install a copy of the file.

Anyone have any suggestions on what to do.  Some websites say it is because of the dual boot and that I should delete it but I don't know how to get rid of the Ubuntu boot drive. 

Another site said to run my XP disk and install the hal.dll file and I haven't tried that yet because I am at work but I thought I would ask and get input before I try anything.

---

### Post by blazercist on 2007-06-01
yea it has NOTHIN to do with a dual boot, I ran into these problems with two machines at my old job where they ONLY used windows and my little brothers PC came up with the same problem on an only windows box... its hal.dll got corrupted, its VERY UNLIKELY although possible that when you where repartitioning the file was copied to another sector to make room and got corrupted in the process, this is usually due to faulty/old hardware... anyway, yes you need to get a copy of hal.dll from your winxp cd and copy it over, there are two ways... either use the windows CD to boot into recovery mode which drops u to a DOS console where you can copy the file over OR you could use a working linux partition with NTFS-3G to copy it over from the CD.  It might just be that simple... I did it a while ago so I don't remember if there were complications...

---

### Post by cpatgs on 2007-06-01
Thanks for the quick response.  When I get home for lunch I will install the hal.dll from my XP CD and see if that works.  

Should I reinstall Wubi or leave it alone and fix the GRLDR problem with the latest fix of the grub file?

---

### Post by cpatgs on 2007-06-01
Ok so I just tried installing it from my XP CD and it says that access is denied.  I followed the steps and typed in 
expand d:\i386\hal.dl_ c:\windows\system32\hal.dll and after that it told me access denied.  If I cannot access the file how am I suppose to install it?

---

### Post by minhmeoke on 2007-06-02
You can use a Knoppix LiveCD with Captive NTFS to access NTFS, the Windows filesystem. Here is the howto: [http://www.shockfamily.net/cedric/knoppix/]("http://www.shockfamily.net/cedric/knoppix/").

---

### Post by flint_ on 2008-04-02
Here is the deal with this bug...

What has happened as you installed Ubuntu, is that the actual partition location of the windows boot disk has moved.  Thus the windows boot loader cannot find hal.dll on the right hard drive partition.

One cool thing to think about here is that grub, the Linux boot loader is working and knows where the windows boot partition is on the disk.

So the way to fix this problem is to boot up into Linux, 7.10 or better and this product automounts the various windows partitions right on the desktop.

Open a terminal and you will find these various hard drive partitions in the directory /media.  One of these will have a lot of "window dressing", say for instance, a directory called Windows or WINDOWS (depends :^).

In the root of this directory you will find a file called boot.ini.

THE VERY FIRST THING TO DO IS TO BACK THIS BAD BOY UP!!!
 ...and here's how:

Lets say you are at a command prompt on the /media/sda4 partition.

Type:
mkdir obe
cp boot.ini obe/orig.boot.ini

now edit the boot.ini.  While we can get religious here try this approach:

gedit boot.ini &

Boot.ini will be in a gui type editor.
To guide you hit <enter> get a prompt and type the following:

gparted &

This will bring up a guide in the GUI.

Finally type the following to see what you are doing...
Hit <enter> get a prompt and type the following:

less /boot/grub/menu.1st

Go to the bottom of this file <shift> G, and see where Linux thinks the boot partition is.


This user had 1 hard drive, partitioned into C and D drives.  His BOOT.INI file looked like this: (the erroneous lines are in "blue")

[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

The 2 in the erroneous lines, above, points to the 2nd partition on the first physical hard disk.  Since this user only had 2 partitions, this value was correct.  We added partitions in between, thus we need to change the value to 3, in both lines, this will allow Windows XP to boot.

The corrected BOOT.INI looked like this:

[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

This was stolen from:
[http://www.kellys-korner-xp.com/xp_haldll_missing.htm](http://www.kellys-korner-xp.com/xp_haldll_missing.htm)
with minor modification. This is a great read, this site deserves support.

Save your gui's and restart.  Note you fool only with boot.ini leave menu.1st alone for now.

Regards,

Flint

---

### Post by subutai1248 on 2008-09-09
Hello,

I'm writing to thank flint_ for his advice. 

I recently installed Ubuntu on my XP box, with the intent of dual booting. For reasons that are not really relevant, my system has 1 disk, with some empty space, data on the "C" drive, and XP on the "E" drive. After installing Ubuntu I too received a "<windows root>/system32/hal.dll The file is missing. Install a copy of the file." message, and was unable to boot into XP. Following flint_'s post, I edited my boot.ini to reflect the fact that XP is now the 3rd partition. 

Thank you kindly flint_.

---

### Post by scbookz on 2009-02-14
this happened to me as well i am working on it now. just to  help with google search i will explain my trouble. i installed a new partition and the system32\hal.dll file was moved as flint said. this is  exactly what seems to have  happened. i hope i can follow his advice here  and find all the directories needed. it explains everything just right. my question is can i get the dll file from  my xp cd and  just copy from there? i will try and see what happens from  a mounted cd drive maybe

---

### Post by scbookz on 2009-02-14
ok it is not working i have 2 hard disk
i use nano to alter my boot file i have tried
0 0 0 2
0 0 0 3
0 1 1 1
not working

---

### Post by mgogonobi on 2009-05-14
> **flint_ said:**
> Here is the deal with this bug...

What has happened as you installed Ubuntu, is that the actual partition location of the windows boot disk has moved.  Thus the windows boot loader cannot find hal.dll on the right hard drive partition.

One cool thing to think about here is that grub, the Linux boot loader is working and knows where the windows boot partition is on the disk.

So the way to fix this problem is to boot up into Linux, 7.10 or better and this product automounts the various windows partitions right on the desktop.

Open a terminal and you will find these various hard drive partitions in the directory /media.  One of these will have a lot of "window dressing", say for instance, a directory called Windows or WINDOWS (depends :^).

In the root of this directory you will find a file called boot.ini.

THE VERY FIRST THING TO DO IS TO BACK THIS BAD BOY UP!!!
 ...and here's how:

Lets say you are at a command prompt on the /media/sda4 partition.

Type:
mkdir obe
cp boot.ini obe/orig.boot.ini

now edit the boot.ini.  While we can get religious here try this approach:

gedit boot.ini &

Boot.ini will be in a gui type editor.
To guide you hit <enter> get a prompt and type the following:

gparted &

This will bring up a guide in the GUI.

Finally type the following to see what you are doing...
Hit <enter> get a prompt and type the following:

less /boot/grub/menu.1st

Go to the bottom of this file <shift> G, and see where Linux thinks the boot partition is.

This user had 1 hard drive, partitioned into C and D drives.  His BOOT.INI file looked like this: (the erroneous lines are in "blue")

[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

The 2 in the erroneous lines, above, points to the 2nd partition on the first physical hard disk.  Since this user only had 2 partitions, this value was correct.  We added partitions in between, thus we need to change the value to 3, in both lines, this will allow Windows XP to boot.

The corrected BOOT.INI looked like this:

[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /fastdetect...
Save your gui's and restart.  Note you fool only with boot.ini leave menu.1st alone for now.


Okay, thanks to Flint I have hope, and the only problem is, when I list contents of /media, the Windows partition is not visible. Any ideas, anybody?

---

### Post by loweehahn on 2009-05-29
I've a similar problem too but I'm too noob to understand all the instructions. Can anyone simplify for me and provide me step by step tutorial? I would appreciate this very much because I don't want to reinstall ubuntu again and start everything from the beginning again.

---

### Post by mikepig on 2011-10-11
> **flint_ said:**
> Here is the deal with this bug...

What has happened as you installed Ubuntu, is that the actual partition location of the windows boot disk has moved.  Thus the windows boot loader cannot find hal.dll on the right hard drive partition.

One cool thing to think about here is that grub, the Linux boot loader is working and knows where the windows boot partition is on the disk.

So the way to fix this problem is to boot up into Linux, 7.10 or better and this product automounts the various windows partitions right on the desktop.

Open a terminal and you will find these various hard drive partitions in the directory /media.  One of these will have a lot of "window dressing", say for instance, a directory called Windows or WINDOWS (depends :^).

In the root of this directory you will find a file called boot.ini.

THE VERY FIRST THING TO DO IS TO BACK THIS BAD BOY UP!!!
 ...and here's how:

Lets say you are at a command prompt on the /media/sda4 partition.

Type:
mkdir obe
cp boot.ini obe/orig.boot.ini

now edit the boot.ini.  While we can get religious here try this approach:

gedit boot.ini &

Boot.ini will be in a gui type editor.
To guide you hit <enter> get a prompt and type the following:

gparted &

This will bring up a guide in the GUI.

Finally type the following to see what you are doing...
Hit <enter> get a prompt and type the following:

less /boot/grub/menu.1st

Go to the bottom of this file <shift> G, and see where Linux thinks the boot partition is.


This user had 1 hard drive, partitioned into C and D drives.  His BOOT.INI file looked like this: (the erroneous lines are in "blue")

[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

The 2 in the erroneous lines, above, points to the 2nd partition on the first physical hard disk.  Since this user only had 2 partitions, this value was correct.  We added partitions in between, thus we need to change the value to 3, in both lines, this will allow Windows XP to boot.

The corrected BOOT.INI looked like this:

[boot loader]
timeout=1
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

This was stolen from:
[http://www.kellys-korner-xp.com/xp_haldll_missing.htm](http://www.kellys-korner-xp.com/xp_haldll_missing.htm)
with minor modification. This is a great read, this site deserves support.

Save your gui's and restart.  Note you fool only with boot.ini leave menu.1st alone for now.

Regards,

Flint

@flint_

Do you know how to do this using the newest version of Ubuntu with GRUB2?

I am having the same problem but cannot solve like this because I am running 11.04 which no longer uses menu.1st and instead uses grub.cfg??

thanks

---

### Post by sffvba[e0rt on 2011-10-11
> **mikepig said:**
> @flint_

Do you know how to do this using the newest version of Ubuntu with GRUB2?

I am having the same problem but cannot solve like this because I am running 11.04 which no longer uses menu.1st and instead uses grub.cfg??

thanks

Thread closed. Chances of the original posters responding in this fashion after this long is very unlikely. 

I would suggest starting a new thread giving as much info as possible.


404

---

