---
title: "Repartitioning Ubuntu"
date: 2020-03-01
forum: General Help
---

### Post by ivatt1815 on 2020-03-01
I have a 2TB SSD drive which was purchased as "used" (from a Microsoft approved seller) from I believe a Dell system and was surprised to find it came with a legit W10 pre install. I installed UBUNTU primarily to run x-plane 11 and when I set the original partition size I thought it would be adequate but I am now finding I am running out of space for UBUNTU and need to extend the partition size.

 I have in the past used Partition Magic with Windows (when it was free) but this was usually easy as there was free space to extend the partition and if I recall it was even possible to slide the size of following partition to make them smaller and free up space.

Attached are 2 image showing my current disc allocations.

I would be grateful if someone could tell if it is possible to extend the UBUNTU partition by say 200GB and if so how to go about it (I am still confused by the way UBUNTU identifies the discs).

I have GPARTED, Partition Manager,Gnome Discs installed.

Thanks in anticipation

---

### Post by CatKiller on 2020-03-01
From your image your Ubuntu partition has plenty of space left; it's not even half full. It's that NTFS partition, whatever that's for, that looks low on available space.

You can make your Ubuntu partition smaller. You'll need to do so from your install disc, since you can't modify partitions while they're mounted and your / partition would necessarily be mounted if you boot from it. You'd have three steps: shrink the partition; move it to the right within the extended partition that contains it; shrink the extended partition. The middle step will take the longest, since that's the step that's actually moving data. 

That will give you some unallocated space between the partitions. You can then increase the size of your NTFS partition into that unallocated space. It's best to do that within Windows, since it's a Windows filesystem. GParted could try to do it, but has limited capacity to fix any problems with it, since NTFS is proprietary and secret and all support has to be reverse-engineered.

---

### Post by yancek on 2020-03-01
In the first image you posted, the windows (ntfs) partition (sda2) shows  as over 97% full.  I find it extremely difficult to believe a windows system would even boot in that case.  Or is this simply a data partition and your windows is on another drive.   I don't see anything showing a 2TB drive in the output you posted.  Your second image shows that you have 3 physical  drives, a 1TB, a 500GB and a 164GB. What's on those?  You'v also somehow misread the problem which is explained
in the post above, plenty of room on the Ubuntu partition but your windows partition is full.

---

