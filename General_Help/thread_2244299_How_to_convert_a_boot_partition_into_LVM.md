---
title: "How to convert a /boot partition into LVM"
date: 2014-09-15
forum: General Help
---

### Post by georgesgiralt on 2014-09-15
Hello,
A long time ago when I set up my server, I used a little md (md0, raid1, 200Mb size) partition as /boot and set up everything else as LVM based on md1 PV (raid 1).
Now, I run 12.04 LTS on this server and would like to increase the size of the /boot filesystem. As this is based on  primary partitions (/dev/sda1 and /dev/sdb1) it is quite impossible to do simply. 
I think I could do the creation of a new LV into my LVM setup and convert the whole system to boot on the LVM instead of the md0 based /boot .
I would be delighted to gather a detailled procedure in order to make this transistion foolproof... 
Many thanks in advance for your advice and wisdom ! 

The setup is :
/dev/sda :
sda1 : 200 mb 
sda2 : remaining disk
Grub boot sector installed
/dev/sdb :
sdb1 : 200 mb
sdb2 : remaining of the disk
Grub boot sector installed

Software raid :
md0 : mirror made of /dev/sda1 and /dev/sdb1
md1 : mirror made of /dev/sdb2 and /dev/sdb2

LVM :
rootvg made on a single PV : md1
filesystems :
/boot made on md0 with ext3
/ made on rootvg/lv1 with ext3
/home made on rootvg/lv2 with ext3 
........

---

### Post by TheFu on 2014-09-16
Let's step back and think a little about this.

When is /boot used? 
a) at boot time
b) when updating the kernel, boot menu

Can it even be put under LVM?
 - no.

If there is a disk failure of /boot, does having a RAID1 mirror actually help?  Perhaps. 
If there is a /boot disk failure, does having RAID1 complicate the solution?  Definitely.

So - for my effort, I don't bother making /boot RAID. It isn't worth the effort.  I can connect a USB flash drive with /boot and get a system up faster than I can troubleshoot the RAID issues.  Heck, I can boot off a liveCD and shove grub to a tiny partition elsewhere, if that is needed.

Just sayin'.

Ok - so there is a great reason to have /boot in a RAID1 setup and you are willing to deal with the extra hassles.  Making /boot larger means you need to make space for the larger storage.  It looks to me like you can't without a disk swap or adding 2 new HDDs or massively reorganizing the existing storage use on the drives. Moving and resizing an LVM partition isn't trivial.

[http://askubuntu.com/questions/196125/how-can-i-resize-an-lvm-partition-i-e-physical-volume](http://askubuntu.com/questions/196125/how-can-i-resize-an-lvm-partition-i-e-physical-volume) was the best solution that I found.  Looks like shrinking LVs, VGs, and PVs will be needed first with the most popular answers.

There is an answer that pointed here: [http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/](http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/) - which uses a GUI tool to resize the LVs inside the VG and PVs. Nice!  After I made a complete backup, I'd try this solution first. Looks promising.  I haven't tried it myself, but I am just curious enough to give it a shot on a spare machine here someday.

Depending on the amount of data, it might be easier just to backup everything and start fresh with new partitions sized the way you want.  Also - is there a specific reason to still use ext3?

---

### Post by georgesgiralt on 2014-09-17
Hello TheFu,
Thanks for your answer ! See my comments inline into your post below.
> **TheFu said:**
> Let's step back and think a little about this.

When is /boot used? 
a) at boot time
b) when updating the kernel, boot menu

Can it even be put under LVM?
 - no.

[COLOR="#FFD700"][COLOR="#008000"]Aha ! I thought that Grub2 and recent kernel vaersion could allow for that. If not, the whole plot dies itself ...[/COLOR][/COLOR]

If there is a disk failure of /boot, does having a RAID1 mirror actually help?  Perhaps. 
If there is a /boot disk failure, does having RAID1 complicate the solution?  Definitely.

So - for my effort, I don't bother making /boot RAID. It isn't worth the effort.  I can connect a USB flash drive with /boot and get a system up faster than I can troubleshoot the RAID issues.  Heck, I can boot off a liveCD and shove grub to a tiny partition elsewhere, if that is needed.

Just sayin'.

[COLOR="#008000"]Humm, at work we use ton of servers running various Linux variants (mostly RedHat and Debian based systems) using this exact design. Easy to maintain, troubleshoot and repair. As I'm used to it, I used it at home for my PC. But with Ubuntu for ease of use for my wife. [/COLOR]

Ok - so there is a great reason to have /boot in a RAID1 setup and you are willing to deal with the extra hassles.  Making /boot larger means you need to make space for the larger storage.  It looks to me like you can't without a disk swap or adding 2 new HDDs or massively reorganizing the existing storage use on the drives. Moving and resizing an LVM partition isn't trivial.

[http://askubuntu.com/questions/196125/how-can-i-resize-an-lvm-partition-i-e-physical-volume](http://askubuntu.com/questions/196125/how-can-i-resize-an-lvm-partition-i-e-physical-volume) was the best solution that I found.  Looks like shrinking LVs, VGs, and PVs will be needed first with the most popular answers.

There is an answer that pointed here: [http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/](http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/) - which uses a GUI tool to resize the LVs inside the VG and PVs. Nice!  After I made a complete backup, I'd try this solution first. Looks promising.  I haven't tried it myself, but I am just curious enough to give it a shot on a spare machine here someday.

Depending on the amount of data, it might be easier just to backup everything and start fresh with new partitions sized the way you want.  Also - is there a specific reason to still use ext3?

[COLOR="#008000"]Ext3 is here for historic reasons. It was the file system to use when I set up the PC years ago, and I stick to it since. If I have to increase the /boot using the same md0/md1 scheme, I would do using a third disk,  onto which I will create a bigger sdc1 and then incorporating this sdc1 partition into md0. (doing the same with sdc2/md1) then removing sda1 from md0 and sda2 from md1 , repartitionning the drive and re-adding sda1 to md0 and sda2 to md1. and repeating it with the sdb disk.  When done, I'll have large partition for md0 but still the same 200M size md0. So I'll have to extend md0 to fill the extra space created. Once done, I'll have to increase the filesystem for /boot to use the extra space created. Then remove the third disk I put in it on step one.
It is time consuming because I've to wait for the raid arrays to synchronize before moving to next step. It is also expensive because I've to use a third disk in order to avoid a degraded array during the removal and work on each disk.  Tjis is why I wanted to convert my system to a full LVM based system. 
I'm still confused because I thought it was now possible.[/COLOR]

---

