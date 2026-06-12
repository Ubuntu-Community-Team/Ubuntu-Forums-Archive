---
title: "Crashed during update, only GNU GRUB version 2.04 prompt"
date: 2020-10-10
forum: General Help
---

### Post by thaumiel-x72 on 2020-10-10
I swear it wasn’t me.  System hung mid update and leaving it run for a while never brought it back.  Any suggestions at all would be appreciated.

---

### Post by thaumiel-x72 on 2020-10-10
Update:  boot repair returns the message:
error: you need to load the kernel first.

---

### Post by thaumiel-x72 on 2020-10-10
Update:
ls (hd1,2)/
returned 
lost+found/ boot/ bin dev/ etc/ home/ ... etc

---

### Post by thaumiel-x72 on 2020-10-10
Update:
after set root=(hd1,2)
I need to enter
linux /boot/vmlinuz-5.4.0-48-generic root=/dev/sda?
how do I ascertain the correct partition number to follow &#8220;sda?&#8221;

---

### Post by CelticWarrior on 2020-10-10
BIOS or UEFI?

---

### Post by Impavidus on 2020-10-11
Boot the computer using the live disk you keep for cases like this. Then install and run [Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) and create a boot info summary. Post the link here. That may tell us more.

---

### Post by thaumiel-x72 on 2020-10-12
System 76 laptop came with Ubuntu already installed.

there is no disk drive attached.  Waiting for a system 76 to tell me if it&#8217;s even possible to boot with a USB stick and if so how do I tell it to do that.

I cannot figure out how to get to the BIOS boot screen to tell it to not boot the usual way.

---

### Post by thaumiel-x72 on 2020-10-12
Took a screen shot of my last post to the System 76 support ticket.

so far not responded to.
i don&#8217;t know if I can post pics here or not...

---

