---
title: "[SOLVED] How can I stop ubuntu automatically mounting a drive?"
date: 2007-10-04
forum: General Help
---

### Post by dornik on 2007-10-04
Hi all

Linux noob here - so lets get that out of the way.

I have ubuntu installed on primary master. Also have another hard disk as primary slave that has 3 partitions on it that are formatted to Fat32. 

Every time i boot ubuntu, the empty FAT32 partitions of the primary slave show up as mounted drives (or as mountable drives if i previously unmounted them) when I browse "Places -> Computer". 

I do NOT want to see the partitions of the primary slave when I boot into ubuntu. How can i prevent ubuntu from displaying them? Isnt there any way that I can sort of blacklist them from ever appearing within ubuntu?

Also, is it possible for me to allow ubutu to "see" one of the partitions on the primary slave but not the other two by mounting it selectively? 

Any help greatly appreciated.
Thanks

---

### Post by MarkieB on 2007-10-04
delete the appropriate entry in /etc/fstab

back it up first:)

---

### Post by zero-9376 on 2007-10-04
if you delete the fstab entries the drives will not be mounted at boot time but im pretty sure you will still be able to see them in places-computer because gnome/the system knows that the partitions exist, you will however need to enter your sudo password if you want to mount them

---

### Post by dornik on 2007-10-04
@MarkieB

There are no entries in /etc/fstab related to that drive (primary slave). The only entries in it refer to /hda1 (primary master).

@zero-9376
> 
if you delete the fstab entries the drives will not be mounted at boot time but im pretty sure you will still be able to see them in places-computer because gnome/the system knows that the partitions exist, you will however need to enter your sudo password if you want to mount them

 
You summed up my problem EXACTLY Zero. Isnt there any way to blacklist the partitions so that they dont appear? Surely there has to be a way to do this?

I really need to do this. Thanks in advance.

---

### Post by zero-9376 on 2007-10-04
alright i came up with a solution and it appears to work without damaging anything:
you need to stop your system seeing the partition/s so you simply delete them during the boot process

sudo nano /etc/rc2.d/S10xserver-xorg-input-wacom or any other low Snumber file
added rm /dev/sdc2 to the top of the file
rebooted and tada the device isnt there for gnome (vfs i think) to see and so it doesnt show up in nautilus

i tried just removing it through gnome-terminal first but the drive was still showing up in nautilus after the dev entry was deleted, although it was unmountable because of this
so i put it in the boot script and it didn't show up when i rebooted
just to make sure i didnt damage anything i removed the line from the script and the drive showed up, was mountable and contained my data

there may be better ways to do this but i dont know of them...it works though for what you want

disclaimer - the partition i rm'ed was my old windows install from when this drive was in my old PC so i really didnt care if i lost it

---

### Post by dornik on 2007-10-04
Hi zero-9376
Thanks for replying but I could not make head or tail of how you solved the problem as I am a first time linux user and what you wrote went way over my head. 

Could you try and explain it a little more in detail?

Thanks...

---

### Post by tgalati4 on 2007-10-04
Perhaps a better way than removing the device during boot is to add the following lines in your .bash_profile:

In a terminal:

>gedit .bash_profile

Add:

sudo umount /dev/sdc2
sudo umount /dev/sdc3

---

### Post by zero-9376 on 2007-10-04
no worries

ok when the ubuntu system boots up it starts a bunch or programs/services which are associated with different runlevels, the scripts that start those services are in the folders /etc/rcX.d/ where X is a number. In ubuntu the default runlevel is 2 so the scripts in the /etc/rc2.d/ folder are the ones that get are executed when ubuntu starts and shuts down.

if you have a look in there, there are K(number)servicename and S(number)servicename. the k and s are scripts that are called during shutdown and startup respectively, the number is used to determine the order in which the scripts are started. 

in linux everything is represented by files, your partitions are probably /dev/hdaX or /dev/hdbX (mine are sd instead of hd because they are sata drives). if you dont want the system to be able to see or mount the partition all you have to do is delete the file that corresponds to the partition so if one of your fat32 partitions is /dev/hdb1 you want to delete that file. you want to do this before gnome starts up so you put the 

rm /dev/sdb1

in one of the /etc/rc2.d/S____ files with a low number, as i said i used S10 that way the device will be deleted before the system can see it and it wont be accessible.

if you change your mind you can just remove the line from the file and reboot and it should work again. again im no expert but it worked for me


EDIT:
So step by step,
if the partition you want to hide is hdb1

open terminal
sudo gedit /etc/rc2.d/S10xserver-xorg-input-wacom
change
```

#!/bin/bash

. /lib/lsb/init-functions

```
to 
```

#!/bin/bash
rm /dev/hdb1
. /lib/lsb/init-functions

```
save the file and close the editor and terminal
reboot your system

