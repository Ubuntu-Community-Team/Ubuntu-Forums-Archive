---
title: "Unable to start Vista"
date: 2007-10-27
forum: General Help
---

### Post by aropupu on 2007-10-27
I bought my new laptop 5 weeks ago, and so far I had used Vista since Feisty didn't work well with LAN and WLAN. I waited till Gutsy came up and installed immediately. After facing few problems I managed to install Ubuntu by devoting whole HD for it (yup, Vista was gone)

Problem is that I need Vista for some programs needed in university. As far as I know, there's no linux version of those, so I decided to get vista back. Ok, i went through partitioning and everything gone almost smoothly. When I tried to boot first time, GRUB gave me no option to start windows.

What's the problem? I'm quite new with Ubuntu, though I share great passion for it. Thanks for help in advance ^^

//Acer 5520G
AMD-Turion X2 TL-58
Ati HD 2400 XT (not working well, screen is strecht to 16:9 while using 1024x768)

---

### Post by suchawato on 2007-10-27
Grub will not automaticly recognize Vista.
Try running Lilo, OR/and, get a copy of [SuperGrubDisc ]("http://supergrub.forjamari.linex.org/"). This is a really great boot disc, which is invaluable for walking you through and fixing boot problems with multi partitions.
you can even use it (as I do) as a fix in itself, to boot to either partition using SGD. It can fix your boot of windows, restore boot of Linux, install LILO, Boot to any partition that you select, and many other options. and it is very user friendly.

---

### Post by PmDematagoda on 2007-10-27
If you did indeed use the entire HD then Vista must be gone.

But do not fear, could you tell us what type of Windows programs you need to use and perhaps we can help you.

EDIT:- Forgive me, I made a mistake, you did install Vista again, but then by rights the MBR should be written using Vista's boot-loader which should allow you to boot into it. But if there is no such thing, you can use SuperGrub/Lilo as suggested by suchawato.

---

### Post by aropupu on 2007-10-28
Thank you so much. But as I told you, I'm so new with this that even starting or installing LILO is a problem. I just downloaded it from Synaptic, but i can't do a thing nor configure it? GRUB is still booting the system....

Damn I am baby =D

---

### Post by logos34 on 2007-10-28
> **PmDematagoda said:**
> but then by rights the MBR should be written using Vista's boot-loader which should allow you to boot into it. But if there is no such thing, you can use SuperGrub

That's what I would have thought too.  

You can try super grub disk or maybe just editing menu.lst to add windows will do the trick:

Check your partitions:

**sudo fdisk -l**

open grub config file as root to edit:

**gksudo gedit /boot/grub/menu.lst**

so, for instance, if vista is sda3, add this entry to bottom:
> 
title		Windows Vista
root		(hd0,2)
savedefault
makeactive
chainloader	+1

---

### Post by wheredidrealitygo on 2007-10-28
Copied and pasted from another thread I was helping someone with ;)

Try this:

load your vista dvd, upon boot, go to "repair your computer" on the bottom left, then go to "open a command prompt"

Type:```
 bootrec.exe /FixMbr
```

Case sensitive.

Refer to [http://support.microsoft.com/kb/927392]("http://support.microsoft.com/kb/927392") for more info on this particular tool (you may want to print it) than I feel like typing lol. But you should be fine with the code I typed above. (I tested it in a VM and worked fine)

Then, if you can only boot into Windows Vista afterwards (which is to be expected) run the supergrub disc again to restore Linux.

See attached pic.

[http://ubuntuforums.org/attachment.php?attachmentid=48090&d=1193546502]("http://ubuntuforums.org/attachment.php?attachmentid=48090&d=1193546502")

---

### Post by logos34 on 2007-10-28
> **wheredidrealitygo said:**
> Then, if you can only boot into Windows Vista afterwards (which is to be expected) run the supergrub disc again to restore Linux.

yes, but then he'll be right back where he started---grub menu without a vista boot entry (vista was installed AFTER ubuntu).

---

### Post by wheredidrealitygo on 2007-10-28
It might have something to do with picking the wrong option in the SuperGrubDisc. [This guy]("http://ubuntuforums.org/showthread.php?t=594367") had the same problem, see the last post on page 1. Apparently he had accidentally set it to boot from the recovery partition and not the OS partition, that's why it wouldn't get recognized.

---

