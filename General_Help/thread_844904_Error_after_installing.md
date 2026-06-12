---
title: "Error after installing"
date: 2008-06-30
forum: General Help
---

### Post by kyle99 on 2008-06-30
Alright, I'm trying to install Ubuntu on my computer, which is really new. It installs fine, then I restarted my computer, selected Ubuntu as the operation-system, then it has the loading screen, and then it gets this error, which keeps repeating.
[IMG]http://img57.imageshack.us/img57/2497/downsized0629082258np9.jpg[/IMG]

Then, I did the exact same thing on my other, older computer and it installed perfectly. What is wrong, and how do I fix it?

Thanks!

~Kyle

---

### Post by VMC on 2008-06-30
It's hard to read but what I could make out, DRDY is usually a drive error.
How was this installed, after Windows or no Windows?

---

### Post by kyle99 on 2008-06-30
It was installed after windows vista, and was burned to a disc.

---

### Post by cariboo on 2008-06-30
You have to edit /boot/grub/menu.lst to get by this bug in your bios. The best way to do this is to boot from the LiveCD. Once you are at the desktop open Applications-->Accessories-->Terminal and type:

```
sudo mount /dev/sda2 /mnt
```
Then hit enter next in the same terminal type:

```
sudo gedit /mnt/boot/grub/menu.lst
```

in the file that opens scroll down till you see

```
title		Ubuntu intrepid (development branch), kernel 2.6.26-2-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.26-2-generic root=UUID=2b9762e0-55e3-4067-81c0-461b956440f9 ro quiet splash
initrd		/boot/initrd.img-2.6.26-2-generic
quiet
```

add noapic next to quiet, save your file and reboot.

Jim

---

### Post by kyle99 on 2008-06-30
Thanks a lot, I got it working.

---

### Post by kyle99 on 2008-06-30
It didn't work. I get a:

ata2.00 status: { DRDY }
ata2.00 exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
cmd a0/00:00:00:00:24:00/00:00:00:00:00/a0 tag 0 pio 36 in

error message which keeps repeating itself. This is just when I try to do a Ubuntu test without installing. What's up?

---

