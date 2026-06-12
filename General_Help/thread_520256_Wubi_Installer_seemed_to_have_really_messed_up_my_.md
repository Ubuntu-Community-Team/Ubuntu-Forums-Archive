---
title: "Wubi Installer seemed to have really messed up my system"
date: 2007-08-08
forum: General Help
---

### Post by oneleaftea on 2007-08-08
Hello,

I just tried to install Ubuntu using Wubi. It finished downloading and rebooted. It then went to the dual-boot menu, and I chose Ubuntu.

From there it installed and then hung during the installation. It was stuck for a long time (about an hour). So I hit the rest button.

Now, the computer does not recognize the hard drive. I go into the BIOS, and it doesn't even see the hard drive there.

I use the Windows XP disk to try to go into recovery mode and it says it cannot find a hard drive.

This is an AMD system using a SATA drive. I am not sure what the problem is, but right now, it seems like it killed my hard drive. I also unfortunately did not do as full a backup as I wished, because I had the impression that the Wubi installer was extremely safe (safer than doing a regular install). 

I am really not sure what to do right now, and would appreciate any advice. Thank you very much

---

### Post by tuxcantfly on 2007-08-08
Wubi really shouldn't have done anything to your BIOS, are you sure it can't be anything else? All cords connected? Maybe try letting the thing power down, unplug it to reset the current, then try booting it again?

In the worst-case scenario, you might be able to just re-flash your BIOS

---

### Post by oneleaftea on 2007-08-08
Whew! Oh man, i finally fixed it.

Yea, everything was plugged in just fine. The Wubi install corrupted my C drive and it was not recognizing the drive. It took me awhile to get recovery mode working with the XP CD, and I checked the C drive. The C drive's directory structure was completely corrupted. But a chkdsk fixed it, and I was able to log into Windows. I'm going to do a regular install on a fresh partition next time.

---

