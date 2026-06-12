---
title: "/bin/sh: can't access tty; job control turned off"
date: 2007-06-19
forum: General Help
---

### Post by Senesence on 2007-06-19
As abruptly as it stopped working, it started up right today......for some reason. 

What I did:

I was on IRC, and someone told me to change the "root=/dev/hda3" in menu.lst to the old UUID format (partition UUIDs can be viewed with the blkid command). This didn't make sense to me, especially when almost everyone before then told me that having it in UUID format would actually be wrong - but ok, I was desparate, and ready to try anything at this point.

I made the modification to UUID through livecd and then continued to try a normal reboot. Long story short - it didn't work, and the guy who suggested it was no longer talking. So I decided to go back an re-re-modify the menu.lst to what it was originally, which was root=/dev/hda3. 

At this point I popped out the livecd, and went on to restart.........fully expecting to see the error again. 

You can imagine my surprise when the filesystem actaully mounted, and my old ubuntu screen was back up and running.

So I have no idea what I did to silence it, or what caused the error in the first place, but I'm back with a fully functional system again.

Thanks to confused57 and wonk-o-matic for their support in the matter.

=====================================================

The story so far:

Still no solution, however this thread did serve in determining what's NOT the cause of the error:

[LIST]
It's not GRUB settings - root=/dev/hda3, and that is my Linux partition. I have also tried booting using the "Super Grub Disk" and implementing the "Automatic Repair Tools" that it features - however the error still appeared, so that takes GRUB out of the equation.
[/LIST]

[LIST]
It's not "fstab" or "menu.lst" entries - I checked them, and they all seem right (all linux entries are set to hda3 - which is my partition).
[/LIST]

[LIST]
The partition and the filesystem are both uncorrupted - Booting through Live CD, I was able to mount the partition in question with no problems, also running e2fsck on the partition returned a "clean bill of health"
[/LIST]

Now I'm not a linux expert (obviously), but from what I have been told, it's the Linux kernel that actually mounts the filesystem - not GRUB. So I though it might be something with the kernel, but then I tried booting with my older kernel versions, and the same error reared it's ugly head.

Is there something else that the kernel uses to mount the filesystem that could be corrupted somehow - and cause the error I describe below?

If anyone has any clue what the problem could be - please help.

==================================================

No, I'm not just installing Ubuntu, or upgrading, or anything else for that matter.

I have been a Dapper user for several months now, and nothing like this error has ever happened to me before.

What I did prior to the error:

In Ubuntu, I copied a .pdf file to my thumdrive. Then I removed the thumbdrive. Then I restarted and booted to windows (I dual boot Ubuntu and XP). While in windows I downloaded a new version of Adobe Reader (so that I could view the .pdf on my thumdrive on windows). After I did that, I restarted again, tried to boot to Ubuntu, but that error was all that I received.

The complete error:

```
mount: mounting /dev/hda3 on /root failed: no such device
mount: mounting /root/dev on /dev/ .static/dev failed: no such file or directory
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /proc on /root/proc failed: no such file or directory
target filesystem doesn't have /sbin/init

BusyBox v1.01 (debian 1:1.01-4ubuntu3) build-in shell (ash)

/bin/sh: can't access tty; job control turned off
```

Everything worked find just a few moments ago, I just don't know what could be causing it.

If anyone could give me specific instructions on how to solve this problem, please do. All my files are on the Ubuntu partitions, so windows (while the only way for me to communicate right now) won't help me get my work done in time. (*Yes, I know I should have backed all my stuff up, but I didn't, and now I'm in a picke.*)

Please help me.

Thanks.

---

### Post by Senesence on 2007-06-19
I still have no solution, but I did some digging and I have additional information for anyone who might be able to provide a solution.

First, my partitions (I have a single Hard Drive from which I boot both Ubuntu and Windows - I got the list by doing "cat /proc/partitions" from the ash terminal that I am kicked to right before Ubuntu boot fails):

**HDA** (from what I can tell this one represents the entirety of my Hard Drive)
**HDA1** (this is the "Recovery" partition that came with my HP computer)
**HDA2** (this is the Windows partition)
**HDA3** (this is Ubuntu Linux)
**HDA4** (and this one is swap)

