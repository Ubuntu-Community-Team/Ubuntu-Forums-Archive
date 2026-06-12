---
title: "After deleting Ubuntu partitions, GNU GRUB appears"
date: 2015-07-06
forum: General Help
---

### Post by ilia3 on 2015-07-06
Hi,

I have bought new HP laptop, which had Ubuntu installed already, I was disappointed that it had many bugs (or it seemed to me so, I had zero knowledge and experience on Linux/Ubuntu), so I decided to install windows on my laptop, which I had on DVD. While I was installing it I deleted every partition and created new ones (before installing I choose option CD/DVD *something* (UEFI), I don't even know what is UEFI) and I ended up with GNU GRUB (another hell), when I type 'exit' this screen loads
[IMG]http://s020.radikal.ru/i721/1507/70/4f5053deb1ef.jpg[/IMG]

Please don't get me wrong posting this in ubuntuforums, but I really need to uninstall ubuntu with everything and install other OS which I am familiar with. Actually I want to learn Ubuntu but don't have time for it at this moment.

Thank you for paying attention.

---

### Post by yancek on 2015-07-06
Did you attempt to install windows complete?
Which version of windows did you try to install?
What happens when you select the second option  on the menu "Windows Boot Manager"?
UEFI is a new method of booting computers.  Previously, a master boot record was used.
I don't use UEFI myself but you can get a lot of information by doing an online search.  Other members should be along who have experience with UEFI to make suggestions.

---

### Post by ilia3 on 2015-07-06
Its windows 8.1 64 bit. When i choose "Windows Boot Manager" same happens (GNU GRUB loads). I searched a lot. I don't want to use new methods like UEFI. Just need to make everything work normal.

---

### Post by dino99 on 2015-07-06
maybe grub has been installed on a hidden partition, or you have both a hdd & a ssd or a combo; check with a live partitioning tool and remove that partition; if you does not find one, then do a low level format
[http://hddguru.com/software/HDD-LLF-Low-Level-Format-Tool/](http://hddguru.com/software/HDD-LLF-Low-Level-Format-Tool/)
you then be ready for a clean installation after a cold reboot

---

### Post by oldfred on 2015-07-06
Almost all new systems since Windows 8 came out are UEFI. And that is how all new systems are configured. You have to force an install in the 35 year old BIOS install, but have to buy a new Windows license as the Windows 8 OEM license is stored in UEFI. 

If Windows is installed, then you should just select the Windows in screen shot you posted.
Also please attach screen shots, not post in line. Not everyone has High Speed Internet.
You can easily attach with advanced editor and paperclip icon.

---

