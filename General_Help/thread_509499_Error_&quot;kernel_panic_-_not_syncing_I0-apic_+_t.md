---
title: "Error: &quot;kernel panic - not syncing: I0-apic + timer doesn't work! boot with apic&quot;"
date: 2007-07-25
forum: General Help
---

### Post by decilling on 2007-07-25
this is the 4th time i have installed ubuntu threw wubi i have tried it on both hard drives but i still get this message.

this is after running the installer and then rebooting from xp i select ubuntu from the boot menu and this comes up

booting 'ubuntu'

(hd1,0)
filesystem type is ntfs, partion type 0x7
   [linux-bzimage, setup=0x1c00, size=0x1a82cc]
   [linux-initrd @ 0x1f85e000, 0x7918a5 bytes]
[    41.516068] ..mp-bios bug: 8254 timer not connected to 10-apic
[    41.694871] kernal panic - not syncing: I0-apic + timer doesn't work! boot with apic=debug and send a report. then try booting with the 'noapic' option
[   41.694873] _  

thats waht it says :( no idea waht to do, i used to have ubuntu and installed it the same way without a problem. i am on windows xp pro incase it matters.

---

### Post by tuxcantfly on 2007-07-26
open the file C:\wubi\boot\grub\menu.lst in Windows with notepad or wordpad

find the line towards the section(s) that says

title Ubuntu ...etc...
find --set-root --ignore-floppies /wubi ...etc...
kernel /wubi/boot/linux ...etc...
initrd /wubi/boot/initrd.gz ...etc...

and at the end of the line that begins with "kernel", add in, without quotes, "noapic", then save the file and reboot, hopefully it'll work

---

### Post by decilling on 2007-07-26
I dont have a C:\wubi\boot\menu.lst, all i have is   F:\wubi\boot in that directory i have 2 folders, one called grub and the other winboot and 2 files, one called linux and the other initrd. wubi installed to my second hard drive, i checked C:\ aswell just incase. 

so no luck im afraid thanx for the reply though :)

---

### Post by tuxcantfly on 2007-07-26
> I dont have a C:\wubi\boot\menu.lst, all i have is F:\wubi\boot in that directory i have 2 folders, one called grub and the other winboot and 2 files, one called linux and the other initrd. wubi installed to my second hard drive, i checked C:\ aswell just incase.


In that case...

open the file F:\wubi\boot\grub\menu.lst in Windows with notepad or wordpad

find the line towards the section(s) that says

title Ubuntu ...etc...
find --set-root --ignore-floppies /wubi ...etc...
kernel /wubi/boot/linux ...etc...
initrd /wubi/boot/initrd.gz ...etc...

and at the end of the line that begins with "kernel", add in, without quotes, "noapic", then save the file and reboot, hopefully it'll work

---

### Post by decilling on 2007-08-30
Hi sorry I did not reply i was away staying with family

so I did what you said and it got to the install and installed then when it restarted itself I get the same message.

This is my boot grub menu list thing

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
kernel /wubi/boot/linux find=/wubi/boot/linux setup_iso=ubuntu-7.04-alternate-i386.iso quiet splash ro noapic
initrd /wubi/boot/initrd noapic
boot


This is the kind of thing that puts me of linux :(

---

### Post by decilling on 2007-08-31
please? I realy would like to get ubuntu running

---

### Post by tuxcantfly on 2007-08-31
do the same thing to the other ubuntu entries as well; add noapic to them. if you need to see what I mean:

# menu.lst - See: grub(, info grub, update-grub(
# grub-install(, grub-floppy(,
# grub-md5-crypt, /usr/share/doc/grub
# and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'boot'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default 0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout 1

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line) and entries protected by the
# command 'lock'
# e.g. password topsecret
# password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title Windows 95/98/NT/2000
# root (hd0,0)
# makeactive
# chainloader +1
#
# title Linux
# root (hd0,1)
# kernel /vmlinuz root=/dev/hda2 ro
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
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=find=/wubi/boot/linux ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=find --set-root --ignore-floppies /wubi/boot/linux

