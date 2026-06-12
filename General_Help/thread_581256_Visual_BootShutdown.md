---
title: "Visual Boot/Shutdown"
date: 2007-10-19
forum: General Help
---

### Post by Naatan on 2007-10-19
Hi,

I'm wondering how to boot up and shut down without getting the Ubuntu logo, I'd like to see the normal linux-like debugging console saying what services it's stopping or starting..

Any idea how?

---

### Post by spliner on 2007-10-19
I'd like to change the boot colors and splash screen all together to something custom.  I'm sure this can be done, but the ol' Ubuntu orange colors aren't that pleasing.  I'm loving Ubuntu more and more each day I use it but that's the one thing that gets me when the system starts.  Yuk.  Now once the desktop is up, it looks wonderful with my own choice of background.

Spliner

---

### Post by Naatan on 2007-10-19
I love it when people hijack my threads

---

### Post by thirddeep on 2007-10-19
You should be happy, you get  bumped ... like this :-)

Thd.

---

### Post by mahousaru on 2007-10-19
To remove the splash screen on boot you have to edit

/boot/grub/menu.1st 

and change the line from

kernel          /vmlinuz-2.6.22-14-generic root=/dev/mapper/hda2_crypt ro quiet splash

to 

kernel          /vmlinuz-2.6.22-14-generic root=/dev/mapper/hda2_crypt ro quiet nosplash=y

I'm using a encrypted partition so mine looks weird.

There will be several sections, the first being the default start up, the second recovery and the third is memory check

Once you have updated it you need to run the following command

sudo update-grub

Sorry can't help with the shutdown screen :p

---

### Post by Naatan on 2007-10-19
Does quiet mean it will just show me a black screen?

I'd like to have as much debugging information as possible.

Thanks for your responce

---

### Post by mahousaru on 2007-10-19
Opps good point *slaps forehead*

quiet is the opposite of debug so only important or sys critical messages are shown.  You have to remove that too. Sorry I missed it!

---

### Post by Naatan on 2007-10-19
hmm I just tried it but it doesnt work, it doesnt seem to accept "nosplash=y"

are you sure this is correct?

---

### Post by mahousaru on 2007-10-19
Hmmm I normally use nosplash=y as a boot setting for laptops that play up during an install.  Can you try it with out splash and see what happens?

I'll test it on my vmbox if you want to wait a mo

*EDIT*
did you run 

sudo update-grub

after you updated the file?

---

### Post by Naatan on 2007-10-19
yes I did,

The odd thing is that it still displays the splash image, even without any splash parameter what so ever.

(note that im using gutsy)

---

### Post by mahousaru on 2007-10-19
*cough cough*

My bad....

Don't run update-grub as that sets the file back to default with the splash setting.

just change it to nosplash=y

---

### Post by Naatan on 2007-10-19
ok,

I managed to remove the splash using an app called 'Startup Manager', but now it just shows a black screen and no debug info :(

---

### Post by mahousaru on 2007-10-19
Can you post the menu.1st line please? I disabled the splash by replacing splash with nosplash=y and NOT running update-grub

---

### Post by Naatan on 2007-10-19
The splash is gone, like I said :)

Now all I need is to get the debug info (eg the services its starting)

Starting network ..             [OK]

That kind of stuff..

here's my menu.lst

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=16204d90-8b0a-4816-ac0e-8a1453cb8dad ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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
# defoptions=vga=775

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
# howmany=3

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
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=16204d90-8b0a-4816-ac0e-8a1453cb8dad ro vga=775
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=16204d90-8b0a-4816-ac0e-8a1453cb8dad ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, kernel 2.6.22-13-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-13-generic root=UUID=16204d90-8b0a-4816-ac0e-8a1453cb8dad ro vga=775
initrd		/boot/initrd.img-2.6.22-13-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-13-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-13-generic root=UUID=16204d90-8b0a-4816-ac0e-8a1453cb8dad ro single
initrd		/boot/initrd.img-2.6.22-13-generic

title		Ubuntu 7.10, kernel 2.6.22-12-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-12-generic root=UUID=16204d90-8b0a-4816-ac0e-8a1453cb8dad ro vga=775
initrd		/boot/initrd.img-2.6.22-12-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-12-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-12-generic root=UUID=16204d90-8b0a-4816-ac0e-8a1453cb8dad ro single
initrd		/boot/initrd.img-2.6.22-12-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by mahousaru on 2007-10-19
Can your monitor display 1280×1024?

I'm off out now, but if your monitor cannot display 1280x1024 then the vga=775 is forcing it into that mode which would make it go black.
1024 x 768 is vga=773

If there is not enough information then you can add debug to the line (which will do the opposite to quiet).

Good luck with it!

---

### Post by Naatan on 2007-10-19
My monitor can display up to 1920x1200 so that can't be it either.. 

I'll try decreasing it though.

---

### Post by Naatan on 2007-10-19
I found the following but it doesn't add up for gutsy..

[https://help.ubuntu.com/community/BootText](https://help.ubuntu.com/community/BootText)

it appears the functionality exists though, I just need to know how to enable it.

---

### Post by mahousaru on 2007-10-19
I have to apologise for leading you down the wrong road with editing the menu.1st, I got my wires totally crossed most probably with needing to run lilo after editing it's conf file.  I have never seen the need to edit the grub menu tbh...

Just for future reference if you wish to update menu.1st you have to edit them in the section

## ## Start Default Options ##

So for your earlier issue you would need to remove quiet and splash from:

# defoptions=quiet splash

I'm off out to kill some brain cells in a mo, but I'll have another look at it, if you haven't solved it, or if no one else has helped.

---

### Post by louieb on 2007-10-19
All I do is remove the **quiet splash** to get all the boot messages. You can do a onetime test from the grub menu by highlighting the entry and pressing e to edit.

---

### Post by Naatan on 2007-10-20
well at one point last night it said the screen resolution was wrong and I chose one of the other options it gave me which worked, and it actually showed me the boot messages! 

Pheraps its cause I have widescreen.. I'll try some more later today :)

---

### Post by nawitus on 2007-10-20
And for the grub boot splash, just google for many guides..

---

