---
title: "Dual boot Windows XP and Ubuntu 7.04 Feisty Fawn"
date: 2007-07-01
forum: General Help
---

### Post by wie6Ein0 on 2007-07-01
I have Windows XP (Service Pack 2) installed on my desktop computer. I am wanting to dual boot XP with Ubuntu 7.04 Feisty Fawn, but I don't know the correct steps to take to do so.

I already have the Ubuntu 7.04 Feisty Fawn disk and have tested the LIVE CD with no problems. Please help me to dual boot!

What I'm wanting is for the computer to ask me which OS I'd like to boot into at startup, and if none is selected in a certain amount of time it should automatically boot into Windows XP. (The computer is shared, so it's important that Windows is the main OS since everyone else in household doesn't like change.)

---

### Post by dpar on 2007-07-02
This site should have everything you need to know.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by justtech on 2007-07-02
I would recommend getting a program called PartitionMagic for Windows.  Resize your partition to allow room for Ubuntu.  Then put in your Ubuntu CD and reboot.  When you format your harddrive for Linux make sure you don't do it over the Windows partition....  Only problem is, I'm not to familer with Ubuntu yet (getting closer) but I do know that it will default to boot into Ubuntu instead of XP after a certain time frame and I'm sure someone on here will know how to customize it.  Hope this helped some.

---

### Post by justtech on 2007-07-02
> **dpar said:**
> This site should have everything you need to know.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Or follow this linke ;)

---

### Post by lisati on 2007-07-02
> **dpar said:**
> This site should have everything you need to know.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

Don't forget to (a) make a backup of important files, just in case Mr Murphy invokes his famous law, and (b) use the "guided resize" option instead of "use the entire disk" when asked how you wish to set up the partitions.

Getting Windows as the default OS may take a little extra tinkering......

p.s. my laptop didn't like the "live" CD for initially setting up Ubuntu, but didn't have a problem on my desktop. There is an "alternate" CD available for download if you need it. Feel free to let us know how you get on.

---

### Post by dpar on 2007-07-02
You will need to edit the /boot/grub/menu.lst to get Windows to boot by default, but that isn't too tough to do.

---

### Post by wie6Ein0 on 2007-07-02
> **dpar said:**
> You will need to edit the /boot/grub/menu.lst to get Windows to boot by default, but that isn't too tough to do.

I ended up installing Ubuntu 7.04 Feisty Fawn on a separate hard disk. I found a [wiki page]("http://ubuntuguide.org/wiki/Ubuntu:Feisty/BootMenu#How_to_add_Windows_entry_into_GRUB_menu") for adding Windows to the grub menu and did as the page instructed, but I'm having some problems. My Windows installation also includes a "backup" partition for easy system recovery (HP - Hewlett Packard) and when I add the line from the wiki to my GRUB menu.lst file, it boots into the recovery partition instead of the actual Windows partition that I want.

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=f61aa453-90ea-483b-a641-bbcc7143ffae ro

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

## ## End Default Options ##

title        Ubuntu, kernel 2.6.20-15-generic
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=f61aa453-90ea-483b-a641-bbcc7143ffae ro quiet splash
initrd        /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title        Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root        (hd0,0)
kernel        /boot/vmlinuz-2.6.20-15-generic root=UUID=f61aa453-90ea-483b-a641-bbcc7143ffae ro single
initrd        /boot/initrd.img-2.6.20-15-generic

title        Ubuntu, memtest86+
root        (hd0,0)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title           Microsoft Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
chainloader (hd1,0)+1
```

Does someone know what I have done wrong and how I can correct it? If I can get that fixed, I suppose I will have everything exactly as I want.

---

### Post by confused57 on 2007-07-02
If Windows is on the 2nd partition, then this should work:
```
title           Microsoft Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
chainloader (hd1,1)+1
```

or

```
title              Windows XP
root               (hd1,1)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

---

### Post by wie6Ein0 on 2007-07-02
> **confused57 said:**
> If Windows is on the 2nd partition, then this should work:
```
title           Microsoft Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
chainloader (hd1,1)+1
```or

```
title              Windows XP
root               (hd1,1)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

Thanks! That worked like a charm. I managed to figure out how to make Windows the default OS to boot on my own. Dual booting was actually easier than I thought it would be to setup -- probably even better using separate HDDs for each OS. Thanks again!

---

### Post by confused57 on 2007-07-02
> **westoncampbell said:**
> Thanks! That worked like a charm. I managed to figure out how to make Windows the default OS to boot on my own. Dual booting was actually easier than I thought it would be to setup -- probably even better using separate HDDs for each OS. Thanks again!
I agree, that's how I have my system(s) set up:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

Glad it worked...

---

