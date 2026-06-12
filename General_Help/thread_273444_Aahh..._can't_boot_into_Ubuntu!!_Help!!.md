---
title: "Aahh... can't boot into Ubuntu!! Help!!"
date: 2006-10-08
forum: General Help
---

### Post by Minyaliel on 2006-10-08
I installed DesktopBDS on a small partition just some days ago, and didn't really care to use my main OS. Now I wanted to boot into Ubuntu and no matter how much I press f1 I can't boot into Ubuntu. All I get is beeping. Please help...

---

### Post by lawina on 2006-10-08
Maybe Desktop BDS(sic.) overwrote your Ubuntu partitons!!

---

### Post by _lynX on 2006-10-08
> **Minyaliel said:**
> I installed DesktopBDS on a small partition just some days ago, and didn't really care to use my main OS. Now I wanted to boot into Ubuntu and no matter how much I press f1 I can't boot into Ubuntu. All I get is beeping. Please help...

You will have to use the Ubuntu Live cd to restore Grub. [http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub](http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub)

---

### Post by Minyaliel on 2006-10-09
I know it's there, I mounted into my ubuntu partition from the bsd install. Anyway, thanks, _lynX, I'm going to try that :)

---

### Post by Minyaliel on 2006-10-09
I've now booted into Ubuntu... unfortunately, it now won't give me the option to boot into my other partition. How do I fix that?

---

### Post by nikhilk on 2006-10-09
So you have booted into Ubuntu after restoring GRUB, is that correct? In that case you might have lost your original menu.lst and need to recreate that.

---

### Post by Minyaliel on 2006-10-09
> **nikhilk said:**
> So you have booted into Ubuntu after restoring GRUB, is that correct? In that case you might have lost your original menu.lst and need to recreate that.

I'vw restored grub, yes, everything seems fine. How do I create a menu.lst? It's the first time I've ever set up a dual- boot (probably why things went a little wrong, too).

---

### Post by nikhilk on 2006-10-09
Ok, first to confirm that menu.lst is the cause of the problem, post your "/boot/grub/menu.lst" file.

---

### Post by Minyaliel on 2006-10-09
Alright... 

> 
timeout 15
color cyan/blue white/blue
foreground ffffff
background 0639a1

gfxmenu /boot/grub/message

title MEPIS at hda1, kernel 2.6.15-26-386
root (hd0,0)
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 nomce quiet vga=791 
boot

title MEMTEST
kernel /boot/memtest86+.bin



---

### Post by nikhilk on 2006-10-09
As you can see there is only one entry in your menu.lst viz. "title MEPIS at hda1, kernel 2.6.15-26-386". So you need to add the corresponding entry for every installation you got in the menu.lst.

---

### Post by Minyaliel on 2006-10-09
Got it working, thanks a lot :)

---

