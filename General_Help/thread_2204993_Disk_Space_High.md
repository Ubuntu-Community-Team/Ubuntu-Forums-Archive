---
title: "Disk Space High"
date: 2014-02-11
forum: General Help
---

### Post by SageOfSmeg on 2014-02-11
Two related questions concerning assessing disk space usage.
 
According to df results my HDD is at either 95% or 77%.
 
```
gjd@gjdpc1:~$ df
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sda1        4032092 3616508    210760  95% /
udev              375996       4    375992   1% /dev
tmpfs             153316     684    152632   1% /run
none                5120       0      5120   0% /run/lock
none              383288       0    383288   0% /run/shm
 
gjd@gjdpc1:~$ df --total
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sda1        4032092 3616516    210752  95% /
udev              375996       4    375992   1% /dev
tmpfs             153316     684    152632   1% /run
none                5120       0      5120   0% /run/lock
none              383288       0    383288   0% /run/shm
total            4949812 3617204   1127784  77%
 
```

Despite reading the man pages for df I’m still not sure which of these figures I should take as gospel (‘df’ or ‘df -–total’), so which is it?
 
 
My other question(s) relate to what happens when disk space usage actually hits 100% and no free space is available. Does Lubuntu stall/freeze/crash? Do any warning message appear (and where)? Can any action be taken interactively, i.e. does Lubuntu prompt for urgent user action or just die?
I’ve looked around in the forums but cannot find a definitive answer to these questions.

Thanks

 
Specs:
Lubuntu desktop 12.04.3
4GB disk, single HDD (/dev/sda1)
768MB SDRAM
CPU Pentium II 350 MHz

---

### Post by IPvFletch on 2014-02-11
I think there's some reserved blocks for the bootloader or partition info which take up that extra space you see there.

BTW you can also do 'du -a / | sort -n | tail -50' [as root ideally] to see which are the biggest files on your system, in case you need to do some cleanup. I happen to have lots of 2-12GB disk images laying around (from OpenStack hacking) so this is a helpful cmd to help me find those so I can nix them.

---

### Post by Impavidus on 2014-02-11
The total number gives the used space and available space of all file systems combined, including the /dev, /run, /run/lock and /run/shm file systems. These are not on your disk, so for your used or available disk space you can ignore them. It appears your disk is 95% full, which isn't surprising if you only have 4GB.

First you get a warning, but when the disk is full, you can no longer login. Some space has been reserved for the root user, so you can still login on the recovery console to get some free space. You can also make free space using a live disk.

A 4GB HDD is the absolute minimum on which you can install Lubuntu nowadays. You'll always have a nearly full disk. If this partition is only part of your disk, make the partition larger. Else, try installing a larger disk, or try moving data to an external drive. You can even move part of the system, like /usr, or the entire system to an external drive. It will not work very fast though.

What does **sudo fdisk -l** say?

---

### Post by SageOfSmeg on 2014-02-12
Thanks for that very helpful reply, just what I wanted.

> **Impavidus said:**
> What does **sudo fdisk -l** say?

```

Disk /dev/sda: 4303 MB, 4303272960 bytes
255 heads, 63 sectors/track, 523 cylinders, total 8404830 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000766e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63     8193149     4096543+  83  Linux
/dev/sda2         8193211     8401994      104392    5  Extended
/dev/sda5         8193213     8401994      104391   82  Linux swap / Solaris
```

I have another 4GB HDD installed in this old machine, currently disconnected but easy to reconnect and format to ext3.
In the meantime I'll move files to an external drive as suggested.

---

### Post by Dennis N on 2014-02-12
Tip: If you use the command **df -h** the result is in bytes, megabytes (M) or gigabytes (G) used, possibly more understandable information:

```
dn@Roxanne:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb7        29G   16G   13G  56% /
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           757M  896K  756M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.9G  900K  1.9G   1% /run/shm
none            100M   20K  100M   1% /run/user

```

---

### Post by Impavidus on 2014-02-12
If you need help deciding how to distribute your directories over both HDDs, just ask.

Tip: so view the disk usage of any particular directory, use **du -s /path/to/directory**.

---

