---
title: "Grub=&quot;Error 17 - Cannot mount selected partition&quot;, Feisty-H3=mounts fine"
date: 2007-02-05
forum: General Help
---

### Post by Ubuntiac on 2007-02-05
Greetings Ubuntites!

I've searched and read just about every post on grub / mbr / partitioning I could find I'm at a loss. Here's the details of my situation:

**HARDWARE:**
[LIST]
[*]IDE HDA (2 x NTFS partitions, #1 with win XP)
[*]IDE HDB (1 x NTFS partition, general data)
[*]IDE HDC (2 x ext3 partitions, 1 for kubuntu edgy and root, 1 for data and a swap partition)
[/LIST]


**SITUATION:**
[INDENT]Edgy had been working fine. I restarted (after doing nothing unusual) and instead of bootloader got "Operating System Not available" or something like that. 

I resinstalled grub fine and am _now able to get the bootloader menu_ by changing BIOS to boot to HDC instead of HDA.

Now whenever I choose _any option in the grub menu_ (EG memtest / ubuntu etc) I get *"Error 17: Cannot mount selected partition"*.

The mystery part is that if I go into the grub CLI via a terminal, I get *"Inconsistant file structure"* with the same commands (root, kernal etc). Any kind of operating system loading through Super Grub Disk also go down with similar errors, yet _in Feisty's file manager all drives mount and show data just fine_.
[/INDENT]

The main menu item in menu.lst is:
[INDENT]
root (hd2,0)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hdc1 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot[/INDENT]

All ideas and/or help greatfully appreciated! :KS

---

### Post by ~LoKe on 2007-02-05
Change
> root (hd2,0)
to
> root (hd1,0)
or
> root (hd0,0)
Or something like that.  Keep messing with it.  It's hdc, so my money is on:
> root (hd0,2)

**EDIT:** In case you didn't already know, you can hit "e" on your kernel line to modify the values, then "b" to boot.  I'm sure you know this, though.

---

### Post by Ubuntiac on 2007-02-05
> or:
root (hd0,0)

All hail ~Loke!

Benevolent ruler of the Ubuntuverse!
Wise sage of the grublands...
Generous aide to n00bs everywhere...


Yes, incase you didn't guess, that worked beautifully.

Many, many thanks! Now I get to keep my hair after all! ;)

---

### Post by ~LoKe on 2007-02-05
You're quite welcome. :)

---

### Post by Jimcanoa on 2007-02-22
I have more or less the same problem as Ubuntiac, but I'm afraid of executing the command

```
root (hd0,0)
```

since XP in installed in the first partition of hd0. Is it safe? If i understand correctly root tells grub where to find GRUB conf files, such as menu.lst, but why would it work? In (hd0,0) I have XP...

---

### Post by Jimcanoa on 2007-02-22
So, I couldn't wait for your answer and I changed menu.lst conf so it would do root (hd0,0)... AND IT WORKED!! 

I humbly join Ubuntiac in his praise, oh ~Loke !!

Thankyou a thousand times!

---

### Post by spanners on 2008-05-21
Loke you're a legend! Google brought me here and I had to register and say thanks as I'd been tearing my hair out!

---

