---
title: "Grub Boot Menu"
date: 2005-07-21
forum: General Help
---

### Post by razul9 on 2005-07-21
anyway to make the grub boot menu where it lists your operating system a higher resolution like 1024x768 or 1280x1024?

---

### Post by Tyche on 2005-07-24
razul9,
    Below is a portion of my menu.lst:

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,4)
kernel		/vmlinuz-2.6.10-5-386 root=/dev/hda6 ro quiet splash vga=0x318
initrd		/initrd.img-2.6.10-5-386
savedefault
boot

The number following "vga=" I got from this chart (which I keep in a backup copy of the menu.lst):

## Screen Settings
#       +--------------------------------------------------------------+
#       |          |   640x480 800x600 1024x768 1280x1024  |
#       +-------+-----------------------------------------------------+
#       |  256  |    0x301    0x303     0x305      0x307           |
#       |  32K  |    0x310    0x313     0x316      0x319           |
#       |  64k  |    0x311    0x314     0x317      0x31A          |
#       |  16M |    0x312    0x315     0x318      0x31B          |
#       +--------------------------------------------------------------+
#

You can access the file by:
    sudo gedit /boot/grub/menu.lst

Hope this helps.

---

