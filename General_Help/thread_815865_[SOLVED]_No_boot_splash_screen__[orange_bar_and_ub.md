---
title: "[SOLVED] No boot splash screen  [orange bar and ubunto logo] fiesty fawn 7.04"
date: 2008-06-02
forum: General Help
---

### Post by kewe86 on 2008-06-02
Hi,

Please can anyone help me enable the boot splash screen at startup so that I am able to see the orange progress bar and ubuntu logo.

All I see is the text based bootup:

* Reading files needed to boot ... [ OK ]
* Setting preliminary keymap ... [ OK ]
* Preparing restricted drivers ... [ OK ]
* Starting basic networking ... [ OK ]
* Starting kernel event manager ... [ OK ] 

Can I switch to the normal bootup screen. Thanks in advance.

---

### Post by PmDematagoda on 2008-06-02
Post the output of:-
```
cat /boot/grub/menu.lst
```

---

### Post by kewe86 on 2008-06-02
Hi,

Thanks for quick reply. I did a search in the forum while waiting for replys and added vga=791 at the end and the boot up splash screen now works.

How do I get this to work for the shutdown as well. 

Thanks. The result of menu.lst is below:


user@user-laptop:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=892ccd11-7f7c-454d-a638-7701eb9f9890 ro

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

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=892ccd11-7f7c-454d-a638-7701eb9f9890 ro quiet splash vga=791
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=892ccd11-7f7c-454d-a638-7701eb9f9890 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by sanus|art on 2008-06-02
edit your
```
/etc/usplash.conf
```

set your screen resolution in:
xres=
yres=

e.g. my screen is 1400x900 so my usplash.conf reads:
xres=1400
yres=900

---

### Post by Zorael on 2008-06-02
edit: Wild and rampant editing!

If modifying usplash.conf, initramfs needs to be regenerated for the changes to take effect.
```
$ sudo update-initramfs -u -k all
```

> **kewe86 said:**
> How do I get this to work for the shutdown as well.
Well, technically it should work automatically. Can you print the terminal output of this command?
```
$ ls /etc/rc0.d/*halt -l
```

---

### Post by kewe86 on 2008-06-03
Thanks for all your replies. I have got it working now following the screen resolution hint. xres and yres 1024 x 768.

Much better to see the orange progress bar and ubuntu logo than text messages that look like error messages. It somehow gets to me. :)

Thanks again.

---

### Post by quaangscu on 2009-09-22
Thank you, this is good news for other visitors

---

