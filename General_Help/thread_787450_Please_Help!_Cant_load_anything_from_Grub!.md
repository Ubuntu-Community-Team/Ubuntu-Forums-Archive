---
title: "Please Help! Cant load anything from Grub!"
date: 2008-05-08
forum: General Help
---

### Post by persianprez on 2008-05-08
i had installed vista a few days ago and noticed that grub wasnt there anymore, so i loaded up the live cd and did the grub setup(o) thing and root or whatever, so now i cant load anything, i keep getting the "cannot mount selected partition error" and none of the solutions on here are working for me. Right now im using the live cd ubuntu trying out the desktop thing, so im not really using a desktop...I really need a solution soon, please and thanks!!!!

---

### Post by persianprez on 2008-05-08
bump** please people, i have an essay due tomorrow, and all my sources are on ubuntu!

---

### Post by louieb on 2008-05-08
Do you get the GRUB menu? 
Also open applications>accessories> terminal and post your partition table
```
sudo fdisk -l
```
thats a lowercase L at the end.

---

### Post by persianprez on 2008-05-08
ok so someone on another site said this, "you tried and mount both the grub and ntldr in the same partition....the good new is it isn't that serious....the bad news is one, if not both of these 2 loaders are now corrupted...you can use druid on your live cd to try and repair/recover the partition...hope this works good luck" 

how do i go about doing that?

---

### Post by persianprez on 2008-05-08
yes i do get the grub menu, but no matter what i press, it gives me the error "cannon mount partition"

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbc22bc22

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       12623   101394216   83  Linux
/dev/sda2           12624       18954    50853757+   7  HPFS/NTFS
/dev/sda3           18955       19457     4040347+   5  Extended
/dev/sda5           19084       19457     3004123+  82  Linux swap / Solaris

---

