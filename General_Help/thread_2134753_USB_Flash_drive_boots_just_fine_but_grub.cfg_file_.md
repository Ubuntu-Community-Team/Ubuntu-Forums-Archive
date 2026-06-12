---
title: "USB Flash drive boots just fine but grub.cfg file is missing, can't edit boot menu."
date: 2013-04-12
forum: General Help
---

### Post by cozway on 2013-04-12
I have BackBox Ubuntu installed on a USB flash drive and it boots and runs just fine. However I would like to modify the boot menu but can't find a grub.cfg file. Therefore grub-update will not work. I've also tried using Grub Customizer but it shows both device.map and grub.cfg missing. Most posts I've found with grub.cfg missing have boot problems which I am not having. Is my setup not really using Grub but an alternative boot system? Any help to reconfigure the boot menu on this system would be appreciated.

---

### Post by rnerwein on 2013-04-12
> **cozway said:**
> I have BackBox Ubuntu installed on a USB flash drive and it boots and runs just fine. However I would like to modify the boot menu but can't find a grub.cfg file. Therefore grub-update will not work. I've also tried using Grub Customizer but it shows both device.map and grub.cfg missing. Most posts I've found with grub.cfg missing have boot problems which I am not having. Is my setup not really using Grub but an alternative boot system? Any help to reconfigure the boot menu on this system would be appreciated.
hi
i think your problem is that you have only a boot-abel usb - not a real system on your stick. did you erver tried to update a CD-read only.
see: [http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu)
you have to install a real system on your usb
good luck and much fun
ciao

---

### Post by cozway on 2013-04-12
System was installed from BackBox ISO with Unetbootin.

---

### Post by ajgreeny on 2013-04-12
As rnerwein says, it looks as if you are simply booting to a live USB system, not a proper installed version of Ubuntu.  If you have another OS on this or some other machine, plug in the USB and tell us what folders are on it.

I suspect it will have a list like my screenshot, which is a live system only, not an installed OS.

---

### Post by cozway on 2013-04-12
I think you both have identified the problem. Thanks, Joseph

---

### Post by cozway on 2013-04-12
SOLVED: The solution was to simply edit the syslinux file. If booted up in Linux, it is in the /CDROM folder. If your flash drive partition is FAT or NTFS you can access this file simply in the root of the flash drive from Windows. Below is the original and newly edited syslinux files with their corresponding boot menus.

Original syslinux file contents:

default menu.c32
prompt 0
menu title BackBox Linux
timeout 100


label ubnentry0
menu label Start BackBox in Persistent Mode
kernel /casper/vmlinuz
append initrd=/casper/initrd.gz file=/cdrom/preseed/backbox.seed boot=casper persistent quiet splash locale=en_US bootkbd=us console-setup/layoutcode=us vga=791 -- persistent


label ubnentry1
menu label Start BackBox in Forensic Mode
kernel /casper/vmlinuz
append initrd=/casper/initrd_forensic.gz file=/cdrom/preseed/backbox.seed boot=casper quiet splash locale=en_US bootkbd=us console-setup/layoutcode=us vga=791 -- persistent


label ubnentry2
menu label Start BackBox in Text Mode
kernel /casper/vmlinuz
append initrd=/casper/initrd.gz file=/cdrom/preseed/backbox.seed boot=casper quiet text vga=791 -- persistent


label ubnentry3
menu label Start BackBox in Compatibility Mode
kernel /casper/vmlinuz
append initrd=/casper/initrd.gz file=/cdrom/preseed/backbox.seed boot=casper xforcevesa ramdisk_size=1048576 root=/dev/ram rw noapic noapci nosplash irqpoll -- persistent


label ubnentry4
menu label Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.gz boot=casper integrity-check quiet splash vga=791 -- persistent


label ubnentry5
menu label Test memory
kernel /install/mt86plus
append initrd=/ubninit  persistent

Original boot menu:
[IMG]http://s931.photobucket.com/user/cozway/media/IMAG0031.jpg.html?sort=3&o=0[/IMG]

Newly edited syslinux file:

default menu.c32
prompt 0
menu title BackBox Linux
timeout 100


label ubnentry0
menu label Start BackBox in Persistent Mode
kernel /casper/vmlinuz
append initrd=/casper/initrd.gz file=/cdrom/preseed/backbox.seed boot=casper persistent quiet splash locale=en_US bootkbd=us console-setup/layoutcode=us vga=791 -- persistent


label ubnentry1
menu label Start BackBox in Forensic Mode
kernel /casper/vmlinuz
append initrd=/casper/initrd_forensic.gz file=/cdrom/preseed/backbox.seed boot=casper quiet splash locale=en_US bootkbd=us console-setup/layoutcode=us vga=791 -- persistent


label ubnentry2
menu label Start BackBox in Text Mode
kernel /casper/vmlinuz
append initrd=/casper/initrd.gz file=/cdrom/preseed/backbox.seed boot=casper quiet text vga=791 -- persistent


label ubnentry3
menu label Start BackBox in Compatibility Mode
kernel /casper/vmlinuz
append initrd=/casper/initrd.gz file=/cdrom/preseed/backbox.seed boot=casper xforcevesa ramdisk_size=1048576 root=/dev/ram rw noapic noapci nosplash irqpoll -- persistent


label ubnentry4
menu label Check disc for defects
kernel /casper/vmlinuz
append initrd=/casper/initrd.gz boot=casper integrity-check quiet splash vga=791 -- persistent


label ubnentry5
menu label Test memory
kernel /install/mt86plus
append initrd=/ubninit  persistent

New Boot Menu:
[IMG]http://s931.photobucket.com/user/cozway/media/IMAG0030.jpg.html?sort=3&o=1[/IMG]

---

