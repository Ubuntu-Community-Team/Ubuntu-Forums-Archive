---
title: "Booting a USB pendrive from a floppy"
date: 2006-12-27
forum: General Help
---

### Post by Steve Smith on 2006-12-27
After Santa brought me a 2GB memory stick to make a [persistent LiveCD installation](https://wiki.ubuntu.com/LiveUsbPendrivePersistent), I've realised my computer won't boot from USB.  I assume that you can boot from a floppy which will then automatically boot the USB pendrive, could someone tell me how please!

---

### Post by paridoth on 2006-12-27
this has been on my todoo list for making a flash drive live distro, as not all computers can boot to usb, but i haven't gotten around to googgling for instructions, my best guess is to install grub on a floppy, then boot the computer to the grub floppy with the usb flash drive plugged in and see if you can root/find files in the usb drive, if you can then it would be simple to have the grub boot loader then boot the OS on the flash drive, otherwise start googgling for guides. a quick search didn't get me anything but i'm sure a more detailed one would turn up something, let me know if you find it!

---

### Post by Steve Smith on 2006-12-28
Thanks!  I've got as far as making a GRUB floppy, which was easier than I thought.  I followed [intructions at Linux Journal](http://www.linuxjournal.com/article/4622).  But I can only make GRUB see the harddisk and the floppy, not the usb stick, which Ubuntu sees at /dev/sda1.  If you press tab for all options, GRUB only lists hd0 and the floppy.

Do I need drivers on the floppy for the USB port?

---

### Post by paridoth on 2006-12-28
don't take anything i'm saying as being engraved in stone, my understanding of usb, and grub are limited, but i'm guessing that whatever allows grub to see usb flash drives is tied in with the motherboards ability to boot to a usb device. i would try searching and posting here at the grub forums at nabble
[http://www.nabble.com/Grub-f1675.html](http://www.nabble.com/Grub-f1675.html)
i posted there a couple times in the past with grub questions and they might no of a way to get grub to see the flash drive.

---

### Post by Steve Smith on 2006-12-28
Thanks, I will do!  Will let you know if I get anywhere.

---

