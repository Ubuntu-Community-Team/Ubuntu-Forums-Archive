---
title: "Formatting boot partition"
date: 2007-06-19
forum: General Help
---

### Post by scottywz on 2007-06-19
Hi, I just switched to Ubuntu Feisty almost a month ago, and I'm now wanting to remove Winblow$ from my laptop completely.  I plan on reformatting the old Windoze partition and moving /home to it.  

Here's my partition layout:

```
/dev/sda
- /dev/sda1 PQSERVICE  (Will merge w/ /dev/sda2)
- /dev/sda2 (Windoze) (BOOT)
- /dev/sda3
  - /dev/sda5 (swap)
  - /dev/sda6 /
```
I want:

```
/dev/sda
- /dev/sda1 /home
- /dev/sda3
  - /dev/sda5 (swap)
  - /dev/sda6 ( / )
```
I pretty much know how to do it except for 1 thing:  the /dev/sda2 that I will be formatting is also the boot partition, as seen above.  So, here's my question:  How can I format that partition so that I am still able to boot?

Thanks, Scot

---

### Post by floke on 2007-06-19
I don't think it matters where the flag is, since grub is on your mbr and will point to your linux partition to boot. I would advise caution in erasing windows after just a month though. Give it a couple more just to be sure. It's always advisable to have another route of access to the web (ie to these forums) in case your ubuntu gets broken ;)

---

### Post by scottywz on 2007-06-19
So, the MBR is not on a partition?

Also, I have used SuSE for a long time last year, and I'm pretty used to Linux therefore.  I have had a better experience w/ Ubuntu; I'm pretty sure that I want to go Linux-only again.  I also have another machine (also Ubuntu, but still w/ Windoze).  Thanks for your opinion though.  :)

---

### Post by floke on 2007-06-19
No the mbr is the very first section of the HD (but correct me if I'm wrong here - I wouldn't call it a partition). You have Feisty on sda3 - so the mbr (grub) will point to that and not to Windows when you boot ubuntu. When I removed Windows I just zapped it and formatted the space as ext3 like you are suggesting.

Fantastic \\:D/

---

### Post by scottywz on 2007-06-19
Also, a burning question I have is this:

When I installed Ubuntu on my laptop, it told GRUB that Ubuntu was on hd(1,5) when it was really hd(0,5).  (I used an interesting method (netboot image on the USB drive) to install, and it thought that the USB drive was the first disk.)  Is there a way that I can tell it now that it's on hd(0,5) and not have to change menu.lst manually whenever I do a kernel update, because that always overwrites menu.lst.  Thanks

---

### Post by floke on 2007-06-19
No idea. Doesn't it know its really on 0,1 now?

---

### Post by scottywz on 2007-06-19
Yes, but it gets overwritten whenever there's a kernel update.  No big deal, I just thought there was a way to change what the data that menu.lst is overwritten with after a kernel update.  :)

---

### Post by scottywz on 2007-06-19
Okay, I just need to change some defaults in menu.lst that I previously ignored. Sorry. :)

---

### Post by scottywz on 2007-06-19
Ok.  I fixed the menu.lst thingy.  Here I go with the partitioning!

---

### Post by floke on 2007-06-20
Did it go ok?

---

### Post by scottywz on 2007-06-24
(Sorry to bump old post) Yes, it did go fine; I just haven't been able to say so 'til now.  Thanks.

---