---

### Post by zero-9376 on 2007-10-04
> **tgalati4 said:**
> Perhaps a better way than removing the device during boot is to add the following lines in your .bash_profile:

In a terminal:

>gedit .bash_profile

Add:

sudo umount /dev/sdc2
sudo umount /dev/sdc3

i dont think this will achieve what the OP is trying to do, the partitions will still be visible in nautilus
as i said the method i proposed didn't damage the file system but there may be an easier/more recommended way of doing it, maybe instead of deleting the /dev/sdxx file the permissions could be changed so that only root can even read the file, that might stop gnome-vfs or nautilus being able to see the drive although im guessing gnome-vfs may have root permissions, which is why i just deleted the file

---

### Post by dornik on 2007-10-04
@zero-9376

This is crystal clear now zero-9376!

I _really appreciate_ your taking out the time to spoon feed me on finding a solution to this issue. 

Will give it a shot and get back to you on whether it worked - or not. :)

Cheers


@tgalati4

Hi, thanks for that but it wont solve my problem as the drives still appear in Nautilus albeit as unmounted. I dont want them to appear at all.

Cheers

---

### Post by bodhi.zazen on 2007-10-04
**Please mark this thread as solved, it saves the time of many volunteers looking to help ...**

FYI, I have always achieved the same thing by mounting drives in /mnt

they then do not appear in nautilus

To keep them from being mounted at boot, add noauto to the optinos in fstab.

Like this:

mount point /mnt/data

fstab:
> /dev/sda10 /mnt/data  vfat  **noauto,users**,uid=1000,gid=100,umask=007,<other_options> 0 2

The noauto option = no mount at boot
users = allow users (rather then just root) to mount

uid/gid/umask sets ownership and permissions at the time of mount.

---

### Post by dornik on 2007-10-04
@zero-9376

Thank you thank you thank you!!! It worked like a charm!!!  :)

This is EXACTLY what I wanted and its a piece of cake to do as well. If I had not been able to do this, I may well have had to abandon Ubuntu which would have been very unfortunate as over the past 2 weeks I have grown to actually prefer it over Windows for almost everything apart from one area - gaming.  

You really are a life saver zero-9376! :) 

Cheers


@bodhi.zazen

Is there any advantage to your technique (eg. the possibility of being able to hide/show partitions on the fly without having to reboot)? ATM, the only minor issue in zero-9376's solution is that it requires a reboot everytime I want to show/hide partitions.  

If not, I thank you for your suggestion but I would prefer to stick to the solution offered by Zero-9376. 

Cheers

---

### Post by zero-9376 on 2007-10-04
whenever i mounted partitions in /mnt they would still show up in natilus under computer, i think i was trying to stop certain partitions showing up on the desktop, but the entries in computer:/// would have the volume size and the full path to the drive which was even more annoying, haven't tried it in fiesty though.

also if anyone knows how to make nautilus stop showing 296GB volume when in computer:/// i would appreciate it, I have two drives this size and im getting two more, its just annoying having the size there

---

### Post by bodhi.zazen on 2007-10-04
> **dornik said:**
> @bodhi.zazen

Is there any advantage to your technique (eg. the possibility of being able to hide/show partitions on the fly without having to reboot)? ATM, the only minor issue in zero-9376's solution is that it requires a reboot everytime I want to show/hide partitions.  

If not, I thank you for your suggestion but I would prefer to stick to the solution offered by Zero-9376. 

Cheers

Advantage ? up to you.

1. I configure the partitions this way at the time of install, so there is no post install configuration, with the possible exception of configuring fstab if you need to modify the default options.

2. If you use fstab you do not need to re-boot, just re-mount your partitions if needed.

3. If you already have a partition in Computer, I do not think my solution will help much.

---

### Post by girard on 2007-11-27
hi... i hope you guys are still checking out this post. i have the same question, but for a different purpose though. the forums is quite big so chose not to start my own thread so they don't crowd the forums (more)

i have a separate partition for my personal data. i have two accounts in ubuntu. the one created during set up (admin) and an unprivileged user. i would like to stop my data partition from mounting only when users login, but i still want to preserve it's mounting when i log in as admin, since i always log in using the admin account when i use the pc. how do i do it?

can i do it with pysdm as mentioned in [this]("http://ubuntuforums.org/showthread.php?t=608348&highlight=stop+partitions+from+mounting") post

---

### Post by zero-9376 on 2007-11-27
if you only want the drive accessible by you what about mounting it inside your home directory with permissions such that only you can read and write?

---

