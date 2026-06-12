---
title: "[SOLVED] system locks w/ hard disk constant activity"
date: 2007-09-09
forum: General Help
---

### Post by a_posse_ad_esse on 2007-09-09
I am running Ubuntu server (feisty-proposed) with mythtv, samba, nfs, and cups.  The system itself is a Tyan Tiger MP with 2x AMD MP 1500+ and 1 GB registered DDR.  

It is locking up several times a day, and does not record scheduled shows (mythbackend goes down apparently) and is unreachable over ssh, samba, and nfs. The LED on the front of the box showing hard disk activity is lighted constantly (no blinking at all) when this happens; a reboot solves the problem for a little while, but ultimately the problem repeats itself.

I looked at the machine's free RAM when it is transcoding episodes, the most intensive task the server is faced with currently, and the swap space isn't touched.  This rules out a memory leak I would believe.

Otherwise, the BIOS settings are pretty conservative, as I let it decide when to conserve power, and have not changed acpi's configuration at all.  Are there any known issues in this regard?  I was thinking that it could possibly be a misconfiguration of the power settings, but I am reluctant to turn off acpi support, as the system should not be running full blast at all times for sake of longevity and power consumption.  

Any suggestions would be appreciated.  Thanks

---

### Post by a_posse_ad_esse on 2007-09-11
Sorry, but this is a large enough problem for me that I have to bump this message.

---

### Post by K.Mandla on 2007-09-11
When you say you're using "Feisty-proposed" ... do you mean you've installed Gutsy?

---

### Post by a_posse_ad_esse on 2007-09-12
My mistake.  I had originally thought that feisty-proposed was the "beta" set of packages, while gutsy was the "alpha."  I checked, and gutsy is the installed version.

---

### Post by a_posse_ad_esse on 2007-09-14
Is this a known issue with gutsy?

---

### Post by a_posse_ad_esse on 2008-02-18
The issue stems from a lack of available RAM.

---

