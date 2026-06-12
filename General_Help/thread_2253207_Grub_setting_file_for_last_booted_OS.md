---
title: "Grub setting file for last booted OS"
date: 2014-11-18
forum: General Help
---

### Post by faglmt on 2014-11-18
Here is a tricky question.


First, let me say that i run a system with 3OS, WinXP, win8.1 and Ubuntu.
I use XP for smartphone repair tools, 'cos you know, everytime you get drivers issues in other os, except xp.
I use win 8.1 for game purposes and other stuff
and finally, i use Ubuntu for pretty much the rest.


Now, i set up GRUB2 to remember the last OS i booted on.


I want to build little script system that lets me choose what os boot on the next reboot. 
Example: 


"I'm on xp, i want to reboot directly to ubuntu without having to select ubuntu in grub window. I run a bat file that modifies the file in ext4 partition (assume that i can read/write that partition), and then rebooting i no longer autoreboot to win xp, but i reboot to ubuntu." 


I'm doing this because i also use SSH, and would be nice to have an option to switch between my OS remotely.




So for all the TL;DRers 
The question is:
Is there a file where the ubuntu information is stored?

---

### Post by oldfred on 2014-11-18
I do not think there is an easy way.

The file is grub.cfg. But Windows cannot read & write to it as it is in the Linux format. And in Linux you do not directly edit it, but have configuration files and use those to create a new grub.cfg. 
But if not in any install you can create & edit at will. 
I have manually installed grub to flash drives with FAT32, NTFS & Linux formatted partitions, so it does work.

But you could create a grub only partition which can be any format.
So create a small NTFS partition and install grub to it. It will not have a grub.cfg and you have to manually make one or three , one for each boot configuration. I might then write scripts to either modify file or copy version that is next boot as grub.cfg.

If a new UEFI system then it would be easy as it has a one time boot option. But XP is so old it does not know what UEFI is, and your hardware has to be UEFI based.

---

