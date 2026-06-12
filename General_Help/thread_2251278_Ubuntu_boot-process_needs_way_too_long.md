---
title: "Ubuntu boot-process needs way too long"
date: 2014-11-03
forum: General Help
---

### Post by yooooy on 2014-11-03
Hello!
 

 I have a strange problem with the boot-process in Ubuntu Studio. I installed it on an older system (Asrock G31M-GS with P4). Here is what happens: When I turn on the computer everything is OK at first. You can see the typical BIOS-screen with the typical BIOS-informations. Then the screen gets black and nothing is happening for about a minute. The hard drive is not working at all during this time. And then suddenly after this delay Ubuntu starts to boot like nothing happened and works just fine.  

 

 The thing is that I have the same strange boot-behavior when booting from Ubuntu-Live-CD. I have the same delay before the CD-drive starts to work. Even stranger, the same applies to Mint-Linux Live-CD.  

 

 Has anyone a clue what could cause this delay? Seems to be like some kind of a weird hardware problem, am I right?  
 

 Cheers,

 

 Robert.

---

### Post by oldfred on 2014-11-03
The BIOS time you cannot directly control. New UEFI systems do have a setting to not check for new hardware every time. Have seen users have BIOS enable floppy or other hardware, but not have one and system goes looking for it and has to time out.

Then grub loads. I think now grub checks all partitions looking for systems. Not sure why as os-prober should be the only time it scans system. I do turn off os-prober so kernel updates are a bit quicker and manually add any extra install's boot stanza to 40_custom. You can also change the default 10 sec that grub waits for a keypress to choose another system, but do not suggest changing to 0 as sometimes you cannot get back into grub when you need it.
If mounting NTFS partitions make sure you have recently run chkdsk. They always mount a bit slower, but I have had NTFS partitions boot but slow down Linux. After chkdsk they worked better in Windows & mounting Linux.

You can check dmesg log file to see if boot process is normal. Long times between entries, outright errors or repeated tries as loading a driver and either failure or later success are things to review. List is otherwise long and just standard loading of drivers.
You should have a log file viewer (system tools?) or just directly view/edit /var/log/dmesg.

---

### Post by yooooy on 2014-11-03
> **oldfred said:**
> The BIOS time you cannot directly control...
   Thanks for your response!


 The Mint-Linux-Live-CD has a compatibility-boot-mode. If you run it you can follow the boot process on the screen. The process halts at the point where I marked it with the red color (see the attached pic). Seems to be a problem with the sata driver/hardware.  The same happens even if you unplug the hard drive.
 

 But never mind.  I decided to go with another mainboard. I just want to set up a linux system for my uncle and have no more time to figure out what the problem with this mainboard is.
 

 But thank you for your effort again.
 

 Cheers!  

R.

---

### Post by yooooy on 2014-11-04
Hello!
 

 I had a look at the pic of the boot-screen again and I have recognized that it could not be a problem with the SATA connection but rather with the IDE connection. So I disabled  the DVD-drive and the problem disappeared!  

 I don't know whether it was a compatibility problem or the DVD-Drive was faulty but I've installed a new one and now everything is OK. For the sake of completeness, the model of the faulty/incompatible DVD-Drive was  TOSHIBA SAMSUNG SH-D162.  

 

 Cheers!

 

 Robert.

---

### Post by oldfred on 2014-11-04
Glad  you figured out issue. :)

Old IDE devices had to have correct cables & jumpers, like primary, slave, or cable select. So if you reconfigured system that could have been an issue.

When I built my new system in 2006, they had been discussing the new SATA replacement for PATA.  And I really hated those tiny jumpers. (old eyes & fat fingers do not help). By the time I finally built system SATA drives were only $10 more than PATA so I decided to go with SATA hard drives. But the only SATA DVD was a Sony and it was twice or about $200 back then. But while walking by shelves looking for a PATA DVD they started putting on shelf a new Samsung SATA DVD that again was only about $10 more than the PATA drives. So I have only bought SATA drives since.

---

### Post by yooooy on 2014-11-04
> **oldfred said:**
> Glad  you figured out issue. :)

....

   Yes, I'm glad too. Don't need to buy another mainboard. I thought it was the jumper or cable at first too, but it turned out it wasn't. I had to install a spare drive. The system is ready. Now my uncle can watch porn and don't care about viruses  lol :D:D:D

 

 Take care!

---

