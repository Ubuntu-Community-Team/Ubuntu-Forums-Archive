---
title: "UUIDs change during reboot"
date: 2013-03-12
forum: General Help
---

### Post by phanosp on 2013-03-12
Hello I am having a strange problem with ubuntu server. I have install ubuntu server 10.04 (64-bit) on INTEL BOXD510MO motherboard as my fileserver. I only installed SSH and Samba roles on that server to have the system as simple as possible. Also I have update my system to its latest update (Ubuntu, Bios etc). 
Since my motherboard only supports 2 Sata ports I have installed a raid controller ([http://www.delock.com/produkte/G_70154/merkmale.html?setLanguage=en](http://www.delock.com/produkte/G_70154/merkmale.html?setLanguage=en)) to expand my sata ports. Please note that I am only using this controller for the extra Sata ports and not the raid functionality. In total I have 4 hard disks installed, two on the motherboard (including the boot partition) and two on the raid controller.

My problem is the following. On almost every reboot the system fails to boot because the UUIDs of the hard disks change!! In order to fix it the boot problem I have to manually recover the information in /etc/fstab. To make things even more complicate if I try to manually mount the partitions after boot using the UUID provided by using the command ls -l /dev/disk/by-uuid, I end up mounting another partition that the one specified by the UUID. For example consider the following 

lrwxrwxrwx 1 root root 10 2013-03-12 08:14 2e29f46e-1a71-4423-842e-abc80bdf66b9 -> ../../sdd1
lrwxrwxrwx 1 root root 10 2013-03-12 08:14 4c689820-8bea-4274-99d1-f5826bdfedd5 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2013-03-12 08:14 8bcf2054-b857-4743-8fe1-f5bcb96ce877 -> ../../sda3
lrwxrwxrwx 1 root root 10 2013-03-12 08:14 bd512215-aa4a-4794-8cbd-226202865725 -> ../../sda1
lrwxrwxrwx 1 root root 10 2013-03-12 08:14 beea943b-667a-473a-8f89-4c6ffce2f0b8 -> ../../sdc1
lrwxrwxrwx 1 root root 10 2013-03-12 08:14 fcf1c81c-6174-4205-a4fd-3955b5c8504f -> ../../sda5

Lets say that I mount the first UUID that points to sdd1 (2e29f46e-1a71-4423-842e-abc80bdf66b9 -> ../../sdd1) using the command sudo mount UUID=2e29f46e-1a71-4423-842e-abc80bdf66b9 /media/harddisk1 the result for example might be for the system to mount for /media/harddisk1 the sdc1 instead of the sdd1. After reboot the above pictures again changes, the UUID change to which partition they point to.

Since I have not that much expertise on Linux as you fine people have can someone clarify things a little bit? Is there a solution to my problem? 

Thanks in advance,

phanosp

---

### Post by schragge on 2013-03-12
Cannot comment on your problem, but there's a workaround. If UUIDs aren't working for you, try to uniquely label each partition with [e2label]("http://manpages.ubuntu.com/manpages/precise/en/man8/e2label.8.html")/[swaplabel]("http://manpages.ubuntu.com/manpages/precise/en/man8/swaplabel.8.html")/[ntfslabel]("http://manpages.ubuntu.com/manpages/precise/en/man8/ntfslabel.8.html")/[dosfslabel]("http://manpages.ubuntu.com/manpages/precise/en/man8/dosfslabel.8.html")/[mlabel]("http://manpages.ubuntu.com/manpages/precise/en/man1/mlabel.1.html")/whatever and mount them by label instead of by UUID.

---

### Post by phanosp on 2013-03-12
> **schragge said:**
> Cannot comment on your problem, but there's a workaround. If UUIDs aren't working for you, try to label each partition with [e2label](http://manpages.ubuntu.com/manpages/precise/en/man8/e2label.8.html)/[swaplabel](http://manpages.ubuntu.com/manpages/precise/en/man8/swaplabel.8.html)/[ntfslabel](http://manpages.ubuntu.com/manpages/precise/en/man8/ntfslabel.8.html)/whatever and mount them by label instead of by UUID.

Hi schragge and thanks for the reply. I will try your suggestion as soon as I get home. My only concern is whether or not the label will point to another partition when the machine is rebooted. For example I label /dev/sdd1 with the keyword disk1 and mount that, but after reboot although the label disk1 still points to /dev/sdd1 the device /dev/sdd1 points to another partition on another harddrive since the devices under /dev/sd* have the tendency to change along with the UUIDS. What do you think? 

phanosp

---

### Post by schragge on 2013-03-12
Wait, I've just re-read your post. I guess what changes is device names, not UUIDs. Say, if your swap partition has the UUID=2e29f46e-1a71-4423-842e-abc80bdf66b9 then it will always stay this. It could be /dev/sda5, or /dev/sdd1 on the next reboot: it's unusual, but changes nothing. If you're referencing all your partitions by UUIDs, the real device names don't matter. Same to labels. The label is stored on partition itself, it cannot change on reboot. However, the device name can. This is usually the case with removable devices like USB pendrives: you usually cannot say for sure what device name it will get next time as it depends on the number and order of USB devices currently attached to the system and both of them can vary. That's why mounting by UUIDS/labels was invented in the first place.

---

### Post by phanosp on 2013-03-12
Thanks schragge but the problem is that in my case UUIDS do change on boot. I can not understand why. I will try to create an actual example when I get home and get back at you.

---

### Post by aarons6 on 2013-03-12
UUIDs cant change, those are created when you format the drive.. 
it looks like you are making links to the uuid folders? 
this is not the way to mount drives.. 

i think you are confused how to mount a drive.
first you want to get the correct uuid
use blkid to get the uuid of the drive partition.. 
sudo blkid /dev/sda1 for example

then in fstab you want to put a line similar to this. for each drive
UUID=90f64d3d-f0e6-4965-970f-52d24e443fc9 /home           ext4    defaults        0       2


it goes UUID /mountfolder type defaults 0 2

then when you boot up your drive should be mounted to that folder..

you dont put /dev/sda1 in the fstab

and you dont link drives to folders.. you mount them.

---

### Post by phanosp on 2013-03-12
> **aarons6 said:**
> UUIDs cant change, those are created when you format the drive.. 
it looks like you are making links to the uuid folders? 
this is not the way to mount drives.. 

i think you are confused how to mount a drive.
first you want to get the correct uuid
use blkid to get the uuid of the drive partition.. 
sudo blkid /dev/sda1 for example

then in fstab you want to put a line similar to this. for each drive
UUID=90f64d3d-f0e6-4965-970f-52d24e443fc9 /home           ext4    defaults        0       2


it goes UUID /mountfolder type defaults 0 2

then when you boot up your drive should be mounted to that folder..

you dont put /dev/sda1 in the fstab

and you dont link drives to folders.. you mount them.

Thanks aarons6 I did not knew that. I will try both of the suggestions as soon as I get home and get back at you.

---

### Post by phanosp on 2013-03-12
One last question before I try you suggestion please. Is there a way to tell to system to boot even in the event when the fstab fails? I am asking this because every time that I have to do a manual recovery I have to take a monitor, keyboard and mouse to my fileserver box in order to recover it which is pretty annoying. Thanks.

---

### Post by phanosp on 2013-03-13
Last night I tried the UUID option suggested by aarons6 and so far it seems to work just fine. I also use he option nobootwait (in fstab) in order to avoid my system not booting up because for some reason it wont be able to mount a partition/drive. A simple test showed it to work as well. I guess time will tell.

schragge I did did not test your suggestetion about labels because the UUIDs seem to work for now. Thanks a lot anyway.


Regards,

phanosp

---

### Post by CharlesA on 2013-03-13
It looked like you were using the device name in fstab instead of UUID. Ubuntu should default to using the UUID at install.

Glad you got it fixed, and nobootwait is handy, especially if you are running the box headless.

---

