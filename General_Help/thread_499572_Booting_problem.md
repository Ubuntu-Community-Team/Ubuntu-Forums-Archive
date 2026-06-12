---
title: "Booting problem"
date: 2007-07-12
forum: General Help
---

### Post by Saxomophone on 2007-07-12
Windows was being a pain, so I decided to reformat that partition, but now windows automatically starts before the grub boot loader. What can I do to fix this?

---

### Post by merlinus on 2007-07-12
If you reinstalled windows after formatting, you will have to reinstall grub.  You can do this from the live cd.

[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)

-merlin

---

### Post by spanky34 on 2007-07-12
similar issue, just backwards.  I wanted to install a different os on over my old linux partition, i reformatted it and now my grub bootloader still starts.  It comes up with an error 17.  I can use the superGRUB bootloader and get into windows that way, just the initial one is messed up.  What can i do to not have to use the superGRUB disc?

---

### Post by merlinus on 2007-07-12
You will have to restore the windows bootloader to the mbr.  SuperGrub has this option.

[LIST=1]
[*]boot SGD
[*]English Super [COLOR=#000000]GRUB[/COLOR] Disk
[*] Windows
[*]Fix Boot of Windows[/LIST]         -merlin

---

### Post by spanky34 on 2007-07-12
Ok i will try looking for that.  I'm sure i'll be back. Just a quick note, where under superGRUB is it?

---

### Post by spanky34 on 2007-07-12
its all good now, it was under the windows tools or w.e... I had to use the xp setting, but it worked just fine for booting windows.  No signs of GRUB anywhere.  Thanks a bunch.

---

### Post by Saxomophone on 2007-07-12
Okay, so do i use the ubuntu live cd, or do i need something else?

---

### Post by merlinus on 2007-07-12
Look at my first response.  You can do it from the live cd, and the url will give instructions.

-merlin

---

### Post by Saxomophone on 2007-07-12
all set. thanks!

---

