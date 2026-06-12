---
title: "Very strange partitioning Gparted vs. parted LVM2 * consistency problem??"
date: 2008-02-18
forum: General Help
---

### Post by aquaraquar on 2008-02-18
Hi guys,
I'm trying to build a flexible and easy to manage partitioning on my 400gb hdd with lvm  but having some problems.

Here is my main partition table
1 ntfs windows
2 kubuntu 32 xfs
3 pardus ext3
4 extended
5 /boot for kubuntu 32 ext3
6 kubuntu 64 ext3
7 unformatted for lvm 60gb
8 unformatted for lvm 60gb
9 unformatted for lvm 60gb
10 unformatted for lvm 60gb
11 unformatted for lvm 90gb

In kubuntu32, I created volume groups and logical volumes, everything is ok with them. But when it comes to create a file system on the logical volumes (lv), parted drives me crazy!!, however gparted( parted with GUI ) works, or "seem to" work well. 

As told in the gnu's lvm documentation, I create a "loop" label on the logical partition. Then when try to create fs on that partition with "mkpartfs logical fat32 0 10GB" or some variations, parted asks me the partition type [ext2?]  as if I did not tell it to do it fat32 within the command line, it insists on ext2 all the time!  Consequently it does create nothing. 

If I make the labeltype msdos, it does create a partition with "mkpartfs primary fat32 0 10GB", but that partition is not available or mountable, it says "bad superblock etc. error when I try to mount that fs.

On the other hand when try to create a fs with gparted on a "loop" labeled ( labeled by parted! ) lv, gparted does not recognize this label type and quits! When I do the same thing with a msdos labeled partition, it does create the fs and the fs is usable!!! However when I check the label type with parted, obaaaa, I see it as "loop" even it was set to msdos!!!!!!!!

I'm totally freaked up and confused, I just wanted to play with the lvm with parted ( not gparted ) but it seems if there is a bug with parted or I do something wrong, waiting for your comments

Thanks in advance

---

### Post by danwood76 on 2008-02-18
One thing you should probably understand about partitioning tools is they all do the different jobs differently as there is no exact standard to partitioning.
You will probably get issues if you for example create a partition table in windows and try to modify it with Gparted.

One thing you should do is create and modify all your partitions using one program, for example parted (or derivatives).

It does sound like these various programs you have been using are getting confused between the different partition tables.

What tool did you use to create the partitions in kubuntu?
It might be worth deleting all the unused partitons and re creating them with parted/gparted as this may help.

---

### Post by aquaraquar on 2008-02-18
> **danwood76 said:**
> 
What tool did you use to create the partitions in kubuntu?
It might be worth deleting all the unused partitons and re creating them with parted/gparted as this may help.
I used gparted to create the main partitions on the disk. Then I resized the lvm partitions and had some problems, that's why I thought the command line tool would be more 'accurate' while doing the stuff. Doesn't gparted use the same library with parted and isn't is the gui version of parted? As I remember the library was sth like libparted1.7.1.

---

### Post by danwood76 on 2008-02-18
Yes I think so.
I normally use fdisk for partitioning as I dont trust parted, its messed me up before.

I read an article the other day about someone who installed 145 OS on one machine (What a nutter, I would get lost) but in that guide he also says he only uses fdisk and cfdisk.
[http://www.justlinux.com/forum/showthread.php?threadid=147959](http://www.justlinux.com/forum/showthread.php?threadid=147959)

I would try deleting all the partitions you dont need and used cfdisk/fdisk to partition. I have never had any troubles with either of these apps.
You can then create the logical volume groups from the command line.

I found this how-to that might help you:
[https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall](https://help.ubuntu.com/community/SettingUpLVM-WithoutACleanInstall)
It is a ubuntu guide so will be more relevant than the man pages.

---

### Post by aquaraquar on 2008-02-19
I've already recreated the lvm partitions/logical volumes. Although both gparted and parted uses same library they seem to be inconsistent each other. Actually now it seems gparted is working, I lost a lot time already, so it would be enough I guess. Thanks for your replies and links.

---

