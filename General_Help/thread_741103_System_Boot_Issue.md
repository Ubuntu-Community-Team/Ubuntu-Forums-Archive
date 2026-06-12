---
title: "System Boot Issue"
date: 2008-03-31
forum: General Help
---

### Post by hp_pavilion_39 on 2008-03-31
hi, i'm running Ubuntu 7.10 Gusty Gibbon on my Acer Aspire 5050.  During startup, the following occurs:

Loading GRUBB 1.5    Please Wait. . .

Starting Up. . .

BIOS GRUBB #81 [494350000]  NOT FOUND
[14.270657]  cannot allocate resource region 7:00:000000
[14.814708]  cannot allocate resource region 8:00:000000
[14.270657]  cannot allocate resource region 7:00:000000
[14.814708]  cannot allocate resource region 8:00:000000
[14.270657]  cannot allocate resource region 7:00:000000
[14.814708]  cannot allocate resource region 8:00:000000
CANNOT ALLOCATE RESOURCE REGION


once the above has been shown, the monitor shows a blank black screen.  The only way to get my machine to continue startup, is pressing "alt+F1"
Once "alt+F1" has been pressed, the system startup resumes as follows:

Loading GRUBB 1.5    Please Wait. . .

Starting Up. . .

BIOS GRUBB #81 [494350000]  NOT FOUND
[14.270657]  cannot allocate resource region 7:00:000000
[14.814708]  cannot allocate resource region 8:00:000000
[14.270657]  cannot allocate resource region 7:00:000000
[14.814708]  cannot allocate resource region 8:00:000000
[14.270657]  cannot allocate resource region 7:00:000000
[14.814708]  cannot allocate resource region 8:00:000000
CANNOT ALLOCATE RESOURCE REGION

Continuing Startup. . .

Under continuing startup the rest of the normal startup codes are placed.  Any help towards this problem?  


here is a copy of the contents of "menu.lst"   hope this helps ;)

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
# kopt=root=UUID=ce319a13-7263-4154-979b-bfe92b449e20 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ce319a13-7263-4154-979b-bfe92b449e20 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=ce319a13-7263-4154-979b-bfe92b449e20 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST




--
Thanks

---

### Post by dannyboy79 on 2008-03-31
edit your boot parameters and add the following:

noapic pci=usepirqmask

If that doesn't correct the problem, try:

noacpi

you can do this by hitting F6 in grub, tehn F6 on the boot line, then just add it to the end. if that works, permanently edit /boot/grub/menu.lst

OR

is there a bios update from your computer manufacturer?

---

### Post by hp_pavilion_39 on 2008-03-31
sounds straight forward, but hitting F6 works as if i hit "alt+F1"  .. it just continues startup.  its supposed to enter a system image menu or something right?

---

### Post by dannyboy79 on 2008-03-31
well, you need to get to the grub boot menu. sometimes grub isn't shown by default so keep hitting ESC and then the grub menu should pop up. then do the F6 trick.

---

### Post by hp_pavilion_39 on 2008-03-31
haha, sorry, but i'm a little slow with working things here :P    

after I enter the Grub boot menu, the followign shows:

Ubuntu 7.10, kernel, 2.6.22-14-generic
Ubuntu 7.10, kernel, 2.6.22-14-generic  (recovery mode)
Ubuntu 7.10, memtest86+

enter "noacpi=usepirqmask" into the command line?
thanks

---

### Post by dannyboy79 on 2008-03-31
scroll down and highlight Ubuntu 7.10, kernel, 2.6.22-14-generic, then hit "e" (not F6, sorry, that's for the livecd), that should take you to another screen where there will be various lines, you want to scroll down again until you highlight the kernel line, which looks similar to this:
/vmlinuz-2.6.20-16-generic root=UUID=522585f4-bbc8-4214-b6b4-a56504723995 ro quiet splash
then hit "e" on that line, now use arrow key to go to the very end of the line and add what I told you before to the very end ensuring that you have a space after the last boot option. 

Following my example above, it would look like this:

/vmlinuz-2.6.20-16-generic root=UUID=522585f4-bbc8-4214-b6b4-a56504723995 ro quiet splash noacpi=usepirqmask

then hit enter, then hit "b" to boot up. if that doesn't help, try the other option or even try them both with a space in between them.

Did you check to see if there was a BIOS update for your motherboard?

---

### Post by hp_pavilion_39 on 2008-03-31
ok, thanks.  um..i haven't checked for BIOS updates.  Should I do that?

---

### Post by dannyboy79 on 2008-03-31
yes.

---

### Post by hp_pavilion_39 on 2008-03-31
ok..then i will
as far as the noacpi=usepirqmask part..it still boots, but it says the following at the top:

BIOS GRUBB #81 [494350000] FOUND

but i still need to press "alt+F1"  i have continued as you said, try it in the other options and so on, yet still ending with the same result.

---

### Post by hp_pavilion_39 on 2008-03-31
um..there aren't any BIOS updates for the Acer Aspire series 5050..according to bios-drivers.com

---

