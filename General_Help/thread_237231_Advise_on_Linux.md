---
title: "Advise on Linux?"
date: 2006-08-15
forum: General Help
---

### Post by 5th_horseman on 2006-08-15
I have just tried the live cd for "Dapper Drake", I like it, but my current hardware has some insolvoable issuses with it as do all linux distro's as I have to use some old "Dos hardware" which also means I am limited to using "Win 98 SE" as an OS, which bring me to my current problem, "Win 98 SE" refuse to run USB hardware, Microsoft claims timing problems with the AMD cpu prevent this, and I should upgrade to "XP" which is useless as it cannot run true dos, and will not recognize any of my burnt backup DVD's, aparentily this is a known problem of "XP", which microsoft keeps quite about till you find out the hard way.

What I need advise on is what is the best live cd or small distro to use to allow me transfer files from a USB harddrive to the harddrives in my machine. The USB drive work fine under linux,(so much for timing problems!), but live cd's don't have write permission for the in-machine drives. I've checked the forum here about this matter and it is suggested that "Ubantu" is not the best distro for this.

I don't need anything fancy, the main requirement is USB support, I don't know if anyone is familar with the old dos program "Xtree", but something of that level of capability is all I require plus USB of course. I'm looking for something with a small footprint that I can either install on the USB harddrive(4.3 Gb), I have boot from USB as a bios option, in this case smaller the footprint the better or run as a live cd with in-machine read/write permission. Any suggestion?

---

### Post by 5th_horseman on 2006-08-15
I must admit I thought that since "Ubantu" isn't suitable someone might had some useful tips on what might be suitable, I guess it's a case "Not Ubantu, it don't matter!" Thanks for help, I guess I'll try elsewhere, and not waste my time here.

---

### Post by meng on 2006-08-15
I don't know the answer myself. But I do know that it often takes more than an hour for someone who does know the answer to respond. If that's too long for you to wait, then you're 100% correct that you're "wasting your time" here.

---

### Post by 3rdalbum on 2006-08-16
I'm not even sure how he managed to get here, unless there's a "www.ubantuforums.org" that redirects?

To the original poster, if you're still wasting your time here: You could always dual-boot Win 98 and XP, or use Knoppix which will mount your existing Fat32 partition and auto-mount USB disks. Note that with Knoppix you will have to get "Properties" on the USB disk and set it to remount with Write permission.

Read/write can be done on Ubuntu, but it will end off being easier for you to do it in Knoppix.

---

