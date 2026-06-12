---
title: "Blank screen w/ cursor on boot"
date: 2005-08-02
forum: General Help
---

### Post by HeWhoWalks on 2005-08-02
When booting from the live CD, I get the following:

Standard status reports ending with:

* Setting up ALSA...
* Starting GNOME Display Manger...
* Starting Common Unix Printing System: cupsd
* Loading ACPI modules...

The screen then goes blank, with a cursor in the top left corner.  The CD access indicator continues to flicker for a while, but eventually goes dark.

CTRL-Shift-F2 gives me a screen with the above status messages, followed by:

* Starting Advanced Configuratieon and Power Interface daemon...
* Starting system message bus:
* Starting Hardware abstraction layer:
* Starting internet superserver...
* PCMCIA not present
* Starting powernowd...
* CPU frequency scaling not supported
* Starting deferred execution scheduler...
* Starting periodic command scheduler...
* Checking battery state...
Linux ubuntu 2.6.10-5-amd64-generic #1 Tue Apr 5 12:21:57 UTC 2005 x86_64 GNU/Linux


Anyone have any idea why I'm just getting the cursor instead of a desktop?

Here's the hardware I'm trying to run this on:

CPU: AMD Athlon64 3200
MBD: MSI K8N Neo4 Platinum SLI
RAM: Infineon 2GB DC kit
Vid: 2x MSI NX6600GT 128-VTD (SLI)
Pioneer 16x DVDRW
HD: 160GB Seagate SATA

-Thanks in advance

---

### Post by Zelut on 2005-08-02
Maybe I'm misreading your Hardware list up here but are you using a 64bit system?  I know you would need the specific live-CD for the 640bit.  I tried it on a roommates 64bit box and got the same error.  I just chalked it up to using the x86 CD on a 64bit system.

If you are using the correct disk... I'm not sure what to tell you.  I have seen other posts in the forum noting some trouble with the 64bit.  You may want to do a search for those.

---

### Post by HeWhoWalks on 2005-08-02
Yes, I'm using the A64 version of the Live CD.  I've searched over the forums for others having the same type of problem for the last couple days, but haven't found anything that's helped.

I thought it might be a video driver issue, so I followed the "how to install NVidia drivers and restart Gnome" info in the FAQ... no change.

Anyone else have any hints?

---

### Post by HeWhoWalks on 2005-08-03
Nobody else has seen this?

---

### Post by ssam on 2005-10-05
try ctrl+alt+f1

you may be able to log in then, it is not a good sign that gdm has not started automatically.

---

### Post by luckyaba on 2005-10-09
You most likely have the wrong pci bus line.

its probably on 4.0.0 in your xorg.conf but it needs to be 5.0.0... for example 

look under lspci to fin the right one.

---

