---
title: "Help booting Ubuntu using Wubi"
date: 2007-07-13
forum: General Help
---

### Post by wakefijr on 2007-07-13
Wanted to try Linux so just installed Wubi 7.04.03 on my Win2k machine on a secondary hard drive (H). Everything appears to be OK and get menu on boot up giving me choice of Win2k and Ubuntu. The Win2k option boots up OK but when I try to boot Ubuntu I get as far as a message saying: Booting 'find /wubi/boot/grub/menu.lst' and thats it - the system just sits there (have waited for about half hour to see if anything will happen - patience eh?). The only way out is to hit the reset button on the machine. Anybody help please as I would really like to play with Ubuntu? Needless to say I'm a novice on Linux.........

---

### Post by ago on 2007-07-13
Uninstall and try this: [http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04-minefield-230.72.exe](http://cutlersoftware.com/ubuntusetup/devel/minefield/Wubi-7.04-minefield-230.72.exe)

---

### Post by wakefijr on 2007-07-13
Thanks AGO but still no joy (still sticks with the same message)

---

### Post by tinybit on 2007-07-13
What are the filesystem types for the partitions? NTFS or FAT?

And how much is the disk size? (problem of 137G limit?)

---

### Post by wakefijr on 2007-07-13
The file systems are: C = FAT32, and E,F & H (where WUBI resides) are all NTFS.

Size of H Drive disk = 80Gb (allocated 15 Gb for Ubuntu during install). The other 3 partitions sit on a 40Gb disk.

Thanks

---

### Post by ago on 2007-07-13
Can you try wubi 7.04.01?

---

### Post by wakefijr on 2007-07-13
Just installed 7.04.01 as suggested. Basically getting the same but with one extra line before it grinds to a halt

i.e.

Booting 'find /wubi/boot/grub/menu.lst'

Followed by: 

find --set-root --ignore-floppies /wubi/boot/grub/menu.lst

---

### Post by bean123 on 2007-07-13
In the boot menu, press c to enter console mode, then enter the following command:

cat (hd1,0)/[TAB]

[TAB] is the TAB key.

And you can use fstest to get NTFS information.

---

### Post by wakefijr on 2007-07-13
Thanks guys but I have solved it!! Managed to clear out the "F" partition on the smaller main drive and installed on there. Once done went as smooth as silk and is now working OK.Looks like it didn't like the second hard drive.  Just going to start my first Linux experience.....!!!

---

### Post by ago on 2007-07-13
> **wakefijr said:**
> Thanks guys but I have solved it!! Managed to clear out the "F" partition on the smaller main drive and installed on there. Once done went as smooth as silk and is now working OK.Looks like it didn't like the second hard drive.  Just going to start my first Linux experience.....!!!


wakefijr, it would be important for us to understand why it failed on the other drive, so if you could retry on that drive and follow the instructions above it would be very helpful. Is there anything peculiar about that drive?

---

### Post by tinybit on 2007-07-16
Other people had reported hung when

find --set-root

So I believe there is something wrong with the find of grub4dos.

I will check the code once again.

Thanks for the report.

---

### Post by bean123 on 2007-07-16
> **tinybit said:**
> Other people had reported hung when

find --set-root

So I believe there is something wrong with the find of grub4dos.

I will check the code once again.

Thanks for the report.

When does it happen, is it related to the NTFS code ?

---

### Post by tinybit on 2007-07-16
Did you noticed in our sysoft forum many people reported that find --set-root was leading to a hang (especially with usb drives)? This seems not related to NTFS, but to the hard drive number.

---

### Post by tinybit on 2007-07-17
Try the latest build of grub4dos at [http://grub4dos.jot.com/](http://grub4dos.jot.com/)

---

### Post by ago on 2007-07-17
It's now in minefield 232 
[http://cutlersoftware.com/ubuntusetup/devel/minefield/](http://cutlersoftware.com/ubuntusetup/devel/minefield/)

---

### Post by solidsnake79 on 2007-07-18
I have the same problem with Wubi. I tried also Minefield and still get the same message. I use the W: partition of my 2nd SATA HD (W for Work, no I don't have that many partitions hehe)

I will try to install on my 1st HD which is the same as the 2nd one (WD 250 Gb SATA) if it works it would mean that wubi can't install on 2nd HD :(, but it doesn't matter if it dont work since Windows ain't running while Ubuntu will be. But it would be nice to be able to find the problem.

I would gladly help you guys if you tell me what data you need to study the problem. Let me know if I can help out.

My system is:

CPU: Intel Core2 Duo E6400 (2x 2.13 Ghz 2 Mb L2 cache)
MB: Intel D975XBX
RAM: 2 Gb DDR2-667 Mhz
HD: 2x WD 250 Gb SATA
GPU: ATI X1600 Pro 512 mb

---

### Post by solidsnake79 on 2007-07-19
After a lot of tries on SATA drives it still wouldn't work on the 2nd HD so i tried on my other PC which has 2 IDE drives 1st 40 Gb and 2nd 80 Gb and it worked on the 1st try on the 2nd HD. Hope this info helps you finding why it wont work on secondary SATA drive.

---

### Post by Spanish Monkey on 2007-10-29
[FONT="Arial"]**:)Hello and HELP!:confused:** I have read several others have the PC hanging after installing wubi and selecting the option for ubuntu. I have played with several 'live' versions and thought this might have been the easy install it claimed. Just click enter it said and go get a cup of coffee and it will be done, but instead it was still busy downloading a 695MB file and then the install to ages after that. On the forst run selecting wubi it took ages to set up and then froze (for ages) So I had no choice but to kill all power.. When I rebooted it came up with this same command --- **Booting 'find/wubi/boot/grub/menu. lst'**

I should have just put Ubuntu on another partition but since this claimed that it could go on my windows partion I figured give it a go. It is a 160 GB partioned hard drive but considering wubi was designed to run on the C drive with windows, and as I did not know if it would run on the Fat partition as well or even the Linux ext3 I set aside previously, I just gave in at a weak moment late at night and went for that 'cup of coffee'

[IMG]C:\Documents and Settings\micros\My Documents\My Pictures\wubi install2.jpg[/IMG]

Now I must say I dont know what to do.. I do have wubildr.mbr, wubildr, in 'C' but I see no 'boot.ini' :(  what now? Is there a way to install it without unistalling everything and would this even be the problem?
Should I just delete everything and install it on the other partition..which is best? Will it even run on a fat32 partition? is Linux ext 2 or 3 better?

and below are the c:\wubi\boot\grub as well as in c:\wubi\boot\winboot files you asked another to post this is what mine say..

Thanks for any help
The Monkey Man

Running Win XP SP2
Compaq 1.7 Pentium (I know a fossil)
1280 RAM
dual 160 hard drives

**WINBOOT LIST**[/FONT]
hiddenmenu
default 0
timeout 0
fallback 1

title find /wubi/boot/grub/menu.lst
find --set-root --ignore-floppies /wubi/boot/grub/menu.lst
configfile /wubi/boot/grub/menu.lst



[FONT="Arial"]
**GRUB MENU LST**[/FONT]
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'boot'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		1

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
# kopt=find=/wubi/boot/linux ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=find --set-root --ignore-floppies /wubi/boot/linux

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-15-generic
		find --set-root --ignore-floppies /wubi/boot/linux
kernel		/wubi/boot/vmlinuz-2.6.20-15-generic find=/wubi/boot/linux ro quiet splash
initrd		/wubi/boot/initrd.img-2.6.20-15-generic
boot

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
		find --set-root --ignore-floppies /wubi/boot/linux
kernel		/wubi/boot/vmlinuz-2.6.20-15-generic find=/wubi/boot/linux ro single
initrd		/wubi/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
		find --set-root --ignore-floppies /wubi/boot/linux
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

title Ubuntu (Original Kernel)
find --set-root --ignore-floppies /wubi/boot/linux
kernel /wubi/boot/linux find=/wubi/boot/linux setup_iso=ubuntu-7.04-alternate-i386.iso quiet splash ro
initrd /wubi/boot/initrd
boot

---

### Post by ago on 2007-10-29
You may want to try 7.10. 

Uninstall wubi 7.04 first, then run "chkdsk /r" from windows, make sure you do not have any wubi folder, wubildr* file or menu.lst anywhere.

Then grab the latest version in [http://wubi-installer.org/devel/minefield](http://wubi-installer.org/devel/minefield)

That will require a new download unfortunately, but you will be on the new Ubuntu version.

---

### Post by Spanish Monkey on 2007-10-30
Many thanks, but now perhaps a stupid question.. how should I delete wubi from Windows being sure to get every last bit? (as I have heard other complaints after uninstall that pieces of the program were left here and there) Is it enough just to use the Start>Control Panel>Add Remove programs mode or is there a better way to delete this program before reinstalling? When I delete in this maner how can I be sure all is wiped before reinstall and potential conficts?

thanks again

---

### Post by ago on 2007-10-30
add/remove should do the job

---

