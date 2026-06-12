---
title: "One last question before install..."
date: 2007-10-16
forum: General Help
---

### Post by rohedin on 2007-10-16
:) Hi again everyone. I've downloaded wubi and the ISO seperately and saved them into my Second hardrive (145gb) which is almost empty. I'd just like to confirm the following things with you guys before I go ahead with the install.

1) My XP install and most of my documents and programs are on Drive C. If I install wubi onto my Drive D would the bootloader (which I presume is kept on the same drive as windows) still be able to boot between Xp on drive C and Ubuntu on D?

2) Stupid question and all, but I'm a bit nervous. I know that quite often the Ubuntu installation messes up, but is the chances of XP messing up quite slim, or is there a high chance that it could break? I have my docs backed up and XP install CD  at the ready just in case! :P

Incase you need to know, my specs are:

Dell Dimension E520
Intell Core 2 Duo 1.86ghz
2Gb RAM
ATI Radeon X1300 Pro graphics card. (256mb) 
2x 150gb hdd.

Cheers.

---

### Post by ago on 2007-10-16
> **rohedin said:**
> 
1) My XP install and most of my documents and programs are on Drive C. If I install wubi onto my Drive D would the bootloader (which I presume is kept on the same drive as windows) still be able to boot between Xp on drive C and Ubuntu on D?
Wherever you install wubi you will still be able to boot windows using windows original bootloader

> 2) Stupid question and all, but I'm a bit nervous. I know that quite often the Ubuntu installation messes up, but is the chances of XP messing up quite slim, or is there a high chance that it could break? I have my docs backed up and XP install CD  at the ready just in case! :P
The worse it can happen that you hardreboot while using wubi (=pull the power plug) and that causes a filesystem corruption. You can recover with the XP CD. Simple rule: never ever hard reboot (whether you use wubi or not).

---

### Post by rohedin on 2007-10-16
OK, thanks for the quick reply. But, eh, if say my PC hang during shutdown or startup and I can't shutdown normally, is there anyway I can restart without hard-rebooting? I heard there's some command of a sort, but I don't know it.

---

### Post by rohedin on 2007-10-16
Nobody gonna answer my question? :(

---

### Post by ago on 2007-10-16
Try first by pressing CTRL+ALT+F2, if you get a shell you can send the "halt" command. Then try CTRL+ALT+DEL.  If that does not work you can normally keep the alt+sysrq keys down and type R-E-I-S-U-B ("busier" in reverse). If you do  hardreboot and end up with a corrupted filesystem, you can use a windows rescue CD and run chkdsk /r. That should recover the situation.

---

### Post by rohedin on 2007-10-17
Great, thanks for answering. Finally I can install Wubi :)

---

