---
title: "Dual Boot results in too many choices"
date: 2016-01-07
forum: General Help
---

### Post by grandad67 on 2016-01-07
Hi, I've used 14.4lts for sometime, now I dual boot (MX). Now when I boot up; instead of a choice of  Ubuntu or MX there are 6 or 7 other alternatives('safe boot' etc). A year or so ago I asked this same question, and although I couldn't fix it from the answers, I managed to get rid of the unwanted alternatives(forgotten how). Two other answers I found through searching the forum  are. a: Try Grub Configure but I don't know how to find it. I tried googling. And b: /boot/grub/menu.lst. I've computer - boot/grub/.....       but no file 'menu list'. You may have gathered by now that I'm a long term nooby. Help on this matter will be much appreciated thankyou

---

### Post by v3.xx on 2016-01-07
Whats MX?

---

### Post by Bucky Ball on 2016-01-07
> **grandad67 said:**
> Now when I boot up; instead of a choice of  Ubuntu or MX there are 6 or 7 other alternatives('safe boot' etc).

Please be specific. What exactly is listed?

And yes, what is MX? :-k

---

### Post by oldfred on 2016-01-07
If you find references to menu.lst that is for grub legacy which Ubuntu have not used as standard since 2010.
Post this:
 List entries in grub
cat /boot/grub/grub.cfg  | grep menuentry

And then what entries do you want to remove?

If you really want a minimal grub menu, this user said this where 06_custom is your own manually created boot stanza for just your system(s). 

 From Ranch hand
You only need 3 scripts for grub to tick like a clock;
00_header
05_debian-theme
06_custom (or 07, 08, 09, 25, 40)

Details of creating custom boot stanza and turning off os-prober.
      
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

I think the tool you were looking for was grub customizer. It is a gui, and makes some simple changes easy to make. But it creates its own new grub scripts and can make it difficult if system wants to update or revert to standard scripts. For those really wanting to modify grub better to learn ways to do it yourself.

---

### Post by Dennis N on 2016-01-07
> You only need 3 scripts for grub to tick like a clock;
00_header
05_debian-theme
06_custom (or 07, 08, 09, 25, 40)

When using custom menus, I usually keep the 10_linux there too, as it allows easy access to specific kernels, and with the "Advanced Options" submenu takes little extra menu space.

---

### Post by grandad67 on 2016-01-12
Sorry, MX is a Linux OS,( most recent '15' issue). There are 9 items all together the only 2 I need are Ubuntu and MX15, the rest concern safe booting etc:. Anyway, my thank for all your replies and especially to Oldfred - ...Grub2 custom menus fixed it...after a bit of fiddling

---

