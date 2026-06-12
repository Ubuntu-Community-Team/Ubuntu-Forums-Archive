---
title: "Ok, I'm stumped.............."
date: 2008-01-22
forum: General Help
---

### Post by jabeez on 2008-01-22
I recently built a machine for my bro-in-law outta some old parts, consisting of an Asus A7V-e mobo, athlon 1400, 1gig of ram. I had a dual boot XP/Ubuntu Studio install up and running, but then he wanted to take his 250 gig storage drive and put it in the Studio box. At this point the Windows drive died (Studio is on separate HD), so I go ahead and install the big drive and update Studio to Gutsy (fresh install).

Well, I go to install XP in VirtualBox, and it keeps spitting out errors when trying to install (windows). Of course I'm stumped and after much poking around I notice the BIOS is detecting the 250 gig drive as an 8.5 gig, which was the size of the drive that died (coincidence?). I've tried finding out if there is a drive limitation with that mobo, but have found no definite answers, and even if there was, wouldn't it recognize up to it's limitation (like 137 gig or whatever)? Also, when I'm in Studio it sees the drive and seems to recognize it correctly, as well as through PartedMagic/Gparted live CD's. If the BIOS isn't capable of handling that size drive, how is this possible?

Well again, I'm completely stumped. My only other thought is maybe since Grub installed to MBR of the large drive, would that somehow corrupt it's reporting in BIOS? Good lord, this is driving me NUTS!!!! Anyone???????

---

### Post by LaRoza on 2008-01-22
It sounds like you have to set the settings in the CMOS for this drive. 

Without being there it is hard to say for sure. Look at the documentation for the drive and the motherboard. Also, look for bios updates.

---

### Post by jabeez on 2008-01-22
There is a BIOS update, but alas none of my machines have floppy drives, and it looks like quite the process to flash from CD and that seems pretty risky. So is Linux smart enough to bypass the BIOS and recognize it as a 250 GB drive when BIOS is apparently seeing it as an 8.5 GB? That's what really has me stumped.

---

### Post by jabeez on 2008-01-22
Oh yeah, and when I tried setting the drive manually in BIOS, there isn't even enough room for the cylinders, it has 480000'ish, but there is only room for 5 numbers, which would leave me to conclude it's a BIOS issue were it not for Studio and the live CD's reporting it's size correctly.

---

### Post by LaRoza on 2008-01-22
> **jabeez said:**
> Oh yeah, and when I tried setting the drive manually in BIOS, there isn't even enough room for the cylinders, it has 480000'ish, but there is only room for 5 numbers, which would leave me to conclude it's a BIOS issue were it not for Studio and the live CD's reporting it's size correctly.

It may be a BIOS issue and probably is. I know that drives sometimes have software in them so the OS can see them when the BIOS can't.

I recommend getting a floppy drive and flashing the bios, or getting a newer motherboard. Find a motherboard will probably be easier than finding a floppy drive nowadays.

---

### Post by Rhubarb on 2008-01-22
Some IDE hard drives have got a jumper in them to restrict the drive to ~ 8GB.
Check to see that the jumpers in the drive are set up correctly.

Upgrading the PC's BIOS is reasonably easy to do, just follow it here:
Start reading at the "Creating the disk (CD-method)" line
[http://ubuntuforums.org/showthread.php?t=318789](http://ubuntuforums.org/showthread.php?t=318789)

---

### Post by jabeez on 2008-01-22
Well thanks for the help, I've got a PCI/IDE card laying around, maybe I'll give that a shot, but I think I'll just surrender for the night.................Cheers!!

---

### Post by jabeez on 2008-01-25
Well sweet Jeebus, this thing just continues to confound.............I ended up flashing the BIOS, which fixed the drive recognition thing, but XP still refused to install, so after much dicking around I ended up pulling both sticks of RAM and re-seating, which allowed XP to install (yay?). I then did a fresh install of Gutsy (K), and all is working well, except XP still REFUSES to install under virtualbox. I have an extra 512 stick 'O ram that I swapped out for both that are currently in the box, but nothing I've tried has gotten me anywhere. So if it's a RAM issue is Linux/Ubuntu able to handle sketchy RAM chips better than XP, or is there any other ideas as to how Kubuntu can be up and running just fine yet XP just chokes? I've never seen such a back-assward situation, usually if the hardware works, it works, and if it doesn't, it doesn't, not it works under some conditions yet not under others. I'm about ready to burn this stoopid thing, any thoughts???????????

---

### Post by LaRoza on 2008-01-25
RAM is funny. It rarely dies completely. 

This situation is complex, there are many things that can be the issue.

---

### Post by jabeez on 2008-01-25
True enough, but if RAM is not the issue, which after swapping sticks with the same results I can only assume it is not, WTF else is there? XP has installed on this very setup at least 3 times, yet now is choking? Winblows "knowledge base" for the error I usually get is that some hardware isn't compatible, but I've eliminated that possibility, so what else????

---

