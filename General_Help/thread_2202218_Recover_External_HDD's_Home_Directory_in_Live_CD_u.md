---
title: "Recover External HDD's Home Directory in Live CD ubuntu 10.4"
date: 2014-01-28
forum: General Help
---

### Post by hot67machine on 2014-01-28
Hello,I have been using Ubuntu 10.4 in my Dell laptop PC and 2 Days ago my external hdd clashed and later,i saw Unknown file system and grub rescue message in my laptop screen So,I using Live CD to fixing problem.


first,I tried to type Terminal for seeing my home directory and i do as


gksudo nautilus 


but it can not find my home directory at there.The external hdd is connected via USB and power is on. 
I want to recover my data from live CD.Can you give me advise?
I plan to purchase USB memorystick and i will install Ubuntu 10.4 to them and booting USB memorystick
as it will same happen in this now? I am afraid of it.

---

### Post by claracc on 2014-01-28
For recovering your /home folder you can use console and command line, I think.

In order to launch consoleyou can type:ctrl+alt+T

Then through command line you can copy your /home folder to the place you have previously mounted, please see: [http://ubuntuforums.org/showthread.php?t=793680](http://ubuntuforums.org/showthread.php?t=793680) for specific commands.

You can use 10.04 live CD in order to recover your files but it is a release which has reached its end of life support, for this reason I recommend once solved the problem, to install a supported release as 12.04 or 13.10.

---

### Post by jeanjd63 on 2014-01-28
Hello

When you boot on LiveCD/USB, the first thing to do, dd USB plugged, is :
[B]sudo  fdisk  -l
[/B]to see yours partitions.

---

### Post by hot67machine on 2014-01-28
Thank you for reply




> **claracc said:**
> For recovering your /home folder you can use console and command line, I think.

In order to launch consoleyou can type:ctrl+alt+T

Then through command line you can copy your /home folder to the place you have previously mounted, please see: [http://ubuntuforums.org/showthread.php?t=793680](http://ubuntuforums.org/showthread.php?t=793680) for specific commands.

You can use 10.04 live CD in order to recover your files but it is a release which has reached its end of life support, for this reason I recommend once solved the problem, to install a supported release as 12.04 or 13.10.





First,I tried these but it does not work.I have an 160GB external hdd and most of space was full by Photo,Video,Text,etc
and the external hdd front light was on and it looks like working.My laptop Internal hdd was broke 4-5 Years ago,anyway
i would trying these again.



1:

sudo cp -Rv /media/disk1/home/myusername/*
cp: missing destination file operand after `/media/disk1/home/myusername/*'




2:


sudo -i
mount /dev/hdx /mnt/oldhome
mount point /mnt/myusername does not exist






> **jeanjd63 said:**
> Hello

When you boot on LiveCD/USB, the first thing to do, dd USB plugged, is :
sudo fdisk -l
to see yours partitions.



Thanks,I wrote command and follow these steps but it no respond in terminal
after the sudo fdisk -l




I checked Disk Utilities and my external hdd was there and showing device /dev/sda
and model number,serial,etc and Volume as it show 154GB as Free and 1.0kb as Unknown 
and 6.2GB as Free.it that something wrong?I do not create partition.

---

### Post by Bucky Ball on 2014-01-28
Replace 'myusername' in those commands with your *actual* user name and run them again.

---

### Post by hot67machine on 2014-01-28
> **Bucky Ball said:**
> Replace 'myusername' in those commands with your *actual* user name and run them again.



Hi,I tried once again but it does not work as follow-



1:


sudo cp -Rv /media/disk1/home/yassys/*
cp: missing destination file operand after `/media/disk1/home/myusername/*'



2:

sudo -i
mount /dev/hdx /mnt/oldhome
mount /dev/hdx /mnt/oldhome does not exist
mount point /mnt/yassys
mount point /mnt/yassys does not exist






Today,I clicked Install Ubuntu 10.04.1 LTS Icon and follow each install step because
I want to checked my external hdd alive and external hdd was there but it said external hdd has 
no Operating System.I cancel Install and I hope I can install Ubuntu in a part of my external hdd
to see or save data.

---

### Post by Bucky Ball on 2014-01-28
Okay, well, you're not filling in *your* information but using the default information that is intended only to tell you what to add. For instance:

```
mount /dev/**hdx **/mnt/**oldhome**
```

hdx: You need to replace that with 'sda5' or whatever the number of your partition is. 'oldhome' you need to replace with the actual mountpoint you are using.

```
sudo cp -Rv /media/**disk1**/home/yassys/*
```

You need to provide the exact path on *your* machine. You are also missing half the command as the full command from that link is:

```

sudo cp -Rv /media/disk1/home/yourusername/* /media/yourdestinationdrive/yourdestinationfolder/
```

You're not copying the file to any destination, thus the missing operand.


What was given were examples only; they are not intended to be used 'as is', unless the paths and names on your machine, by some freakish coincidence, happen to match the details in the examples. ;)

---

### Post by hot67machine on 2014-01-28
I do not have Partition and All data contain at the entire disk and I wrote
"sda" and mount point as "/." or Do I need write /home ?




sudo -i
mount /dev/sda /mnt/.
mount: /dev/sda: can't read superblock

---

### Post by jeanjd63 on 2014-01-28
Can you give the return of command :
[B]sudo  fdisk  -l
[/B]or[B]
sudo  parted -l[/B]

---

### Post by hot67machine on 2014-01-28
> **jeanjd63 said:**
> Can you give the return of command :
[B]sudo  fdisk  -l
[/B]or[B]
sudo  parted -l[/B]




#1:

ubuntu@ubuntu:~$ sudo fdisk -l
ubuntu@ubuntu:~$ 



#2:

ubuntu@ubuntu:~$ sudo parted -l
Error: /dev/sda: unrecognised disk label                                  

Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label

---

### Post by jeanjd63 on 2014-01-28
Your disk seems to be sick

---

### Post by dragonfly41 on 2014-01-28
There is a clue in your post #9

> mount: /dev/sda: can't read superblock

It does looks like you will need to recover superblock in /dev/sda.

For this you need to run [color=blue]testdisk[/color] from your live CD in a command terminal.

Test if your LiveCD does not have testdisk already installed by opening terminal and running [color=blue]sudo testdisk[/color] which gives permission to write testdisk.log.

At first menu > Create a new log file (by pressing Enter key).

This tutorial explains how to recover superblocks.   Also refer to testdisk forum 

[http://unix.stackexchange.com/questions/33284/recovering-ext4-superblocks](http://unix.stackexchange.com/questions/33284/recovering-ext4-superblocks)

and search ubuntu forum for "superblock recovery".

If you cannot recover superblock you can go on to recover lost files using testdisk.  But you will need space into which you actually write your recovered files and LiveCD will not provide this.  You would then need to install Ubuntu on another USB drive with plenty of space and recover data from your sick drive.  Create ubuntu on ext USB drive using unetbootin.

 For this search "data recovery" in this forum.

"Testdisk" is the tool for recovery .. superblocks, partitions, mbr's, files, images.

"Photorec" will recover photo images .. but you lose the file structure, file names etc.

---

### Post by hot67machine on 2014-01-29
Thank your for reply.


I Install testdisk and I checked disk as select "Analyse"



```
Disk /dev/sda - 160 GB / 149 GiB - CHS 152627 64 32
Current partition structure:
     Partition                  Start        End    Size in sectors


Partition: Read error
```





then I closed terminal and I checked as





```
ubuntu@ubuntu:~$ sudo fsck /dev/sda
fsck from util-linux-ng 2.17.2
```

---

### Post by hot67machine on 2014-01-29
I am really worry about my data and I need advice how to see or save my data.
Recover superblock does not seem to work.Should I Install Ubuntu to another hdd or USB memory sticks?





```
ubuntu@ubuntu:~$ sudo fsck /dev/sda
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: No such file or directory while trying to open /dev/sda

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>
```




The /sda changed to /sdb after I checked testdrive.



```
ubuntu@ubuntu:~$ sudo fdisk -l

Unable to read /dev/sdb
```





then I tried to mount external hdd again but it does not work.



```
mount /dev/sdb1 /mnt/.
mount: /dev/sdb1 is not a valid block device
```

---

### Post by dragonfly41 on 2014-01-29
Did you follow the advice from sudo fsck /dev/sda

> you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

The bad news is that your same symptoms are reported here 

[http://askubuntu.com/questions/260467/partition-read-error](http://askubuntu.com/questions/260467/partition-read-error)

Partition: Read error

---

### Post by hot67machine on 2014-01-29
Thank you for information and I reading the page of link and
I tried type e2fsck with an alternate superblock in Terminal.




```
ubuntu@ubuntu:~$ e2fsck -b 8193 /dev/sdb1
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: Permission denied while trying to open /dev/sdb1
You must have r/w access to the filesystem or be root
```




```
root@ubuntu:~# e2fsck -b 8193 /dev/sdb1
e2fsck 1.41.11 (14-Mar-2010)
e2fsck: No such device or address while trying to open /dev/sdb1
Possibly non-existent or swap device?
```

---

### Post by dragonfly41 on 2014-01-29
You have to keep trying different superblock values (your stored backups in your sick device) .. possibly multiple times until you hit the jackpot (if you are lucky)
[URL="http://http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/"]
http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/[/URL]

[http://www.cyberciti.biz/faq/linux-find-alternative-superblocks/](http://www.cyberciti.biz/faq/linux-find-alternative-superblocks/)

sudo mke2fs -n /dev/xxx

[color=maroon][Edit] Your device /dev/sdb1 you are analysing must be unmounted first.

Here is an example when I run command on one of my unmounted partitions .. /dev/sda8 [/color]

```

$ sudo mke2fs -n /dev/sda8
mke2fs 1.42 (29-Nov-2011)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
3203072 inodes, 12800000 blocks
640000 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
391 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000, 7962624, 11239424

```

---

### Post by hot67machine on 2014-01-29
Thank you for link and advise.


I type "sudo mke2fs -n /dev/sdb" and I checked external hdd USB cable and power and its ok.I have no partition 
and My All data contain entire disk and I looked at Disk Utilities and it shows as 154GB(dev/sdb1)Unknown and 
Maybe The Data contain this part of disk and 1.0KB(dev/sdb2)Unknown and 6.2GB(dev/sdb5)Unknown.




```
root@ubuntu:~# sudo mke2fs -n /dev/sdb
mke2fs 1.41.11 (14-Mar-2010)
/dev/sdb is entire device, not just one partition!
Proceed anyway? (y,n) y
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
9773056 inodes, 39072726 blocks
1953636 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
1193 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000, 7962624, 11239424, 20480000, 23887872
```

---

### Post by jeanjd63 on 2014-01-29
The command is to be done on /dev/sdb1 and not on /dev/sdb :
** [COLOR=#000000][FONT=Ubuntu Mono]sudo mke2fs -n /dev/sdb1[/FONT][/COLOR]**

---

### Post by hot67machine on 2014-01-29
```
ubuntu@ubuntu:~$ sudo -i
root@ubuntu:~# sudo mke2fs -n /dev/sdb1
mke2fs 1.41.11 (14-Mar-2010)
Filesystem label=
OS type: Linux
Block size=4096 (log=2)
Fragment size=4096 (log=2)
Stride=0 blocks, Stripe width=0 blocks
9396224 inodes, 37569280 blocks
1878464 blocks (5.00%) reserved for the super user
First data block=0
Maximum filesystem blocks=0
1147 block groups
32768 blocks per group, 32768 fragments per group
8192 inodes per group
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000, 7962624, 11239424, 20480000, 23887872
```




I try to next step and reboot.

---

### Post by hot67machine on 2014-01-30
I tried type command in terminal and I could not take a goods result and I spend a 
lot of times.The My external hdd was working during fixing and I felt that it will 
back to normal.I will trying again after taking break a few times.




```
sudo e2fsck -b 163840 /dev/sdb1
```




```
Couldn't fix parent of inode 8650756: Ext2 inode is not a directory

Pass 3A: Optimizing directories
Segmentation fault (core dumped)
```

---

### Post by hot67machine on 2014-01-30
Thank you very much for all support.


The My External hdd was mounted successfully at Live CD 
and My file is Safe:p and filesystem was modified.



```
/dev/sdb1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sdb1: 530298/9396224 files (0.9% non-contiguous), 32281634/37569280 blocks
```

---

### Post by dragonfly41 on 2014-01-30
Good news!

Now since you have had problems test the "health" of your repaired drive
and perhaps now is the time to backup your files into a newer drive (e.g. external USB drive or Dropbox account or Ubuntu One account) before you have another failing device.

Mark the thread as solved.

---

