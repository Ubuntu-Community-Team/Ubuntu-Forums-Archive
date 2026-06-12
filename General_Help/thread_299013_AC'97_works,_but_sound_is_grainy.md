---
title: "AC'97 works, but sound is grainy"
date: 2006-11-13
forum: General Help
---

### Post by J-Rod on 2006-11-13
I have an onboard VT8233/A/8235/8237 AC97 Audio Controller detected, and it is functioning. However I noticed that the sound quality is pretty bad, grainy is the best way I can describe it. In Windows, I would check for some updated chipset drivers, but in Ubuntu it doesn't seem like that's how it works, since everything is wrapped in the kernel. Can anyone point me to some troubleshooting I can try to see if I can't get some better quality audio?

---

### Post by ReaderRat on 2006-11-13
Comprehensive Sound Guide:  **[http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide](http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide)**
[**AC'97 ICH6 Audio**](http://ubuntuforums.org/showpost.php?p=1733758&postcount=3)

---

### Post by J-Rod on 2006-11-13
Exactly what I was looking for, it appears I didn't look hard enough. Thanks!

---

### Post by J-Rod on 2006-11-13
Wel this is interesting, I went to purge the ALSA drivers as per the tutorial, and I get this:

A faster way, is to just remove the problematic packages and reinstall them cleanly.

   1. Remove these packages sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
   2. Reinstall those same packages sudo apt-get install linux-sound-base alsa-base alsa-utils

> jrodder@jrodder-desktop:~$ sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils
Password:
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  alsa-base* alsa-utils* gdm* gnome-applets* gnome-control-center*
  gnome-panel* gnome-session* gnome-terminal* linux-sound-base* nautilus*
  ubuntu-base* ubuntu-desktop* ubuntu-minimal*
0 upgraded, 0 newly installed, 13 to remove and 1 not upgraded.
Need to get 0B of archives.
After unpacking 23.3MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.


The tutorial says a couple of extra packages might need to be reinstalled in addition to the ALSA stuff, but that's a bit much, no?

---

