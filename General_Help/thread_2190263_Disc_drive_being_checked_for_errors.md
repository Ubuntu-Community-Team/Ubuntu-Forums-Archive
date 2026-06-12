---
title: "Disc drive being checked for errors"
date: 2013-11-26
forum: General Help
---

### Post by itshilei on 2013-11-26
[COLOR=#333333][FONT=UbuntuRegular]Every time I lanched my ubuntu 12.04 (installed with wubi). I get the Message "Your disc drive being checked for errors. This will take some time. checking.. 3%. Press C to cancel." 

How can I skip it forever?

I heard the following command is not safe.[/FONT][/COLOR]
[COLOR=#000000]sudo touch /forcefsck

[/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][COLOR=#222222][FONT=Verdana]But with this command 
[/FONT][/COLOR][/FONT][/COLOR]
[COLOR=#000000]tune2fs -c 0 -i 0 /dev/sda1

[/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][COLOR=#222222][FONT=Verdana]I got:
tune2fs: Permission denied while trying to open /dev/sda1[/FONT][/COLOR][/FONT][/COLOR]
Couldn't find valid files ystem superblock.

Do you guys know what I should do?

Thx

---

### Post by oldos2er on 2013-11-26
Wubi installs Ubuntu to a "virtual disk" inside your NTFS Windows installation, not to a partition. I think you'd want to boot Windows and run its file check.

---

### Post by jdeca57 on 2013-11-26
First of all you could start your computer in the evening / during a lunch break and let that check do its work. After all, there's a reason why it checks your drive and I wouldn't know why you'd skip that. And a permission denied is for two reasons: either you're not root (sudo) or that check can't be done on a mounted drive. (start from a live CD)

---

### Post by itshilei on 2013-11-28
Almost everytime I let the check does its work. But I can't bear it does so every time I boot my computer (Every time the system can't find any error.)

The check begines because one day the disc where I put the Ubuntu was full. (I put something into that disc when I use windows.)

---

### Post by itshilei on 2013-11-28
You mean I have to do the disc check on Windows?

---

