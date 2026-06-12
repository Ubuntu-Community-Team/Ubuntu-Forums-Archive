---
title: "[server] Need advice on screwed up partition table"
date: 2013-01-19
forum: General Help
---

### Post by danxtc on 2013-01-19
Hi guys--

First-time post, so go easy :)

So I think I've screwed my Ubuntu server after using PING (it's a tool like Norton Ghost) to try and create a backup image.

Basically the system got to an unbootable state just with the `grub rescue>` prompt. After much messing around with a Live CD and `testdisk` I managed to get the system to boot again (yay).

Buuuut, when I boot now, the MOTD tells me that the system is using 90% of diskspace. This isn't true, I don't think.

```
    Welcome to Ubuntu 12.04.1 LTS (GNU/Linux 3.2.0-35-generic x86_64)

    * Documentation:  https://help.ubuntu.com/

    System information as of Sat Jan 19 20:35:50 GMT 2013

    System load:  0.0                Processes:           112
    Usage of /:   1.4% of 223.21GB   Users logged in:     1
    Memory usage: 32%                IP address for eth0: 10.0.0.250
    Swap usage:   0%

  => /boot is using 91.7% of 60MB
```

The system's got the following config:
   
    /dev/sda  - 250GB Hard drive that came with the microserver containing Ubuntu server and it's packages
    /dev/sdb  - 1TB data volume
    /dev/sdc  - 1TB data volume
   

The result of fdisk reports a load of things that are beyond my linux knowledge:

```
    Disk /dev/sda: 250.1 GB, 250059350016 bytes
    255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0x000a2883

    Device Boot      Start         End      Blocks   Id  System
    /dev/sda1   *        2048      135781       66867   83  Linux
    /dev/sda2          501760   488396799   243947520   8e  Linux LVM

    Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
    81 heads, 63 sectors/track, 382818 cylinders, total 1953525168 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0xef459d3e

    Device Boot      Start         End      Blocks   Id  System
    /dev/sdb1            2048  1953525167   976761560    5  Extended
    /dev/sdb5            4096  1953525167   976760536   83  Linux

    Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
    81 heads, 63 sectors/track, 382818 cylinders, total 1953525168 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0xf7a74b79

    Device Boot      Start         End      Blocks   Id  System
    /dev/sdc1            2048  1953525167   976761560    5  Extended
    /dev/sdc5            4096  1953525167   976760536   83  Linux

    Disk /dev/mapper/dumbo-root: 243.5 GB, 243491930112 bytes
    255 heads, 63 sectors/track, 29602 cylinders, total 475570176 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0x00000000

    Disk /dev/mapper/dumbo-root doesn't contain a valid partition table

    Disk /dev/mapper/dumbo-swap_1: 6304 MB, 6304038912 bytes
    255 heads, 63 sectors/track, 766 cylinders, total 12312576 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0x00000000

    Disk /dev/mapper/dumbo-swap_1 doesn't contain a valid partition table

```

My understanding is that I've not got swap as such, which is dangerous, and I've somehow ended up with LVM.

I want to restore the system to a state with a simple partition structure, no LVM, and I'd like to use Clonezilla, or something to get a backup image as I dont have the time to reinstall the server again.

I've been looking at the Gparted Live CD to re-partition the drive, but I'm not confident I can do this without making the system unbootable again or loosing any data.

I've just got the fdisk off another healthy Ubuntu install on an almost identical Microserver, and it's something like this: 

```
/dev/sda1 * 2048 484466687 242232320 83 Linux 
/dev/sda2 484468734 488396799 1964033 5 Extended 
/dev/sda5 484468736 488396799 1964032 82 Linux swap / Solaris
```


Any help greatly appreciated.

---

### Post by dabl on 2013-01-19
/dev/sda2 may or may not really be LVM -- the partition type is definitely set to 8e. What is on that partition -- anything important?  The other partitions appear to be in normal condition, as far as one can tell from the fstab output.

One command that is helpful in straightening out booting and mounting issues is this one:

