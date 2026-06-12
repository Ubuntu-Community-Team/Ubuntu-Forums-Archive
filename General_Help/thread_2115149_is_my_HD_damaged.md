---
title: "is my HD damaged?"
date: 2013-02-12
forum: General Help
---

### Post by nosmokenofire on 2013-02-12
Hi all,

I am having problems with my Ubuntu partition (sda1), no way to mount it or access files. In Gparted from live cd the partition just looks empty, as though all has been wiped off. What I'd like to do now is ascertain whether the actual HD is damaged in which case I will need to get a new one, or whether all the data is just lost in which case I can try to format the partition and use it again (assuming there is absolutely no way of getting my files back from the installation. I have a backup about 3 weeks old which is better than nothing...

On sda5 I have another ubuntu install, which although I cannot boot into it (not yet a least) I can mount the partition from a live cd.

any ideas?

PS this thread explains what happened: [http://ubuntuforums.org/showthread.php?t=2114888](http://ubuntuforums.org/showthread.php?t=2114888)

---

### Post by unheeding on 2013-02-12
You should start [here](https://help.ubuntu.com/community/TestingStorageMedia), hopefully that will tell you what you  need to know.

---

### Post by nosmokenofire on 2013-02-12
> **unheeding said:**
> You should start [here]("https://help.ubuntu.com/community/TestingStorageMedia"), hopefully that will tell you what you  need to know.
Thanks Unheeding,

With a deeper search in testdisk I get ```
No file found, filesystem may be damaged
``` for sda1...

I'm going to try gnu ddrescue...

---

### Post by nosmokenofire on 2013-02-12
here are the results from testdisk
```
TestDisk 6.14-WIP, Data Recovery Utility, December 2012
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 80 GB / 74 GiB - CHS 9729 255 63
     Partition               Start        End    Size in sectors
>D Linux                 2891   9 63  9092 201  5   99631104
 D Linux                 2899 115 33  9101  51 38   99631104
 D Linux                 2899 148  2  9101  84  7   99631104
 D Linux                 2902 130 45  9104  66 50   99631104
 D HPFS - NTFS           5394   0  8  6201 254 63   12980513
 D Linux                 6202   1  1  9638 254 63   55215342
 * Linux Swap            9639 175  9  9729  78 13    1439744





Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
ext4 blocksize=4096 Large file Sparse superblock Recover, 51 GB / 47 GiB

```To be honest I'm completely lost with all this. If anyone out there wants to try to help me step by step to try to get my data back off the damaged partition then I'd be very grateful. If not I understand. I google a lot to try to find information but the problem is that I have trouble with some of the technical jargon...

---

### Post by speartip on 2013-02-12
OK, It looks like all your partitions are still there.
If you have the live CD you installed with, boot into that, open up a terminal & run:
```
sudo fdisk /dev/sda
```
If all the partitions look correct type: p  & then  w
This writes them to the disk.
It might also help to run afterward: (if you have a problem with grub)
```
sudo mount /dev/sdaX /mnt
``` - X being the no. of your / linux partition.
Then:
```
sudo grub-install --boot-directory=/mnt/boot /dev/sda
```
Then Reboot.

---

### Post by nosmokenofire on 2013-02-12
Hi Speartip, thanks for getting involved.> If all the partitions look correct type...how do I know if the partitions look correct?

---

### Post by nosmokenofire on 2013-02-12
I did it anyway and got this ```
ubuntu@ubuntu:~$ sudo fdisk /dev/sda

Command (m for help): p

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf1d46d1e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    99633151    49815552   83  Linux
/dev/sda4        99635130   156301311    28333091    5  Extended
/dev/sda5        99635193   154850534    27607671   83  Linux
/dev/sda6       154861568   156301311      719872   82  Linux swap / Solaris

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource busy.
The kernel still uses the old table. The new table will be used at
the next reboot or after you run partprobe(8) or kpartx(8)
Syncing disks.
```

---

### Post by dino99 on 2013-02-12
Something is confused here, as :
- the post #7 above show /dev/sda1 as the bootable partition (which seems good)
- but a post #4 above shows " * Linux Swap" which is clearly wrong: the swap file might not be set as bootable.

So to confirm:
- boot on a livecd/usb
- and start gparted to check the bootable partition : might be the one where / is installed

After that, open a terminal (from the livecd) to update-grub:

```
sudo update-grub
```

and reboot

[http://ubuntuforums.org/showpost.php?p=12495221&postcount=2](http://ubuntuforums.org/showpost.php?p=12495221&postcount=2)

note:
- please post : cat /etc/fstab

note2: as the swap partition is set as bootable, and is by definition empty when it is not used (aka most of the time), then dont be worry about your hdd, nothing is damaged (just a borked config)

---

### Post by nosmokenofire on 2013-02-12
I am unable to mount sda1 here is what gparted says[IMG]http://ubuntuforums.org/attachment.php?attachmentid=231301&d=1360607169[/IMG]I'll try updating grub but I'm sure I've tried before with no success...

---

### Post by nosmokenofire on 2013-02-12
here is the result> ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: failed to get canonical path of /cow.
ubuntu@ubuntu:~$ 

---

### Post by dino99 on 2013-02-12
into #9 above, is it from the livecd ?

as you can see:
- there is a red point about sda1: select that partition, and right click on that red point to unmount it if possible, or grab some information to know why it complaint
- the partition showing a "key" means they are locked due to the mounted status: can be unmounted with a right click.

if you cant resolve the sda1 issue, it might be quicker to reinstall over it.

 [http://askubuntu.com/questions/207663/cannot-update-grub-with-paramters-on-live-usb](http://askubuntu.com/questions/207663/cannot-update-grub-with-paramters-on-live-usb)

[http://ubuntuforums.org/showpost.php?p=12495221&postcount=2](http://ubuntuforums.org/showpost.php?p=12495221&postcount=2)

note: always use gparted (or any other formatting tool) on unmounted partition.

---

### Post by speartip on 2013-02-12
I think you were on the right track in post 7.
"error 16: Device or resource busy" was probably because 1 or more of the partitions were mounted.
Try again, but using gparted on the live CD, make sure every partition is unmounted first.

---

### Post by nosmokenofire on 2013-02-12
I unmounted everything that was mounted in live cd, took swapoff, tried again and got this far:```
ubuntu@ubuntu:~$ sudo fdisk /dev/sda

Command (m for help): p

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf1d46d1e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    99633151    49815552   83  Linux
/dev/sda4        99635130   156301311    28333091    5  Extended
/dev/sda5        99635193   154850534    27607671   83  Linux
/dev/sda6       154861568   156301311      719872   82  Linux swap / Solaris

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

---

### Post by speartip on 2013-02-12
Sorry i'm out of ideas now.
"Bad superblock" on sda1 doesn't look good though.
Maybe someone with more technical know how will chime in.

---

### Post by nosmokenofire on 2013-02-12
Thanks very much for your help anyway...

---

