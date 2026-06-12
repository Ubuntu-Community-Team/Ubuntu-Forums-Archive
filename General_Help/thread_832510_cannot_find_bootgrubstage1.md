---
title: "cannot find /boot/grub/stage1"
date: 2008-06-17
forum: General Help
---

### Post by jacobnorton on 2008-06-17
Okay, well I installed Ubuntu no problem. Than I installed Windows Xp on my other partition. Everything went fine, but now my grub is all messed up and i have literally tried everything that i have found to make it work again. I even tried using Super Grub Disk, and that couldnt restore my grub.

I get errors like this:

```

grub> root (hd0,0)

grub> setup (hd0)

Error 17: Cannot mount selected partition

grub>
```

When I try this:

```

find /boot/grub/stage1

```

...it cant find that file.

I am on the live CD right now, and when i go into the filesystem, under the boot folder, there isnt even a folder titled grub. Its just gone.

I am so lost. I even booted up my PC with my windows xp cd, deleted the partition xp was on, and than when i reboot, it just gives me some BS about how windows can't load.

Any help would be much appreciated, even though I've done everything suggested to every other user on this forum.

---

### Post by rbmorse on 2008-06-17
Don't panic. If you run gaprted (system > administration > partition editor) does the partition layout on the disk look like you expect it to look?

---

### Post by jacobnorton on 2008-06-17
It looks fine as far as I can see. Image below.

[img]http://i10.photobucket.com/albums/a148/jacobnorton1/Screenshot-2.png[/img]

Do I need to change it from ntfs to ext3?

I don't think that Windows deleted my Ubuntu partition, because when i go to Places>Computer, Filesystem is still there.

---

### Post by jacobnorton on 2008-06-17
Also, when I viewed Hidden files, and went to /boot/boot/grub/ the only file in there was device.map.

Shouldn't there be stage 1 and 2 in there?

---

### Post by manfer on 2008-06-17
With that partition scheme when you type on grub:

root (hd0, 0) you are referencing that first swap partition. Not /boot there.

Next partition is (hd0, 1), next (hd0, 2) and last one (hd0, 3)

well not exactly, i think the unalocated space does not count so only three partition by now:

swap (hd0,0)
next (hd0,1)
then unalocated space
then (hd0,2)

---

### Post by jacobnorton on 2008-06-17
alright, well i still get this error if i do it with hd0,1:

```

grub> root (hd0,1)

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found

grub> 

```

---

### Post by meierfra. on 2008-06-17
deleted.

---

### Post by logos34 on 2008-06-17
yeah, where is ext3 root?  Is the 'unallocated' really /?  (maybe gparted isn't reading the partition table correct;ly or tha latter is screwed up?)

Maybe you're seeing the livecd filesystem files, and not root (which might not even be mounted)

FYI: When you install windows, it overwrites grub on the MBR.

If you just installed linux, try reinstalling.  But install windows first.

---

### Post by meierfra. on 2008-06-17
Forget about my last post. According to the Gparted snapshot your ubuntu partition is gone.  But you have a huge amount of unallocated space. So  maybe only your partition table is messed up.  testdisk (see my signature) might be able to fix that.

---

### Post by jacobnorton on 2008-06-17
I unmounted the unallocated space and put it to ext3 and all of my ubuntu stuff is there and seems to be intact...but when I load up my computer, it will start to boot, than go black and this error will come up:

```

BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs)

```

I tried booting off of Super Grub Disk, I even tried using the repair grub on the Super Grub Disk, and it said it was successful, but It wont let me load up linux.

Any help now? Should I delete the Windows Partition? Is that messing things up, because i dont really need that partition anyhow.

---

### Post by logos34 on 2008-06-17
> **jacobnorton said:**
> I unmounted the unallocated space and put it to ext3 and all of my ubuntu stuff is there and seems to be intact...

not sure exactly what you mean here (can't 'unmount' unallocated space).

When did you install ubuntu?  'Cause if this is a new install, I'd recommend you backup any saved files to the fat32, then reinstall linux.  It'll take less time than trying to troubleshoot.  If you still have problems after that, then maybe remove windows.

---

### Post by jacobnorton on 2008-06-17
how can i back anything up if i cant even get onto the ubuntu.

Oh and what i meant was, well actually i dont know what i meant, but somehow i got the unallocated space back to the ext3 and all of my stuff was still there.

But now it wont let me mount that partition. I did set that one as boot partition though.

---

### Post by jacobnorton on 2008-06-17
and I am now getting this error when it loads up:

```

target file system doesn't have /sbin/init

```

...So i don't have any clue what to do.

---

### Post by logos34 on 2008-06-18
> **jacobnorton said:**
> how can i back anything up if i cant even get onto the ubuntu.

Oh and what i meant was, well actually i dont know what i meant, but somehow i got the unallocated space back to the ext3 and all of my stuff was still there.

But now it wont let me mount that partition. I did set that one as boot partition though.

Well, you keep saying you can see your stuff, and for that to happen then ubuntu must be mounted.  And if you can mount it, you can copy files to another partition.  But I'm still not clear on your current status

What does gparted show now? 

Also, you never did answer my queation on whether this was a new install.  Because unless there are saved files you can't live without, reinstalling this baby would be a lot easier.  But if you insist on troubleshooting, try TestDisk.  (just know what you're doing before writing any changes to disk)

---

### Post by alimooghashang on 2009-04-29
> **jacobnorton said:**
> 
 
I get errors like this:
 
```

grub> root (hd0,0)
 
grub> setup (hd0)
 
Error 17: Cannot mount selected partition
 
grub>
```
 
When I try this:
 
```

find /boot/grub/stage1

```
 
 

 
the same problem i have...
what to do?
i execute this in Live Mode to repair ubunto boot
thanks
:(

---

### Post by unutbu on 2009-04-29
Here are instructions on running boot_info_script:
[http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3)
Please attach the RESULTS.txt file here.

---

### Post by alimooghashang on 2009-04-29
look at the attachment

---

### Post by alimooghashang on 2009-04-29
look at the attachment

---

### Post by unutbu on 2009-04-29
alimooghashang, right now you have the Windows bootloader installed. 

To install GRUB: 

Boot from the LiveCD.
Open a terminal (Applications>Accessories>Terminal).
Type

```
sudo grub
root (hd0,8)
setup (hd0)
quit

```
Then reboot. 

By the way, you have a /boot partition (sda9). So your stage1 file is located at /grub/stage1 on sda9. So the grub command that should work for you is```
 

find /grub/stage1
```

rather than
```

find /boot/grub/stage1
```

And this grub command should return 
```

(hd0,8)
```

for you. (hd0,8) is GRUB-speak for /dev/sda9.

---

