---
title: "Add another Linux OS to Grub"
date: 2006-07-20
forum: General Help
---

### Post by ahaslam on 2006-07-20
Hi all,

Before I found Ubuntu, I used to swap & change my distribution on a regular basis. I've just read about Vector Linux and installed it on another partition. I'm very interested to see what the fastest non source distro is like. I chose not to install Lilo as I don't want it to interfere with my current setup.

I've tried adding it in my menu.lst without success. I've never played with grub before & my bios is very picky (many live cd's don't boot, without being pointed to the precise location of the kernel).

I really want to add Vector Linux to my grub menu but my trial & error methods are not working, I need advice from an experienced user. For your information VL is installed on my second partition, hda2 .

If you need any other details, I'll be straight back to you (I really want to try this today).

All suggestions are very welcome, my experience with Grub is next to zero.

Thanks in advance,

Tony.

---

### Post by Irony on 2006-07-20
Its quite easy (or should be).

Just mount your Vector partition in Ubuntu and navigate your way to the boot folder of Vector to find the exact title of the kernel and initrd.

Then you can add it to your Ubuntu menu.lst.

Here are a couple of examples in my /boot/grub/menu.lst (commented out so that I can remember for future installations);

[PHP]# This entry added by me as an example
# installation on /dev/hdb4
#title		Zenwalk 2.01, hdb4
#root		(hd1,3)
#kernel		/boot/vmlinuz root=/dev/hdb4 ro
#savedefault
#boot

# This entry added by me as an example
# installation on /dev/hda9
#title		Fedora Core 4, hda9
#root		(hd0,8)
#kernel		/boot/vmlinuz-2.6.11-1.1369_FC4 root=/dev/hda9 ro quiet splash
#initrd		/boot/initrd-2.6.11-1.1369_FC4.img
#savedefault[/PHP]

---

### Post by ahaslam on 2006-07-20
Am I right to assume that my second partition of my sole hdd would be ***hd0,1?***

---

### Post by Irony on 2006-07-20
Yes; hda2 = (hd0,1)

Note you have to uncomment the actual entries.

---

### Post by ahaslam on 2006-07-20
Thanks mate. I've added the following and it boots (just need to set up X):

title		Vector Linux
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12 ro 
boot

Thanks again,

Tony.

---

### Post by ahaslam on 2006-07-20
**That doesn't do it** :(

It just tries to load Ubuntu with the kernel from Vector Linux (and doesn't work).
I assume that it needs an initrd line adding to the menu.lst (which I had originally) but that file is not present in Vector, see attached:

[ATTACH]13019[/ATTACH]

Any ideas?

Tony

---

### Post by ahaslam on 2006-07-20
Trial & error always prevails ;)

This entry gets it working properly:

title		Vector Linux
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12 root=/dev/hda2
boot

BTW Vector is very fast (much faster than xubuntu) but quite basic. Though it's too basic for an all purpose desktop, it'll be ideal to play games on. :)

Tony.

---

### Post by Irony on 2006-07-20
Glad it worked!

Probably you could put this and it would work;

[PHP]title Vector Linux
root (hd0,1)
kernel /boot/vmlinuz root=/dev/hda2 ro
boot[/PHP]

This assumes that the link shown in your picture leads to the vmlinuz-2.6.12 (right click on the link to find out). This means if you update the kernel you won't have to change grub - the link would presumably be updated or you would do it manually.

---

### Post by ahaslam on 2006-07-20
> **Irony said:**
> Glad it worked!

Probably you could put this and it would work;

[PHP]title Vector Linux
root (hd0,1)
kernel /boot/vmlinuz root=/dev/hda2 ro
boot[/PHP]

This assumes that the link shown in your picture leads to the vmlinuz-2.6.12 (right click on the link to find out). This means if you update the kernel you won't have to change grub - the link would presumably be updated or you would do it manually.

Cheers, the link does exist so I'll do that (sounds like a good idea).

Thanks again,

Tony.

---

