---
title: "Accessing a printer shared on OSX"
date: 2006-10-09
forum: General Help
---

### Post by bsander on 2006-10-09
I'm trying to get my Kubuntu laptop connected to a HP PSC 1200 USB printer shared on an iMac on the network. So far I'm unsuccessful. I know Its authenticated and I have to provide username/password of the mac account, there's no way to disable that as far as I could tell.
Trying it as a SMB shared printer doesn't work (no errors on the machine, just no printing), Trying Network printer w/IPP also doesn't detect the printer, and only when using a remote cups server the printer gets detected fine.
Then when I try to print a test page, sometimes the printer shows some activity (components moving), but even that isn't reliable. It still doesn't print though.
I tried using the hpijs drivers and the generic postscript driver (which I couldn't seem to access through the wizard but I just manually selected the ppd file), both with no succes.
I read something that on windows people have the same problem and they need apple's Bonjour to set up the printer correctly. Maybe does that correspond to something on Linux?
Thanks for any help and/or clues..

---

### Post by lawina on 2006-10-10
Did u try using the UNIX network printer option besides the SMB and CUPS?

---

