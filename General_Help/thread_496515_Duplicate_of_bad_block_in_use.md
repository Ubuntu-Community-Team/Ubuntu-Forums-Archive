---
title: "Duplicate of bad block in use"
date: 2007-07-09
forum: General Help
---

### Post by j_evenstar on 2007-07-09
I found similar posts regarding this, but didn't get a decent answer. Anyway, my pc won't boot into the desktop. Here's what is says:
```
Checking root file system...
/dev/hda1 contains a file system with errors, check forced.
/dev/hda1:
Duplicate or bad block in use!
```
Is there a way to solve this without reformatting the computer?
My pc specs are 80GB, 1.65GHz AMD Athlon, 2x256 Mb RAM.
Anybody's help is greatly appreciated.

---

### Post by Soybean on 2007-07-09
Well... it sounds like hardware failure (something physically wrong with the hard disk or the disk controller). Could be bad, but there are a few things you can try.

Do you still have your Ubuntu install CD? You could boot from that, and run fsck from there. You may have to read up on fsck to be able to use it manually. Also, you may be able to mount hda1 when you're running from the CD, and maybe get at your data that way (so you can back it up if you do have to reinstall).

---

### Post by j_evenstar on 2007-07-10
i don't think it's with the hard drive. the hard drive's just a little older than a year actually.
how do i run fsck from there? i don't even know what fsck is in the first place. and how do i do the second one you recommended? thanks.
i'll research on this as soon as this is posted.

---

### Post by Soybean on 2007-07-11
> **j_evenstar said:**
> i don't think it's with the hard drive. the hard drive's just a little older than a year actually.
Well, it's fairly common for hard drives to have a few sectors go bad here and there. It could be that yours just happened to develop a bad sector in a particularly unfortunate place. Also, a power surge or a bad capacitor could make your disk controller go wonky at any time.
> how do i run fsck from there? i don't even know what fsck is in the first place.
fsck is a command-line program that checks for file system errors and tries to fix them. It's comparable to scandisk or chkdsk from Microsoft, if you're familiar with either of those. When you're booted into the Live CD, you should be able to get a command line by going to Applications-Accessories-Terminal. Then you can type "man fsck" to find out more about fsck's options, and then run it on /dev/hda1. (e.g. "fsck /dev/hda1", but there may be some more helpful options you can add in there too, I'm not sure).
>  and how do i do the second one you recommended? thanks.
I haven't used one of those CDs for this sort of thing in a while, so I'm afraid I can't give a detailed step-by-step guide... it may mount your hard drive automatically, or there may be some easy GUI way to do it, or you may need to learn about some more command-line programs (mainly "mount"). Basically, the idea is that some of your boot files are obviously broken, but the rest of your files may still be intact if you can get the system booted (using the Ubuntu CD). If you can access your files, you can burn them to a CD or copy them to a network share or an external hard drive or something, so you've got a backup in case the problem isn't fixable.

Sorry for being kind of vague here... it's a tricky problem. It's the kind of thing I would normally approach more by instinct than by a formal procedure, so I'm having a hard time giving good advice. Good luck!

---