## should update-grub create alternative automagic boot options
## e.g. alternative=true
## alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
## lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
## lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
## altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
## howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
## memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title Ubuntu, kernel 2.6.20-15-generic
find --set-root --ignore-floppies /wubi/boot/linux
kernel /wubi/boot/vmlinuz-2.6.20-15-generic find=/wubi/boot/linux ro quiet splash noapic
initrd /wubi/boot/initrd.img-2.6.20-15-generic
boot

title Ubuntu, kernel 2.6.20-15-generic (recovery mode)
find --set-root --ignore-floppies /wubi/boot/linux
kernel /wubi/boot/vmlinuz-2.6.20-15-generic find=/wubi/boot/linux ro single noapic
initrd /wubi/boot/initrd.img-2.6.20-15-generic

title Ubuntu, memtest86+
find --set-root --ignore-floppies /wubi/boot/linux
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.

title Ubuntu (Original Kernel)
find --set-root --ignore-floppies /wubi/boot/linux
kernel /wubi/boot/linux find=/wubi/boot/linux setup_iso=ubuntu-7.04-alternate-i386.iso quiet splash ro noapic
initrd /wubi/boot/initrd noapic
boot

---

### Post by tuxcantfly on 2007-08-31
also you should change this line:

```
# kopt=find=/wubi/boot/linux ro
```

to

```
# kopt=find=/wubi/boot/linux ro noapic
```

so that the error doesn't resurface after a kernel upgrade

---

### Post by Tjalfe on 2007-08-31
hey people


just install'ed Ubuntu with Wubi and had to fix a problem with the menu.lst file that where well documented in another post and it worked lik charm.


Installation ran flawless but when i started up Ubuntu it wrote "Error 17 : File not found press any button" 

then i got a menu with some "mem test" and "Ubuntu original kernel"

all options besides "Ubuntu original kernel" come's up with the same error message

when i run "Ubuntu original kernel" it starts to load and then comes up with this message "Kernel panic - not syncing : IO-APIC + timer dosent work


can anybody help me with this problem please?

thanks for the great support forum so far Greetings Tjalfe

---

### Post by decilling on 2007-08-31
thank you so much! it works ;D

---

### Post by tuxcantfly on 2007-09-01
seems like an apic error, maybe try opening C:\wubi\boot\grub\menu.lst and adding "noapic" to the ends of the lines lines beginning with "kernel" and "#kopt"?

fyi, I think this is a very similar issue to one addressed at [http://ubuntuforums.org/showthread.php?t=509499](http://ubuntuforums.org/showthread.php?t=509499) so you should look there if you need more details and instructions on fixing it

---

### Post by tuxcantfly on 2007-09-01
seems to be a duplicate thread of the one I mentioned above, so I'm merging them together

---

### Post by decilling on 2007-09-01
> **Tjalfe said:**
> hey people


just install'ed Ubuntu with Wubi and had to fix a problem with the menu.lst file that where well documented in another post and it worked lik charm.


Installation ran flawless but when i started up Ubuntu it wrote "Error 17 : File not found press any button" 

then i got a menu with some "mem test" and "Ubuntu original kernel"

all options besides "Ubuntu original kernel" come's up with the same error message

when i run "Ubuntu original kernel" it starts to load and then comes up with this message "Kernel panic - not syncing : IO-APIC + timer dosent work


can anybody help me with this problem please?

thanks for the great support forum so far Greetings Tjalfe

Thats the same kind of message that I used to get, do what i did  and maby it will work

---

### Post by Shust One on 2007-10-30
Sorry to bump this old thread but I had a question.

First of all thanks for your answers because I have now jumped ship fully to Ubuntu :) I love OPEN SOURCE!

Anyway, I don't have Windows anymore. I open my menu.lst file but I can't save the changes. It says I do not have permission. Is there a way to get around this so I can save?

Nevermind, I found my answer in another thread. Incase anyone else needs help here is how to edit the files as a super user:

> gksudo gedit /boot/grub/menu.lst

---

