---
title: "Unable to find swap-space signature"
date: 2007-01-21
forum: General Help
---

### Post by CSMatt on 2007-01-21
It seems that, ever since I upgraded to Edgy, the swap partition always fails.  Edgy still works, probably because I rarely exceed 1 GB of memory usage (which is how much memory I have), but I can't hibernate anymore.  If I boot into failsafe, I get this.

I'm using a Sony VAIO VGN-FE660G.

---

### Post by dcstar on 2007-01-21
> **CSMatt said:**
> It seems that, ever since I upgraded to Edgy, the swap partition always fails.  Edgy still works, probably because I rarely exceed 1 GB of memory usage (which is how much memory I have), but I can't hibernate anymore.  If I boot into failsafe, I get this.


What is in your /etc/fstab file?

---

### Post by hal10000 on 2007-01-21
post your /etc/fstab file and the ouput of [COLOR="Red"]sudo fdisk -l
[/COLOR]

---

### Post by nayo on 2007-01-22
I have the same problem and the same description of my computer.  Here is the file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=963319c0-9e59-4a28-a923-a6ddf5c59c32 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=3abdd9c9-8ddc-4949-931b-38c119251f37 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0




and nothing happens when I do the prompt sudo fdisk -|


any help much appreciated

---

### Post by hal10000 on 2007-01-23
> and nothing happens when I do the prompt sudo fdisk -|
sudo fdisk -l NOTE: It's a lower case L

Please post the output of [COLOR="Red"]free[/COLOR] too.

---

### Post by volkyl on 2007-01-23
I've got the same issue.  (Please try to contain your laughter when you see how badly I need to upgrade my system) ](*,) 

```
$ sudo fdisk -l

Disk /dev/hda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        3649    29310561    c  W95 FAT32 (LBA)

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               2        7650    61440592+   f  W95 Ext'd (LBA)
/dev/hdb2            7651        7779     1036192+  82  Linux swap / Solaris
/dev/hdb3            7780       14946    57568927+  83  Linux
/dev/hdb5               2        7650    61440561    7  HPFS/NTFS

Disk /dev/sda: 1024 MB, 1024966656 bytes
32 heads, 63 sectors/track, 993 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         992      999813+   6  FAT16

$ free
             total       used       free     shared    buffers     cached
Mem:        515860     502212      13648          0       7808     223016
-/+ buffers/cache:     271388     244472
Swap:            0          0          0
```

I'm guessing this is related to the UUID's added during the edgy upgrade to my /etc/fstab file?  What is the purpose of that anyway?

Thanks in advance for any help!

---

### Post by hal10000 on 2007-01-24
@volkyl:
1. [COLOR="Red"]sudo mkswap /dev/hdb2[/COLOR]
2. [COLOR="Red"]sudo swapon /dev/hdb2
[/COLOR]
then try, if your swap space is recognized: [COLOR="Red"]free[/COLOR]
Now in the "Swap" line under the "total" column there should be a value differ from 0.
If this is o.k., then (if not already done) make this change in your /etc/fstab:
```

/dev/hdb2       none            swap    sw               0       0

```
That's all.

The purpose of the UUID's is not need to know wether your swap (or any other) partition is in /dev/hdb1 or e.g. in /dev/hdc63 , but i must admit that is is really new to me too, and i'm used to the traditional way. By now, you have the choice to use UUID or the conventional way to handls partitions.

---

### Post by volkyl on 2007-01-24
Thanks for the advice, hal10000.

Shortly after posting last night, I tried a procedure similar to the one you outlined and it worked.  However, I did not modify the /etc/fstab file to go back to the non-UUID approach.

After powering up this evening, the swap mounted successfully, even though the /etc/fstab used the UUID, not /dev/hdb2.  I'm not sure why it failed last night, but worked tonight.  I'll keep an eye on it, and if it continues to happen, I'll follow your last bit of advice and switch /etc/fstab back to /dev/hdb2, and use the "old way".

Thanks again for post!

volkyl

---

### Post by CSMatt on 2007-01-25
I was able to fix my swap partition with the information you gave volkyl.

---

### Post by Arun2610 on 2007-02-18
Thanks hal1000...
Screwed up my swap partition by allowing slackware installer to run mkswap to modify the same swap partiotion that ubuntu uses...
Tried what u suggested and it worked like a charm thanks again... :)

---

### Post by danbh on 2007-02-26
hi, I seem to be having a similar problem.  I am running some sort of Dell desktop, and my swap seems to be failing to load on boot.  mkswap /dev/swap_location and then swapon -a does in fact work for me.  Note the '-a' directive.  That loads swaps from the fstab file.  But still on reboot, swap agains fails to load.  

I will try the advice given, of changing fstab.  Do you think some sort of bug report should be filed?

---

### Post by danbh on 2007-02-26
great!  the solution worked.

I left a note about this discussion on the following bug report:
[https://launchpad.net/ubuntu/+source/util-linux/+bug/66637](https://launchpad.net/ubuntu/+source/util-linux/+bug/66637)

take care

---

