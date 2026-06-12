---
title: "Help! (I just need somebody...)"
date: 2007-09-29
forum: General Help
---

### Post by oryxgazella on 2007-09-29
I think I´ve made a fatal mistake. I´m sure it´s reversible, but, as a newbie it´s beyond the scope of my skill to fix it. Here´s the story: Two months ago I bought a home-PC with Ubuntu Feisty installed. Soon enough my  employer wanted me to take a course based on a windows-compatible software (only). Bummer! Since I wanted to study as much as possible from home I decided to install winXP on my home-PC. First I tried out the possibilities to create a VM (with Ubuntu as host), but I didn´t manage to get it right. The second best alternative was to dual-boot, so that´s what I did (using this step-by-step guide [http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)). Initially everything worked fine but soon the OS went unstable. I decided to uninstall winxp and remove the partition (using the same step-by-step guide), in order to start all over again with a new partition and a new winXP install. Removing the partition was no problem, however, when I rebooted ubuntu wouldn´t start. 

Now BIOS starts but then nothing happens. I followed the instructions of the uninstall guide ([http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)) with only ONE exception, and I guess this is what made it all go wrong(?); instead of using the partition software (Gnome Partition Editor) in a Ubuntu LiveCD I used the one I burnt on a CD when first creating the winXP partition (Gnome Partition Editor 0.3.4-7.iso). What happens now is that I can still see the original Ubuntu partition on my PC using GPartEd, and I can start Ubuntu using a Ubuntu LiveCD. But I can´t start it from the hard drive. 

Please help me out and remember that my computer skill is rather rudimentary. Thus, I prefer step-by-step guidance.

/Oryxgazella

---

### Post by bronze on 2007-09-29
Can you boot into Windows XP now? My guess is that when you installed Windows XP, GRUB was overwritten. It's reversible, no problem, but I'll let someone more qualified than my give exact instructions.

Edit: It seems you were using the windows bootloader, and that when you deleted the winXP partition, the bootloader went with it. If this is the case, you should download and burn the GRUB cd, and use it to install GRUB.

---

### Post by louieb on 2007-09-29
Don't know why removing XP would trash your Ubuntu install unless you were using NTLDR. See if setting up Grub form the Live CD doesn't fix the problem. It happens often enough after adding XP that I have the how to in my signature. Under Reinstall Grub.
or  [IDBS GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm")

---

### Post by cmost on 2007-09-29
Installing Windows after Ubuntu often destroys the Grub bootloader.  Windows software acts as if it's the only OS in town and has no regard for alternative boot loaderrs, often overwriting the bootloaders for other versions of Windows.  Regardless, your best option would have been to setup Windows in a Virtual Machine (assuming you had enough RAM / Memory to allocate to the VM sufficient for a usable experience - no pun intended.)  If that went awry, it's very easy to fix the issue.  Now, you're apparently locked out of both OS's.  You may want to Google Grub and dual boot to see how others have solved the problem.  Alternately, you may end up having to reinstall both Ubuntu and Windows to get your computer back on track.

---

### Post by BrownCoal on 2007-09-29
It sounds like you have inadvertently erased your master boot record. Here's a quick recovery guide ([taken from here]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=recall&rev=26#head-09167948173503db5923da717a106f0c3aac1cd2")([this may also be helpful]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub"))):

1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.
2. Go to applications>accessories>terminal
3. Type "sudo grub" which makes a GRUB prompt appear.
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.
5. Type "root (hd0,3)".
6. Type "setup (hd0)"<<TO REPLACE MBR, or whatever your harddisk number is.
7. Quit grub by typing "quit".
8. Reboot.

---

### Post by oryxgazella on 2007-10-01
Thanx felllas,

for your immediate response to someone desperately in need of assistance. Feels safe to know that you guys are out there when newbies are messing up things. I have set up my GRUB again like you suggested, and I get into the MBR like before when booting. Hooray!

You´ve made my day shiny (although its raining) and that would bring you a lot of good Karma,

Oryxgazella

---

