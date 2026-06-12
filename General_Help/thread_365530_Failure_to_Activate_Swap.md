---
title: "Failure to Activate Swap"
date: 2007-02-19
forum: General Help
---

### Post by Miniberger on 2007-02-19
The past few times I have booted Edgy I noticed that the swap partition failed to activate, and I was given a message telling me this. I'm not sure exactly how long this has been going on although I do know that it was working at one point.

Does anyone have any ideas as to why this might happen?

---

### Post by moshuptrail on 2007-02-19
What is the message?  (exactly)
And could you post a listing of your fstab?
Also, right after booting, dmesg | tail, and post the output.
That should get us started!

---

### Post by dcstar on 2007-02-19
> **Miniberger said:**
> The past few times I have booted Edgy I noticed that the swap partition failed to activate, and I was given a message telling me this. I'm not sure exactly how long this has been going on although I do know that it was working at one point.

Does anyone have any ideas as to why this might happen?

If you are referring to the text message during boot, I get this as well but my swap partition is still working.

I'm not sure what causes the message, but it doesn't seem to actually affect my system.

---

### Post by Miniberger on 2007-02-20
Sorry, I should I have been more specific. This message appears when it checks my main partition every 30th time it boots. It says "Activating swap partition - failed." It then gives a message at the end that indicates that the swap partition has failed to activate.