### Post by ivatt1815 on 2020-03-01
[SIZE=2][FONT=arial][COLOR=#333333]Thanks for the replies. As I said I haven't got to grips with the way UBUNTU identifies different drives (too stuck in Windows way).

I will give it awhile to check exactly what I am being told when UBUNTU gives me the boot options. Glad to know that my UBUNTU partition isn't getting full up.

The SDD I bought was definitely 2TB [/COLOR][/FONT][COLOR=#333333][FONT=arial](Western Digital WD20EVDS 2TB 7200 RPM 32MB CACHE SATA 3.5" Hard Drive)[/FONT][/COLOR][/SIZE][SIZE=4][FONT=arial][COLOR=#333333][SIZE=2]
[/SIZE]
[/COLOR][/FONT][/SIZE]

---

### Post by oldfred on 2020-03-01
Have you updated SSD firmware?
Many are not seen if firmware not updated.

Windows likes 30% free and at 10% free you have so little room that a defrag takes forever. 
You have so little room, you probably cannot even run a defrag. Either major houseclean or expand partition.

---

### Post by CatKiller on 2020-03-01
> **ivatt1815 said:**
> 
The SDD I bought was definitely 2TB (Western Digital WD20EVDS 2TB 7200 RPM 32MB CACHE SATA 3.5" Hard Drive)
If it's got a rotational speed it's not an SSD.

The drive you've got in there is a 1 TB Hitachi HDD (as well as two others).

---

### Post by TheFu on 2020-03-01
The output from 
```
lsblk -e7 -o name,size,type,fstype,mountpoint
```
would clearly show the attached disks.  

It won't show storage that isn't recognized by the OS, however.  

I don't know of any way to exclude the loop devices from **parted**. Sorry.  Normally, I'd like to see **sudo parted -lm** output, but when it is full of loop devices, it is a pain.

---

### Post by ivatt1815 on 2020-03-02
I am quite confused as the drive was sold as ssd and I am sure shows in windows as 2TB I will have to check my W10 install and see what that tells me and report back. The details I quoted were from the sale site so may not match what the dive details actually are hence the need to check.

---

### Post by TheFu on 2020-03-02
```
sudo lshw -C disk
```
or
```
sudo  hdparm -I /dev/sd[a-z]
```
will show more details about connected storage than most people care to see.

---

### Post by CelticWarrior on 2020-03-02
> **ivatt1815 said:**
> [SIZE=2][COLOR=#333333][FONT=arial]Western Digital WD20EVDS 2TB 7200 RPM 32MB CACHE SATA 3.5" Hard Drive[/FONT][/COLOR][/SIZE]

is definitely HDD, not SSD.

If you were told by the store otherwise you were deceived. And even worse if you payed a SSD price for that.

[This one]("https://www.newegg.com/western-digital-av-gp-wd20evds-2tb/p/N82E16822136494") should be yours, the exact model, and 3.5" which in itself is a giveaway. Now compare the price you payed that should be similar of the Newegg's (cheaper at Amazon, I think) with the [prices of 2TB SSDs]("https://www.newegg.com/p/pl?d=2tb+ssd&N=100011693") in the same store. Also please note they're all 2.5".

---

### Post by ivatt1815 on 2020-03-02
Afternoon, problem identified. Firstly the drive isn't SSD as expected, my mistake I must have looked at an ssd and then decided it was too expensive. Non the less the drive as advertised is not the drive that has been delivered namely an [COLOR=#231F20][FONT=Helvetica]Hitachi HUA721010KLA330 with a 1TB capacity. This was not spotted when my friend installed the drive but has been checked by physically pulling the drive.

I have messaged the retailer and wait to get their response.

According to W10 there is only about 13GB free space so I may need to do some pruning if I can't find another solution. Most of the space will be taken up with x-plane 11[/FONT][/COLOR]

---

### Post by ivatt1815 on 2020-03-03
Hi a quick update. I contacted the seller who was very apologetic about the mistake. I have agreed with him that he will send me the correct 2TB drive so that I can clone the 1TB across rather than having to start from scratch and also to give me time to erase all my personal data.

In the past I have used Macrium Reflect with Windows and this have been perfect but I understand that it isn't too stable with Ubuntu. 

This means I need to pick a different package and in particular one that will allow me to extend the W10 partition. I would prefer to use a Windows based system as I am more familiar but this might not be possible, so I have briefly looked at a selection of Linux packages such as GParted, Partclone, System Rescue Disc (FS Archiver) , Mondo Rescue, Clonezilla of course. As I am a novice when it comes to Ubuntu I need a simple package that doesn't need too much command line input i.e one that installs itself.

I am open to any guidance on this.

---

### Post by CelticWarrior on 2020-03-03
> **ivatt1815 said:**
> In the past I have used Macrium Reflect with Windows and this have been perfect but I understand that it isn't too stable with Ubuntu. 

Macrium Reflect works correctly with Linux partitions. And, like any other similar tool, it can and should be used in a OS agnostic way. It allows the creation of rescue bootable disks/USB and all operations can be done within that environment, not from any running OS (of course you'll need to install Macrium in Windows and then produce the bootable media but the actual operations should be done in that environment, particularly when dealing with partitions from different OSes). 

So, some purist may not like it, but there's no problem in using such tools. Clonezilla actually does the same.

---

### Post by ivatt1815 on 2020-03-04
Thanks for info on Macrium Reflect that's good to know. I always ran it from the rescue disc although my original W7 dul booted with Macrium. I have always used MR to create backup images not just straight cloning. As stated aside from clong the two drives i also need to enlarge the W10 partition so need to see how to do that in MR.

So far I haven't seen any Ubuntu software that looks as easy to use as MR as I haven't yet got the hang of the terminal options in Ubuntu.

---

