---
title: "custom grub theme for multiboot usb"
date: 2013-03-13
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2013-03-13
i set my flash drive like this guide says
[http://www.pendrivelinux.com/boot-multiple-iso-from-usb-via-grub2-using-linux/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-via-grub2-using-linux/)

how can i get a fancy theme to work on it?
i have the theme in /boot/grub/themes/ubuntu
the theme is here:
[http://ubuntuforums.org/showthread.php?t=2081013](http://ubuntuforums.org/showthread.php?t=2081013)

edit: i got it, here is my grub.cfg
```
insmod part_msdos
insmod fat
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 10A9-AFCE
loadfont /boot/grub/fonts/unicode.pf2
set gfxmode=auto
insmod vbe
insmod vga
insmod gfxterm
terminal_output gfxterm
insmod gfxmenu
loadfont ($root)/boot/grub/themes/ubuntu/dejavu-sans-10.pf2
loadfont ($root)/boot/grub/themes/ubuntu/dejavu-sans-12.pf2
loadfont ($root)/boot/grub/themes/ubuntu/dejavu-sans-bold-14.pf2
insmod png
set theme=($root)/boot/grub/themes/ubuntu/theme.txt

set timeout=10
set default=1

menuentry "Ubuntu 12.10 Desktop 64bit" --class ubuntu --class gnu-linux {
 loopback loop /ubuntu-12.10-desktop-amd64.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/ubuntu-12.10-desktop-amd64.iso noeject noprompt splash --
 initrd (loop)/casper/initrd.lz
}

menuentry "Xubuntu 12.10 Desktop 64bit" --class xubuntu --class gnu-linux {
 loopback loop /xubuntu-12.10-desktop-amd64.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/xubuntu-12.10-desktop-amd64.iso noeject noprompt splash --
 initrd (loop)/casper/initrd.lz
}

menuentry "Gnome Ubuntu 12.10 Desktop 64bit" --class gnomeubuntu --class gnu-linux {
 loopback loop /ubuntu-gnome-12.10.1-desktop-amd64.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/ubuntu-gnome-12.10.1-desktop-amd64.iso noeject noprompt splash --
 initrd (loop)/casper/initrd.lz
}

menuentry "Kubuntu 12.10 Desktop 64bit" --class kubuntu --class gnu-linux {
 loopback loop /kubuntu-12.10-desktop-amd64.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/kubuntu-12.10-desktop-amd64.iso noeject noprompt splash --
 initrd (loop)/casper/initrd.lz
}

menuentry "Lubuntu 12.10 Desktop 64bit" --class lubuntu --class gnu-linux {
 loopback loop /lubuntu-12.10-desktop-amd64.iso
 linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/lubuntu-12.10-desktop-amd64.iso noeject noprompt splash --
 initrd (loop)/casper/initrd.lz
}

menuentry "Linux Mint 14 Cinnamon 64bit" --class linuxmint --class gnu-linux {
 loopback loop /linuxmint-14.1-cinnamon-dvd-64bit.iso
 linux (loop)/casper/vmlinuz file=/cdrom/preseed/mint.seed boot=casper initrd=/casper/initrd.lz iso-scan/filename=/linuxmint-14.1-cinnamon-dvd-64bit.iso noeject noprompt splash --
 initrd (loop)/casper/initrd.lz
}

menuentry "Linux Mint 14 Mate 64bit" --class linuxmint --class gnu-linux {
 loopback loop /linuxmint-14.1-mate-dvd-64bit.iso
 linux (loop)/casper/vmlinuz file=/cdrom/preseed/mint.seed boot=casper initrd=/casper/initrd.lz iso-scan/filename=/linuxmint-14.1-mate-dvd-64bit.iso noeject noprompt splash --
 initrd (loop)/casper/initrd.lz
}

menuentry "DBAN ISO (Delete EVERYTHING)" --class dban {
 loopback loop /dban.iso
 linux (loop)/DBAN.BZI nuke="dwipe" iso-scan/filename=/dban.iso silent --
} 

menuentry "Memtest 86+" --class recovery {
 linux16 /memtest86+.bin
}

# menuentry "Tinycore ISO" {
#  loopback loop /tinycore.iso
#  linux (loop)/boot/bzImage --
#  initrd (loop)/boot/tinycore.gz
# }

# menuentry "SystemRescueCd" {
#  loopback loop /systemrescuecd.iso
#  linux (loop)/isolinux/rescuecd isoloop=/systemrescuecd.iso setkmap=us docache dostartx
#  initrd (loop)/isolinux/initram.igz
#}

```

---

