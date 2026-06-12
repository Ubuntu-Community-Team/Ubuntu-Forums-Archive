---
title: "No such partition error, can't boot my USB Disk Drive?"
date: 2019-06-25
forum: General Help
---

### Post by gnome100 on 2019-06-25
Hello everyone! I'm new to the forum. I apologize if I'm not up to date with the computer lingo, as I'm not a seasoned computer user, but I have a fair amount of understanding in computers. 

I have an issue when trying to boot up my hard drive and don't know how to proceed. 

So long story short: my HP laptop suffered (what I suspect is) a circuitboard problem and is out of commission.

I had Windows 7 and Linux installed on it and it had grub so I could select which OS I wanted when I booted the laptop up. 

I also have an Acer Aspire PC and I wanted to take the laptop Disk Drive out and plug it into my Acer (I have a USB adapter for it) so I could boot up my windows 7 and Linux desktops on my Acer since my laptop is finished. 

:oUnfortunately when I put my laptop's disk drive into the adapter and plugged it into my Acer and selected it on the boot menu, I was immediately given a blank screen that said, "error: no such partition" and it gave me a grub rescue prompt. 
I know my OSs are still there, I just can't access them because there's no grub anymore apparently and I doesn't wanna boot.

Does anybody know how to fix this? I couldn't find anything useful online anywhere. 

Side note: I've done this before, and booted a USB disk drive with my Acer and had no issues. But it only had one Linux OS on it, and no grub. 

Thank you!

---

### Post by oldfred on 2019-06-25
Is this an USB adapter that worked before?

My USB adapter is USB powered and works well with an old SSD (why I got it). But tried using it on a HDD and it just did not have enough power to spin up drive. Drive worked fine when plugged into a SATA port on desktop.
Some older adapters do not work with larger drives, gpt drives or any drive needing more power. Then you need newer adapter or one with external power.

       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by gnome100 on 2019-06-25
Oh, I haven't tried it before. This adapter is a newer one and my laptop's disk drive is a smaller one.  You think the issue could lie with the adapter itself? It seems to be fine to me and spins up alright, no noises that would indicate a problem wit the disk itself, but I'm not an expert on that. 

I used another adapter before. Not the same one I'm using now as it doesn't fit the disk drive.

you want me to give you a boot info summary report you say?

---

### Post by oldfred on 2019-06-25
Report should show if drive correctly seen.

---

### Post by gnome100 on 2019-06-29
Hi friend. Sorry for the late reply, but I have found a solution to the problem. Thanks for the help of course, and I may ask another question in the future, as I am still having trouble with the operating system. Thanks again for your help!

---

### Post by wildmanne39 on 2019-06-29
Hello gnome100, will you please share your solution for the good of the community, then use thread tools at the top of the page to mark the thread solved?

Thanks

---

### Post by gnome100 on 2019-06-30
Of course friend. But it wasn't really a solid solution. I Am simply going to clone the HDD to a SSD which I'd then put directly into my computer. It seems to work so long as it's not USB, and the no such partition error goes away.  I originally wanted to have an external USB SSD but I got a new commuter, and now my efforts are focused on the drive. The source disk is larger than my target disk in this case (I'm using clonezilla) so I might have to do a little reformatting and perhaps even reinstall the bootloader, and Windows startup keeps crashing, so I may have more to do in the future.

PS: Nice to meet a fellow Texan.

---

