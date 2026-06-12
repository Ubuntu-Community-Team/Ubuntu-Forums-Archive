---
title: "Cant boot from CD anymore"
date: 2008-02-27
forum: General Help
---

### Post by welder_tim on 2008-02-27
I've got Ubuntu 7.10 on a dell insprion b120 laptop, I've also had it installed on an old PC sitting in a back room. Live CD's always booted up just fine and installed as I tried different Distros. One day, I decided to expand my little knowledge and try out Ubuntu Server Edition 7.10 on the old PC. Went though the prompts easly and completed the install, followed by reboot. Boots up (I guess) normal. I was using [http://www.howtoforge.com/perfect_server_ubuntu7.10](http://www.howtoforge.com/perfect_server_ubuntu7.10) as a guide. Well, I'm having trouble installing new packages (using apt-get), won't update or upgrade, ect... I have no idea where to go now. So I decided to wait until later down the road to try server again (more experience) and go back to regular Ubuntu. Problem is. Now my computer wont boot from CD anymore. no matter what cd i put in there. Windows, Kubuntu, SAM OS, GoblinX. everything still starts up just fine though, 'cept that. It says 

Verifying DMI Pool Data ........
Boot from ATAPI CD-ROM : Failure ...
DISK BOOT FAILURE, INSERT SYSTEM DISK AND PRESS ENTER

Like I said, it would always boot up from any Live CD at this point no problem. Now it wont. Yes the BIOS is set up correctly. Yes the computer recongizes the CD-ROM Drive (both of them). Yes the CD is inserted (same one used to install Ubuntu before.) So any idea where I go from here? What info is needed?

Insert cliché "I'm a newbie, take it easy on me please" line here.

---

### Post by dcstar on 2008-02-27
> **welder_tim said:**
> ........
Like I said, it would always boot up from any Live CD at this point no problem. Now it wont. Yes the BIOS is set up correctly. Yes the computer recongizes the CD-ROM Drive (both of them). Yes the CD is inserted (same one used to install Ubuntu before.) So any idea where I go from here? What info is needed?

Insert cliché "I'm a newbie, take it easy on me please" line here.

Hardware fails, replace the CD drive and see what happens.

---

### Post by welder_tim on 2008-02-27
sorry, i forgot to mention. I did try a different CD drive. No dice.

---

### Post by satn3ver on 2008-02-28
i am having the same issue. I have managed to fubar my 7.04 install (some mismatch of the new nvidia driver and the x window module) and decided to download 7.10 and burn a new install cd. 

My vesa running fubared 7.04 recognizes the cd rom, burned the new disk and i can explore the 7.10 install disk. 

I go to boot from the cd rom and get the "insert boot disk..." error the OP has. I then rebooted several times, trying my old install disks, install dvd's, etc etc. No dice. My system refuses to see the cdrom install disk when asked, but can read, access, and burn cd's and dvd's from the current install.

My system is a custom build from a few years ago:

epox sli 939 motherboard running a opteron 170 proc
2 gigs ddr500 gskill ddr 
lite-on cd-rw/dvd-rw
western digital sata 36g 10k rpm
western digital sata 250g 7200 rpm
ocz 500w sli power supply
Nvidia gforce 7800gt 256
soundblaster audigy(1)  mp3+ 
random usb 11 in 1 card reader


Any ideas? The drive works....when booted into my now current messed up 7.04 system. It does play and read and burn fine.

Is there a way to wipe the bios cache or something or is that not the issue?

---

### Post by welder_tim on 2008-02-29
Actually, I got mine working last night. Perhaps its a mix of hardware failure and plain bad luck. The CD drive in question for me still works, just wont boot. I dug out an old drive and put it in. still did not work. then I realized that the jumper was set to slave and not master (same as 2 disk tray in computer), little switch and now its working. Try a new cd drive, and make sure that it is set as master, (and if there is a second, master and slave) It worked for me, hopefully it will work for you. Oh, you might also try a 6-pack as it was part of my process too.

---

