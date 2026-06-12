---
title: "keyboard doesnt work during grub screen"
date: 2006-07-04
forum: General Help
---

### Post by Trab on 2006-07-04
almost all problems ive had that i cant solve myself with ubuntu involve grub.
i've brought my machine up to my dads house for the summer, and am using one of his spare p/s2 keyboards. (similar to the one i use at home)
now, during the grub screen, no keys work. i cant select another OS (other than the default) nor can i hit enter to select the default.
i know a few work arounds (un plugging hard drives, editing the grub menu)
but thats rather a pain.
any suggestions?

--Trab


Ps. totally unreleated but how i can i Dehex a passphrase for my wpa key?

---

### Post by erimar77 on 2006-07-04
does the keyboard work during the bios, or is it grub only

---

### Post by Trab on 2006-07-05
its only for grub that it doesnt work.
works fine for bios.

---

### Post by Guard][an on 2006-07-07
same here
keyboard is not responding while being in the grub menu screen (text mode)
i have a dell inspiron 8600 laptop

---

### Post by Guard][an on 2006-07-17
bump ? today it prevented me from entering the recovery mode :(
anyone else experiencing this problem ?
anyone having a solution for this please ?

---

### Post by punx45 on 2006-07-24
i am having the same problem with an install i did this past weekend.

keyboard (USB) is responsive at BIOS, but unresponsive at GRUB (as well as live CD boot menu).   I am running a dual boot with Windows, but fortunately on separate drives so i can select a boot drive in BIOS.

motherboard is a VIA chipset.

---

### Post by Nightdrive on 2006-07-28
Yup, same here. Only using a dual boot Ubuntu for a day, but now I can't get into Windows, and all my networked shared files are on it!
My wireless USB keyboard work fine in BIOS, and in Ubuntu, but doesn't work at the OS selection screen (I assume this is the GRUB screen)

Surely someone most have an idea

---

### Post by nmcl86 on 2006-08-25
i have the same problem. i installed winxp first, and then ubuntu. the keyboard didn't work very well in the live cd menu (i had to press the arrows a few times before it worked) and i managed to boot into windows a couple of times, even though the keyboard was very slow to respond, and now it doesn't work at all. at the grub screen, if i press anything on the keyboard the timeout counter disappears but then nothing else works. can't enter the default o/s, which is ubuntu (something i would also like to change!). i deleted ubuntu using the winxp boot cd so i could use windows, but now i can't reinstall ubuntu because the menu of the live cd menu doesn't respond to the keyboard, just like the grub screen. this is driving me crazy! if anyone has experienced this problem and has a solution, i would greatly appreciate it! thanks.

---

### Post by nmcl86 on 2006-08-25
bump!

---

### Post by peabody on 2006-08-25
> **nmcl86 said:**
> bump!

This is probably due to problems with communication between grub and the bios.  Grub has no native USB support/ ps/2 support, it has to rely on what the BIOS presents it with.  The only advice I can give is to fiddle with the bios settings for the keyboard (if there are any) or upgrade the bios.  I'll try and do some more digging.  There may be a way to patch grub so it'll work with your bios.

---

