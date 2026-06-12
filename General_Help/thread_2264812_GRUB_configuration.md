---
title: "GRUB configuration"
date: 2015-02-10
forum: General Help
---

### Post by cl-netbox on 2015-02-10
One of the greatest advantages of GRUB is customizability.
Especially the possibility to boot from ISO files is a big 'plus'.

You don't need to burn a CD or create an USB disk anymore.
The only exeption is when you can not boot to GRUB menu.
Then naturally you need to have such a separate boot media.

You just have to create a menu entry and you are ready to go.
This is my setup meant to serve as an example for illustration:

gksudo gedit /etc/grub.d/40_custom

menuentry "clonezilla" {
set isofile="/ubuntu/clonezilla-*.iso"
loopback loop (hd0,5)$isofile
linux (loop)/live/vmlinuz boot=live config union=aufs noswap noprompt vga=788 ip=frommedia toram=filesystem.squashfs findiso=$isofile
initrd (loop)/live/initrd.img
}

menuentry "gparted" {
set isofile="/ubuntu/gparted-*.iso"
loopback loopg(hd0,5)$isofile
linux (loop)/live/vmlinuz boot=live config union=aufs noswap noprompt vga=788 ip=frommedia toram=filesystem.squashfs findiso=$isofile
initrd (loop)/live/initrd.img
}

menuentry "ubuntu-rescue" {
set isofile="/ubuntu/ubuntu-*.iso"
loopback loop (hd0,5)$isofile
linux (loop)/casper/vmlinuz.efi boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}

sudo update-grub

(* = file name | hd0,5 = disk 1 / partition 5)

---

### Post by oldfred on 2015-02-10
More info here:

 This will boot an ISO from a hard drive or any second drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)

---

