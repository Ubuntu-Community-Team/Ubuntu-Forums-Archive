---
title: "Ubuntu and PXE Server Boot?"
date: 2015-10-22
forum: General Help
---

### Post by R3MMY88 on 2015-10-22
Hello!

My laptop has had its day with windows 7 as it is getting really slow. I want to convert to Ubuntu because there are versions that are not as taxing on the system. I do face a problem though. I tried to install Ubuntu in the past but my laptop keeps booting into the PXE server and try to connect, this is what I'm stuck on. I looked up guides online, to see how to sort this out, but they all call for going into the bios setup and disabling the PXE boot command. I can't do this because there is no setting for it. I looked over the setup thoroughly and turned up empty, so I have no way of turning it off. It would be simpler to disable it from the command prompt inside windows itself but it seems that's not the case. Any help would be appreciated!

Sorry in advance if this post is in the wrong place.

Thanks for reading!

---

### Post by doctorbighands on 2015-10-22
This almost has to be a BIOS setting. Search thoroughly through your BIOS and be sure there's nothing selected regarding PXE, network boot, etc. Check the system menu(s), the boot priority...everything.

There should be a key you can hammer on at boot time to allow you to select a boot device (usually F2, F12, or DEL). Are you able to get around PXE that way, on a per-use basis? If so, that's another clue that you have a BIOS setting in the way.

What is the make/model of your laptop?

---

