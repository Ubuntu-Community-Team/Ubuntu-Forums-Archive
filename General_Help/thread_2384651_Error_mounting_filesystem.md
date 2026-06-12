---
title: "Error mounting filesystem"
date: 2018-02-09
forum: General Help
---

### Post by xasipots on 2018-02-09
Hello. I`m new to all this with ubuntu but I`m trying to get used to it !!
Anyway. 
The Problem : I insert my sd card on my laptop (ubuntu 16.04) and I get the following error
> 
Error mounting filesystem

Error mounting /dev/mmcblk0p1 at /media/frikots/0403-0201: Command-line `mount -t "vfat" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,shortname=mixed,utf8=1,showexec,flush" "/dev/mmcblk0p1" "/media/frikots/0403-0201"' exited with non-zero exit status 32: mount: /dev/mmcblk0p1: can't read superblock
 (udisks-error-quark, 0)

Please help me, any help would be much appreciated. I don`t know what to do next..What specs of my laptop could help you help me ??? :o

---

### Post by TheFu on 2018-02-10
A few ideas:

Can you mount it from the command line?  Sometimes GUI tools get confused.  ```
sudo mount -t fat -o uid=1000,gid=1000 /dev/mmcblk0p1 /mnt
``` Any errors with this?

Have you checked the file system for corruption?  ```
sudo fsck -t fat /dev/mmcblk0p1
```

Have you reformatted the SD card and tried again?  Occasionally, I've seen flash memory just lose stuff. Formatting the seems to be the only answer. Might want to clone the storage using **ddrescue** first, assuming there is some data on there.  Wish I knew why this happens. IME, it is very seldom, but still can happen.

Wait for a few more ideas from others before doing anything destructive, please.

---

### Post by xasipots on 2018-02-10
Obviously I don`t want to fotmat my card because I have files in there ;)!!!

- for your first suggestion (it needed to be "vfat" not "fat"), i got :

> mount: /dev/mmcblk0p1: can't read superblock


- and checking for errors (the output is the same if i change "fat" to "vfat") i got :

> fsck from util-linux 2.27.1
fsck.fat 3.0.28 (2015-05-16)
/
  Contains a free cluster (2). Assuming EOF.
FAT32 root dir starts with a bad cluster!


what do all these mean ??? can you help me please ..?

---

### Post by TheFu on 2018-02-10
I don't know of anyway to fix it AND retain data on the same device.  Use ddrescue to get the raw bytes off, then try reformatting.  You can run data recovery on the image that you tell ddrescue to make.

If a fresh format doesn't fix it, then the storage is dying/dead. Time to buy a new one.  Might be worth trying to recover/copy files using a different SDHC reader.  Either on a different system or buy a USB reader for $8 if you don't have a few lying around already.

If you google for "ubuntu data recovery" there might be some options.

---

### Post by xasipots on 2018-02-10
I just tried ddresque : 

> 
sudo ddrescue -f --no-split /dev/sda1 /dev/mmcblk0p1 logfile


The process ended like this :

> 
GNU ddrescue 1.19
Press Ctrl-C to interrupt
rescued:    16013 MB,  errsize:       0 B,  current rate:   11206 kB/s
   ipos:    16013 MB,   errors:       0,    average rate:    6218 kB/s
   opos:    16013 MB, run time:   42.91 m,  successful read:       0 s ago
Copying non-tried blocks... Pass 1 (forwards)
ddrescue: Write error: No space left on device


eventhought my sd card is 16GB..

I opened logfile text and saw : 

> 
# Rescue Logfile. Created by GNU ddrescue version 1.19
# Command line: ddrescue -f --no-split /dev/sda1 /dev/mmcblk0p1 logfile
# Start time:   2018-02-10 17:18:48
# Current time: 2018-02-10 18:03:13
# Copying non-tried blocks... Pass 1 (forwards)
# current_pos  current_status
0x3BA800000     ?
#      pos        size  status
0x00000000  0x3BA800000  +
0x3BA800000  0x173C600000  ?


 Do you have any Idea ?? or someone please have any clue ..?? !!!

(thanks :))

---

### Post by TheFu on 2018-02-10
Ouch.  If you ran the ddrescue command posted above, then you just wiped the SD card with whatever was on /dev/sda1 up to the limit (16G?).

I don't think that was your intent, but that is what that command does.

It won't help anymore, that data is gone, but I would have used something like this:
```
sudo ddrescue  /dev/mmcblk0p1 /tmp/my-16g-sdcard.img /tmp/logfile
```

The order of parameters matters greatly.  
ddrescue {source} {target} {logfile}

There is good news, in a way.  If you'd gotten the devices you used backwards, then you would have wiped your OS, boot record, and any other information in the first 16G of the main disk (most likely).

---

### Post by xasipots on 2018-02-10
Anyway thanks dude !!

---

