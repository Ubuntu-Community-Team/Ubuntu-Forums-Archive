---
title: "How to install Ubuntu Studio 20.10 on a USB Stick permanently?"
date: 2020-10-24
forum: General Help
---

### Post by isza on 2020-10-24
Hi all,
after reading a few days ago about the release of Ubuntu Studio 20.10 I became interested. I downloaded this version onto a 64GB USB 3.0 Stick to try it out.
My other hardware is an Apple Mini (mid 2011) with a 500GB SSD where the OS and the important apps live, and a 500 GB internal HD where data is at home.
My intention is to run either Apple OS or Ubuntu Studio 20.10, but not both simultaneously. I want the 2 worlds separated.
When booting from the USB Stick, after a longish wait I get after 1 click the Ubuntu Studio desktop with a single icon. Clicking on this icon offers the installation of Ubuntu. However, this option only offers as possible locations either the 500GB SSD or the 500GB internal HD. I have no intention of altering these existing disks, let alone reformatting one of them. So, how do I install Ubuntu onto the USB Stick, from where I booted? I'd like any customisation I shall make to be saved and not vanish after a restart.
Can anybody offer a simple solution without command lines in the Terminal? Help appreciated!
Andy

---

### Post by tea for one on 2020-10-24
> **isza said:**
> So, how do I install Ubuntu onto the USB Stick, from where I booted? 

Unfortunately, you cannot install to the USB stick, from where you booted because it is already in use.
You will need another USB thumb drive.

Back up all your data - [COLOR="#0000FF"]essential[/COLOR]
Preferably disable, de-activate or remove your internal drives (to prevent installing to the wrong device)
Burn your ISO on a smaller USB device (say 8GB?)
Insert the small USB device and boot the [COLOR="#0000FF"]live[/COLOR] session
When ready, insert your 64Gb stick
Install to the 64GB destination

The installer will wipe anything on your 64GB destination disk during the process.

Please be cautious and read all the screens carefully (assuming that this is your first time installing an Ubuntu OS)

---

### Post by isza on 2020-10-25
Hi, thank you for resolving my problem. Your explanation is logical and simple. Thanks, I've done the installation and it works now.[IMG]https://ubuntuforums.org/images/icons/icon7.png[/IMG]

---

