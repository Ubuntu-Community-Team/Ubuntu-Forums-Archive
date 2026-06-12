---
title: "grub trouble cant dual boot xp and edgy"
date: 2006-12-09
forum: General Help
---

### Post by kelean on 2006-12-09
I an not able to boot both ubuntu and xp right now.  It is one or the other at this time.  I had to reinstall my ubuntu and since then i cannot dual boot. 

I am running XP Pro and Edgy.  I was duel booting both of them until i reinstalled ubuntu.  After the install xp would not boot.  It would have the text from grub about starting xp but that was it.  I tried several things that did not work.  Several things from this forum and super grub.  Nothing worked.  I could not even start xp from super grub so i reinstalled xp.

Once xp was installed I could boot xp but not ubuntu.  I started the live cd and from terminal started grub and followed how to install grub from live CD.

sudo grub
find /boot/grub/stage1
root (hd?,?)
setup (hd0)
quit

All went well but when i rebooted xp was not listed and it booted right into ubuntu.

Here are my fdisk and brub info.

```
kevin@Weezer:~$ sudo fdisk -l
Password:

Disk /dev/hda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1216     9767488+   7  HPFS/NTFS
/dev/hda2            1217        2401     9518512+  83  Linux
/dev/hda3            2402        2434      265072+  82  Linux swap / Solaris

```


```
## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=5502c23e-485d-4a5d-af71-247174d998fc ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=5502c23e-485d-4a5d-af71-247174d998fc ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=5502c23e-485d-4a5d-af71-247174d998fc ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=5502c23e-485d-4a5d-af71-247174d998fc ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=UUID=5502c23e-485d-4a5d-af71-247174d998fc ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=UUID=5502c23e-485d-4a5d-af71-247174d998fc ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```


I have read several threads in the forums and get really confused with all of the different partitions and hard drives in them.  I have a very simple setup as you can see from my fdisk -l output.

How can I get grub back to dual booting xp and ubuntu without starting from scratch (and i have thought about it).

---

### Post by bscbrit on 2006-12-09
Add this to the end of your grub/menu.lst :

```

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Pro Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

---

### Post by kelean on 2006-12-09
can i do that from terminal with sudo grub?

Do I have to update grub when I am finished.

---

### Post by bscbrit on 2006-12-09
At a command line, type:

gksudo gedit /boot/grub/menu.lst

Cut and paste the code I provided to the bottom of the menu.lst file.  Save it.

Reboot the computer.

---

### Post by kelean on 2006-12-09
I did what you said and added the lines to my boot/grub/menu.lst file, rebooted and it started the same straight to ubuntu

---

### Post by bscbrit on 2006-12-09
Did you press 'Esc' during the menu countdown to allow you to choose which operating system you want to boot from?

Edit /boot/grub/menu.lst to ensure that

timeout = 10

#hiddenmenu

Then the menu will show for 10 seconds each time you boot before defaulting to whatever default OS you have selected.

---

### Post by kelean on 2006-12-09
Oops!!  It did work sorry.  The only thing now is that I have to hit Esc key within 3 seconds to bring up the list of boot options.  Thank you for the help.  Now i can dual boot again.  I just have to change /boot/grub/menu.lst file to give me more time.

Once again thanks bscbrit.

---

### Post by bscbrit on 2006-12-09
You're welcome.  See you around the forum....

---

### Post by kelean on 2006-12-10
XP will not boot anymore.  It was going fine I could boot to both xp and ubuntu.  Today I booted into ubuntu for a while.  I rebooted and selected windows from the menu when I got this on a black screen.

[INDENT][INDENT]root  (hd0,0)

filesystem type unknown, partition type 0x7

makeactive

chainloader +1[/INDENT][/INDENT]

When I get this it freezes and I have to restart the computer.

So what do I do now?

---

### Post by bscbrit on 2006-12-10
Well, you might have corrupted your Windows partition.  Did you try to write to it from Ubuntu? (Because you cannot do that!)

It was working so the original problem was solved.  This is something new. If you cannot recover it you might have to re-install windows again and, depending on how lucky you are, it might not trash your Ubuntu installation at the same time.  Back up important data from the OS that are still working before you try to recover the Windows partition.

---

### Post by bscbrit on 2006-12-10
No, perhaps your OK. Windows uses a partition type 07, so it might not be a problem.  Can you show me the current contents of /boot/grub/menu.lst please.

---

### Post by kelean on 2006-12-10
> **bscbrit said:**
> No, perhaps your OK. Windows uses a partition type 07, so it might not be a problem.  Can you show me the current contents of /boot/grub/menu.lst please.

Here it is.

```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		30

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=5502c23e-485d-4a5d-af71-247174d998fc ro

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

