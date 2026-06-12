---
title: "Scanner problems after upgrade to 22.04"
date: 2022-08-27
forum: General Help
---

### Post by illiterate on 2022-08-27
Hi all,

I'm not the OP but have the same problem.

I'm on an HP elitebook 820g1 laptop and using a HP Deskjet 2720e wireless printer/scanner. Printing works fine. I can scan documents using simple scan (i.e. the scanned pages appear in simple scan prior to saving them) but cannot save the scanned files.

I tried to attached a screenshot of the problem but it's my first time using this forum so I might miss something.

When I click the save button in simple scan's GUI it brings me to Nautilus to save the file. But it immediately shows an error message stating "The folder contents could not be displayed. Operation not supported". I can click "ok" in the error message pop-up, but the "save" button doesn't work afterwards.

I'll try to answer TheFu's questions.

a) Did you look at the system logs?

No

b) Which OS, exactly is being used?

Ubuntu 22.04.1. Upgraded from 20.04.3 about a week ago. Until now everything worked fine). Kernel: Linux 5.15.0-46-generic

c) Which DE, exactly, is being used?

Gnome (vanilla/Canonical) on wayland.

d) Which program (look in the process tablet) is being used?  The name  in the "menu" is less helpful. The actual executable program-file is  best.  How was it installed?  From Canonical repos? From a .deb package  download?  From a snap?  From a flatpak? Following manual install  instructions?  Is it an appimage?

simple-scan (Document Scanner in the menu). Installed from Canonical repos.

e) Which version of the program, if it isn't the current one?

42.0-1 (checked in Synaptic Package Manager). It's the latest version available.

f) Did you run sudo apt update && sudo apt full-upgrade already to ensure everything is fully patched on the system?

Yes.

g) If there is a peripheral involved, exactly, what is the vendor, model, and revision level of the hardware?

HP Deskjet 2720e wireless printer/scanner

h) If there is a peripheral involved, exactly, what is the driver version being used?

Unknown. Just using what comes out of the box in Ubuntu's installation/upgrade. hplip is installed. Software & Updates indicates no proprietary drivers available.

i) Did it ever work?  When it did, what were the conditions, OS,  drivers, DE, and program that did work?  What's different this time?

Printing and scanning worked perfectly in Ubuntu 20.04 using the same programs (although I suppose different versions of them). The only change I'm aware of is the upgrade to 22.04.1. This was the first time I had to use the scanner since the upgrade to 22.04.1.

I'm trying to save the file to whatever location is automatically selected by the OS, which is what I always did when running 20.04, and it always worked.

Any help would be greatly appreciated.

Best regards.

---

### Post by illiterate on 2022-08-27
Hi again,

Just to add that everything still works in ubuntu gnome/vanilla 20.04.3. I still had a bootable usb pendrive with that version and I used it to scan the required document (and save the file). In 20.04.3, simple-scan's version is 3.36.3.

While this isn't a solution for others with the same problem, it might be a temporary workaround until this gets sorted in 22.04.1.

Best regards.

---

### Post by ajgreeny on 2022-08-27
Posts moved from [https://ubuntuforums.org/showthread.php?t=2478435&p=14109843#post14109843](https://ubuntuforums.org/showthread.php?t=2478435&p=14109843#post14109843) to a new thread.

@ illiterate.
Please do not hijack other posts as however similar, there will always be differences and confusion may reign if both are left in the one thread.

---

### Post by TheFu on 2022-08-27
> **illiterate said:**
> HP Deskjet 2720e wireless printer/scanner

Appears that HP created a new driver for 22.04. Try loading that. Think I linked to the source in the other thread.

---

### Post by illiterate on 2022-08-28
Hi


Sorry for hijacking the other thread, @ajgreeny. I didn't want to duplicate things since the problem seems to be the same. Thanks for creating the new thread.


Thanks for the help, @TheFu. I was going to install the driver, but I decided to try another scanner program first. I installed skanlite 21.12.3-0ubuntu1 from synaptic package manager and my scanner is working again. I can scan documents and save the file afterwards.

 
 
 
I don&#8217;t understand much about computers, but I think this means that the problem isn&#8217;t the driver but something with version 42.0-1 of simple-scan, right?

 
 
 
Although I prefer the GUI for simple-scan over the one for skanlite I&#8217;ll just use the latter for now.


 
 
 @ajgreeny, I&#8217;m unsure if I should post this workaround on the other thread to help the OP there. I&#8217;ll leave it up to you.

 
 
 
Best regards.

---

### Post by ajgreeny on 2022-08-28
Yes, by all means post on that original thread as it may help the original poster.

---

### Post by illiterate on 2022-08-30
Hi all

Ok, so I finally managed to save the scanned file using simplescan. What I did was this: 1) simply press "ok" on the first error message (attached screenshot in the first message); 2) select another location to save from nautilus left menu (this highlights the "save" button again, allowing it to be pressed); 3) save.

 A different error message pops-up now (see attached screenshot) stating that the file could not be saved, but it's saved in the chosen location (tried saving to /Documents and to /Downloads and both worked).

Best regards.

---

### Post by TheFu on 2022-08-30
I think you are confusing /Documents and to /Downloads with   ~/Documents and to ~/Downloads 

Good that you found a work-around, but did you ever get and install the new software from HP?

Also, if this is "SOLVED", please use the Thread Tools button to mark it that way to help other people find that fact without having to read the entire thread.

---

### Post by illiterate on 2022-08-30
Hi @TheFu

You're right. I meant ~/Documents and ~/Downloads.

I've been trying to find a way for this to work without installing a driver that isn't provided in Canonical repos since I prefer to wait and see if the new version of hplip comes through said repos. So, no, I didn't install the new driver. Thanks anyway.

I'm unsure if this is "SOLVED" according to forums guidelines. There are still pop-up errors when saving in simple-scan 42.0-1, although it does save. I leave it up to the moderators.

Best regards

---

