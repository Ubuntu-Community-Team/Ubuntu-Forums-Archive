---
title: "Help with lilo version 22.1"
date: 2008-05-26
forum: General Help
---

### Post by blackzeus on 2008-05-26
hello,

i am tryng to undertsand a problem that i have with lilo v. 22.1 in a project that i am  developing based on a special distro that i had access.

the problem is as follows,

in this distro i have a image during boot that i would like to change but the problem is that i dont understand how the process of putting the mage there works...

the boot loader is lilo v. 22.1 and this version does not support the "bitmap=..." option and still i get what it seems like a bitmap image on boot

the content of the lilo.conf is as follows:

disk=/dev/discs/disc0/disc
  bios=0x80
boot=/dev/discs/disc0/disc
backup=/dev/null
map=/boot/map
install=/boot/boot.b
lba32
compact
prompt
timeout=30
message=/boot/message
image=/boot/vmlinuz
    label=linux
    root=/dev/discs/disc0/part1
    read-write
    append="video=vesa:mtrr pci=noacpi usb_storage.delay_use=0 usbserial.vendor=0xaf0 usbserial.product=0x5000"
    vga=788


and inside /boot i have the following files:

boot.b
chain.b
map
mbr.b
message
message.1024x768
message.640x480
vmlinuz

i believe that the logo image is related with the message.1024x768 or message.640x480 but i cant in nay form or program open the files or undertsand how they were created, if i change or rename the file message the logo no longer appears same as if i coment the line "message=/boot/message" on lilo.conf

i understand very little of this but if anyone could help i would be very pareciated.

thanks.

---

### Post by blackzeus on 2008-05-26
the files i belive that have the logo are the atached one´s...

---

