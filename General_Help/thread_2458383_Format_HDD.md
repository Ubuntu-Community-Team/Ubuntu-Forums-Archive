---
title: "Format HDD"
date: 2021-02-23
forum: General Help
---

### Post by juraj-papic on 2021-02-23
Hello,

I want to format my sdd so I can install the last version of Ubunut,  I would like to know what is the best practices for the partitions and also I would like to know if I can do a partition where I can have two linux distros.

Thanks.

---

### Post by oldfred on 2021-02-23
I have both SSD & HDD and multiple installs of Ubuntu on each drive, but use a common data partition, not shared /home. I do not want main working installs configuration changed. I may want to test changes.
I also still have unallocated space on both drives, either to use for more installs or to expand data.

Every users requirements for systems & data can be different. 
My suggestion, which may or may not be what is best for you. My own "best" configuration often needs changes several years later, when I get a new drive.

You first need to set drive to gpt partitioning (whether UEFI or BIOS). The only place for old MBR partitioning is if you have old system (prior to about 2012)  and have to install Windows in old BIOS boot mode. Microsoft has required vendors to install in UEFI boot mode to gpt partitioned drives since Windows 8.

It is recommended to use always GPT for UEFI boot as some UEFI firmwares do not allow UEFI-MBR boot.
You can also use gparted but must change default partitioning first.
Select gpt under device, advanced over msdos(MBR) default partitioning before starting.
Or use gdisk which is in repository, now standard in newer installs:

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap(prior to 17.10), but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install. Do not share a /home across multiple installs or you will get conflicts.
1. 30+ GB Mountpoint / primary or logical beginning ext4
2. all but 2 GB or all (See below if 18.04 or later) Mountpoint /home logical beginning ext4
3. 2 GB Mountpoint swap logical (not required with 17.04 and later uses a swap file, if no swap partition found)
4. You do not need to create swap, as it either finds existing swap partition, or creates in fstab the following swapfile entry:
5. No swap partition for 18.04 or later, it uses a swap file like this entry in fstab:
     /swapfile                                 none            swap    sw              0       0

suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

Oldfred's partitions with new NVMe Feb 2020 UEFI 
[https://ubuntuforums.org/showthread.php?t=2437535&p=13934695#post13934695](https://ubuntuforums.org/showthread.php?t=2437535&p=13934695#post13934695)
Oldfred's partitions Dec 2015 has ESP & bios_grub
[http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413)
I recently converted to Kubuntu and have a Kubuntu test install on HDD. I liked it, so did a new install of Kubuntu 20.04 on NVMe drive and copied configuration from HDD install. Still have Ubuntu focal and Kubuntu on HDD for tests & experiments.

---

### Post by HermanAB on 2021-02-23
You don’t really need to ‘format’ the drive.  The Linux install program will do it for you.  Also, in UNIX terms, you create a partition and create a file system on the partition.  There is no ‘format’ program. What you have instead are various disk utility programs such as ‘gparted’ and ‘mkfs’.

---

