---
title: "Dual booting - What am I doing wrong?"
date: 2005-10-23
forum: General Help
---

### Post by Dolphin on 2005-10-23
I keep hearing how incredibly easy it is to set up a dual boot with Ubuntu, I'm just not seeing it though.

I had Hoary for a few months as my only desktop OS, now that I've learned to use it well enough, I'm going to go back to using windows for a few tasks. So I'm trying to set up a windows/breezy dual boot like so (on my 200gb HD):

-Make 1 80GB partition
-Install Windows on partition
-Boot Ubuntu installer and when it gets to partitioner I select "Use largest continous free space"
-Near end of installation it pops up with a message saying it detects my windows installation and should it go ahead and install GRUB on my MBR to use for both OS's.  I select yes.
-After reboot, I get nothing but a cursor on my screen.

This is on my SATA 200GB.  I also have a 40GB IDE drive for backup purposes.  I'm not using it for either OS, I'm just mentioning it in case it's somehow causing my problem.

Can anyone point me in the right direction?  Thanks.

---

### Post by Ocxic on 2005-10-23
[QUOTE=Dolphin]I keep hearing how incredibly easy it is to set up a dual boot with Ubuntu, I'm just not seeing it though.

I had Hoary for a few months as my only desktop OS, now that I've learned to use it well enough, I'm going to go back to using windows for a few tasks. So I'm trying to set up a windows/breezy dual boot like so (on my 200gb HD):

-Make 1 80GB partition
-Install Windows on partition
-Boot Ubuntu installer and when it gets to partitioner I select "Use largest continous free space"
-Near end of installation it pops up with a message saying it detects my windows installation and should it go ahead and install GRUB on my MBR to use for both OS's.  I select yes.
-After reboot, I get nothing but a cursor on my screen.

This is on my SATA 200GB.  I also have a 40GB IDE drive for backup purposes.  I'm not using it for either OS, I'm just mentioning it in case it's somehow causing my problem.

Can anyone point me in the right direction?  Thanks.[/QUOTE]


check to make sure that the drive ubuntu installed grub to the MBR is the primary boot device in your BIOS settings, I had the same problem and it took me day's of tinkering to figure it out.

---

### Post by Dolphin on 2005-10-23
It is the primary boot device in my bios

---

### Post by Dolphin on 2005-10-23
Problem figured out.  Even though my SATA drive was primary in bios, my IDE drive was still tripping up the Ubuntu installer.  I unplugged the IDE drive for the duration of the install and it worked fine.

Note to any devs if they read the forums: this problem SUCKED! :)

---

### Post by hesee on 2005-10-23
[QUOTE=Dolphin]
This is on my SATA 200GB.  I also have a 40GB IDE drive for backup purposes.  I'm not using it for either OS, I'm just mentioning it in case it's somehow causing my problem.
[/QUOTE]

Could you remove that 40GB IDEdrive when installing ubuntu, and add it later? (Don't know, maybe there's better ways to solve this...)

Edit: i see you already fixed the problem, nice :)

---

### Post by Dolphin on 2005-10-23
[QUOTE=hesee]Could you remove that 40GB IDEdrive when installing ubuntu, and add it later? (Don't know, maybe there's better ways to solve this...)

Edit: i see you already fixed the problem, nice :)[/QUOTE]

Mere seconds too late.  Thanks though :)

---

### Post by Pigmudgeon on 2005-10-24
I had the same problem under Ubuntu 5.04 - GRUB just wouldn't work, or it would hose my MBR, and replacing an MBR under Windows is a white-knuckle process. So I was running Ubuntu by botting from floppy and then manually passing the boot commands (VM, RD, and Kernel). 

Under 5.10, the process worked perfectly, and I get the GRUB menu at boot-up, which allows me to choose Ubuntu 5.10 or Win2k. 

Now if I could only keep those cute animal names sorted out in my slowly collapsing mind ... 

--p!

---

