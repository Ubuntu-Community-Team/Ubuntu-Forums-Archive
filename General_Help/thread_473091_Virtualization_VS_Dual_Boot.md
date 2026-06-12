---
title: "Virtualization VS Dual Boot"
date: 2007-06-13
forum: General Help
---

### Post by Dylnuge on 2007-06-13
I like Ubuntu and Linux. However, there is some Windows software that I cannot live without, and which cannot run very well or at all under Wine on Linux, such as the Adobe CS3 suite. I am currently dual booting to run software, which becomes a huge disconnect, because the files are not shared between the two OSes, and I have a web server set up in Ubuntu but Dreamweaver runs in Windows, etc. I have tried some alternatives, but they don't work as well for what I am doing.

I am wondering if using software like VirtualBox or VMWare Server would be a better solution. I have no need to run 3D under them, so I don't care that it does not work. Would CS3 run too slow while virtualized? Would my current solution be better? Would using VirtualBox or VMWare make sharing files eaiser?

Some notes: I have a Dell XPS M1710 Laptop, single 100 GB hard drive, 20 GB given to Linux, 60 GB to windows, 20GB to a special "shared files" FAT32 partition. I program in Linux and design in Windows, which means I reboot a lot. If I virtualized, I would keep the Windows partition but shrink it, leaving only the few things I must absolutely run under Windows on it (mostly games) and some basic software to use while in Windows (Firefox, Outlook, etc). I am open to purchasing an external hard drive, however I don't have a ton of money to spend, so I would prefer not to have to.

Thanks,
Dylan

---

### Post by scott_g on 2007-06-13
Hi,

I just installed VirtualBox, and like it a lot.  It lets you specify the exact amount of ram you give to the virtual computer, and creates a virtual hard drive.  I find it fairly fast (especially since I only gave it 200mbs of ram), but haven't used it very much yet.  My advice would be to try the VirtualBox or VMWare (no experience with this one), and see if it can run it; if it doesn't, there's no harm done.  I wouldn't want to do anything overly intensive in a vitual machine (like video editing, or gaming), but other than that, I havent had a problem yet (I find that its nice to be able to view things, like website, in other OS's without having to reboot).

Scott

---

### Post by Dylnuge on 2007-06-13
Thanks. I will try the software, however, my main problem is that without a second hard drive, my space is too taxed to create a Virtual Machine.

---

### Post by scott_g on 2007-06-13
My virtual drive is very small (2GBs); I access the files on the rest of my computer through shared folders (fast cause they're on the same computer).

Scott

---

### Post by Citizin on 2007-06-13
Try a program called Crossover, its WINE only 100% better I think, works a lot faster, and runs games as well.

---

### Post by mark2741 on 2007-06-14
So you're saying that Crossover supports Adobe CS3 now?

---

### Post by Citizin on 2007-06-14
I don't know I havn't tried it.

---

### Post by Dylnuge on 2007-06-14
It does not. Last I checked, Photoshop 7 and Studio MX were the latest versions. I don't really feel like paying $60 for something that won't help me with my problem...everything else I got working fine under Wine, except Civilization, which now works fine under Cedega.

Crossover Office does not focus on the Adobe product line because their primary customer base is Mac users, and Mac has native Adobe products.

---

