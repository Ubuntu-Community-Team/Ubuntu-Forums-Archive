---
title: "GRUB not working"
date: 2007-09-13
forum: General Help
---

### Post by init1 on 2007-09-13
Recently, I installed GeeXboX. The menu.lst for the GRUB it used did not contain any other OS, so I added them from a previous menu.lst. But when I select anything other than GeeXboX or Dream Linux, I tells me that the file is not found. I can, however, enter in the boot information manually. Do I need a new GRUB installation, or is there an error in my menu.lst?
 
default  0
timeout  5
color cyan/blue white/blue
splashimage=(hd0,10)/boot/grub/grub-splash.xpm.gz

title	GeeXboX
root	(hd0,10)
kernel	/vmlinuz root=/dev/ram0 rw init=linuxrc boot=sda11 lang=en splash=silent vga=791 keymap=qwerty remote=D-10 receiver=animax video=vesafb:ywrap,mtrr
initrd  /initrd.gz
boot

title	GeeXboX (debug)
root	(hd0,10)
kernel	/vmlinuz root=/dev/ram0 rw init=linuxrc boot=sda11 lang=en splash=0 vga=791 keymap=qwerty remote=D-10 receiver=animax video=vesafb:ywrap,mtrr debugging
initrd  /initrd.gz
boot

title	Dreamlinux MMGL Edition
root	(hd0,9)
kernel	/boot/vmlinuz-2.6.18.1-kanotix-1 root=/dev/sda10 ro quiet vga=791 splash=silent
initrd	/boot/initrd
boot

title	Dreamlinux MMGL Edition (recovery mode)
root	(hd0,9)
kernel	/boot/vmlinuz-2.6.18.1-kanotix-1 root=/dev/sda10 ro quiet vga=791 single
initrd	/boot/initrd
boot

title	Ubuntu 6.06.1 LTS (6.06)
root	(hd0,5)
kernel	/boot/vmlinuz-2.6.15-27-desktop root=/dev/sda6 ro quiet vga=791 splash=silent
initrd	/boot/initrd.img
initrd.img-2.6.15-27-desktop
initrd.img.old
savedefault
boot

title	Ubuntu 7.04 (7.04)
root	(hd0,6)
kernel	/boot/vmlinuz-2.6.20-16-generic root=/dev/sda7 ro quiet vga=791 splash=silent
initrd	/boot/initrd.img-2.6.20-16-generic
initrd.img-2.6.20-16-generic.bak
savedefault
boot

title	Slackware Linux (Slackware 11.0.0)
root	(hd0,7)
kernel	/boot/vmlinuz-2.6.18.5 root=/dev/sda8 ro quiet vga=791 splash=silent
savedefault
boot

title	Debian GNU/Linux (4.0)
root	(hd0,8)
kernel	/boot/vmlinuz-2.6.18-5-686 root=/dev/sda9 ro quiet vga=791 splash=silent
initrd	/boot/initrd.

---

### Post by rsambuca on 2007-09-13
> **init1 said:**
> Recently, I installed GeeXboX. The menu.lst for the GRUB it used did not contain any other OS, so I added them from a previous menu.lst. But when I select anything other than GeeXboX or Dream Linux, I tells me that the file is not found. I can, however, enter in the boot information manually. Do I need a new GRUB installation, or is there an error in my menu.lst?
 
default  0
timeout  5
color cyan/blue white/blue
splashimage=(hd0,10)/boot/grub/grub-splash.xpm.gz

title	GeeXboX
root	(hd0,10)
kernel	/vmlinuz root=/dev/ram0 rw init=linuxrc boot=sda11 lang=en splash=silent vga=791 keymap=qwerty remote=D-10 receiver=animax video=vesafb:ywrap,mtrr
initrd  /initrd.gz
boot

title	GeeXboX (debug)
root	(hd0,10)
kernel	/vmlinuz root=/dev/ram0 rw init=linuxrc boot=sda11 lang=en splash=0 vga=791 keymap=qwerty remote=D-10 receiver=animax video=vesafb:ywrap,mtrr debugging
initrd  /initrd.gz
boot

title	Dreamlinux MMGL Edition
root	(hd0,9)
kernel	/boot/vmlinuz-2.6.18.1-kanotix-1 root=/dev/sda10 ro quiet vga=791 splash=silent
initrd	/boot/initrd
boot

title	Dreamlinux MMGL Edition (recovery mode)
root	(hd0,9)
kernel	/boot/vmlinuz-2.6.18.1-kanotix-1 root=/dev/sda10 ro quiet vga=791 single
initrd	/boot/initrd
boot

title	Ubuntu 6.06.1 LTS (6.06)
root	(hd0,5)
kernel	/boot/vmlinuz-2.6.15-27-desktop root=/dev/sda6 ro quiet vga=791 splash=silent
initrd	/boot/initrd.img
[COLOR="Red"]initrd.img-2.6.15-27-desktop
initrd.img.old[/COLOR]
savedefault
boot

title	Ubuntu 7.04 (7.04)
root	(hd0,6)
kernel	/boot/vmlinuz-2.6.20-16-generic root=/dev/sda7 ro quiet vga=791 splash=silent
initrd	/boot/initrd.img-2.6.20-16-generic
[COLOR="Red"]initrd.img-2.6.20-16-generic.bak[/COLOR]
savedefault
boot

title	Slackware Linux (Slackware 11.0.0)
root	(hd0,7)
kernel	/boot/vmlinuz-2.6.18.5 root=/dev/sda8 ro quiet vga=791 splash=silent
savedefault
boot

title	Debian GNU/Linux (4.0)
root	(hd0,8)
kernel	/boot/vmlinuz-2.6.18-5-686 root=/dev/sda9 ro quiet vga=791 splash=silent
initrd	/boot/initrd.

I would remove the lines in red.  I don't know why your debian and slackware ones aren't booting, offhand.

---

### Post by bodhi.zazen on 2007-09-13
> **rsambuca said:**
> I would remove the lines in red.  I don't know why your debian and slackware ones aren't booting, offhand.

My guess is malformed initrd

The slackware entry has none (I do not know if it needs one, but the rest seem to ...)

The Debian one is "initrd /boot/initrd." which does not look correct either.

---

### Post by rsambuca on 2007-09-13
Yeah, I just chainload my grubs.

---

### Post by init1 on 2007-09-13
Looks like the file is messed up. I'll just make another from scratch. 
Explain to me how chainloading works; I've only used it for Windows/DOS.

---

### Post by bodhi.zazen on 2007-09-14
You install grun into the root partition of each distro.

Then, in the /boot partition, in you case the last distro you installed, edit /boot/grub/menu/lst

Title <distro here>
root (hdx,y)
chainload +1
boot

You will get a second grub screen. Edit /boot/grub/menu.lst in the target partition to minimize other distros, select a default distro, and a short time out ... ect.

HTH

---

### Post by confused57 on 2007-09-14
This guide explains chainloading, configfile, or symlink booting of multiple Linux OSes:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

---

