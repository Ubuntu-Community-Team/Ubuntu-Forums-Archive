---
title: "Ubuntu 7.10 on USB dongle"
date: 2008-03-11
forum: General Help
---

### Post by LinuX-M@n1@k on 2008-03-11
Hi
I found [this site]("http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/") where is described how to install Ubuntu 7.10 on USB dongle, but I'm looking for something like EWF (Enhanced Write Filter) on Windows XP Embedded, but for Linux.
Does anyone know where to find it ? I asked Google, but I didn't find anything. Any help would be appreciated :)

---

### Post by LinuX-M@n1@k on 2008-03-11
*bump*

---

### Post by LinuX-M@n1@k on 2008-03-12
Bump 2 !

---

### Post by Jim! on 2008-03-12
Nope, Sorry dude. But with all the users on this forum I'm sure you'll get some good info sooner or later.;)

---

### Post by Rhubarb on 2008-03-12
The partition named "casper" on the website there is a partition where changes are saved.
So in theory you may be able to create a RAMdisk, name it casper, and set the partition up etc.
Just remember if you want changes to be saved, it must be saved to non-volatile memory.

Could you please state why you want to do do this, as there may be better ways of accomplishing it.

---

### Post by LinuX-M@n1@k on 2008-03-12
> The partition named "casper" on the website there is a partition where changes are saved.
So in theory you may be able to create a RAMdisk, name it casper, and set the partition up etc.
Just remember if you want changes to be saved, it must be saved to non-volatile memory.
Thanks
> Could you please state why you want to do do this, as there may be better ways of accomplishing it.
Just for fun :)

Edit: I can't boot from it and I don't know why... it's flagged "boot" (in gparted) and my motherboard supports booting from USB-HDD, USB-FDD and USB-DVD(or CD). Any ideas ? I'll create a new thread if I must... :(

---

### Post by Rhubarb on 2008-03-12
In your BIOS settings, have you told it to boot from USB before booting from CD / HDDs?
It could just be a simple boot sequence issue.

---

### Post by LinuX-M@n1@k on 2008-03-13
i told it to boot only from USB-HDD and/or the other USB-*, but it says that there's no bootable media or something...

---

### Post by Rhubarb on 2008-03-15
That's weird, and I can't really explain why.
Anyone else have any good ideas?

---

