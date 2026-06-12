---
title: "Ext3 - Folder containing files turned into just a single file??"
date: 2008-06-11
forum: General Help
---

### Post by futaihikage on 2008-06-11
There was a folder named "Sekei" that contained about 6 files about 75megs apiece, for some reason I just have a FILE now called "Sekei" and its size is 400megs?  

I didn't have any crashes or sudden reboots, the files themselves were about a month old.  I tested the drive with SpinRite and it didn't find any errors.  Is it possible to change the "bit" that tells Linux that "Sekei" is NOT a file, but a folder?  Or any other help would be appreciated.

---

### Post by Ramses de Norre on 2008-06-11
What does the "file" command say about that file?

---

### Post by futaihikage on 2008-06-11
I figured it out, it was the IDE channel on this motherboard.  It's corrupting data thats being sent to the drive.  I put a known good hard drive into the same system and the same problem occured.  So I need a new motherboard if I can't get a PCI IDE card to work.

Thanks.

---

