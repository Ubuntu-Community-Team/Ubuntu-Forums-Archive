---
title: "I/O error on Ubuntu 12.06"
date: 2013-12-09
forum: General Help
---

### Post by rhinosfl on 2013-12-09
I'm using Ubuntu 12.06 in "try out" mode and am getting an I/O error when I try to copy data from one logical partition of a drive to another logical partition of the same physical drive. In other words, it's a Windows XP machine and I am booting Ubuntu from a CD and haven't actually installed Ubuntu on the computer. 

This approach has worked fine for me for the last few months but is messing up now. Long story short, I am unable to access the drive in any other way since replacing the motherboard a few months back. I've been told that is because my old mobo was a Northbridge while the current one is a Southbridge; Windows thinks the drive is empty but Ubuntu sees two of the three logical partititions just fine and that's good enough for me. 

Anyway, using the GUI, Ubuntu sees my C: and D: drives (which are separate 750 GB drives) and sees my F: and G: drives (which it knows as "Old" and "Current" respectively). F: and G: are two of the three logical drives on my third hard drive, which is a 3 TB internal SATA drive. (C: and D: are also internal SATA drives; E: is the third logical drive on the 3 TB drive but I can't see that one even in Ubuntu.) I use Ubuntu to move data back and forth between D:, F: and G:. But today, that stopped working. I was copy a fairly large folder over from G: to F: (Current to Old) and I started getting I/O errors on every file partway through that copy. I suspect the F: drive may be full but I'm not sure how to verify that in Ubuntu. I have some Linux/AIX background but I'm darned if I remember how to get a command prompt in Ubuntu so that I can determine the amount of space left on each logical drive. 

I also can't do "Move to trash" for any files on F: or G: but I can "Empty trash". If the F: drive IS full, I don't understand how I can rectify the situation if I can't move the data to another drive or delete it. I'm hoping this isn't one of those Catch 22 things where you can't delete anything any more if the drive is too full because the OS needs some room to do deletes but I'm hoping Ubuntu isn't that badly written. Maybe I've misdiagnosed the problem; maybe there IS a way to delete files even from a drive that is overly full. Assuming the drive IS full; I don't think I've proven that yet. Anyway, that's why I looked for these forums. I hope someone can help me figure this out. 

There's one complicating factor that I should mention. The problem is happening on my desktop computer, which is in my apartment. My apartment has no Internet access and probably won't for at least another couple of weeks. I'm posting this at the local library via my laptop. In other words, I'm only online intermittently and NOT on the computer that is having the problem so it may take a few days of back and forth for us to sort this out.  Please bear with me; I'll be for several hours every day but I won't be at home when I am online so I can't easily try something and then report back right away.

---

### Post by bashiergui on 2013-12-09
Use Gparted to see how much space is on the windows volumes.

---

### Post by 3rdalbum on 2013-12-09
Control-Alt-T brings up a terminal.

I/O Error usually means that either the source disk or destination disk is faulty. Usually the source disk. If Windows XP couldn't read it, my feeling is that the part of the disk that stores the data you are trying to copy, is corrupted and simply can't be read.

Unfortunately I'm not aware of how to force such a copy with unreadable data.

---

