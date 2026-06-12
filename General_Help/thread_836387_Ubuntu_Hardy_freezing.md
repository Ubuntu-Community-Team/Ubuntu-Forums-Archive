---
title: "Ubuntu Hardy freezing"
date: 2008-06-21
forum: General Help
---

### Post by jamesdcarroll on 2008-06-21
I'm trying to migrate from Windows to Ubuntu. Here's what I've done so far:
1. I have 2 physical hard drives, so I copied everything to the c: drive from the D:
2. Formatted D:
3. Installed Ubuntu to D:

At that point everything looked good. I could boot into either: Windows runs as it always did, but the Ubuntu side is freezing up for some reason. By freezing, I mean that everything in the system becomes unresponsive, EXCEPT the mouse. Which I thought was interesting; when a system drops usually the mouse freezes too, but not in these cases.

The first time it did so it was right after the install during the update process. The second time I was setting up my gmail account in Evolution. The third, was when I was playing a video on you tube. There just doesn't seem to be a single cause that I can replicate. 

Here's what I have tried:
1. uninstalled/ reinstall Ubuntu (twice in fact)
2. Ran memtest; nothing came up
3. Looked system logs, but couldn't really decipher what it was they were saying. 

Any suggestions would be greatly appreciated and if there's any information you would like me to gather, just let me know.  Stuff that you may or may not find useful:

MOBO: Intel D865GBF; On board LAN;
Mem: 1.5G Corsair XMS
Vid: ATI Radeon 9700 All in Wonder (note: not using ATI drivers yet)
Snd: Creative Audigy 2 (running ALSA; no creative drivers yet)
KBM: MS Natural
C: Western Digital WD2500JB (250 gig)
D: Western Digital WD3200AAJB (320 gig)




Thank you very much.

James

---

### Post by cmnorton on 2008-06-21
Are there any errors in the output of dmesg, tail /var/log/messages, tail /var/log/syslog, or tail /var/log kern.log? I'm not sure I'll know what they mean either. You'd extract these on the next reboot. Also, I'd boot into recovery mode to try to get this stuff, so you don't hang again.

---

### Post by Gatemaze on 2008-06-21
Freezes in hardy are common for a lot of users... there is an update coming early july that should resolve them... i would suggest to either wait till then or try 7.10 gutsy

---

### Post by JBull on 2008-06-21
> **Gatemaze said:**
> Freezes in hardy are common for a lot of users... there is an update coming early july that should resolve them... i would suggest to either wait till then or try 7.10 gutsy

Ironic that is an issue that Linux users criticize Windows for (locking up or freezing).  I've never had that problem in several years using XP.  I have had that problem using various versions of Ubuntu and Debian.  Can't remember ever having that problem with Fedora but i only used it for a couple weeks before switching to Debian.

I'm having a similar problem with a new Ubuntu-Server install but I think my issue is ACPI.

---

### Post by jamesdcarroll on 2008-06-21
Thanks, I'll guess I'll wait.  At least I know my system is set up and ready. If I do decide give Gutsy a try, is the upgrade path "clean"? That is, would I basically have to start from scratch or would Hardy just pick up where Gutsy left off?  And where can I download Gutsy from?  The only thing that I can find is Hardy on the site.

Thanks again.

---

### Post by MaindotC on 2008-07-05
Gatemaze do you have a link that documents this supposed early July fix?  I'm using Hardy and Evolution has crashed after unspecified periods of use - usually no later than a minute of being open.  I've been downloading all those updates and when I see the ones that say evolution-common or just evolution I pray that's going to resolve the issue but nothing yet :(

---