title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=5502c23e-485d-4a5d-af71-247174d998fc ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=5502c23e-485d-4a5d-af71-247174d998fc ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=5502c23e-485d-4a5d-af71-247174d998fc ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=5502c23e-485d-4a5d-af71-247174d998fc ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Pro Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

---

### Post by bscbrit on 2006-12-10
Well, the menu.lst seems fine, so it looks like you have a corrupt windows partition on your hard drive.

It looking for a Type 7 (which is what it expects for NTFS) but it doesn't like what it finds.  It looks like you might need to re-install XP again.  Make a linux boot floppy so that you can repair grub from your Ubuntu distro  to use as soon as XP has stopped trashing it. ](*,) 

Of course, as an alternative, do what many of us have done and throw the windows away altogether.  Can't say that I've missed it but I agree that Ubuntu cannot do some of the things that Windows can, although it can a lot more of the things that Windows can't :-D 

Good luck.

---

### Post by kelean on 2006-12-10
thanks for the help Ill try a few things like reinstalling grub like i did be fore.  As I would love to remove windows for good I am not quite ready for that.  

I dont understand it though, all I have done since fixing the problem last night was install the generic kernel and install java runtine and the java browser plugin.

Once again thanks for the help, bscbrit.

---

### Post by adrian15 on 2006-12-11
> **kelean said:**
> thanks for the help Ill try a few things like reinstalling grub like i did be fore.  As I would love to remove windows for good I am not quite ready for that.  

I dont understand it though, all I have done since fixing the problem last night was install the generic kernel and install java runtine and the java browser plugin.

Once again thanks for the help, bscbrit.

In your menu.lst in the Win title where it reads:
root (hd0,0)
put
rootnoverify (hd0,0) and windows will boot.

I would bet that you had Winxp with fat32 and now you have converted to ntfs or something similar.

adrian15

---

### Post by Relain on 2006-12-11
I had the same problems sort of. I had a 3 parition Ubuntu install and i realised i needed XP (for powerpoint sigh) so i gparted myself some more space and an ntfs partition (the forth one on the drive). 

Then after installing windows, no ubuntu boot. I did the live cd thing and yeah most of it worked but i found that the live cd didn't mount my old FS automatically. 

So i did:

sudo su -
mkdir /mnt/temp1
mkdir /mnt/temp3
mount /dev/hda1 /mnt/temp1 
mount /dev/hda3 /mnt/temp3 

this is all pretty obvious i guess but i was initially trying just mount /dev/hda1 and getting errors about the mtab etc. So yeah you have to have somewhere to mount the fs's. The other thing i had to was start grub from the old boot partition (dev/hda1) and then do find.
so to fix i finally did:

cd /mnt/temp1/
grub
find /grub/stage1/
root (hd0,1) 
setup (hd0)

where you gotta put in the right things for root(hd?, ?) etc

just wanted to throw that in incase people were stuck too

---

### Post by kelean on 2006-12-11
Well I wiped the hard drive and installed everything over again.  I  had no trouble with my dual boot until i reinstalled dapper and upgraded to edgy.  Then i installed the generic kernel, thats where all of the trouble came fron AFAIK.  It happened 2 times over the weekend. 

adrian15, I had NTFS from the start.


thanks for the pointers if I decide to upgrade edgy I will keep it in mind.  I am not going to upgrade for a little while as I am tired of upgrading!

Thanks for all of the help.

---

