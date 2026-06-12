---
title: "automount usb-disk fat32 assign rights"
date: 2008-02-18
forum: General Help
---

### Post by mättu on 2008-02-18
Hi folks

Much of my data is on a huge usb-stick. It is formatted fat32, because I use it on different machines, some of them Windows or Mac. I don't have admin-rights there, so installing ext-drivers on these machines and formatting ext2 is not an option.
When I mount the disk in (x)ubuntu it is assigned 700 file rights.
This becomes a problem when I want to upload some files to a server on the internet, where they need 644 to be read & processed by apache.

I wondered if there was any possibility to "simulate / assign" (or whatever) 644 file rights and 755 directory rights for / to this disk. 
I found some threads mentioning entries in /etc/fstab, which sounds strange to me, as this disk is not always present at startup.

I read through my udev-rules and found:
SUBSYSTEM=="usb_device",                MODE="0664"

Now what?!

help appreciated.
:m)

---

