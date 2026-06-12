---
title: "Need GRUB help"
date: 2006-08-13
forum: General Help
---

### Post by Moodles on 2006-08-13
This is my harddrive setup:

> 
/dev/hdb : /dev/hdb1 is a storage drive - /dev/hdb2 is my swap drive
/dev/sda : /dev/sda1 is a storage drive - /dev/sda2 is where ubuntu is installed
/dev/sdb : /dev/sdb2 is a storage drive


I want to use /dev/hdb to boot ubuntu from /dev/sda2. No matter how much try I can't get GRUB to write to the MBR. 

I'm currently booting from a super grub disk cd. I really need step by step directions on how to do this.

---

### Post by vijirajan on 2006-08-13
Can you tell which hard drive is your BIOS default boot drive? Can't your BIOS boot /dev/sda directly?

Also, to which drive's MBR are you trying to install GRUB? Please clarify.

---

### Post by Moodles on 2006-08-13
/dev/hdb is my default BIOS boot drive, my motherboard can't boot from SATA drives (/dev/sda and /dev/sdb). I want the MBR on /dev/hdb obviously.

---

### Post by vijirajan on 2006-08-13
Now can you tell me what error you get when you tried to install GRUB on /dev/hdb's MBR?

---

### Post by vijirajan on 2006-08-13
This is how you would install GRUB to MBR (just in case you don't know):

```

> grub
> root (hd0,0)
> setup (hd0)
> quit

```

---

