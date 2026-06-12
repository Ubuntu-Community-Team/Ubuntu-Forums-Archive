---
title: "Grub info for issue with quad-boot"
date: 2007-04-07
forum: General Help
---

### Post by accludetuner on 2007-04-07
I've searched online and on this forum and haven't found anything quite the same.

I have a quad-boot system with:

Ubuntu CE - 2.6.17.10 & 11 - (hd0,0) sda1
Ichthux CE - 2.6.15.26 & 28 - (hd0,1) sda2
Ubuntu 64-bit - 2.6.17.10 - (hd1,0) sdb1 (unaltered)
Ubuntu 64-bit - 2.6.17.10 - (hd1,2) sdb3 (to be altered)

I know this seems excessive and unnecessary but I have my reasons for the quad-boot.  I've got 64-bit machine so I've installed that version, but it is missing all of the awesome Christian features of the ubutnu CE and kubuntu Ichthux so I did two installs so that I could alter one 64-bit and add those features play around with it.  I wanted individual Ichtux and CE even though you can add either gnome or kde environment to each, I wanted them seperate as well.  I'm trying to dig into ubuntu and perhaps start getting involved in the development and testing of things.

Anyways, after install, and after editing /boot/grub/menu.lst to my liking, I had a successful quad boot system with all 4 versions functioning correctly with zero issues.  Grub worked perfect.  I then started installing updates one OS at a time.  After a kernel update for one version, Grub is totally messed up now.  It lists 25+ memtest options, 20 kernel options, and lists wrong boot locations and root.  I can manually edit each entry and boot into all 4 just fine.  None of the /boot/grub/menu.lst files for any of the OS's reflect anything like what is shown in grub now.  I've tried editing all 4 and it has no effect on grub.  For now, I'm just manually editing grub depending on which one I want to boot to.

So what am I missing and how can I prevent this from happening again when there's a new kernel update for any OS version?

Thanks in advance for your help!

---

### Post by accludetuner on 2007-04-08
The info shown in /etc/fstab on sda1 (hd0,0) and in /boot/grub/menu.lst did not match what was being shown in grub.  I then tried a few things and finally got it to do what I want it to.  It is all good for now, but we will see what happens after the next kernel update.

Here's what to do in case anyone else runs across something similar.


make note of all of your partitions and what's on them by using this command.  use a liveCD and go to terminal and type
```
sudo fdisk -l
```

should pop a list of all your partitions.  just make sure you take note of which one you know has your linux OS on it.  (like- /dev/sda1  or  /dev/hda1  or whatever)

Then, to see what your actual fstab contains (not the live CD version) you have to do a little more.

xxxx= your linux partition ex. hda1 or sda1 shown in the fdisk info
```
sudo mkdir /media/xxxx
sudo gedit /etc/fstab
```

add the following line of code and save and exit back to the terminal  (xxxx=your linux partition)
```
/dev/xxxx /media/xxxx ext3 defaults 0 1

```

in the terminal type 
```
sudo mount -a
sudo gedit /media/xxxx/boot/grub/menu.lst
```

make sure the correct boot info is listed for your linux partitions (hd0,0 is your first hard drive, first partiton - hd0,1 is first HD, second partition - hd1,0 is second HD, first partiton and so on....)  hda1 or sda1 is usually hd0,0 so it looks something like this:

```
title Ubuntu for winners
root (hd0,0)
kernel /boot/vmlinuz-2.6.17-11-generic root=/dev/sda1 ro quiet splash
initrd /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Windows for losers
root		(hd1,1) 
savedefault
makeactive
chainloader	+1
```

this should all be good except you may have to change "root (hd0,0)" for either to make it match with what drive/partition your linux is on.  For some reason, mine were all screwed up and showing hd2,0 when it should have been hd0,0 and so on.


save if you made any changes and exit gedit and type "exit" in the terminal.  reboot without the liveCD.  Next time grub loads, see if it will load linux fine.

if that did not take care of it, you can still edit the grub entries manually at the bootloader and find "the magic combination".  at the menu where it lists all of the available OS's/kernels highlight the one you are trying to boot into and type "e" to edit the commands manually.  hit "e" again to edit the line that you want to.  You have to edit them one line at a time.  You will probably have to edit the root line and the kernel line.  For example, mine showed 

```
root **(hd[B]2**,0)[/B]
kernel /boot/vmlinuz-2.6.17-11-generic root=/dev/**sd[B]b**1[/B] ro quiet splash
```

