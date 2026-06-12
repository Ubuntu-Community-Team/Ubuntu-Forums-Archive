---
title: "[SOLVED] NTFS windows partitions not always visible on the desktop"
date: 2008-02-13
forum: General Help
---

### Post by new2ubun2linux on 2008-02-13
Hi, can anyone help with an odd problem I seem to have in Ubuntu 7.10?

I have it installed on a Sony Vaio SZ1 dual booting with Windows XP Pro. When I first installed it it worked beautifully with my various NTFS partutions available and read/write accessible. However a few times recently I have found when booting into Ubuntu that the NTFS partitions no longer appear. I thought they had gone for good, but yesterday they all reappeared!

I don't think I've altered any settings, I have simply been trying out Ubuntu and using it for web browsing and writing a few letters just to see if it is for me.

Perhaps the fault is fixed, but does anyone know what may have caused it as it is a pain if I can't access my data files from Ubuntu. Be gentle with any answers as although I am an experienced windows user I have no idea when it comes to Linux!

---

### Post by taurus on 2008-02-13
You need to remember to shut down XP cleanly which means no hibernation or sleep mode while you are using XP.  If you don't, Ubuntu won't automount it without using the force option.

---

### Post by new2ubun2linux on 2008-02-13
Ah! That makes sense:) - I have tended to use hibernate.

What do you mean by "Force mode" - is that easy and would it mean I could go back to using hibernate or are there any other issues?

---

### Post by taurus on 2008-02-13
Force option is only used if you need to recover your data on ntfs.  Use it all the time to mount ntfs partition in Ubuntu just because you like to use the hibernation in windows will eventually trash your ntfs partition.

So, it's up to you whether you want to shut down windows cleanly or you want to put it to hibernate.

---

### Post by new2ubun2linux on 2008-02-13
OK, thanks for the info - I'll stick to shutting down XP - and hopefully not use windows much at all...

---

