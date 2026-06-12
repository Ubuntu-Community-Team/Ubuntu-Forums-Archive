---
title: "Add/Remove applications problem"
date: 2007-03-16
forum: General Help
---

### Post by merike on 2007-03-16
I added one program and later wanted to add one more. But when I clicked add/remove applications then after opening the window it searches what I already have installed and does so forever. It continuously reads/writes to hard disk, however whole process is still stuck even after ten minutes. I don't think it should take so long, first time when I added a program that scan was slow too, but it was bearable.
While the process is stuck I am unable to open anything else, I can't shut down or anything. I tried couple of times and each time I was forced to hold power button dows until it turns computer off.

---

### Post by kerry_s on 2007-03-16
I never liked that program, always uninstalled it, Just use the real application "synaptic" it's the same thing but without baby-fi-ing.

Press alt+F2 and type> gksu synaptic <or just find it in the menu if they haven't hidden it.

---

### Post by merike on 2007-03-17
I had a weird hunch so I looked around some more. It seems that the main / folder is using 9GB out of of 8.7GB and is 100% full. But how comes? When I first installed Ubuntu it was only couple of GB-s and I have only downloaded updates ever since and added one program. Does Ubuntu have some temporary files folder that could be emptied to free space? Mounted partitions like my Windows one and FAT32 for documents wont add to partition usage, right? How can I find out what's eating space? I don't think I can add partition tool to resize Ubuntu's partition because of the original problem that I described. What about swap partition, how do I know if it's big enough?

That was a lot of questions, hope you can answer those.

---

### Post by Kateikyoushi on 2007-03-17
First follow these instructions to clean up your machine and free up some space. [LINK]("http://ubuntuforums.org/showthread.php?t=140920")
Then check your disk usage with Applications > Accessories > Disk usage analyser.

---

### Post by merike on 2007-03-17
It shows still / in red and 100%, even terminal takes minutes to open if I have firefox open at the same time :(.

---

### Post by Kateikyoushi on 2007-03-17
Try to find out which folder takes up the space, then we can have a better guess what might be wrong.

---

### Post by merike on 2007-03-17
After analyzing disk usage it killed firefox and when I reopened it then it wouldn't respond properly, :(.

From what I understand it shows 13.6GB free? But acts as slow as it had no free space..

---

### Post by Kateikyoushi on 2007-03-17
Could you show the output of this ?
```
free -m
```

---

### Post by merike on 2007-03-17
> **Kateikyoushi said:**
> Could you show the output of this ?
```
free -m
```

```
             total       used       free     shared    buffers     cached
Mem:           186        183          3          0          2         66
-/+ buffers/cache:        114         72
Swap:            0          0          0
```

It doesn't swap at all? Saw another similar thread so I'll post fstab aswell.
```
# /etc/fstab: static file system information.
#
# <file system>         <mount point>           <type>          <options>      <dump>           <pass>
proc                    /proc                   proc            defaults       0        0
# /dev/hda3
UUID=503403af-3347-493d-adf2-4e91b91a4a7c /     ext3            defaults,errors=remount-ro      0               1
# /dev/hda7
UUID=a5d6f01d-3b13-4485-ad24-059f22426edb none  swap            sw             0        0
/dev/hdc                /media/cdrom0           udf,iso9660     user,noauto    0        0
#Added by diskmounter utility
/dev/hda5               /media/hda5             vfat            rw,user,fmask=0133,dmask=0022,uid=1000,gid=1000 0 0
```

---

### Post by Kateikyoushi on 2007-03-17
The problem is that your swap stopped working right now the same thing happened to someone else.

Copy the following commands to terminal.

```
sudo mkswap /dev/hda7
sudo swapon /dev/hda7
```

Also try to reboot to see if it works after a reboot.

---

### Post by merike on 2007-03-17
> **Kateikyoushi said:**
> 
```
sudo mkswap /dev/hda7
sudo swapon /dev/hda7
```


The first gives me no such file or directory.

---

### Post by Kateikyoushi on 2007-03-17
Then copy this to terminal and post the output.
```
sudo fdisk -l
```

---

### Post by merike on 2007-03-17
```
merike@merike-laptop:~$ sudo fdisk -l
Password:
omitting empty partition (5)

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1305    10482381    7  HPFS/NTFS
/dev/hda2            1306        3951    21253995    f  W95 Ext'd (LBA)
/dev/hda3            3952        4864     7333672+  83  Linux
/dev/hda5            2611        3907    10418121    b  W95 FAT32
/dev/hda6            3908        3951      353398+  82  Linux swap / Solaris

```

---

### Post by merike on 2007-03-21
Up?

---

### Post by nikhilk on 2007-03-21
It seems that '/dev/ha6' not '/dev/hda7' is the swap partition. The entry in '/etc/fstab' has been messed up, did you resize or change your partitions in any way lately?. See if the the mkswap and swapon commands work by changing '/dev/hda7' to '/dev/hda6'. You will have to edit the fstab to reflect that.

---

### Post by merike on 2007-03-21
Didn't notice that 6 and 7 are different numbers :). I deleted one partition lately so that's probably it. Now I can get gparted without worrying about crashing while it installs and divide the space I freed.
Thank you.

---

