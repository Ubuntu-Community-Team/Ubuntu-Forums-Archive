---
title: "Ubuntu and Unity 7 error"
date: 2016-05-28
forum: General Help
---

### Post by TBK on 2016-05-28
I installed Ubuntu 15.10 32bit and it was upgraded to 16.04.
Since after installing Ubuntu 15:10, it often can not boot and requires  manual fsck and I must to use Ubuntu live (or other Ubuntu on other  parrtition) to fix this problem, I don't meet this problem with other  Ubuntu version (13.10, 14.04, 16.04,...).
Ubuntu has been operating normally for a time but now after logging in  to my account (admin) with Unity 7, panel and laucher don't appear but I  still can Ubuntu (I met this problem before upgrade Ubuntu to 16.04,  and now this problem still isn't solved)
I set swap partition for Ubuntu 15.10 during installation but after  installation, I have deleted that swap partition and made another swap  partition and used Gparted to mount it after each time I loggin. Now I  want to edit "fstab" to mount it automatically but I can't save any  change, it is "read only" although I opened this file as root, I also  can't edit this file via Linux Mint 17.3 (on other parrtition).
Help me to solve these problems, Ubuntu 32bit is my main OS!
I also have Ubuntu 16.04 64bit, Ubuntu Gnome 64bit, and Linux Mint 17.3 64 bit on this computer.

---

### Post by DuckHook on 2016-05-29
Without better info, just guessing, but it sounds like your HDD may be dying. If you haven't already done so, you must do immediate backup of all important data. Look at the health of your HDD using the *Disks* app > {Ctrl}+{s} which will bring up the disk's SMART data and general state of health.

When asking for help, especially dealing with disks and such, always post extensive HW description, specs, settings etc. Otherwise, we are just stumbling around in the dark. Please read my signature item: [COLOR="#B22222"]How to Ask for Help[/COLOR]

Please post results of:```
sudo parted -l
``````
sudo blkid
``````
df -h
``````
cat /etc/fstab
```

How did you try to edit fstab? Using *sudo nano* or another method? Such details can be important. Post results of:```
ls -la /etc/fstab
```

...please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by TBK on 2016-05-31
```
Model: ATA ST1000VX001-1HH1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  100GB   100GB   primary   ntfs
 3      100GB   400GB   300GB   extended                  lba
 5      100GB   199GB   99,5GB  logical   ext4
 6      199GB   200GB   499MB   logical   ext4
 7      200GB   202GB   2001MB  logical   linux-swap(v1)
 8      202GB   400GB   198GB   logical   ntfs
 4      400GB   1000GB  600GB   primary   fat32
```

This is a new hard disk

```
sudo blkid
/dev/sda1: LABEL="WINDOW 10" UUID="65C7EA61620579D9" TYPE="ntfs" PARTUUID="5f1aa708-01"
/dev/sda4: LABEL="TBKDATA" UUID="D955-BE70" TYPE="vfat" PARTUUID="5f1aa708-04"
/dev/sda5: LABEL="UBUNTU" UUID="5474b623-8624-44e2-9672-9809014167c4" TYPE="ext4" PARTUUID="5f1aa708-05"
/dev/sda6: LABEL="UbuntuBoot" UUID="af6526ed-52b4-4470-8538-251f2b7880b4" TYPE="ext4" PARTUUID="5f1aa708-06"
/dev/sda7: UUID="bd1d5591-ce08-456e-8cb4-f4dfc0ca1605" TYPE="swap" PARTUUID="5f1aa708-07"
/dev/sda8: LABEL="ARCHIVE" UUID="4E1576705BFFEB7D" TYPE="ntfs" PARTUUID="5f1aa708-08"
```

```
df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            461M     0  461M   0% /dev
tmpfs            96M  4,9M   91M   6% /run
/dev/sdb2        19G   17G  921M  95% /
tmpfs           479M  1,2M  478M   1% /dev/shm
tmpfs           5,0M  4,0K  5,0M   1% /run/lock
tmpfs           479M     0  479M   0% /sys/fs/cgroup
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs            96M   40K   96M   1% /run/user/1000
/dev/sda4       559G  202G  358G  37% /media/tbk/TBKDATA
```

```
cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb2 during installation
UUID=02fb74ae-63c5-4b73-a3c1-45c6acd17b30 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=bd1d5591-ce08-456e-8cb4-f4dfc0ca1605 none            swap    sw              0       0
# swap was on /dev/sdb3 during installation
UUID=0fb9b983-7e5b-4246-8fc4-37d4c32f096d none            swap    sw              0       0 
```

```
ls -la /etc/fstab
-rw-rw-r-- 1 root root 730 Th04 29 11:38 /etc/fstab
```

I used this comand : ```
gksu gedit /etc/fstab
```

---

### Post by DuckHook on 2016-05-31
According to your output, you have two disks and Ubuntu is installed on the second one: sdb. This disk is 95% full which probably accounts for the erratic behaviour of your system. When filled like that, you will not be able to save any files (no space), install apps, upgrade anything, etc. often with no explanation.

You must either free up space or increase the size of your root partition. You have only given 19GB to it and this is easily used up with old kernels alone. You can try running:```
sudo apt-get autoremove && sudo apt-get clean
```to see if this frees up enough space immediately to at least get you a working configuration, but this will not work in the long term. You need more space, especially since your /home directory is included in the same partition.

---

### Post by TBK on 2016-05-31
I have Ubuntu 16.04 and Ubuntu Gnome 15.10 installed on sdb2 and sdb6, but they have no problem, I only have problem with Ubuntu 32 bit on sda5.

---

### Post by DuckHook on 2016-05-31
Some of the above commands needed to be run from inside your problem installation. If you can boot into it, try running the commands again and posting output back to this thread. I am also puzzled by some missing output. Both parted and blkid should show the other disks and partitions that you have (at the very least sdb), but they don't. Did you report all of the output?

---

### Post by DuckHook on 2016-05-31
> **TBK said:**
> I have Ubuntu 16.04 and Ubuntu Gnome 15.10 installed on sdb2 and sdb6, but they have no problem......even though these installs are running OK for now, they really are just centimetres from the edge of the cliff. Free up room or move them/increase to a larger partition. 95% full is playing with fire.

---

### Post by TBK on 2016-06-01
You don't need to care about sdb, I only meet problem with Ubuntu 16.04 on sda5
[https://drive.google.com/file/d/0B0YPxoTYHWAZaGFFMk9iczR5R1U/view?usp=sharing](https://drive.google.com/file/d/0B0YPxoTYHWAZaGFFMk9iczR5R1U/view?usp=sharing)

---

### Post by DuckHook on 2016-06-01
> **TBK said:**
> You don't need to care about sdb, I only meet problem with Ubuntu 16.04 on sda5...

The disks app report cannot tell us what we need to know. I repeat:

> **DuckHook said:**
> **Some of the above commands needed to be run from inside your problem installation**. If you can boot into it, **try running the commands again and posting output back to this thread**. I am also puzzled by some missing output. Both parted and blkid should show the other disks and partitions that you have (at the very least sdb), but they don't. **Did you report all of the output?**

---

