---
title: "Laptop volume button alter's wrong sound level"
date: 2005-10-22
forum: General Help
---

### Post by DanielT on 2005-10-22
Hello,

I just upgraded to breezy and the multimedia buttons on the front of my laptop, the sound controling ones, alter the sound level brillently, just on the wrong device, it tries to alter the ALSA device but my ubuntu is configured to use OSS.

so how do i change what device ( and which sound level, master, PCM, etc.) it edit's?  


thanks!

---

### Post by kronepils on 2005-10-22
What kind of laptop?
I use an ibm thinkpad and my volume is controlled by tbp.
Read the tpb man and include the correct mixer on the commandline or change /etc/tpb.rc

If you don't have an ibm, check the /etc/acpi for vol[up/down]btn.sh.

---

### Post by DanielT on 2005-10-22
it's a dell 6000,

just been taking alook at this, and manged to switch over to alsa, but now the problem is that it edits the 'Master' not 'PCM' and PCM is the one that actully controls my volume, i am thinking this is a bug with ACME in gnome, and therefor is a more upstream bug than to be filed with ubuntu, im just going to have a play around with gnome first before i fill a bug report.

---

