---
title: "[SOLVED] Can't open remote files in the GIMP"
date: 2007-10-29
forum: General Help
---

### Post by jordon on 2007-10-29
I'm using the GIMP 2.4.0-rc3 on Gutsy. When I try to load a remote file from the "Open Location" dialog, I get two error messages at once, typically of the form:

JPEG image Message
Could not open 'http://www.theworldofstuff.com/me.jpg' for reading: No such file or directory
GIMP Message
Opening 'http://www.theworldofstuff.com/me.jpg' failed:
JPEG image plug-In could not open image

Does anyone know what's up here?

---

### Post by Dawa on 2007-12-31
I'm going to bump this; I get the exact same error.  Opening a remote file in GIMP is impossible for some reason.  Really annoying since there's no "copy image" in firefox.

Anyone know of a fix?

---

### Post by patrickgule on 2008-01-02
I've got the same problem as well.. Anyone filed an bug?

Edit:
Found this: [https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/146290]("https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/146290")
Apparently you have to install gimp-libcurl or gimp-gnomevfs on your own now, quite sure this was done by default before..

---

### Post by jordon on 2008-01-02
Thanks! I installed gimp-libcurl, and now I can open remote images.

---

