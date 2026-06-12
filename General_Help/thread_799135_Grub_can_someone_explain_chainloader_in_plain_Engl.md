---
title: "Grub: can someone explain chainloader in plain English?"
date: 2008-05-18
forum: General Help
---

### Post by Tken on 2008-05-18
I've seen definitions for it in various places, but nothing more explanatory than "chainloader +1 indicates that GRUB should read one sector from the start of the partition".  To a layman, that's pretty useless.

My setup is about as simple as it gets: Windows XP on hda(0,0) and Ubuntu 8.04 on hda(0,1).  The upgrade to Hardy reset my boot/grub/menu.lst, so now I need to add XP to it, and I'm unsure whether I need to add "chainloader +1".  A yes or no to that question would be great, but an English explanation of chainloader would be even better.  :)

Thanks in advance.

---

### Post by Gunman1982 on 2008-05-18
Yes, but don't have an explanation right now, sry ;)

---

### Post by philinux on 2008-05-18
> **Gunman1982 said:**
> Yes, but don't have an explanation right now, sry ;)

That's as useful as a chocolate teapot. :lolflag:
[edit] missed the lolflag , that sounded a bit to terse sorry.

[http://linuxbasics.org/tutorials/during/booting](http://linuxbasics.org/tutorials/during/booting)

---

### Post by Tken on 2008-05-18
> **philinux said:**
> That's as useful as a chocolate teapot.

I think he was answering 'yes' to my question of whether or not I need the line "chainloader +1" with my Windows entry in menu.lst, not just answering the topic title.  :)

So, reading that link, it sounds like chainloader +1 causes whatever boot loader Windows uses to execute after grub is done?  Why is that necessary if I don't need to make any further choices after grub?

---

### Post by Gunman1982 on 2008-05-18
@Tken:
Exactly ;)

@philinx:
Sorry that I don't always just answer the title, would be hard on some topics like "Need help"
and regarding that teapot: I like my tea without chocolate flavour.

---

### Post by meierfra. on 2008-05-18
Just want to point out that there is no such thing as "hda(0,0)"  Linux would call this partion "/dev/hda1" or "/dev/sda1". Grub calls it "(hd0,0)"

---

### Post by meierfra. on 2008-05-18
"chainloader +1" tells grub to turn control over to the first sector  ("+1")  of the root partition ( the partition named by the "root ... " statement)

Also grub does not know how to boot windows. That's why it calls on the windows boot loader in  the first sector  of the Windows partition to do the job.

---

