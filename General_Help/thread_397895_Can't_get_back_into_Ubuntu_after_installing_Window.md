---
title: "Can't get back into Ubuntu after installing Windows partition"
date: 2007-03-31
forum: General Help
---

### Post by Digital Spaghetti on 2007-03-31
Hey folks,

I play WoW, but just could not get it to run under WINE or under a VM image of Windows, so I decided to put a small partition on my drive soley to play WoW.

However, Windows has taken over at boot time, and will not give me the option to dual boot.  What is the best way to fix this without having to fully re-install Ubuntu again?  I've tried to go into Computer Managment, and mark partition as active, but it won't let me do it for either the main partition or swap partition/

Thanks

---

### Post by 67GTA on 2007-03-31
From the ubuntu terminal
Code:

sudo grub

You will get a grub> prompt. Enter
Code:

find /boot/grub/stage1

You should see two locations for the stage1 grub. ie. (hd0,0) and (hd0,1)

One will be your ubuntu grub and one will be your kubuntu grub. As long as you know which is which (Let's assume (hd0,0) for this example), just enter at the grub prompt
Code:

root (hd0,0)

You would of course enter the location for your specific stage1 location

then write the instructions to the MBR
Code:

setup (hd0)

type "quit" to exit grub and your rig should now be using your ubuntu grub loader.

---

