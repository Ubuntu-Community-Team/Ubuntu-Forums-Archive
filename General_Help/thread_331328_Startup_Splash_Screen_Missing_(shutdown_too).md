---
title: "Startup Splash Screen Missing (shutdown too)"
date: 2007-01-04
forum: General Help
---

### Post by davidshere on 2007-01-04
Either I'm really bad at searching or a similar question hasn't been posed.  At startup, I am not getting the splash screen proudly featured here:

[https://wiki.ubuntu.com/EdgyReleaseNotes?#head-5a3364105deb3bd323ac3ffa2f228973a0171b61]("https://wiki.ubuntu.com/EdgyReleaseNotes?#head-5a3364105deb3bd323ac3ffa2f228973a0171b61")

Instead of the splash screen, I get a blank text screen with a cursor in the upper left corner.  I am running Edgy 6.10 on a Dell Dimension 3000.  The problem started when I upgraded from Dapper.  I've installed Edgy on two other machines here and they don't have the problem.

Any advice would be greatly appreciated.  Showing off Ubuntu to Windows-lovers loses some of its appeal when there's no pretty splash screen at startup.

Thanks
Dave Shere
Information Technology
Steele Rubber Products

---

### Post by energiya on 2007-01-04
I think it could be your /boot/grub/menu.lst file. You should have "quiet spash" on the end of the kernel line.
Just to be sure, could you please post your /boot/grub/menu.lst file ?

---

### Post by davidshere on 2007-01-04
Thanks.  It does appear to be there:
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		11

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
# kopt=root=UUID=d0ac0178-4d92-4a9b-aab8-3240728c3c66 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=d0ac0178-4d92-4a9b-aab8-3240728c3c66 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=d0ac0178-4d92-4a9b-aab8-3240728c3c66 ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=d0ac0178-4d92-4a9b-aab8-3240728c3c66 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=d0ac0178-4d92-4a9b-aab8-3240728c3c66 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=d0ac0178-4d92-4a9b-aab8-3240728c3c66 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=d0ac0178-4d92-4a9b-aab8-3240728c3c66 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.12-10-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=UUID=d0ac0178-4d92-4a9b-aab8-3240728c3c66 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=UUID=d0ac0178-4d92-4a9b-aab8-3240728c3c66 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=UUID=d0ac0178-4d92-4a9b-aab8-3240728c3c66 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=UUID=d0ac0178-4d92-4a9b-aab8-3240728c3c66 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb2
#title		Microsoft Windows XP Professional
#root		(hd1,1)
#savedefault
#makeactive
#map		(hd0) (hd1)
#map		(hd1) (hd0)
#chainloader	+1


```

---

### Post by energiya on 2007-01-04
It seems ok to me... this is weird
have you tried 
```
sudo update-grub
```
and does any error apear on the prompt? becouse if an error ocours, the boot kills the nice spash screen...
removing the quiet will make your screen output all that happens when your linux boots.

Can't think off anything else...

---

### Post by davidshere on 2007-01-04
I did update-grub, no problems, reset, still no splash screen.  I removed "quiet splash" from the boot line, now I have an all-text load.  

What do you mean by "the boot kills the splash screen"?

Results from update-grub:

```
root@raptor:/# update-grub
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.17-10-386
Found kernel: /boot/vmlinuz-2.6.15-27-386
Found kernel: /boot/vmlinuz-2.6.15-26-386
Found kernel: /boot/vmlinuz-2.6.12-10-386
Found kernel: /boot/vmlinuz-2.6.12-9-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

root@raptor:/# 

```

---

### Post by davidshere on 2007-01-04
I see the part that has "Searching for splash image ... none found, skipping ..." -- why would that file be missing?

I have Edgy 6.10 on a virtual machine, and the splash works there.  Let me check that.

---

### Post by davidshere on 2007-01-04
This is the menu.lst  from the Edgy 6.10 virtual machine:```


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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
# kopt=root=UUID=cd90b73c-2af5-4ad8-b46b-09f88715104a ro
# kopt_2_6=root=/dev/sda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```

---

### Post by quartzy on 2007-01-04
It would seem to me that the splash screen itself is missing.

Try this:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_alternate_boot_splash_screen]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_alternate_boot_splash_screen")

You may need to run update-grub again after doing that. See if it fixes the 

Searching for splash image ... none found, skipping ...

line.

---

### Post by energiya on 2007-01-04
first, restore the "quiet splash" on the kernel line...
if you like the standard Ubuntu splash, you could try
```
sudo apt-get install usplash-theme-ubuntu
sudo update-grub
```
I'm not on my computer now, so I can't test ...

---

### Post by davidshere on 2007-01-05
Thanks... I tried all that... still no splash screen.

Thanks anyway for your help.  I'm giving up now.

---

### Post by Buck2348 on 2007-01-05
> **davidshere said:**
> Thanks anyway for your help.  I'm giving up now.

I read your thread while trying to restore my boot usplash.  My menu.lst was corrupt--I thought I had removed the "quiet" from "quiet splash" but that's not what was in the file.  Anyway that fixed mine.  I noticed one difference between my menu.lst and yours--I doubt this is the problem but will tell you anyway, just in case.  The relevant part of my file:
> title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb2 vga=769 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
savedefault
boot
Notice the vga=769?  I don't know exactly what that means but I think the usplash images are particular about the resolution.

Buck

---

### Post by energiya on 2007-01-05
> **Buck2348 said:**
> I read your thread while trying to restore my boot usplash.  My menu.lst was corrupt--I thought I had removed the "quiet" from "quiet splash" but that's not what was in the file.  Anyway that fixed mine.  I noticed one difference between my menu.lst and yours--I doubt this is the problem but will tell you anyway, just in case.  The relevant part of my file:

Notice the vga=769?  I don't know exactly what that means but I think the usplash images are particular about the resolution.

Buck

Yes, you could try that (I use it too). Here is the table
```

                      640x480  800x600 1024x768 1280x1024 1600x1200
-----------------+---+--------+----------+-----*----+----------+---------
256 (8 bit)       |  769        771        773          775          796
32,768 (15 bit) |  784        787        790          793          797
65,536 (16 bit) |  785        788        791          794          798
16.8M (24 bit)  |  786        789        792          795          799

```

(I have taken this from DaveBorealis's post [here]("http://ubuntuforums.org/showthread.php?t=316261&highlight=vga+table"), so credit goes to him :) )

---

### Post by Buck2348 on 2007-01-05
I'm getting the usplash screen I installed (peace theme) between power-up and the boot menu, then the standard ubuntu screen after that.  I haven't seen this problem mentioned here.  Any idea how to fix that?

Thanks,
Buck

Edit:  Never mind--I fixed it finally.  I was getting the usplash during reboot power-down but not during bootup.  Running the command
```
sudo dpkg-reconfigure linux-image-$(uname -r)
```
and then fixing the menu.lst where that command screwed it up was what did it.

---

