---
title: "/home partitioning failed"
date: 2007-09-20
forum: General Help
---

### Post by maaylix on 2007-09-20
So I followed [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome) guide to make a /home partition in my second hard drive

I followed all the steps rebooted and to my amazement it worked! Even though I had aperantly lost all my configurations as the desktop had the default panels and wallpaper of a fresh install, but home was mounted on my second hard drive, all apps were working, everything was fine UNTIL... I decided to reboot

(Before rebooting I installed gkparted to verify my partitions, I didn`t edit them in any way, I just installed and ran gkparted to see my partitions, I opened up gkparted using the following command in terminal

```
gksudo gparted
``` 

I don`t think this could have altered anything, but I`m just letting you guys know)

So I did that and during Ubuntu boot up terminal tells me that it failed on checking the filesystem, I type in reboot, and ubuntu continues to load, gdm opens up I type in my login and password and gdm gives me more bad news, it tells me that my home directory is set to /home/myusername/ but no such directory was found.

Ok... so good thing the guide told me to back up my stuff... I go through the restore procedures with Ubuntu Live Cd and once again reboot, unfortunately after loging in Ubuntu again tells me that my home directory doesn't exist.

So I`m stuck

One more thing that I think might be important is that when I rebooted I forgot to do the last step on the guide that was to delete my home_backup using this command

```
sudo rm -rf /home_backup
```

Any help would be greatly appreciated

---

### Post by prince_niceguy on 2007-09-21
post your fstab you can find the same in /etc/fstab

---

### Post by maaylix on 2007-09-21
> **prince_niceguy said:**
> post your fstab you can find the same in /etc/fstab

```
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
```

---

### Post by imbjr on 2007-09-21
> **maaylix said:**
> ```
unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda5 swap swap defaults 0 0
```

I may be wrong but that looks like the fstab of the livecd. You might have to mount your hard drive's  ext3 partition to get at the real fstab.

I've fallen into the trap of believing I'm looking at the right directorys before when using the livecd - you have to ensure you are not looking at something that's part of the livecd setup.

---

### Post by maaylix on 2007-09-21
> **imbjr said:**
> I may be wrong but that looks like the fstab of the livecd. You might have to mount your hard drive's  ext3 partition to get at the real fstab.

I've fallen into the trap of believing I'm looking at the right directorys before when using the livecd - you have to ensure you are not looking at something that's part of the livecd setup.

I tried mounting by issuing this command

```
sudo mount /dev/sda1 /mnt
```

That`s my root hard drive, the command successfully monted my hd, so I again tried opening fstab and it showed up just like the way I posted

Also I`ve gone ahead and re-installed ubuntu to see if by partitioning home during installation would help, it didn't... Ubuntu always gives me this strange fstab... I have already tried editing the fstab, and I have been able to make one that booted up ubuntu with no problems (home working on my second hard drive)... but once again when I reboot, ubuntu seems to rewrite fstab and it gets me stuck again during boot up

---

### Post by maaylix on 2007-09-21
OMG... I just don`t know what the hell is going on... I just rebooted and Ubuntu booted up fine, and that with me doing NOTHING... I reboot again and boot up fails telling me filesystem check failed

So I decided to edit fstab on the spot, I type in nano /etc/fstab and nano shows me a diffrent fstab

This time it showed me all of my partitions correctly, everything looked fine... which is weird as during login Ubuntu complains that it can`t find my /home directory, yet there I see my /home directory... 

So I decided to erase the UID line for my swap, root and home partitions

I did that and Ubuntu booted up showing no error messeges during boot up, BUT when I try to login, Ubuntu tells me that my /home/myusername directory don`t exist

My current fstab->

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1 /               ext3    defaults     0       1
# /dev/sdb1 /home           ext3    defaults        0       2
# /dev/sda5 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by maaylix on 2007-09-21
I tried editing fstab this way, but gdm still gives me the home directory doesnt exsist error->

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1 /               ext3    auto,user,rw,suid,dev,exec,async     1       1
# /dev/sdb1 /home           ext3    auto,user,rw,suid,dev,exec,async        1       2
# /dev/sda5 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

Also I have tried deleating the empty /home directory on the root partition as I thought that might be confusing ubuntu, but still, Ubuntu isn`t detecting my /home partition 

One detail that I think might be relevant is that my /home partition isn`t detected by the live cd unless I add 

```
pci=nomsi
```

to the live cd boot up by pressing F6

---

### Post by prince_niceguy on 2007-09-21
is your drive working correctly?

do not delete the /home directory. your other drive will never mount.

not sure but can you check which of your drive is primary and which one is marked as secondary from the jumper settings.

---

### Post by maaylix on 2007-09-21
> **prince_niceguy said:**
> is your drive working correctly?

do not delete the /home directory. your other drive will never mount.

not sure but can you check which of your drive is primary and which one is marked as secondary from the jumper settings.

I'm pretty sure it is, BIOS detects it with no problems 

Both my hard drives are SATA, as far as I know, jumpers in this case are only needed to limit my hard drive speed in case my motherboard doesn't support SATA II, which is not the case 

But why would I need an empty /home directory on root?

---

### Post by dcstar on 2007-09-21
> **maaylix said:**
> I tried editing fstab this way, but gdm still gives me the home directory doesnt exsist error->

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
**#** /dev/sda1 /               ext3    auto,user,rw,suid,dev,exec,async     1       1
**# /dev/sdb1 /home           ext3    auto,user,rw,suid,dev,exec,async        1       2**
**#** /dev/sda5 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
```


Of course it will, you have all of the necessary entries **COMMENTED OUT**!

Remove those comments "**#**" and things should change!

---

### Post by maaylix on 2007-09-22
> **dcstar said:**
> Of course it will, you have all of the necessary entries **COMMENTED OUT**!

Remove those comments "**#**" and things should change!

Yeah I already tried removing the ''#'' , it still didn't work. I found out recently that my motherboard (Asus M2N-X) is not very Linux compatible. It's SATA controllers don't work very well under Linux

---

### Post by maaylix on 2007-09-25
Well, I finally figured it out, [by googling a bit](http://ubuntuforums.org/archive/index.php/t-528412.html) I found out someone had the exact same problem that I did (he also was using a M2N-X). The motherboard Asus M2N-X and Feisty's kernel are not a good combination (at least if you want to have two sata hard drives working at the same time).

If someone using a M2N-X has the same problem with two or more sata drives, consider upgrading the kernel to that of Ubuntu 7.10. Here is an excellent tutorial on how to do it:

[http://ubuntuforums.org/showthread.php?t=511974](http://ubuntuforums.org/showthread.php?t=511974)

I'm currently running Feisty with the new kernel with no problem and both hard drives are working perfectly!

---

