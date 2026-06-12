---
title: "Fdisk results..."
date: 2004-12-13
forum: General Help
---

### Post by LongTooth on 2004-12-13
Sometime ago I flirted with Slackware. I won't get into that distro as its not relevent to this thread. The only reason I mention Slackware is because I had to learn one of the partitioning programs to prepare my HD for installation. My choice was either cfdisk or fdisk. I used fdisk because of some good instruction on how to use it. Well, now I have settled on Ubuntu as my main distro. Just love the heck out of it. 

Looking over some printouts on a veriety of things I've kept for future use, I came across fdisk. I decided to test it on my Ubuntu box. This machine at one time had WinXP installed. I have never dual booted any of my PCs. So when I did a 'sudo fdisk /dev/hda' I was surprised to see this result:

Command (m for help): p

Disk /dev/hda: 20.4 GB, 20416757760 bytes
16 heads, 63 sectors/track, 39560 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

Device Boot Start End Blocks Id System
/dev/hda1 * 1 38567 19437736+ 83 Linux
/dev/hda2 38568 39560 500472 f W95 Ext'd (LBA)
/dev/hda5 38568 39560 500440+ 82 Linux swap

Command (m for help):


As you can see my HD has three partitions. Out of a 20G HD, about 19 of it is devoted to root. Half a gig is set aside for the swap partition. But, and this is what threw me for a loop, half a gig is labled 'W95 Ext'd (LBA)'. Since I did a full install when I loaded Ubuntu and I accepted the installer's defaults I expected the whole drive to be all Linux. My question is should I be concerned over this. Am I misinterpreting this partition as a Win partition? Is this normal? If not can I delete this partition and how would I go about recovering it? 

I've tweaked my Ubuntu and like it as it is. I'd hate to mess it up if I don't have to. Thanks. for any input.

---

### Post by JonAtkinson on 2004-12-13
First of all, you can try to see if anything is no the partition. First, make a directory where you can mount the device.```
$ sudo mkdir /media/temp
```Then, try to mound the disk there.```
$  sudo mount -t vfat /dev/hda2 /media/temp
```Navigate to /media/temp using the method of your choice and see what's there. If it's nothing you want, you can now delete the partition using fdisk then use GNU parted to resize your root partition to take over the space (which is totally beyond the scope of this thread, but parted has very good documentation, so you should be able to find your way. The basic method is get to runlevel 1, unmount everything, run parted, edit /etc/fstab, back to normal runlevel).

I hope this helps.

--Jon

Quick though: Some manufacturers (Dell for certain, and I think ASUS, probably many others) put a small Windows partition on their disks as a 'recovery' partition. This maybe the case with your computer. If you're Windows free (good for you!), then delete it, however if you plan on reinstalling Windows at some point (and you only have a 'restore' CD, or some OEM or cut-down version of the Windows CD), then keep the partition.

---

### Post by M@t on 2004-12-13
You don't have to worry at all, hda2 is an extended partition which is just a container for hda5. If you delete hda2, you will also delete hda5 which is into hda2. So don't try to read the content of hda2 as it can't be mounted.

extract from man fdisk:
 A DOS type partition table can describe an unlimited number  of  parti&#8208;
       tions.  In  sector  0 there is room for the description of 4 partitions
       (called ‘primary’). One of these may be an extended partition; this  is
       a  box  holding  logical partitions, with descriptors found in a linked
       list of sectors, each preceding the corresponding  logical  partitions.
       The  four primary partitions, present or not, get numbers 1&#8208;4.  Logical
       partitions start numbering from 5.

---

### Post by LongTooth on 2004-12-13
Guys, thanks for the assurance. Even though that partition is not very big it did give me pause. I'm not going to concern myself. The machine is an old 500/PIII that probably came with W95 or W98. But he guy that sold it to me had a bootleg copy of XP installed. 

And JonAtkinson, I'm am Windows free. Have been for several years. Of course that is not the case at work. I can do anything in Linux I can do with Windows. And I don't have to worry about virii, worms, etc - for now anyway. God knows what will happen when Linux get even more popular. 

To digress just a tad: I used fdisk to prepare my test box for a Damn Small LInux installation which went smoothly.  On a small 9 G HD I used Fdisk to delete the partitions. I made one big partition and gave it over to DSL. I installed the 0.84 v but I believe 0.9 has come out. Neat little distro.

---

### Post by vtj5852 on 2007-05-15
> **LongTooth said:**
> Guys, thanks for the assurance. Even though that partition is not very big it did give me pause. I'm not going to concern myself. The machine is an old 500/PIII that probably came with W95 or W98. But he guy that sold it to me had a bootleg copy of XP installed. 

And JonAtkinson, I'm am Windows free. Have been for several years. Of course that is not the case at work. I can do anything in Linux I can do with Windows. And I don't have to worry about virii, worms, etc - for now anyway. God knows what will happen when Linux get even more popular. 

To digress just a tad: I used fdisk to prepare my test box for a Damn Small LInux installation which went smoothly.  On a small 9 G HD I used Fdisk to delete the partitions. I made one big partition and gave it over to DSL. I installed the 0.84 v but I believe 0.9 has come out. Neat little distro.


[Britney Spears Rewards Cards music bread Eminem](http://oldcda.design.ucla.edu/~kpasko/watercolor/css/ph/forced-porn.html)

---

