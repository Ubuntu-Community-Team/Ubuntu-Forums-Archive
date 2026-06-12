---
title: "Grub doenst load anything"
date: 2006-10-07
forum: General Help
---

### Post by bananasareformonkeys on 2006-10-07
When I start my computer, I just get a screen with GRUB_ in the top left corner, and it freezes there.  I can use the live CD and click "Load from primary Harddrive" which then lets me choose either ubuntu or WinXP, but without the CD i cant startup at all.  

Please help.  I followed Bulldog's thread to reinstall grub from the live cd but it didnt help.

here's the fdisk -l:
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6546    52580713+   7  HPFS/NTFS
/dev/hda2            6547        9341    22450837+  83  Linux
/dev/hda3            9342        9729     3116610   82  Linux swap / Solaris

I don't know why hda1 is the boot... that's actually the windows partition and i want to start with ubuntu.

please help

---

### Post by bananasareformonkeys on 2006-10-07
btw, here's my menu.lst file:
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
# kopt=root=/dev/hda2 ro

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=1

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

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

---

### Post by bananasareformonkeys on 2006-10-09
doesn't anyone want to help me??

---

### Post by jalm111 on 2006-10-09
First thing backup your menu.lst (cp -v /boot/grub/menu.lst /home/woot)!!!!

I'm not sure if the LiveCD mounts your /boot, I haven't used for ages but if does not than you can try mounting it. 

You might want to try and boot off the live cd than blow grub away try 
sudo -s
apt-get remove grub
dpkg purge grub (if this doesn't work do dpkg -l | grep grub and see what the GRand Unified Bootloader column has all the way to the left after 'ii')

Now everything needed should be gone out of /boot/grub, if menu.lst is still there than blow that away too (rm -v /boot/grub/menu.lst), don't worry about other stuff if it's in there.

Now reinstall grub (apt-get install grub). Make sure you have it write to the MBR (not sure if it asks this but if it does say yes). If you don't write to the MBR than Microsoft's OS loader will still be in there and yada yada yada.....

Look at the newly generated menu.lst and make sure the installer picked up your OSs

See if this works. Kind of hard to diagnose with no error.

---

### Post by tommcd on 2006-10-09
When you boot, does it look like this:
[http://users.bigpond.net.au/hermanzone/p15.htm#cli](http://users.bigpond.net.au/hermanzone/p15.htm#cli)
If you can boot the system from the live CD, try
'sudo update-grub' from terminal. That might automatically update grub. If that don't work, try using the tutorial in the above link. 
For anything you would ever want to know about grub:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
 Hope this helps.
I don't know why you can't boot. Your menu.lst file looks ok as near as I can tell.

---

### Post by bananasareformonkeys on 2006-10-09
tomm: that's not the screen.  It's not a command line where i can type anything.  It just says GRUB_ and freezes there.


unfortunately its still not working after updating.  I think that the problem has something to do with the fact that hda1, which is flagged as boot, is the windows partition, and hda2 is linux, 3 is swap.  

Maybe i'm way off.  I'm a noob.  I dont know what to do.

---

### Post by Bigbluecat on 2006-10-09
I'd recommend Super Grub Disk:

[http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)

This can let you boot and fix juts about anything.

Extremely useful in these situations. Please do lot's of reading first both on Adrain15's site and Herman's (previously posted).

---

### Post by Herman on 2006-10-09
Hello everyone,
Thanks for recommending my web page on Grub, tommcd and Bigbluecat, I'm glad if it helps people, and if Super Grub Disk (by adrian15) does too.
bananasareformonkeys, those should both help you some, you should be able to boot your system with Super Grub Disk alright. You should also be able to use it to re-install Grub to MBR, and see if that helps. 
I believe in trying the easiest things first.

If that doesn't fix it completely, then probably jalm111's advice is correct. To me, what jalm111 had to say made a lot of sense. Allow me to translate, 
jalm111  thinks that  likely your installation contains some faulty or corrupted Grub files.  He thinks you should uninstall Grub completely from your system, and then install it again brand new.  We're not just talking re-installing  the tiny MBR part of  Grub here, we're talking about removing every last bit of Grub from your system, ('Heavy Duty'), and totally re-installing it fresh and new again, and perfect this time. 
jalm111 has given you the commands you can type into your terminal to do that. You can also just copy them right off the post he wrote and then paste them into your own terminal with your mouse. It's easier, and saves time and typing errors.  
(I'm not sure about that first command though, unless you have a folder called 'woot)!!!!').  :)

I am inclined to agree with jalm111. The menu.lst file given looks correct to me for the sudo fdisk -l output. I also think that the most likely cause of your problem is missing or corrupted files in either /boot/grub, and/or deeper inside the operating system where there are powerful Grub files that can even regenerate the files that are in /boot/grub.

You can try backing up your menu.lst file with this command, (and please make sure you include the space and the 'full-stop' at the end (called a 'period' in some countries), or the command won't work right. ```
cp /boot/grub/menu.lst .
``` Then you can remove all your files in your Grub folder with this command,
```
    sudo rm /boot/grub/*
```Regenerate new Grub files in /boot/grub and install Grub's IPL to MBR simultaneously with this command:
```
    sudo grub-install /dev/hda
```And then re-install your backup of your menu.lst with this command,
```
    sudo cp menu.lst /boot/grub
```If that doesn't work, then you should either try jalm111's commands (except the 'woot!!!!' part of the first one),. Those commands should do the complete job for you, they would be very thorough. If you feel a little nervous with the command line, you can also uninstall Grub with Synaptic Package Manager in 'System'-->'Administration', and re-install it again. That would probably work okay.

Any questions, or anything you don't understand, please don't be shy to ask, 
Regards, Herman :D

---

### Post by jalm111 on 2006-10-14
Heh. sorry I just used woot as some random directory, really you can put it wherever you want as long as you can find it later.

As Herman said, my steps will completely wipe away grub and reinstall it fresh so you can try other less invasive troubleshooting steps mentioned here first.

Let us know how it goes.

-Luke

---