& needed to be

```
root **(hd[B]0**,0)[/B]
kernel /boot/vmlinuz-2.6.17-11-generic root=/dev/**sd[B]a**1[/B] ro quiet splash
```

type "b" to boot after you have made the necessary changes.  It will either boot successfully or give you an error (usually 15 or 17).  Keep trying until you get the right "(hdx,x)" and "root=/dev/xxxx".    

Once you find the "magic combination" and boot sucessfully, you can then edit the menu.lst properly so that you do not have to manually edit it everytime you boot with this command.  

```
sudo gedit /boot/grub/menu.lst
```

and again, correct the root and kernel root paths properly


I only went through all of this because the menu.lst from all 4 OS's did NOT match what was actually shown in the grub boot loader.  Maybe a lot of this is unecessary for most of you guys but I had to do this to get it straightened out.  All menu.lst changes made (for all 4 OS's) had zero effect until I went through all of this.  Now it is working fine again.

---

### Post by accludetuner on 2007-04-08
Here's my current fdisk -l info:

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6562    52709233+  83  Linux
/dev/sda2            7200       13815    53143020   83  Linux
/dev/sda3           13816       14593     6249285   82  Linux swap / Solaris
/dev/sda4            6563        7199     5116702+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 120.0 GB, 120000000000 bytes
255 heads, 63 sectors/track, 14589 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        6558    52677103+  83  Linux
/dev/sdb2            6559        7310     6040440   82  Linux swap / Solaris
/dev/sdb3            7311       13952    53351865   83  Linux
/dev/sdb4           13953       14589     5116702+  82  Linux swap / Solaris

Disk /dev/hda: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2482    19936633+   b  W95 FAT32

Disk /dev/hdb: 40.0 GB, 40060403712 bytes
255 heads, 63 sectors/track, 4870 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        4870    39118243+   b  W95 FAT32

Disk /dev/sdc: 1009 MB, 1009254400 bytes
255 heads, 63 sectors/track, 122 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         122      979933+   b  W95 FAT32

```



FSTAB info:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=ba8df7cf-99e8-4fc6-bf21-6c1d7cb916a9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=005df1ad-7b74-4c6b-b255-3167314b847a /media/ichthuxCE ext3    defaults        0       0
# /dev/sdb3
UUID=480f7e68-8114-4ef9-9571-a5768c9c2de8 /media/ubuntu64 ext3    defaults        0       0
# /dev/sdb1
UUID=d7f993ed-0aeb-47b1-8d58-3fd4b19ca70c /media/ubuntu64-hacked ext3    defaults        0       0
# /dev/sda4
UUID=5c3b5170-31d6-4328-9108-f288600491d5 none            swap    sw              0       0
/dev/hdc 	/media/cdrom0	udf,iso9660 	user,noauto 	0 	0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1   /media/hda1   vfat    iocharset=utf8,umask=000  0    0
/dev/hdb1   /media/hdb1   vfat    iocharset=utf8,umask=000  0    0
/dev/sdc1   /media/sdc1   vfat    iocharset=utf8,umask=000  0    0
```


and menu.lst info:

```
## ## End Default Options ##

title		Ubuntu CE, kernel 2.6.17-11-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title		Ubuntu CE, kernel 2.6.17-11-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-11-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.17-11-generic
boot

title		Ubuntu CE, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu CE, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu CE, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Kubuntu Ichtux, kernel 2.6.15-28-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/sda2 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-28-386
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Kubuntu Icthux, kernel 2.6.15-28-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-28-386 root=/dev/sda2 ro single 
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Kubuntu Ichthux, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda2 ro quiet splash 
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Kubuntu Ichthux, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/sda2 ro single 
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title		Kubuntu Ichthux, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin  
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 64-bit CE PH Edition, kernel 2.6.17-10
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sdb1 ro quiet splash 
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 64-bit CE PH Edition, kernel 2.6.17-10 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sdb1 ro single 
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb1.
title		Ubuntu 64-bit CE PH Edition, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title		Ubuntu 64-bit, kernel 2.6.17-10
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sdb3 ro quiet splash 
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title		Ubuntu 64-bit, kernel 2.6.17-10
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sdb3 ro single 
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb3.
title		Ubuntu 64-bit, memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin  
savedefault
boot
```



maybe this will help someone out there?!?!?

---