```
sudo blkid -c /dev/null -o list
```

You can run that from a booted Live CD/USB stick, and then use the UUIDs to fix /etc/fstab and/or /boot/grub/grub.cfg (temporarily, just to get it to boot).

If GParted will show you the partitions correctly, and if whatever is on /dev/sda2 is backed up, you might be able simply to remake the filesystem ext4 and get on with it.

---

### Post by steeldriver on 2013-01-19
I don't see anything particularly messed up - if you type 'mount' it will show you which partitions are which but it looks like sda1 is your boot partition and it's rather small (60MB) so unsurprisingly pretty full (over 90%), whereas there's plenty of space on your root partition i.e. everything except /boot and your data (aka '/') which is likely inside the LVM on sda2 (along with your swap)

60MB *might* be enough for /boot if you are scrupulous about cleaning out old kernels

Ignore the messages about not containing a valid partition table - that's just because fdisk doesn't understand LVM

---

### Post by danxtc on 2013-01-19
Thanks guys, I've got the thing booting, and I've managed to use GParted to resize the boot partition to 240MB which takes up all the remaining free space on the hard drive.

So, LVM. Sda2 seems to be LVM, and it seems to have these logical volumes - I've gone from not knowing what LVM was an hour ago, to throwing around the various bits of terminology associated with it, but I hope you know what I mean. Anyway, so it seems the LVM has the rest of the free space on the drive, and contains root and swap.

/dev/mapper/dumbo-root
/dev/mapper/dumbo-swap_1


So I started thinking I should copy all the data off the root volume, destroy the LVM and create normal partitions which I can manipulate with conventional tools like Gparted. But you've got me thinking I should leave it, if this is 'expected behaviour' for LVM?

I'm still very green when it comes to Ubuntu, but if you think my current set up should last without loads of maintenance then I'll leave it be.  I've now got 240MB for /boot - will this be enough?

Thanks again.

---

### Post by danxtc on 2013-01-19
...And the other question I have been green, is when I'm using the shell prompt to do a ```
du -sh
``` on either /dev/sda1 or sdb2, sdb2 won't mount as it's LVM, but how does the system use these volumes if they're not mounted, or is it that the volumes within the LVM are mounted and thus give me a working filesystem.

---

### Post by steeldriver on 2013-01-19
It all looks OK to me - I wouldn't mess with it unless it's causing problems

The /dev/mapper/dumbo-root and /dev/mapper/dumbo-swap_1 are the LVM equivalent of disk partitions - iirc they get auto-named based on the hostname (presumably dumbo?) - if you run 'mount' you should see them mounted like

```
/dev/mapper/dumbo-root  on / type ext4 (rw)
```

(or possibly with UUIDs instead of /dev/mapper/xxxx)

---

### Post by danxtc on 2013-01-19
That's awesome, thank you, pretty relieved I can leave that alone now.

And I was originally going for disney character names for naming the servers, 'dumbo' was just too ironic :)

---

### Post by steeldriver on 2013-01-19
haha - well fyi if you ever need to change it (as I wanted to do recently after reinstalling to an old LVM with a new hostname) there's a handy command 'lvrename'

---

### Post by danxtc on 2013-01-20
:)

I'm in the middle of trying to fix a little weirdness with grub, and it seems that manipulating the LVM when things have gone wrong seems much more work than doing so with regular partitions.

So, I came across this--  [http://daniel-albuschat.blogspot.co.uk/2008/02/converting-lvm-to-normal-partition.html](http://daniel-albuschat.blogspot.co.uk/2008/02/converting-lvm-to-normal-partition.html)


-- I know it's not for Ubuntu, but would this work with Ubuntu server? I figure, dd the data off, overwrite it back to sda2, resize that partition down, and then create a swap partition. I guess Ubuntu would then need the fstab updating and grub reinstalling so it would boot off the 'new' /dev/sdb2 partition containing the root partition containing the existing data?

Or am I incredibly wrong?

---

