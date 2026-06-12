---
title: "Gutsy boots to command line after a possibly bad shutdown."
date: 2008-03-05
forum: General Help
---

### Post by WoShiWes on 2008-03-05
I am having a problem getting Ubuntu Gutsy to start up properly. 
 
**Overview:** I have had no problems on a new computer for the past 2 months until about a week ago when I left the computer on overnight. The next morning the monitor was not receiving a signal so I moved the mouse to get everything going again but nothing happened. The computer power light was still on so I figured it may have gone into standby or something and pressed the power button. It ended up making it shut down. At the time it was unremarkable so I don't remember if it gave any odd warnings or if it even shut down properly. The next time I turned it on the gui wouldn't load. It got to the logon screen but it flickered off immediately and the round thingy was there forever. 
 
**Since this happened I restarted and have received some hanging up and doing nothing as well as errors that seem random:** 
 
1. "kinit: No resume image, doing normal boot..." 
2. "fsck died with exit status 8" 
3. "Display server has been shutdown 6 times in 90 seconds..." when the gui attempts to start. 
4. "The greeter app keeps crashing..." or something like that. 
5. "Invalid MIT-MAGIC-COOKIE-1..."
6. "sed: error while loading shared libraries: unexpected PLT reloc type 0x17"
7. MANY segmentation faults.
 
 
**My computer specs:** 
Intel Core 2 Duo 2.66 
Intel GMA 3100 for graphics 
2GB RAM 
SAMSUNG 20X DVD±R DVD Burner SATA 
Western Digital 320GB 7200 RPM SATA 
 
 
**There are some other little tidbits that might be helpful:** 
 
- Windows XP is on the same disk (WD SATA 320GB) and is also having issues. OK, I know...but a lot more than usual. This made me think it could be an overheating problem but I checked all the fans and temps and they are all good. 
  
- I installed a program in XP to read EXT3 and my main Linux drive seems fine...everything is there. But the swap partition gives a dialogue box saying that it is unformatted. I assume I can reformat it without too much of a problem since it's a swap BUT I fear Windows touching anything to do with Linux. 
 
- If I try to manually start gnome (sudo gdm) it will briefly show my usual logon screen but then goes blank and after a few seconds the monitor starts cycling between digital and analog inputs as if it is searching for a signal. 

- In Xorg.0.log there are a few warnings: VESA(0): Bad v_bios checksum & VESA(0): Failed to get set up write-combining range. 
 
 
**Miscellaneous pathetic attempts to resolve this issue:** 
 
- I have unmounted and remounted the swap drive 
 
- Attempted to apt-get update but I think it couldn't get a network connection. 
 
- I tried the live CD to try to see if it could fix things but it asks for a password (and it's not 'Ubuntu' or my normal username and password). 

- Tried to reconfigure xorg.conf but it didn't change anything. 
 
 
Any help would be greatly appreciated. I miss my new computer with Ubuntu :-( By the way, I have done fdisk and looked at my fstab and xorg.conf (etc.) but i don't know how to copy them to a file or print them so i can show them here. 
 
 
Thanks, Wes.

---

### Post by pointone on 2008-03-05
Boot with the live CD and run a filesystem check on your root partition with "fsck /dev/sda1" or whatever your root partition might be. Make sure it isn't mounted when attempting to run fsck or it could result in data loss.

---

### Post by WoShiWes on 2008-03-06
Hi,

Thank you for your suggestion. But my live CD was wanting me to login. HOWEVER, I noticed for the first time that there was a memory test on the CD menu and I figured I might as well do that since I have done everything else. And, HAPPY DAY!!! One of my memory chips was bad so I removed it and it all works great now.

Wes.

---

