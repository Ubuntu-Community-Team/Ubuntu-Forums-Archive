---
title: "HELP! I screwed up my boot-loader"
date: 2018-08-27
forum: General Help
---

### Post by galacticstone on 2018-08-27
Hi Folks,

I messed up. I was trying to change the image on my login screen (which I had done previously without a problem). I copied the image file to the proper directory (/usr/share/backgrounds) and then I edited the gdm.css (or something like that) file. Well, apparently, I didn't copy-paste something correctly and now my PC will not boot. The boot process stops at the point where the login screen would load - it gets caught in some kind of loop and just sits there. 

I can still access the BIOS and I can hit Esc during boot and get the Ubuntu rescue menu. Is there a way I can restore this corrupted file to default and save my data? The good news is, I backed up my data. The bad news is, my backup failed. So, if I cannot somehow get this PC to successfully boot, I will lose a lot of personal and business data.

Any help would be greatly appreciated.

MikeG

---

### Post by oldfred on 2018-08-27
You should be able to boot with your Ubuntu live installer and mount install or do a full chroot into install.

Or can you boot second line or recovery mode and get to terminal command line. That does not automatically start gui, so you can manually edit files. I use nano which is installed by default and is command line only, but old school arrow keys and control keys use is required.

---

### Post by galacticstone on 2018-08-27
Update :

I got in through the grub menu and edited the boot options to include a single boot to root. Once I had root, I reinstalled the gnome shell and rebooted. Works fine now and back to default.

I won't go tinkering willy nilly with critical config files again.  LOL.

---