### Post by persianprez on 2008-05-08
so what should i do? nothing seems to be working, ive gone through the forums and tried different solutions, still no go :(

---

### Post by persianprez on 2008-05-09
well this freaking sucks, i have no operating systems, boot loader is a piece of shitake mushrooms, and on top of that i cant open my essay *10 pages* whoopdeedoo, i have 5 hours to write all this **** again yay for me, **** vista, **** linux, **** mac, everything crashes on me for the most simple tasks.

---

### Post by louieb on 2008-05-09
ok do a quick and dirty fix to get Ubuntu to boot. 
easiest way is to get a [Super Grub Disk]("http://forjamari.linex.org/projects/supergrub/") it should be able to fix your boot problem. Just follow the prompts.  or heres a good page on it.  [IDBS on SuperGrub]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

Or as an alternate get a   [Knoppix Linux CD]("http://www.knoppix.net/")  boot with it and you will be able to read and write to your hard drive.   There will be icons on the desktop for your Linux and visa installs on the hard drive. ( actually you can do it from the Ubuntu live CD too but I  use the alternated CD, and I can't remember how. to do it with Ubuntu's live CD.  
Good luck.

---

### Post by persianprez on 2008-05-09
the first method isnt working, trying the second momentarily.

---

### Post by strabes on 2008-05-09
The GRUB link in my signature should help you reinstall grub.

---

### Post by persianprez on 2008-05-09
ive tried it all, now im getting 

"error 22: no such partition"

now i know they are there, and they are in the correct format, but when using super grub to boot ubuntu it says it doesnt recognize the partition format or something, but i got windows to boot off of super grub. without the cd in, nothing works;

ubuntu
ubuntu recovery
mem test
windows

none of these work in regular grub! i tried uninstalling and re-installing grub but it doesnt work :( :( :( *sigh*

---

### Post by louieb on 2008-05-09
> **persianprez said:**
> ive tried it all, now im getting 
"error 22: no such partition"
The fact that you get the GRUB menu is good. That means the data in your Linux Partition is good. 
To get GRUB to work again the file /boot/grub/menu.lst will have to be fixed. 

Once you boot with the Knoppix CD  please post file /boot/grub/menu.lst

---

### Post by persianprez on 2008-05-11
heres the menu.lst but i couldve just booted with the ubuntu live cd to get this couldnt i:?

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
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

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
# kopt=root=UUID=b4cefdb5-b36c-48e6-b757-4585d7bfbf0b ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b4cefdb5-b36c-48e6-b757-4585d7bfbf0b ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b4cefdb5-b36c-48e6-b757-4585d7bfbf0b ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by persianprez on 2008-05-11
btw idc if my windows partition wont boot from the grub list as i will GET RID OF VISTA as soon as i fix my grub.  I will be replacing it with linux xp

---

### Post by louieb on 2008-05-11
> **persianprez said:**
> heres the menu.lst but i couldve just booted with the ubuntu live cd to get this couldnt i:?

```

title        Ubuntu 7.10, kernel 2.6.22-14-generic
root        [COLOR=Red](hd0,2)[/COLOR]
kernel        /boot/vmlinuz-2.6.22-14-generic root=UUID=b4cefdb5-b36c-48e6-b757-4585d7bfbf0b ro quiet splash
initrd        /boot/initrd.img-2.6.22-14-generic
quiet

```

Yea you could but Knoppix is what I know. 

Anyway according to the fdisk output you posted earlier   (hd0,2) is incorrect, should be [COLOR=Red](hd0,0)[COLOR=Black] that[/COLOR] [COLOR=Black]should get get it booting Ubuntu again. 

If not then theres something else wrong. next  thing to check will be the [/COLOR][/COLOR]root=UUID=b4cefdb5-b36c-48e6-b757-4585d7bfbf0b  statement. [COLOR=Red][COLOR=Black] 

[/COLOR][/COLOR]

---

### Post by louieb on 2008-05-11
Oh while your at it change the root in your widows entry to (hdo,1)   thats where fdisk shows Vista lives.

---

### Post by persianprez on 2008-05-11
how do i go about doing these?  should i be changing the menu.lst from root (hd0.2) to root (hd0,0)?

btw none of the grub menu items work...the memtest, recovery mode, windows, or ubuntu...so if i just change one, then the others still wouldnt work?

---

### Post by louieb on 2008-05-11
Use you Konppix CD. right  click and choose to mount for read and write.  

Knoppix uses the KDE desktop, so you can use kedit or kate to edit /boot/grub/menu.lst. 

And yes your right the other won't work until you make the same change. 
 
 While you editing do a find on **groot **and make the same change there.

---

### Post by persianprez on 2008-05-11
ok this seems like it would work but i cant get the permissions to save the change, i keep getting this "You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."

---

### Post by louieb on 2008-05-11
Are you using the Ubuntu Live CD or Knoppinx?

As a quick test  boot to grub on your hard  drive highlight the Ubuntu entry and press e to edit then highlight the root statment and press e to edit again, make the change and press enter then press b to boot.

This just makes a temporary change but at least you'll know if its going to work or not.

---

### Post by persianprez on 2008-05-11
everything worked fantastic! hopefully with a few more years of experience on ubuntu ill get as good as you ^-^ im taking linux classes in college next semester hopefully that helps.

one more question; if i install linux xp, will it delete grub again? or does that platform use the same bootloader?

---

### Post by louieb on 2008-05-12
Nice you got it working again. 
Haven't tried Linux XP.  :)But I've tried a dozen or so other Linux distros.  So heres my guess
According to [DistroWatch.com: Use Linux, BSD.]("http://distrowatch.com/") its Fedora and red hat based. 
When installed it will want to replace Ubuntu's GRUB  with its own copy of GRUB. Should be alright.

If you want to use multiple types of Linux its a good thing to understand GRUB.
Check the [IDBS GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm")  its all good, You will want to look at the **chainload** and** configfile** options for sure. 

Good luck in school.

---

