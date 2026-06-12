---
title: "Swap file - have I got one?"
date: 2007-02-02
forum: General Help
---

### Post by phstpok on 2007-02-02
I've been having a few odd problems, firefox crashing, apps freezing requiring kill command etc. I think it has something to do with my swap file.
Ubuntu6.10, 1Gb ram, 2Gb swapfile on /dev/hda1

fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=3aaacb2d-737b-40fe-a26a-5a0a4b9164fb /               ext3    defaults,error
s=remount-ro,noatime,auto,rw,dev,exec,suid,nouser,data=writeback 0       1
# /dev/hda4
UUID=2364a5a6-989a-4940-a950-5eb75a6501e1 /home           ext3    defaults      
  0       2
# /dev/hda2
# UUID=18916bab-33d7-4614-9

robs@thor:~$ free
             total       used       free     shared    buffers     cached
Mem:       1035680     703112     332568          0      47044     325324
-/+ buffers/cache:     330744     704936
Swap:            0          0          0

So I have no swap file in use. What's the best way to fix this. I presume I need to mkswap then add swapon -a to a startup script, but where? Do I need to set a flag with mkswap to make sure I don't overwrite the mbr? Do I need to mkswap at all. I created the swap partition originally with gparted, then when setting up ubuntu, set /dev/hda1 as swap, /dev/hda3 as / and /dev/hda4 as /home. I don't understand how I've managed to lose it. I have another distro (dreamlinux) on /dev/hda2 which shares /dev/hda1 as swap and /dev/hda4 as /home with no problems.  :confused: 

btw I really don't like the new format of fstab.

---

### Post by phstpok on 2007-02-02
The fstab didn't copy over in full. Here it is again.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=3aaacb2d-737b-40fe-a26a-5a0a4b9164fb /               ext3    defaults,error
s=remount-ro,noatime,auto,rw,dev,exec,suid,nouser,data=writeback 0       1
# /dev/hda4
UUID=2364a5a6-989a-4940-a950-5eb75a6501e1 /home           ext3    defaults      
  0       2
# /dev/hda2
# UUID=18916bab-33d7-4614-91df-b0308979a5b5 /media/hda2     ext3    defaults    
    0       2
# /dev/hda1
UUID=a01f800f-b21f-47e5-a871-d637d0be5c64 none            swap    sw            
  0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by po0f on 2007-02-02
phstpok,

To see if you have a swap partition on /dev/hda, look through the output of `sudo fdisk -l /dev/hda`.  Something like the following should be output:
```
[FONT="Courier New"]$ sudo fdisk -l /dev/hda

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1          16      128488+  83  Linux
**/dev/hda2              17         277     2096482+  82  Linux swap / Solaris**
/dev/hda3             278        3541    26218080   83  Linux
/dev/hda4            3542        5499    15727635    5  Extended
/dev/hda5            3542        5499    15727603+  83  Linux
[/FONT]
```

If a line like the above isn't shown, you don't have a swap partition.  If one does show up, turn it on with `sudo swapon /dev/hdaX`, with X being the partition.

---

### Post by pseudonym on 2007-02-02
You've got a swap partition according to your fstab. 2GB is way too big, though, unless you're using suspend-to-disk or hibernation, or similar. I have 2GB RAM and 512MB swap and it never gets used (but I keep it anyway just in case). 2GB swap won't cause problems, btw, it's just a waste of disk space.

So your app crashes have nothing to do with swap. Try running some of them in a terminal and see what error messages show up when they crash...

---

### Post by phstpok on 2007-02-02
2GB is a large swap, but I work with multiple large image files in the gimp at times, as well as having half a dozen apps running on different desktops, so I'd expect the swap file to get a bit of a workout sometimes. 

Which init file turns on swap during bootup? I dop't know what has turned swap off, but turning it back on should be all that's needed there.

I'll try running my regular apps in terminals as suggested. Should have thought of that myself. I'll redirect errors to files and see what comes up.

Cheers.

---

### Post by bodhi.zazen on 2007-02-02
Your swap should be mounted at boot if fstab is correct.

My thought would be was your swap partition reformatted thus changing the uuid ?

You can list your partitions by uuid with:

```
ls /dev/disk/by-uuid/ -l
```

You could also modify your fstab to this:

> /dev/hda1 none swap sw  0 0

---

