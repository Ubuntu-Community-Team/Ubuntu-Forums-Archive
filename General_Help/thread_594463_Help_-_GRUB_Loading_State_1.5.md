---
title: "Help - GRUB Loading State 1.5"
date: 2007-10-28
forum: General Help
---

### Post by benson_cosprings on 2007-10-28
I need help.  I have been running Ubuntu for some time now.  However, today, I installed Kubuntu on a separate system which is running Windows 2000.  I changed the BIOS so the installation was saved to an external hard drive.  So, I never really touched the hard drive running Win2K.  When I was finished installing Kubuntu, I changed the BIOS back to boot from IDE-0 (which is the setting it was set to originally).  However, now when I try to boot this computer up in Windows (it is my wife's work computer...ugggh) it goes through its normal boot and POST process and when it gets to the section where it searches for boot devices, it says "Searching for Boot Record from IDE-0..OK."  Then, it suddenly stops and says "GRUB Loading state 1.5."  Then, it says "GRUB loading, please wait..."  Then it returns the following error "Error21."  How do I get this to stop so I can still boot the box in Win2K.  (I hate Windows).  

Any help or direction towards someone or something that might help is very, very, much appreciated.  Needless to say, my wife is not happy with me.  

Thx.  Tom Benson

---

### Post by Six_Digits on 2007-10-28
Ugghh, I take it you're completely stuck? Sounds kinda bad unless you have a boot disk of some sort - you don't, huh? Can you get to any console? Try this [thread.]("http://ubuntuforums.org/showthread.php?t=593794")

---

### Post by aidanr on 2007-10-28
Get your windows cd, boot up into the [recovery console]("http://support.microsoft.com/kb/229716") and type:
fixboot
fixmbr

---

### Post by benson_cosprings on 2007-11-04
Well, you both were right.  I checked with a more technically savvy friend at work and he told me that GRUB is the boot file that Linux uses.  Apparently, when I tried to install Kubuntu (even though I was trying to install in a separate drive) the boot file GRUB still gets written to the boot drive -- in this case C:\ and, thus, I overwrote my Windows boot file.  You were right -- fitxboot and fixmbr did the trick.  Thanks for the help!

Tom

---

