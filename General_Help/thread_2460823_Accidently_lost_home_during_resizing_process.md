---
title: "Accidently lost /home during resizing process"
date: 2021-04-19
forum: General Help
---

### Post by niclasrieger on 2021-04-19
I tried to decrease size of my /home in order to increase my root / which is too small. I tried to achieve this by following this [walkthrough]("https://pingtool.org/online-resize-lvm-partitions-shrink-home-extend-root/?unapproved=39065&moderation-hash=68684e835375646de01d336115648ebb#comment-39065"). Unfortunately, I wasn't aware of the differences between standard partitions (which I use) and the logical volume management (LVM) which the walkthrough is based on...at least that's what I suppose.

In brief what I did: 

1. Login as root
2. Unmount my /home via

```

umount /home

``` 3.Shrink my /home partition from 436G by 10G to 426G
```
e2fsck -f /dev/my_home
resize2fs /dev/my_home 426G

```

4. Try to reduce /home to 426G
```

 lvreduce -L 426G /dev/my_home
```

Here I get the error that the location /dev/my_home does not exists. Indeed, checking via

```

df -h

```

does not show my /home anymore. 

I'm pretty much stuck here and have the strong fear that I have somehow destroyed my /home partition with the resize2fs command. I'm still actively in the session, since I don't dare to reboot. Help is very much appreciated!

System: Ubuntu 20.04

---