### Post by ago on 2007-10-30
Might be worth trying 7.10 [http://wubi-installer.org/devel/minefield/](http://wubi-installer.org/devel/minefield/)
Uninstall first, then run chkdsk /r

---

### Post by tEChniiQue on 2007-11-01
> [30.619013] MP-BIOS bug: 8524 timer not connected to IO-APIC
[30,797850] Kernel panic - not syncing: IO-APIC + timer doesn't work Boot with apic:debug and send report Then try booting with the "noapic" option
[30.797850]

This is the error I get when trying to install Feisty on an AMD64 X2 system. I've read the replies to this thread, but not sure how I could edit anything when this is a fresh install.

I've tried with both the 64Bit disk and the x86 version for Feisty. The 64Bit disk says the following:
> 
[Kernel Alive]
kernel direct mapping tables up to 100000000 @ 8000-d000

Not too sure what to do in either case. Thanks in advance!

---

### Post by CoolDreamZ on 2007-11-01
I had the same problem but also had to add "nolapic" as well, I couldn't even boot from the Live CD!

 It took me quite a while searching these forums to solve the problem. This is a really bad experience for a new Ubuntu user and should be added to the Release notes.

---

### Post by tEChniiQue on 2007-11-01
Yeh, it's a pain. Thing is I'm not really a new user so to speak but this is the first time I've installed (or tried to) install the distro on an AMD64 system.

You had the same problem? What did you do to rectify?

---

### Post by CoolDreamZ on 2007-11-01
Sorry, meant "new user" in general (like me!!) ;)

To boot from the live CD I added kernel options "noapic nolapic" using F6 on the GRUB menu.

To fix the problem permanently I added those options to the menu.lst file. I will post the menu.lst file when I next have access to the machine.

---

### Post by tEChniiQue on 2007-11-01
haha, nah, no biggie. But I appreciate it. I would like to see the menu list once you have available. Thanks for the help Later today, I'll give it a shot and let you know how it turned out.

---

### Post by CoolDreamZ on 2007-11-01
Here is my menu.lst file:

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
# kopt=root=UUID=1da587a7-b75a-4655-9b76-acc3fc53458e ro noapic nolapic

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
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=1da587a7-b75a-4655-9b76-acc3fc53458e ro quiet splash noapic nolapic
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=1da587a7-b75a-4655-9b76-acc3fc53458e ro single noapic nolapic
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows NT/2000/XP (Recovery)
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb2
title		Microsoft Windows XP Professional
root		(hd1,1)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

---

### Post by ago on 2007-11-02
ro quiet splash noapic nolapic **acpi=off**

---

### Post by tEChniiQue on 2007-11-02
@CoolDreamZ
Thank you for the replies...I will give this a shot and let you know the status. Man...it's frustrating. I've been using Ubuntu and Mandriva a little over a year (just learning normal use) but I've never had an issue. This install was the first thing that really made "search" for answers. Your help is appreciated.

---

### Post by tEChniiQue on 2007-11-11
@CoolDreamZ
Hey man,
I did like suggested...used 'noapic nolapic' in the F6 menu option. This got Ubuntu to boot the LIVE cd and my system got as far as the desktop. Once there, my mouse and keyboard were not responsive. I know tey work because I obviously used them in the boot setup to enter the information above. This is odd.

The sstem is an AMD 64Bit and I'vetried with both Ubuntu 7.04 32 and x64 version. I'm going to give it a go with Gutsy and see if the results are any different.

Would you or anyone reading this have any ideas as t why the screen locks once the LIVE CD is on the desktop. CoolDreamZ, your initial advice gt the system to at least boot in LIVE mode...I'm just curious if there is someting else that would let me get this bad boy installed. 

Thanks in advance.

EDIT: Using the 'noapic nolapic' command worked this time by using 7.10. Seemed to be a glitch with 7.04. Either way, it's fine...I was going to upgrade to Gutsy anyway. It saved me a couple minutes of downloading. The help on this was appreciated man.

---

### Post by CoolDreamZ on 2007-11-13
> **tEChniiQue said:**
> @CoolDreamZ
 Either way, it's fine...I was going to upgrade to Gutsy anyway. It saved me a couple minutes of downloading. The help on this was appreciated man.

Your welcome, glad you got it working :)

---

### Post by home ubub on 2009-11-08
I have got the New Ubuntu 9.10 Live cd,,,,but when i try to install with xp sp3 through wubi it says [B]Error: "kernel panic - not syncing: I0-apic + timer doesn't work! boot with apic

plz do help meh,,,,[/B]:cry:

---

