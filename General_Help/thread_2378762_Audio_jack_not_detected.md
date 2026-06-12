---
title: "Audio jack not detected"
date: 2017-11-26
forum: General Help
---

### Post by totalolage on 2017-11-26
Greetings,
I am having and issue where my audio jack is not being seen as an output device (not just not outputting audio). the problem manifests like so: there is no difference whether headphones are plugged in or not, the system never offers them as a viable output device.
I've already tried all the suggested solutions, namely those involving pavucontrol, alsamixer, and even adding options onto some .cfg files; none of the have worked.
Any help to do with this will be greatly appreciated.

I am running:
Ubuntu 17.10
on an Acer Aspire E 15 E5-575G-54MM

if there is any more information I can provide that might help, please do not hesitate to ask

---

### Post by Kirk Schnable on 2017-12-04
It's possible that this is just wonky hardware that either doesn't have Linux drivers, or that the Linux drivers aren't looking for the device the way it's identifying itself...

Anecdotally I have worked on someone else's Acer laptop in the past (on Windows) where the webcam drivers provided by Acer didn't work and I never was able to find totally functional drivers, so to that end I'm no stranger to Acer using weird hardware with funky driver requirements.

If you could open up a terminal and run:  **lspci -vv**

This will provide some more information about the hardware and any drivers the system has loaded.  You can find the Audio Device section and paste just that, or paste the whole thing.

---

