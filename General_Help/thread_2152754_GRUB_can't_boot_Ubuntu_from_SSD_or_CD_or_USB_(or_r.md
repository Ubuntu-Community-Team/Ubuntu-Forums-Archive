---
title: "GRUB can't boot Ubuntu from SSD or CD or USB (or reinstall either)"
date: 2013-06-08
forum: General Help
---

### Post by rghpkp on 2013-06-08
Ubuntu 12.04 LTS, Asus P8Z68-V LX motherboard w/ Asus bios 0703, Linux 3.2.0-45

After my wireless card went down and the normal software/driver/config   fixes didn't work, I powered down my machine, pulled the card, cleaned   the contacts, reinstalled, and powered up.  The card began working   again, but Ubuntu was very glitchy.  I restarted after about 5 minutes,   and, kaboom.

GRUB 1.99 will now not boot Ubuntu on my single-boot machine under any circumstances.  

After the bios loads, but before grub loads, I get 
> error: prefix is not set

After grub menu loads, when booting the existing install from the SSD, 

When selecting "Install Ubuntu" from CD or USB (with SSD disabled in   bios boot menu) I get the very first Ubuntu screen, then the machine   freezes.  

When selecting "Try Ubuntu without installing", i get
> 
error: couldn't read file

When checking disk from CD/USB, grub freezes immediately.

Here are some results from the GRUB command line:

grub> ls
(memdisk) (fd0) (fd0,msdos1) (hd0) (hd1) (hd2) (hd2,msdos5) (hd2,msdos1) (hd3) (hd3,msdos5) (hd3,msdos1) (cd0) (cd0,msdos1)

grub> boot
error: no loaded kernel

grub> cat (memdisk)/boot/grub/grub.cfg
search --file --set=root /.disk/info
set prefix=($root)/boot/grub/x86_64-efi
source $prefix/grub.cfg

---

### Post by oldfred on 2013-06-09
Did you have system configured to boot in UEFI mode or BIOS mode and is it still booting in that mode?

If you have two hard drives, do you have an install in both drives? Which drive is set as default to boot from?

---