I found my old Dapper Live CD, and I booted from it in order to run "fsck /dev/hda3" - to see if anything was wrong with my old filesystem. I get back a "clean bill of health" - nothing seems to be wrong with - so I doubt it has anything to do with the filesystem (*which has been working just fine for as long as I used Dapper - just over 6 months)*

So I hope that can help you help me.

PS: I tried to do "mount /dev/hda3" but it wouldn't let me because I don't have permission or something......I need to get my files back, is there any way to do that at this stage through the live cd? Well, I hope I can get my Ubuntu distro running completely again, but if not I need to get my files out at least.

---

### Post by confused57 on 2007-06-19
> **Senesence said:**
> I still have no solution, but I did some digging and I have additional information for anyone who might be able to provide a solution.

First, my partitions (I have a single Hard Drive from which I boot both Ubuntu and Windows - I got the list by doing "cat /proc/partitions" from the ash terminal that I am kicked to right before Ubuntu boot fails):

**HDA** (from what I can tell this one represents the entirety of my Hard Drive)
**HDA1** (this is the "Recovery" partition that came with my HP computer)
**HDA2** (this is the Windows partition)
**HDA3** (this is Ubuntu Linux)
**HDA4** (and this one is swap)

I found my old Dapper Live CD, and I booted from it in order to run "fsck /dev/hda3" - to see if anything was wrong with my old filesystem. I get back a "clean bill of health" - nothing seems to be wrong with - so I doubt it has anything to do with the filesystem (*which has been working just fine for as long as I used Dapper - just over 6 months)*

So I hope that can help you help me.

PS: I tried to do "mount /dev/hda3" but it wouldn't let me because I don't have permission or something......I need to get my files back, is there any way to do that at this stage through the live cd? Well, I hope I can get my Ubuntu distro running completely again, but if not I need to get my files out at least.

You can mount your Ubuntu partition from the live cd:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/hda3 /media/ubuntu
```

Then you should be able to open Nautilus, navigate to your /media/ubuntu folder, then drag & drop your files to an external drive.

Have you tried booting with the pen drive disconnected, then with it connected?
You might want to mount your root partition, then post the output of your menu.lst & fstab:
```
gedit /media/ubuntu/boot/grub/menu.lst
gedit /media/ubuntu/etc/fstab
```

You might want to check the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"

I don't know how using a thumbdrive could be causing the problem your having, maybe posting the output of your menu.lst, fstab, & fdisk -l will show something.

---

### Post by Senesence on 2007-06-20
First, I should thank you for the mounting commands. It's good to know that I can recover my stuff now. (*I guess the fact that I can actually mount the partition also rules out the possibility that the partition itself is somehow "bad"*)

Now, as for the output you told me to get:

menu.lst (I didn't include all the default options stuff that comes in the beginning because it was all commented - assuming that anything preceded by a "#" is a comment):
```
title		Ubuntu, kernel 2.6.15-28-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-28-386
boot

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Microsoft Windows Whistler Personal
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

fstab:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda4       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

fdisk -l:
```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1         688     5201248+  12  Compaq diagnostics
/dev/hda2   *         689        6246    42018480    7  HPFS/NTFS
/dev/hda3            6247       10066    28879200   83  Linux
/dev/hda4           10067       10337     2048760   82  Linux swap / Solaris

```

I'm not an expert (obviously), but from all the threads that I have read which touch on the topic (none providing a solution that works though) all of this seems to be just fine.

Which brings me to something that happened when I tried to shutdown from the Live CD:

You know how when you go to shutdown, you get that ubuntu logo and then a listing under it of all the things that are being shutdown: like shutting down services and closing network connections - stuff like that. Well in this case, it didn't actually make it to shutdown, because the ubuntu screen just popped back into a big terminal looking thing - which did show all the same "shutting things down" with the "[ ok ]" marks on the right - but on the last line there was something that the shutdown procedure seemed to be stuck on, and that was:

```
mount: Fucntion not implementedups...
```

And it just stood like that, until I had to pull the plug and boot to windows again (to write this reply).

So, what do you think?

---

