---
title: "Problem removing empty residual sdb1 folder?"
date: 2015-04-03
forum: General Help
---

### Post by ortermagic on 2015-04-03
I had a little tinker with my desktop yesterday, I have 2x500g hd's, one (sdb1) had mint on it which i didn't need, (the other sda1 has Ubuntu 14.04, my preferred o/s), so i decided to reformat /sdb1.
 I formatted it out of existence using gparted, combined with another run using disk utility. Anyhow after finally  deleted the partitions, I find that when I start up I get a grub boot-up process which hangs whilst it looks for the now defunkt /mnt/sdb1. 

Then I get the dialogue "The disk drive for /mnt/sdb1 is not ready or not present" followed by "continue to wait or press 's' to skip mounting, or 'm' for manual recovery" I have to opt for the 's' option because I am clueless re the 'm' option. After pressing 's' the screen goes black for half a minute or more, then the screen suddenly pings to life rather startlingly, I have tried to erase /sdb1 from /mnt but it refuses to go, I'm fairly sure that a simple command in a terminal will clear it out! Can anyone tell me what is going on please?

---

### Post by coffeecat on 2015-04-03
It sounds as though you have a line in /etc/fstab that is trying to mount the now defunct Mint sdb1. Removing a folder is not the answer. Post the output of these terminal commands and we can see where to go from there:

```
cat /etc/fstab
sudo fdisk -lu
sudo blkid
```

Highlight the output in the terminal, right-click -> copy, and then you will be able to paste the outputs into your post. Please enclose each output between [noparse]```
 and 
```[/noparse] tags to preserve formatting. You can use the # icon in the toolbar of the advanced message editor for this if you wish.

---

### Post by sudodus on 2015-04-03
Maybe you have an entry (a line) in the file /etc/fstab that assumes that you still have such a device available to be mounted at /mnt/sdb1. In that case you can edit fstab. It might be a good idea to back it up before editing.

```
sudo cp -p /etc/fstab /etc/fstab0
```

```
sudo nano /etc/fstab
```

and remove the line 'with sdb1'.

---

### Post by ortermagic on 2015-04-03
Dear coffeecat thank you for the interest here are the results.

```
ortermagic@cosier:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=50f61fff-1e62-4460-a1bd-3ebe7a51d4b9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=9fffaf86-8850-400e-8f3e-aa8a76a8322d none            swap    sw              0       0
/dev/sdb1 /mnt/sdb1 auto nosuid,nodev,nofail,x-gvfs-show 0 0



ortermagic@cosier:~$ sudo fdisk -lu
[sudo] password for ortermagic: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008cee2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   960030719   480014336   83  Linux
/dev/sda2       960032766   976771071     8369153    5  Extended
/dev/sda5       960032768   976771071     8369152   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000c9325

   Device Boot      Start         End      Blocks   Id  System



ortermagic@cosier:~$ sudo blkid
/dev/sda1: UUID="50f61fff-1e62-4460-a1bd-3ebe7a51d4b9" TYPE="ext4" 
/dev/sda5: UUID="9fffaf86-8850-400e-8f3e-aa8a76a8322d" TYPE="swap" 
ortermagic@cosier:~$ 

```

---

### Post by ortermagic on 2015-04-03
Thankyou sudo as well, I will try your suggestion

---

### Post by ortermagic on 2015-04-03
I will now restart my computer

---

### Post by coffeecat on 2015-04-03
> **ortermagic said:**
> Dear coffeecat thank you for the interest here are the results.

```
ortermagic@cosier:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=50f61fff-1e62-4460-a1bd-3ebe7a51d4b9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=9fffaf86-8850-400e-8f3e-aa8a76a8322d none            swap    sw              0       0
/dev/sdb1 /mnt/sdb1 auto nosuid,nodev,nofail,x-gvfs-show 0 0
```

Be very careful when editing /etc/fstab. Making a backup first as sudodus suggests is a good idea. When you installed Ubuntu, your root partition was designated as sdb1 but it is now sda1. The installer put the comment "# / was on /dev/sdb1 during installation" before the line for your root partition, so be careful **not** to remove the line for your root partition. The line you need to remove is at the end and is:

```
/dev/sdb1 /mnt/sdb1 auto nosuid,nodev,nofail,x-gvfs-show 0 0
```

Which is quite an odd line. Do you know where that came from?

---

### Post by ortermagic on 2015-04-03
I removed the line...```
/dev/sdb1 /mnt/sdb1 auto nosuid,nodev,nofail,x-gvfs-show 0 0
``` made a copy (I think) and restarted, so far so good. Bootup seems to take an age though did i do right?

```
  ortermagic@cosier:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb1 during installation
UUID=50f61fff-1e62-4460-a1bd-3ebe7a51d4b9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=9fffaf86-8850-400e-8f3e-aa8a76a8322d none            swap    sw              0       0


```

---

### Post by sudodus on 2015-04-03
It looks good to me. There should be not complaint: "The disk drive for /mnt/sdb1 is not ready or not present". The bootup speed may depend on other things.

---

### Post by ortermagic on 2015-04-03
Thank you for your help.
coffecat No I have no idea where the odd line came from, unless it has something to do with me making a mistake trying to install mint on my spare hard drive
Has anyone noticed any other anomalies in the outputs I posted?
 I am getting a seamless boot now but there seems to be an extended hang after grub.

---

### Post by coffeecat on 2015-04-03
Doing a bit of searching around, I think that odd line with "auto" instead of defining the filesystem type, and x-gvfs-show in the options is probably from using Disk Utility - now Disks - to mount the Mint partition. Anyway, that's all theoretical now. I'm glad the main problem is fixed. You may need to start a new thread if your bootup time persists in being a problem. When you say "extended hang", what sort of time period do you mean? How long does it take to get from the grub screen to the Ubuntu login screen?

---

### Post by ortermagic on 2015-04-03
After grub the screen goes blankly black and silent for up to 2 minutes then suddenly springs to life, but as you say that is another topic thanks all for your help I will mark this as solved

---

