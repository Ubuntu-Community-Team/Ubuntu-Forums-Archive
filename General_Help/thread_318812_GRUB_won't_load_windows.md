---
title: "GRUB won't load windows"
date: 2006-12-14
forum: General Help
---

### Post by tahnok on 2006-12-14
After I installed something on my ubuntu partition (I forget what) GRUB was missing the option to boot windows. I tried to add it myself by adding this to the menu.list file in /boot/grub

rootnoverify (hd0,0)
makeactive
chainloader +1
boot

When I choose the it, it just goes back to the grub OS selection screen. Any ideas on how to  make it work?

---

### Post by migla on 2006-12-14
Don't know, but maybe the GrubEd script would help...
[http://ubuntuforums.org/showthread.php?t=228104](http://ubuntuforums.org/showthread.php?t=228104)
(link for download at the bottom of the first post)

---

### Post by mcduck on 2006-12-14
Could you run 'sudo fdisk -l' and post the output here?

---

### Post by tahnok on 2006-12-14
here is the output:
"Disk /dev/sda: 118.5 GB, 118526284800 bytes
255 heads, 63 sectors/track, 14410 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13899   111643686    7  HPFS/NTFS
/dev/sda2           13900       14384     3895762+  83  Linux
/dev/sda3           14385       14410      208845    5  Extended
/dev/sda5           14385       14410      208813+  82  Linux swap / Solaris
"

---

### Post by Azakus on 2006-12-14
Replace "rootnoverify" with just "root".
For comparison, here's my grub entry for Windows (first partition on the first harddrive).
```
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

---

### Post by tahnok on 2006-12-14
I tried that configuration, but it did the same thing as it did last time.

---

### Post by mcduck on 2006-12-14
well, the partition sure is right (hd0,0).. You should remove the 'boot' from the end of the windows entry and add a title  though.. Actually what Azakus posted is the exact way how it should work. You can try with both 'root' and 'rootnoverify'

---

### Post by tahnok on 2006-12-14
That is exactly what I did. It still didn't work.

---

### Post by Azakus on 2006-12-14
Post your full menu.lst file with```
cat /boot/grub/menu.lst
```

---

### Post by rlozano on 2006-12-14
> **tahnok said:**
> here is the output:
"Disk /dev/sda: 118.5 GB, 118526284800 bytes
255 heads, 63 sectors/track, 14410 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       13899   111643686    7  HPFS/NTFS
/dev/sda2           13900       14384     3895762+  83  Linux
/dev/sda3           14385       14410      208845    5  Extended
/dev/sda5           14385       14410      208813+  82  Linux swap / Solaris
"

maybe you can try **sd** instead of **hd**, since i think you are using sata and not ide. see if that will help.

---

### Post by tahnok on 2006-12-14
here is the cat /boot/grub/menu.lst
```
#splashimage (hd0,1)/boot/grub/images/GrEdSplash.xpm.gz
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color light-green/black red/black

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1cc
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=9b90b779-e9ea-46df-abc0-6ca3ad1f506c ro
# kopt_2_6=root=/dev/sda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##
title           Windows XP Media Center
root            (hd0,0)
savedefault
makeactive
chainloader      +1

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by rlozano on 2006-12-14
if you  make this 

root            (hd0,0)

to

root (sd0,0).

what is the result?

---

### Post by tahnok on 2006-12-14
It says
```
 Error 23: Error while parsing number
Press any key to continue...
```
then goes back to the OS menu

---

### Post by rlozano on 2006-12-14
sorry, i meant sda0,0. see what happens.

---

### Post by tahnok on 2006-12-14
It gives me the same error as before. Error 23

---

### Post by rlozano on 2006-12-14
hmmm...... maybe you can try several combination, like sda0,1

---

### Post by tahnok on 2006-12-14
Same result as the last two tries.

---

### Post by shane2peru on 2006-12-14
One thing that I can help you with, is that once you get it fixed, you really should put your windows towards the bottom.  What happens is when the Kernel is updated, the menu.lst is re-written, and usually the first choice is overwritten.  If that is where your windows option was before then that would have been the problem, when the kernel was just udpated recently.  Here is my menu.lst ```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
[COLOR="Red"]default		0[/COLOR]

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs


## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```
I deleted some of the commented material.  If you wanted to make Windows boot first, then you would change the default (I highlighted it in red above) to # 5 in my example to boot windows first.  It counts every title line.    I'm going to look around and see if I can find some the grub commands.  I have played around quite a bit with grub, but don't remember all the commands.

Shane

---

### Post by tahnok on 2006-12-14
Thanks shane2peru, that's the reason windows is first, so that by default it booted. If and when I get this fixed I'm going follow your advice.

Also is it possible that I could try a different bootloader, like Lilo? I'm not sure how to install it, but maybe it would work? Maybe its a problem with grub.

---

### Post by shane2peru on 2006-12-14
Ok, here is what I have come up with ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup 
```
We are going to re-install grub, and it should pick up your windows partition.  The reason we are backing it up is because if this fails you are going to boot from your Ubuntu Live CD (you do have one laying around right?), and restore your backup so at least you can get back into Ubuntu.

I have done this once, the thread is [here]("http://www.linuxquestions.org/questions/showthread.php?t=244455&page=2") from another distro.  
Also if you have serious grub problems, this disk is a life saver!  It is called the Super Grub Disk  you can get [it here.]("http://adrian15.raulete.net/grub/tiki-browse_gallery.php?galleryId=2")  I keep a copy just for that purpose.  I have used it before, and I think it will boot into Windows XP, and earlier editions.  Ok, here we go:
```
sudo grub-install /dev/sda
```  This should re-install grub.  Compare your ```
cat /boot/grub/menu.lst
``` to the previous one and see if there is any difference.  Also you should notice that it will fix any mapping issues if you have any.  That is the best thing I can offer at this point.  I hope this helps!

Shane

---

### Post by tahnok on 2006-12-14
It's exactly the same as before......

---

### Post by shane2peru on 2006-12-15
I would give that Super disk a try.  You boot from the disk, and then you can A.  Restore your grub through that.  B.  Boot into your windows and get what you need in case you have to re-install.  I'm sorry I really can't be of much more help to you.  As far as Lilo, I really don't know anything about it.  

Shane

---

### Post by tahnok on 2006-12-15
I tried using the super disk to boot windows, without success. I then removed and installed Grub with the disk. Now when I try and boot windows it goes:
```
Error 13: Invalide or unsupprted exectuable format
```

---

### Post by shane2peru on 2006-12-15
Now what does your ```
cat /boot/grub/menu.lst
``` look like? I assume you can still boot into Ubuntu.  I don't think you ever mentioned what version of Windows you are using?  I'm not sure that I can be of much more help to you.  I'm sorry I don't know more!

Shane

---

### Post by tahnok on 2006-12-15
I'm using media center XP
here is menu.list
```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=64e83d41-3790-4435-86cf-186de1ab716f ro
# kopt_2_6=root=/dev/sda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet
boot

title           Windows 95/98/NT/2000
root            (hd0,0)
makeactive
chainloader     +1
### END DEBIAN AUTOMAGIC KERNELS LIST

```

Thanks for all your help, I probably did something to mess it up by accident, I'm just too new to know what it was.

---

### Post by Azakus on 2006-12-15
Put in "savedefault" before "makeactive" and see if that works.

---

### Post by shane2peru on 2006-12-15
The good news is that it seems as though you Windows is there and healthy, that is why the re-install of grub is picking it up, and seeing it.  Just as a hunch, I don't know if it will do anything, but I noticed that some others don't have the makeacitve line.  At this point it couldn't hurt to remove it, and try it.  Then try and remove the default thing, and see if that works.  Try some combination of those.  Also when you get to your menu, you can press 'e' to edit the line you have highlighted.  Highlight the Windows title and press e look and see it will tell you in the bottom, then you can play with the settings without editing your menu.lst.  You can remove lines, or edit lines and see if that works.  That is a little easier.  Keep playing with those lines and see if you can get anywhere.  

Shane

---

### Post by hikaricore on 2006-12-15
I had this happen to me, I made a boot floppy for winxp since I didn't care to mess with it anymore.
This worked perfectly, just leave it in the drive and pop it in when you're not wanting to boot linux.  *shrug*

***** Humor Incomming, DO NOT ATTEMPT *****

[I]I recently solved this issue by removing my windows partition
Though I know this solution will not work properly for you.   :P[/I]

***** Humor Ending, You may safely continue reading. *****

---

### Post by tahnok on 2006-12-15
I would like to try the windows boot floppy, only this is a laptop without a floppy drive. I've been fiddling with the super grub CD and now booting windows gives me the message GRUB and then just hangs. Is there someway for me to access the files on the windows partition? I could just reinstall windows, but I really need to get some of the files off of there.

---

### Post by Azakus on 2006-12-15
This will kill GRUB, but a reinstall of the Windows MBR will allow you to boot into Windows 100%. You can do this by inserting the Windows Install Disk, going into repair mode by pressing "R" when asked, and running "fixmbr". After that, get a GRUB disk and remake grub.

---

### Post by tahnok on 2006-12-15
I tried fixmbr and it did the same thing it booted and displays GRUB just like before.

---

### Post by shane2peru on 2006-12-16
Ok, here is what you are going to need to do.  You should be able to mount your windows partition from Ubuntu.  You can read NTFS, writing to it is another story.  If you have a usb drive to save files to you can mount this partition and rescue your files.  ```
sudo mkdir /media/windows 
``` then run in a terminal ```
sudo mount /dev/sda1 /media/windows 
```  Now if you want to use nautilus you can run this command ```
sudo nautilus
```  now you can navigate to your /media/windows and find the files you need and save them elsewhere, burn them to a CD, or get store them somewhere safely.  Or you can just use the terminal to get your files.  Then you can re-install Windows.  Also, look up how to backup and restore your ubuntu partition on this forum so that you can re-install ubuntu easily, without having to mess with all the downloads and updates.  Just make sure before you restore your Ubuntu from your backup, you copy down your menu.lst before hand so that when you restore it doesn't overwrite your menu.lst with a bad backup, and you are back to square one.  The resotre process shouldn't mess up your actuall grub installation, however it probably will overwrite your menu.lst which is critical to booting as we have found out.  Also, before that try playing around with the command and using sda0,0 in place of hd  or sd0,0 and remove the makeactive line, and the default line if you haven't done this.  

Shane

---

### Post by tahnok on 2006-12-16
When I try the mount command it gives me this
```
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

---

### Post by Azakus on 2006-12-16
Uh oh. That sounds like your Windows Partition got all corrupted. I had that happen my first time with GRUB, but I restored a back up and got it to work the second time.

---

### Post by shane2peru on 2006-12-16
Hum, that is odd.  I just tried the same thing, and mine mounted.  Can you post the output of ```
dmesg | tail 
```  Also ```
sudo fdisk -l
``` and ```
cat /etc/fstab
```  I'm thinking it is not a menu.lst problem but somehow you may need to check that partition and make sure the file structure is correct.  I have had that problem before in FAT32, but I don't know if you can check the NTFS structure the same way.  I will have to look that up.  If anyone else knows can chime in and help that would be great!

Shane

---

### Post by tahnok on 2006-12-18
Sorry for taking so long to respond, I haven't had inernet access for a few days. Here is the output for the commands you wanted.
dmesg | tail
```
[17179601.888000] Bluetooth: RFCOMM ver 1.7
[17179612.412000] NET: Registered protocol family 10
[17179612.412000] lo: Disabled Privacy Extensions
[17179612.412000] IPv6 over IPv4 tunneling driver
[17179616.152000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17179730.936000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179730.960000] NTFS-fs warning (device sda1): is_boot_sector_ntfs(): Invalid boot sector checksum.
[17179730.960000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17179730.960000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17179730.960000] NTFS-fs error (device sda1): ntfs_fill_super(): Not an NTFS volume.
```

sudo fdisk -l
```
Disk /dev/sda: 118.5 GB, 118526284800 bytes
255 heads, 63 sectors/track, 14410 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       13899   111643686    7  HPFS/NTFS
/dev/sda2   *       13900       14384     3895762+  83  Linux
/dev/sda3           14385       14410      208845    5  Extended
/dev/sda5           14385       14410      208813+  82  Linux swap / Solaris
```

cat /etc/fstab
```
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=45a58ec6-6dde-4c70-9f9e-d67187b4d850 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=e7ceacb0-288f-46bf-9d5f-29f34f278f69 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
```

---

### Post by shane2peru on 2006-12-18
> [17179730.960000] NTFS-fs warning (device sda1): is_boot_sector_ntfs(): Invalid boot sector checksum.
[17179730.960000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Primary boot sector is invalid.
[17179730.960000] NTFS-fs error (device sda1): read_ntfs_boot_sector(): Mount option errors=recover not used. Aborting without trying to recover.
[17179730.960000] NTFS-fs error (device sda1): ntfs_fill_super(): Not an NTFS volume.  This is not good.  It seems as though your NTFS - which is the windows partition has been corrupted.  There are two things that I have found.  This [thread]("http://www.knoppix.net/forum/viewtopic.php?t=7805")  is a similar problem, and they could read there Windows partition with Knoppix.  That may be a possibility to get your info off.  There is only one other solution I can come up with.  I really don't know anything about it, just did some searching, and it may leave you no option but to completely re-install, which at this point, we may be there anyway.  ```
 sudo apt-get install ntfsprogs
```  After that in the terminal, you have a few options ```
ntfs
``` and then type (tab) it will show you all the options you have.  I would start with ```
ntfsinfo /dev/sda1
```  I think this will give you more info about your ntfs partition.   I don't know if you have space, (an external hdd) but if you do, the next thing I would imagine would be a good idea is```
ntfsclone
```  I really can't give you too much help on these as I have never used them.  If you use ```
ntfsclone --help
``` it will explain how to use this command.  Then after all of that I would try ```
ntfsfix /dev/sda1
```  I'm roughly guessing on how to use these commands, you may have to do some searching on these and learn the proper way to use them.  Let us know what you find out.  I really wish I had more experience to help.

Shane

---

### Post by tahnok on 2006-12-19
The ntfsprogs don't work because the drive can't be corrupted. I've given up trying to fix and am going to take into someone who can recover the data off of it. After that I'll simply reinstall. Thanks alot for all of the help you've given me.

---

### Post by shane2peru on 2006-12-19
No problem, sorry we couldn't fix it.   Most install guides do say to back up before installing the OS, this is one of those cases.  They should be able to recover the data.  Probably just the partition table is messed up, or something simple.  I hope.  

Shane

---