I have confirmed that the swap is in fact not working (I filled up my physical RAM (512 MB) and it didn't use any of the swap.

---

### Post by dcstar on 2007-02-20
> **Miniberger said:**
> Sorry, I should I have been more specific. This message appears when it checks my main partition every 30th time it boots. It says "Activating swap partition - failed." It then gives a message at the end that indicates that the swap partition has failed to activate.

I have confirmed that the swap is in fact not working (I filled up my physical RAM (512 MB) and it didn't use any of the swap.

Check that you actually have a swap partition, and it is in your /etc/fstab file, then:
```
sudo swapon
``` should enable it (I think that is the right command).

---

### Post by Miniberger on 2007-02-21
First I checked my fstab file which appears to contain my swap partition.

Ok, so I typed in "sudo swapon -a" and I got this message:

swapon: /dev/disk/by-uuid/de67a3a9-f1c3-4c99-9e37-f79cb426dfd4: Invalid argument

What does this mean?

---

### Post by Miniberger on 2007-03-15
Ok, so now the command seems to work, but the swap partition doesn't appear active (with RAM at 90%, swap is listed as being at 0 bytes out of 0 bytes.

Any ideas?

---

### Post by taurus on 2007-03-15
Can you post the output of these commands from a terminal?

```
free
sudo fdisk -l
cat /etc/fstab
```

---

### Post by Miniberger on 2007-03-18
Ok, here it is.

alex@alex-desktop:~$ free
             total       used       free     shared    buffers     cached
Mem:        515560     508768       6792          0      66552     195764
-/+ buffers/cache:     246452     269108
Swap:            0          0          0
alex@alex-desktop:~$ sudo fdisk -l
Password:

Disk /dev/hda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hda2            2551        4143    12795772+  83  Linux
/dev/hda3            4144        9726    44845447+   5  Extended
/dev/hda5            4144        4274     1052226   82  Linux swap / Solaris
/dev/hda6            4275        9726    43793158+   b  W95 FAT32
alex@alex-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2 -- converted during upgrade to edgy
UUID=bb6947b7-2936-4e51-acfd-89d2f70d6fbd / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=de67a3a9-f1c3-4c99-9e37-f79cb426dfd4 swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
# /dev/hda6 -- converted during upgrade to edgy
UUID=44EF-6E2D /mnt/shared vfat defaults,uid=1000,gid=100 0 0

---

### Post by taurus on 2007-03-18
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and replace this line

```
UUID=de67a3a9-f1c3-4c99-9e37-f79cb426dfd4 swap sw 0 0
```
with this one.

```
/dev/hda5   none   swap   sw   0   0
```
Save the change.  Then see if you can mount the swap now.

```
sudo mount -a
free
```

---

### Post by Miniberger on 2007-03-18
Here's what I get:

```
             total       used       free     shared    buffers     cached
Mem:        515560     495040      20520          0      12456     208688
-/+ buffers/cache:     273896     241664
Swap:            0          0          0

```

It doesn't appear to be working...

also I tried 
```
alex@alex-desktop:~$ sudo swapon -a
swapon: /dev/hda5: Invalid argument

```

---

### Post by Miniberger on 2007-03-18
Oh yes and here is the updated fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2 -- converted during upgrade to edgy
UUID=bb6947b7-2936-4e51-acfd-89d2f70d6fbd / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
/dev/hda5   none   swap   sw   0   0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
# /dev/hda6 -- converted during upgrade to edgy
UUID=44EF-6E2D /mnt/shared vfat defaults,uid=1000,gid=100 0 0

```

---

### Post by taurus on 2007-03-18
Try

```
sudo mkswap /dev/hda5
sudo mount -a
free
```

---

### Post by Miniberger on 2007-03-18
Yes! It's working now! Thanks for the help taurus.

Note to others: To activate swap add ```
sudo swapon -a
```

Thanks.

---

### Post by arlen on 2007-03-19
Thanks tarus and miniberger. I had an identical problem and solved it using your method. To recap:

Edit  /etc/fstab and replace the UUID with the correct partition. In my case, /dev/hda2 had been commented out when I upgraded to Edgy.

```
sudo fdisk -l
``` will show you a list of partitions if you're not sure what your swap is.

```
sudo mkswap /dev/hda2
sudo swapon -a
```

It now mounts on boot. Huzzah!

---

### Post by arijarot on 2007-03-20
Thanks for the help. I had the same problem and this fixed it. Cheers!:)

---

### Post by arijarot on 2007-03-22
Ignore post, it's been fixed. thank you.
-------------------------------
Swap was working but now it's not. I can't manage to get the swap to mount/turn on. 

Here is:
```
free
sudo fdisk -l
cat /etc/fstab
```
as follows:

```
 total       used       free     shared    buffers     cached
Mem:        255668     249048       6620          0        832      58072
-/+ buffers/cache:     190144      65524
Swap:            0          0          0

```

```
Disk /dev/hda: 60.0 GB, 60000000000 bytes
255 heads, 63 sectors/track, 7294 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2622    21061183+  83  Linux
/dev/hda2            2623        2814     1542240   82  Linux swap / Solaris
/dev/hda3            2815        7294    35985600   83  Linux

```

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1 -- converted during upgrade to edgy
UUID=b4b6d148-80ec-4bb7-be70-839b32db6250 / ext3 defaults,errors=remount-ro 0 1
# /dev/hda3 -- converted during upgrade to edgy
UUID=e24f8961-4776-4c1c-8bb7-88b74c38806e /home ext3 defaults 0 2
# /dev/hda2 -- converted during upgrade to edgy
UUID=8519e4fd-115d-42f5-9e8c-7f07b673c16d none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

and 

```
sudo swapon -a
```

```
swapon: cannot stat /dev/disk/by-uuid/8519e4fd-115d-42f5-9e8c-7f07b673c16d: No such file or directory

```

anybody have any idea what happened/to do?

---

### Post by taurus on 2007-03-22
Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and replace this line

```
UUID=8519e4fd-115d-42f5-9e8c-7f07b673c16d none swap sw 0 0
```
with this one.

```
/dev/hda2   none    swap   sw   0   0
```
Save it.  Then, run

```
sudo mount -a
free
```

---

### Post by arijarot on 2007-03-22
Thank you, Taurus, This is what I did again and it's working this time after the reboot. Cheers!

---

### Post by Miniberger on 2007-04-21
Unfortunately, my swap is not working (again) after upgrading to Feisty. Sorry I used the wrong code tags but I'm too lazy to fix them. Oops.

Here is what's happening:

[HTML]alex@alex-desktop:~$ free
             total       used       free     shared    buffers     cached
Mem:        515660     499392      16268          0       8012     185016
-/+ buffers/cache:     306364     209296
Swap:            0          0          0
[/HTML]

My fstab:

[HTML]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2 -- converted during upgrade to edgy
UUID=bb6947b7-2936-4e51-acfd-89d2f70d6fbd / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
/dev/hda5   none   swap   sw   0   0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
# /dev/hda6 -- converted during upgrade to edgy
UUID=44EF-6E2D /mnt/shared vfat defaults,uid=1000,gid=100 0 0[HTML][/HTML][/HTML]

If I try to make a swap partition:
[HTML]alex@alex-desktop:~$ sudo mkswap /dev/hda5
/dev/hda5: No such file or directory
[/HTML]

If I try to mount a swap partition:
[HTML]alex@alex-desktop:~$ sudo mount -a
[mntent]: warning: no final newline at the end of /etc/fstab
[/HTML]

And if I try to turn swap on:
[HTML]alex@alex-desktop:~$ sudo swapon -a
swapon: cannot stat /dev/hda5: No such file or directory
[/HTML]

Any help would be much appreciated!

---

### Post by taurus on 2007-04-21
What's the output of this command from a terminal?

```
sudo fdisk -l
```

p.s.  I bet you it is now /dev/sda5.

---

### Post by arijarot on 2007-04-22
> **Miniberger said:**
> Unfortunately, my swap is not working (again) after upgrading to Feisty. Sorry I used the wrong code tags but I'm too lazy to fix them. Oops.

Here is what's happening:

[HTML]alex@alex-desktop:~$ free
             total       used       free     shared    buffers     cached
Mem:        515660     499392      16268          0       8012     185016
-/+ buffers/cache:     306364     209296
Swap:            0          0          0
[/HTML]

My fstab:

[HTML]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2 -- converted during upgrade to edgy
UUID=bb6947b7-2936-4e51-acfd-89d2f70d6fbd / ext3 defaults,errors=remount-ro 0 1
# /dev/hda5 -- converted during upgrade to edgy
/dev/hda5   none   swap   sw   0   0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
# /dev/hda6 -- converted during upgrade to edgy
UUID=44EF-6E2D /mnt/shared vfat defaults,uid=1000,gid=100 0 0[HTML][/HTML][/HTML]

If I try to make a swap partition:
[HTML]alex@alex-desktop:~$ sudo mkswap /dev/hda5
/dev/hda5: No such file or directory
[/HTML]

If I try to mount a swap partition:
[HTML]alex@alex-desktop:~$ sudo mount -a
[mntent]: warning: no final newline at the end of /etc/fstab
[/HTML]

And if I try to turn swap on:
[HTML]alex@alex-desktop:~$ sudo swapon -a
swapon: cannot stat /dev/hda5: No such file or directory
[/HTML]

Any help would be much appreciated!

I had the same problem when I upgraded. For some reason hda... became sda... and that it why it could not be found for me. try creating it using sda.

---

### Post by Miniberger on 2007-04-22
Yes, it did change itself to /dev/sda5, and all other partitions also changed from "hda" to "sda."

However, their names didn't change in /etc/fstab, so I changed the swap name in the fstab to /dev/sda5, mounted it, turned the swap on and now it works. 

Should I also change the names of all of my other partitions to "sda" from "hda" in my fstab? Why did they change?

---

### Post by arijarot on 2007-04-22
> **Miniberger said:**
> Yes, it did change itself to /dev/sda5, and all other partitions also changed from "hda" to "sda."

However, their names didn't change in /etc/fstab, so I changed the swap name in the fstab to /dev/sda5, mounted it, turned the swap on and now it works. 

Should I also change the names of all of my other partitions to "sda" from "hda" in my fstab? Why did they change?

I don't know why they changed or if there is any point in changing the info in fstab-- IMHO, as long as it is working, I would leave things alone.

---

### Post by Miniberger on 2007-04-22
Good point. If it ain't broke, don't fix it.

---

### Post by lupin492 on 2007-10-05
> **arijarot said:**
> Thanks for the help. I had the same problem and this fixed it. Cheers!:)
The same goes for me, but I didn't have to "mkswap". Thanks Taurus, and "cross your fingers" for it to don't  mess the things up in the next upgrade !   <-|

---

### Post by gabrielmenini on 2007-12-04
Thanks, Miniberger.

The tips provided by you did the trick.

---

### Post by NeoFax on 2007-12-04
This fix does not work on a system with a PATA and a SATA drive in the sytem as each reboot changes the /dev/sdX pointer.  The best way to fix this is to get the actual UUID code or LABEL of the partition, then adding this to your fstab file.  You can do this by going to /dev/disk/by-uuid and then typing ls -l.  You will now get an ouput that shows the uuid of each partition and the "old school" /dev/sdX1 attached.  Now do fdisk -l /dev/sdX and figure out which partition your swap is located.  Copy the uuid to fstab and upon next reboot, udev should mount your swap for you.

---