### Post by CelticWarrior on 2021-04-19
Also asked here [https://askubuntu.com/questions/1332537/accidently-lost-home-during-shrinking-process-with-resize2fs](https://askubuntu.com/questions/1332537/accidently-lost-home-during-shrinking-process-with-resize2fs)

---

### Post by grahammechanical on 2021-04-19
Is this a desktop system or a server system? If it is desktop, what do you see when you open the file manager and go to Other Locations>Computer? Do you see a folder called Home? And in that folder is there another folder with the name of your User?

Or, from the terminal type

```
pwd
```

Do you see?

> /home/your user name

Regards

---

### Post by scorp123 on 2021-04-19
> **niclasrieger said:**
>  
```

 lvreduce -L 426G /dev/my_home
```

Here I get the error that the location /dev/my_home does not exists. Indeed, checking via "df -h" ...


Are you sure you're not misinterpreting the error message?? Since you said above that you were not using LVM ... then there's simply no logical volume that "lvreduce" can reduce in size. And of course "df -h" won't show your home since you unmounted it. Why not check with e.g. 
```
sudo fdisk -l
```

Does the partition that "/home" was on get listed there? You can check "/etc/fstab" which partition that was:
```
cat /etc/fstab
```

---

### Post by niclasrieger on 2021-04-20
@grahammechanical: 
I'm in a terminal as a root with no GUI. The working directory is just ```
/
```. I see all the standard folders like bin/, boot/, etc/, home/, media/, run/ ..., but when I enter /home it's just empty.

@scorp123:
The output of 
```
sudo fdisk -l
```

yields a whole bunch of 
[LIST]
[*]Disk /dev/loop# (where # denotes a number from 0-19; everyone has has a size of about some 100 MB) 
[*]Disk /dev/nvme0n1: 476,96 GiB 
[/LIST]
The last one is subdivided then into[INDENT]**Device |                Boot |               Start |                End          | Sectors |       Size |     Id |    Type**
[/INDENT]

[LIST]
[*]/dev/nvme0n1p1 |    * |                  2046 |   1000214527 |    1000212482 |      477G |      5 |    Extended 
[*]/dev/nvme0n1p5 |                       2048 |       31250431 |        31248384 |      14,9G |    82 |    Linux swap / Solaris 
[*]/dev/nvme0n1p6 |               31252480 |       70311935 |        39059456 |      18.6G |    83 |    Linux 
[*]/dev/nvme0n1p7 |               70313984 |   1000214527 |       929900544 |   443,4G |    83 |    Linux 
[/LIST]

This actually looks alright to me! device *5 is the swap, the size seems correct. Device *6 is the / directory I tried to increase. And device *7 is my /home which I wanted to decrease by 10GB. The sizes shown here are the original ones.
What bothers me is that the Id of *6 and *7 is the same. Isn#t the idea of IDs that they are different?

```
cat /etc/fstab
```

seems to agree with that (though there seems to be one error?):

# / was on /dev/nvme0n1p6 during installation 
UUID=REALLY LONG NUMBER | / | ext4 | errors=remount-ro | 0 | 1

# /home was on /dev/nvme0n1p7 during installation
UUID=REALLY LONG NUMBER | /home | ext4 | defaults | 0 | 2

and similar for my swap.


PS: Sorry for the bad format, but since I cannot access internet from my problematic machine, I use another one and copy/paste the output is thus not possible.

---

### Post by coffeecat on 2021-04-20
A few comments:

> **niclasrieger said:**
> 
3.Shrink my /home partition from 436G by 10G to 426G
```
e2fsck -f /dev/my_home
resize2fs /dev/my_home 426G

```

4. Try to reduce /home to 426G
```

 lvreduce -L 426G /dev/my_home
```


> **niclasrieger said:**
> [LIST]
[*]/dev/nvme0n1p1 |    * |                  2046 |   1000214527 |    1000212482 |      477G |      5 |    Extended 
[*]/dev/nvme0n1p5 |                       2048 |       31250431 |        31248384 |      14,9G |    82 |    Linux swap / Solaris 
[*]/dev/nvme0n1p6 |               31252480 |       70311935 |        39059456 |      18.6G |    83 |    Linux 
[*]/dev/nvme0n1p7 |               70313984 |   1000214527 |       929900544 |   443,4G |    83 |    Linux 
[/LIST]

This actually looks alright to me! device *5 is the swap, the size seems correct. Device *6 is the / directory I tried to increase. And device *7 is my /home which I wanted to decrease by 10GB. The sizes shown here are the original ones.


The sizes shown would be the originals. Your resize2fs command merely shrunk the filesystem, not the actual partition. They are different things - you have a filesystem within a partition. 

> **niclasrieger said:**
> 
What bothers me is that the Id of *6 and *7 is the same. Isn#t the idea of IDs that they are different?


The id column in fdisk output refers to partition type, here type = 83, a Linux partition. Both your root and home partitions are type 83.

And I think you may have missed this important point from scorp123:

> **scorp123 said:**
>  And of course "df -h" won't show your home since you unmounted it.

Your home hasn't disappeared - you've simply unmounted it and not remounted it. My guess is that you probably have an undamaged system, with the exception of a slightly undersized filesystem within its partition. 

I don't want to belabour your original mistake, which was to use an inappropriate howto for the job at hand, but the way I would have done this exercise would have been to use gparted from a live session. Time-consuming but easy. No howto needed. I'm not sure whether gparted would do the job now with the reduced filesystem within nvme0n1p7 - perhaps others might want to comment - but I'll make one last and very important point:

**Before manipulating partitions, *always, always, always* make sure you have adequate backups of any data.** Do you? Partition and/or filesystem resizing always carries the risk of something going wrong with catastrophic data loss.

---

### Post by niclasrieger on 2021-04-20
Thanks coffecat! At this point I would be also very glad to just go back to the original state, that is, redoing resize2fs. Form what I read  **resize2fs /dev/my_home **should just add the freed space back to the filesystem. Would you think that'd work? 

What would happen if I reboot the computer at that point? Is there a risk of additional data loss?

I have made a backup of my home so worst case scenario of replaying everything would not be that catastrophic. However, recreating my setup from scratch would still be quite time consuming so it wouldn't be my preferred solution.

---

### Post by coffeecat on 2021-04-20
I suggest you attempt to remount home first. Assuming your /etc/fstab is OK - what you've managed to post of it looks OK - simply do:

```
sudo mount -a
```

And then test home.

I said "time-consuming" when referring to using gparted. On reflection, probably not. I was thinking of times I've used it in the past with spinning disks and doing major resizes. You're using a SSD disk. What you want to do should be quite quick. You could use resize2fs to restore the filesystem to its original size, but why not start up a live system and see what gparted can do for you? Don't mount any of the partitions that you want to manipulate. You could then finish the job you've started. Shrink the nvme0n1p7 partition and then enlarge the nvme0n1p6 partition, and gparted would grow the filesystem in nvme0n1p6 to match. 

Growing nvme0n1p6 would, of course, have a potential risk for data on your root partition, which includes configurations for your system, so that's something you need to balance against your desire not to set up from scratch.

---

### Post by HermanAB on 2021-04-20
The most important question is: Do you have a backup of your data?
If yes, then you can simply reinstall, which takes about 20 minutes.
If no, then I would boot from install media, mount /home and backup the data, then reinstall.  
Fixing a problem like this without destroying the data in the process is possible, but far more hassle than reinstalling, which will also give you a nice new up to date system.
As you have found, playing with partitions is an almost sure fire way to mess up a system - not recommended in the best of times.

---

### Post by niclasrieger on 2021-04-20
Phew, thanks for pointing that out. I indeed could just mount the disk and from what I see the resize2fs command correctly shrinked the filesystem /home. It now has 419G of which 380 is used. I can enter /home/my_user/ and accessing my data seems to work as well. As to whether I corrupted data or not with my actions I unfortunately don't know. 

So if I understand you correctly, you suggest that I start a live system now and continue the work with gparted. Some questions that I'm sure you can quickly answer:
[LIST]
[*]do I also have to unmount / if I want to increase this filesystem? or is unmounting /home enough?
[*]do I have to unmount before going in live session or can this be done from within the live session?
[/LIST]

---

### Post by HermanAB on 2021-04-20
The install disk is necessarily a fresh boot.  Before doing anything to the file system of /home again, first make a backup of your data.  After that you can play with the disk utilities and if you are lucky you may still have your data intact.

---

### Post by scorp123 on 2021-04-20
> **niclasrieger said:**
>  but when I enter /home it's just empty. 

**Of course** it is empty. You **_unmounted _**it!

I agree with the others: Please reboot a live CD / live USB-stick and use "**gparted**" from there. In that state none of your harddrive partitions should be mounted and they are a lot safer to manipulate that way.

---

### Post by niclasrieger on 2021-04-20
Well, that's definitely another lesson learned for me :) Thanks for all your helpful comments, it seems I managed to resize my partitions without (obviously) corrupting my data. 
1. unmounted again my /home
2. expanded my /home to its original size via [B]resize2fs /dev/my_home
[/B]3. reboot and start from live USB
4. resize via gparted
5. reboot 

I actually expected to reinstall GRUB because I had to move my /home partition to increase the space of /, but surprisingly my computer boots normally without complaining + I can access all my data without problem.
Thanks again :)

---

### Post by TheFu on 2021-04-20
Whenever looking at LVM stuff, use these commands to get an overview:
```
sudo pvs
sudo vgs
sudo lvs
lsblk -e 7 -o name,size,type,fstype,mountpoint
```
They make nice text tables/graphs of the layout.  Also, I'm confused that /dev/my_home worked at all.  Normally, the location for LV links to the device-mapper "devices" are either:
/dev/mapper/{vg}-{lv}
or
/dev/{vg}/{lv}
For example:
```
lrwxrwxrwx 1 root root 7 Apr 20 01:35 /dev/hadar-vg/root -> ../dm-1
lrwxrwxrwx 1 root root 7 Apr 20 01:35 /dev/hadar-vg/swap_1 -> ../dm-2

```
VG name = hadar-vg
LV names = swap_1 or root

On a different system:
```
$ ls -l /dev/vgubuntu-mate/
total 0
lrwxrwxrwx 1 root root 7 Apr 20 01:15 home -> ../dm-2
lrwxrwxrwx 1 root root 7 Apr 20 01:15 root -> ../dm-0
lrwxrwxrwx 1 root root 7 Apr 20 01:15 swap_1 -> ../dm-1
```
VG name = vgubuntu-mate
LV names = swap_1 or root or home

The dm-[0-99] values can change with every boot.  There are other symbolic links generated by the device mapper that point to dm-[0-99] under /dev/disks/* too. That's where the LABEL and UUID links are placed.

Regardless, happy that you seem to have found an answer, though it is unclear how from the data posted.  If this is **solved**, please use the "_Thread Tools_" button near the top of the page to mark it that way so other people don't waste time.

---

### Post by coffeecat on 2021-04-20
> **TheFu said:**
> Whenever looking at LVM stuff, 

But the OP **wasn't** looking at lvm stuff, as is mentioned in the first post:

[quote=niclasrieger]Unfortunately, I wasn't aware of the differences between standard partitions (which I use) and the logical volume management (LVM) which the walkthrough is based on.[/quote]

---

