---
title: "Cannot Boot to Ubuntu Anymore (Only Windows)"
date: 2008-06-07
forum: General Help
---

### Post by recasper on 2008-06-07
Hello All, this place has answered and helped me greatly and was curious if I could get a bit of assistance on this recent issue I have ran into.

A friend recently wanted to install a game to my computer and it of course Wine wont handle all games, this being one of them (SIMS, Deluxe). 
However I figured I'd install it onto mt Windows partition. But I had forgotten to enter my program authorization for windows before the time ran out after my last complete harddrive wipe, and never thought about it till now when I actually needed it. Well last night I attempted to install Windows back onto the computer and then authorize it. Sadly the Windows install buzzed through without optioning me anything so now I have windows on a 3GB partition with 8MB left, and it will not give me the option to Boot to Ubuntu anymore. So I am stuck with a Windows computer and 3GB harddrive partition. (No other partition is available for viewing or access)... I don't even have the option to Boot anything, goes straight to windows.

I hope that this made sense and one of you great people out there could lend some advice I would greatly appreciate it. 

Thank you so much in advance.

---

### Post by housam on 2008-06-07
- [[COLOR="Red"]_Reinstall grub_[/COLOR]]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub") to boot ubuntu.
- resize ubuntu using Gparted from ubuntu live cd to give windows some space.

---

### Post by TeoBigusGeekus on 2008-06-07
From what I can make out, it seems that you've lost grub, the Ubuntu bootloader.
[How to recover grub]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by Victormd on 2008-06-07
get supergrub cd to reinstall your grub (don't worry, you will not loose your windows install) and use gparted live CD to resize your partitions...

---

### Post by recasper on 2008-06-07
You cats are awesome... Im about to start the above processes... Will update my progress soon.

---

