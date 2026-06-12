---
title: "oh no, what did i do? sudo cp -ax / ~/copy"
date: 2015-03-17
forum: General Help
---

### Post by pgib8 on 2015-03-17
I was trying to copy the root fs from an SD card to my home folder, so I could copy it back to another sd card later.

I cd to the root directory of the sd card and I type this command:
cp -ax / ~/copy

I don't even know what happened. After a long time it said cannot copy directory in itself I believe.

du showed that the root directory of the sd card was mounted at / and that the disc was completely full.
now when i start up the host computer and type in the password, nothing else happens.

i was able to boot into recovery mode and have a console. i'm trying to delete this ~/copy folder but it says cannot remove ... read-only file-system.

i did this: [FONT=Ubuntu Mono]mount -o remount,rw /
now i'm able to delete the folder. i'm pretty sure i know what i did wrong and I think i'm getting things back to normal now.[/FONT]

---

### Post by Holger_Gehrke on 2015-03-17
What you did ? You recursively copied all of your (root-) hd into ~/copy, filling up the hard disk completely, including the 5% emergency reserve that only root can use, since you had root-privileges at the time. Boot from a live usb or cd (for example your install media in 'Try Ubuntu" mode), mount the disk and erase the contents of ~/copy. The boot process stalls because it tries to write to some files (log files etc.) and can't.

---

