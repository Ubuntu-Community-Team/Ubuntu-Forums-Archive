---
title: "Kernel panic problem..."
date: 2013-06-11
forum: General Help
---

### Post by AndrewS on 2013-06-11
Hello

I am still having a problem with Ubuntu (all versions since, I think, 9.04) crashing on my PC.  The basic spec of the machine is: Core 2 Duo processor, Asus P5L-MX motherboard with 2GB RAM, Intel 954G graphics.  The problem is that every so often (arbitrary intervals, no pattern that I can discern) the screen goes black, and a message like the one attached is displayed.  The system re-starts after 30 seconds,but anything I was doing just before the crash is of course gone...  The strange thing is this only happens with Ubuntu (and IIRC Mint, which is I think Ubuntu-related); openSuse runs faultlessly and I have had to adopt this as my default OS.  This is a pity as I'd like to give the Unity interface a fair testing.

Any thoughts?

TIA

Andrew

[ATTACH=CONFIG]243734[/ATTACH]

---

### Post by sanderj on 2013-06-11
Did you Google the messages? For example: [https://en.wikipedia.org/wiki/Machine-check_exception](https://en.wikipedia.org/wiki/Machine-check_exception) and [https://wiki.archlinux.org/index.php/MCE_Handling](https://wiki.archlinux.org/index.php/MCE_Handling)

Did you run memtest86 (from the GRUB boot menu) for a few hours?

---

### Post by AndrewS on 2013-06-11
I have in the past run the Memtest86 utility that is accessed from the grub menu. Once it got to test #7, it started giving lots of red error messages. So I thought that's it, I have some bad memory. However, I ran other versions of Memtest86 (from various Ubuntu alternate install discs, openSuse liveCDs, even the standalone version, no memory errors detected.  I have recently replaced the memory (and increased it from 1GB to 2GB), and i still have the problem.

I'll look at your other suggestions, thank you.  Does seem strange that I only have the issue with Ubuntu?

Thanks again for your reply.

Andrew

---

### Post by sanderj on 2013-06-12
The problem might be in the motherboard too (not the RAM module itself): physical problems, temperature stuff or BIOS settings.

I had the same problem when going from Mandrake to Ubuntu. It turned out Mandrake used the kernel module "BadRAM" to circumvent bad RAM. So maybe OpenSuSE uses that too? You could try that for Ubuntu: check /etc/default/grub for "badram"

---