### Post by confused57 on 2007-06-20
Here's instructions by Herman for doing a filesystem check on your Linux partition, using the live cd:
[http://ubuntuforums.org/showpost.php?p=2848047&postcount=2](http://ubuntuforums.org/showpost.php?p=2848047&postcount=2)

You might also try burning a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
you might try using SGD to boot your Ubuntu

---

### Post by wonk-o-matic on 2007-06-20
Ok, I found this: 

Alright, I can see your problem. Reboot and bring the Grub boot menu up by pressing ESC as soon as it asks. The default ubuntu boot option is selected. Press e and select the line beginning with kernel. Press e again and make sure that the option root=/dev/hdaX is really root=/dev/hda3 and not root=/dev/hda1 I suspect it is set to /dev/hda1 (for whatever reason). Change it to /dev/hda3, press ESC and then b (for boot). See if it works now. Please come back and tell me about error messages. If it did work, we have to modify your /boot/grub/menu.lst file (which is trivial).

This is from:
[https://answers.launchpad.net/ubuntu/+question/3548](https://answers.launchpad.net/ubuntu/+question/3548)

If you go to that URL, you'll see the boot up messages mention hda1.  Do you get something similar?  You also need to use hda3.

---

### Post by Senesence on 2007-06-20
sudo e2fsck - C0 -f -p -v /dev/hda3
```
 135393 inodes used (3%)
    2629 non-contiguous inodes (1.9%)
         # of inodes with ind/dind/tind blocks: 9039/145/0
 1941680 blocks used (26%)
       0 bad blocks
       0 large files

  114762 regular files
   11688 directories
     340 character device files
      59 block device files
       3 fifos
     435 links
    8529 symbolic links (8236 fast symbolic links)
       3 sockets
--------
  135819 files
```

sudo e2fsck -f -y -v /dev/hda3
```
e2fsck 1.38 (30-Jun-2005)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  135393 inodes used (3%)
    2629 non-contiguous inodes (1.9%)
         # of inodes with ind/dind/tind blocks: 9039/145/0
 1941680 blocks used (26%)
       0 bad blocks
       0 large files

  114762 regular files
   11688 directories
     340 character device files
      59 block device files
       3 fifos
     435 links
    8529 symbolic links (8236 fast symbolic links)
       3 sockets
--------
  135819 files
```

No change. I still get the error when I try to boot.

[quote=confused57]You might also try burning a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzo...bDiskPage.html](http://users.bigpond.net.au/hermanzo...bDiskPage.html)
you might try using SGD to boot your Ubuntu[/quote]

Will doing this fix my system to work as before - because it's not really worth it if I have to boot with the SGD  each and every time (*assuming that it all works in the first place*).

**wonk-o-matic>**

That's not it. If you look at my previous post, you'll notice that I posted my menu.lst, and that in it it's /dev/hda3 all across the board. Since /dev/hda3 is my ubuntu partition, those entries are fine as they are - right?

============================

It's almost as if the loading method for ubuntu that takes over on boot has a faulty mount function. Is there any way that something like that could have happened?

Because it doesn't seem like a filesystem or grub settings problem - I don't know what's in the middle (the loader?), but to me that seems to be where the problem is. I don't know, just throwing it out there.

I mean I have no idea what it could be at this point.

---

### Post by confused57 on 2007-06-20
I think it would be worthwhile to try SGD, just to see if it's able to boot your Ubuntu partition...SGD is a small download(5-7 Mb) and might take 10-15 minutes from download to cd burn.  I would recommend keeping an SGD on hand, never know when it might come in handy.

---

### Post by Senesence on 2007-06-20
> **confused57 said:**
> I think it would be worthwhile to try SGD, just to see if it's able to boot your Ubuntu partition...SGD is a small download(5-7 Mb) and might take 10-15 minutes from download to cd burn.  I would recommend keeping an SGD on hand, never know when it might come in handy.

Well it's not coming in handy now, that's for sure. I tried almost every single option they have there and it did nothing. I still end up with the same errors, even though I did all that "automatic repair to MBR" and "Boot Linux" stuff. 

I think I'm getting a pretty good idea of what "SGD" was actually made for - and from what I observed it's just a tool to have around when something's wrong with GRUB or the master boot record itself. I don't think it can solve what appear to be internal troubles with Ubuntu's loader itself.

You know I actually do get that Ubuntu loading screen for a second; it gets stuck on "Mounting filesystem" and then the error hits - so that leads me to believe that Grub settings and boot records really have nothing to do with why this is happening.

Is there anything else - some mounting options file in ubuntu maybe - that could be causing something like this?

---

### Post by Senesence on 2007-06-21
Gurus, don't be shy. :)

---

### Post by wonk-o-matic on 2007-06-21
Please try the method where you hit ESC for the grub menu.  I'd be interested to know what you see.

---

### Post by Senesence on 2007-06-21
> **wonk-o-matic said:**
> Please try the method where you hit ESC for the grub menu.  I'd be interested to know what you see.

kernel    /boot/vmlinuz-2.6.15-28-386 root=/dev/hda3 ro quiet splash

It's the same exact thing as in my menu.lst file. That's not it.

---

### Post by Senesence on 2007-06-22
Still no solution, however this thread did serve in determining what's NOT the cause of the error:

[LIST]
It's not GRUB settings - root=/dev/hda3, and that is my Linux partition. I have also tried booting using the "Super Grub Disk" and implementing the "Automatic Repair Tools" that it features - however the error still appeared, so that takes GRUB out of the equation.
[/LIST]

[LIST]
It's not "fstab" or "menu.lst" entries - I checked them, and they all seem right (all linux entries are set to hda3 - which is my partition).
[/LIST]

[LIST]
The partition and the filesystem are both uncorrupted - Booting through Live CD, I was able to mount the partition in question with no problems, also running e2fsck on the partition returned a "clean bill of health"
[/LIST]

Now I'm not a linux expert (obviously), but from what I have been told, it's the Linux kernel that actually mounts the filesystem - not GRUB. So I though it might be something with the kernel, but then I tried booting with my older kernel versions, and the same error reared it's ugly head.

Is there something else that the kernel uses to mount the filesystem that could be corrupted somehow - and cause the error I describe below?

If anyone has any clue what the problem could be - please help.

---

### Post by Senesence on 2007-06-23
As abruptly as it stopped working, it started up right today......for some reason. 

What I did:

I was on IRC, and someone told me to change the "root=/dev/hda3" in menu.lst to the old UUID format (partition UUIDs can be viewed with the blkid command). This didn't make sense to me, especially when almost everyone before then told me that having it in UUID format would actually be wrong - but ok, I was desparate, and ready to try anything at this point.

I made the modification to UUID through livecd and then continued to try a normal reboot. Long story short - it didn't work, and the guy who suggested it was no longer talking. So I decided to go back an re-re-modify the menu.lst to what it was originally, which was root=/dev/hda3. 

At this point I popped out the livecd, and went on to restart.........fully expecting to see the error again. 

You can imagine my surprise when the filesystem actaully mounted, and my old ubuntu screen was back up and running.

So I have no idea what I did to silence it, or what caused the error in the first place, but I'm back with a fully functional system again.

Thanks to confused57 and wonk-o-matic for their support in the matter.

---

### Post by confused57 on 2007-06-23
> **Senesence said:**
> As abruptly as it stopped working, it started up right today......for some reason. 

What I did:

I was on IRC, and someone told me to change the "root=/dev/hda3" in menu.lst to the old UUID format (partition UUIDs can be viewed with the blkid command). This didn't make sense to me, especially when almost everyone before then told me that having it in UUID format would actually be wrong - but ok, I was desparate, and ready to try anything at this point.

I made the modification to UUID through livecd and then continued to try a normal reboot. Long story short - it didn't work, and the guy who suggested it was no longer talking. So I decided to go back an re-re-modify the menu.lst to what it was originally, which was root=/dev/hda3. 

At this point I popped out the livecd, and went on to restart.........fully expecting to see the error again. 

You can imagine my surprise when the filesystem actaully mounted, and my old ubuntu screen was back up and running.

So I have no idea what I did to silence it, or what caused the error in the first place, but I'm back with a fully functional system again.

Thanks to confused57 and wonk-o-matic for their support in the matter.

Glad you got it working...not sure I was that much help, but your /dev/hda3 entries in menu.lst & fstab looked like it "should" work...with my limited Linux experience, I was out of ideas for you to try... good job troubleshooting the problem.

---

### Post by wonk-o-matic on 2007-06-24
Glad you got it working.  

It's very strange, but in the past I've had problems that "seemed" to be solved by re-saving a file after adding a line feed to the last line in the file.

---

### Post by MarseHole on 2007-06-28
I can confirm Senesence's erratic experience. 

Until a week ago my Dapper system had worked problem free. One night however, after installing an routine update (I think it was on the 22.06.2007 and contained mostly libraries for 'Evolution Mail'), I shutdown my machine normally and upon trying to boot up the next morning I was dumped straight into the BusyBox shell and received the dreaded warning:

```
mount: mounting /dev/hda1 on /root failed: no such device
mount: mounting /root/dev on /dev/ .static/dev failed: no such file or directory
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /proc on /root/proc failed: no such file or directory
target filesystem doesn't have /sbin/init

BusyBox v1.01 (debian 1:1.01-4ubuntu3) build-in shell (ash)

/bin/sh: can't access tty; job control turned off
```

After trawling through the posts here I managed to boot from my Ubuntu CD, open up a sensible shell, and backup my important files to my usb drive. I then tried rebooting using all available kernels in normal and safe-modes with no success.

I then checked that the entries in the GRUB menu were all pointing to the correct partition (ie: hda1 for me) and that they also matched **/boot/grub/menu.lst**.

Finally, getting annoyed with the whole thing, I booted using the CD again and edited **menu.lst**, just deleting ***and then rewriting*** the line

```
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/hda1 ro quiet splash
```

As it turned out, the only editor available in my shell was vi, and my editing had gone slightly awry :roll: so when I rebooted I got an error and was taken to the GRUB menu to correct my mistake. Upon correcting the line back to what it was originally (see above), I rebooted and all was well.

Very strange...

---

### Post by omegavirus on 2007-10-03
Hi, I have the same awful error... the curios thing is that I had my ubuntu 7.04 working just fine, then I had decided to use xubuntu and then the nightmare begun... now I have the same error not mather which distribution I use to install ubuntu, using ubuntu 7.04, xubuntu 7.04 and xubuntu alternate 7.04...

From the live CD I'm able to give you this information:

menu.lst

```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=01fe0667-c495-48ba-bf9a-952c5efd294f ro quiet splash locale=es_ES
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=01fe0667-c495-48ba-bf9a-952c5efd294f ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=01fe0667-c495-48ba-bf9a-952c5efd294f /               reiserfs notail          0       1
# /dev/hda1
UUID=865C552D5C55196F /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=45B8-296E  /media/hda6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hdb1
UUID=48B9-665C  /media/hdb1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=f25fa69e-2c36-448c-8bf8-62fc4a376cf7 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

fdisk -l

```
Disco /dev/hda: 40.0 GB, 40020664320 bytes
255 cabezas, 63 sectores/pista, 4865 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/hda1   *           1        1305    10482381    7  HPFS/NTFS
/dev/hda2            1306        2089     6297480   83  Linux
/dev/hda3            2090        4865    22298220    f  W95 Ext'd (LBA)
/dev/hda5            2090        2179      722893+  82  Linux swap / Solaris
/dev/hda6            2180        4865    21575263+   b  W95 FAT32

Disco /dev/hdb: 6448 MB, 6448619520 bytes
255 cabezas, 63 sectores/pista, 784 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/hdb1               1         784     6297448+   b  W95 FAT32
```

Thanks a lot for your help, sorry for my bad technical english... :confused:

---

### Post by MarseHole on 2007-10-10
Hi omegavirus,

Have you tried just deleting and then rewriting the "kernel" line in **menu.lst**? I can't guarantee it'll work, but it did for me.

Hope it works

---

### Post by raymonda on 2007-12-15
I hope my addition might help someone out there.
My system was all working ok, rebooted and then got this drama. After many reboots and fiddling, I went through the BIOS settings. Somehow the reboot screwed things up. 
But one setting was the culprit. In the video setup it defaulted to pci card instead of onboard video.
After correcting this it all worked ok again.

---

