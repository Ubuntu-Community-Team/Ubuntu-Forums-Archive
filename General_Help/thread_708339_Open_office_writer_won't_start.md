---
title: "Open office writer won't start"
date: 2008-02-26
forum: General Help
---

### Post by flightless bird on 2008-02-26
Up until a few days ago everything was fine, there have been no updates I'm aware of, and now OpenOffice.org writer (oowriter) does not open. It displays the splash screen and the blue bar moves across, but no main window appears. Running oowriter in terminal brings up:
```
~$ oowriter
X-Error: BadValue (integer parameter out of range for operation)
        Major opcode: 12 (X_ConfigureWindow)
        Resource ID:  0x0
        Serial No:    1235 (1235)
These errors are reported asynchronously,
set environment variable SAL_SYNCHRONIZE to 1 to help debugging

** (process:11884): WARNING **: Unknown error forking main binary / abnormal early exit ...

```
This is quite a big issue for me at the moment - any ideas?

---

### Post by strabes on 2008-02-26
Have you tried uninstalling it and reinstalling it?

```
sudo aptitude purge openoffice.org-writer
sudo aptitude update && sudo aptitude install openoffice.org-writer
```

---

### Post by flightless bird on 2008-02-26
I have used synaptic to reinstall open-office-base, core and writer, but that didn't help. I would like to purge it as above, but it keeps insisting I uninstall ubuntu-desktop and kubuntu-desktop, which seems excessive to me

---

### Post by Hagar Delest on 2008-02-26
You can try to install the official version of OOo : [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

The ubuntu-desktop is a meta package, you can remove it.

---

### Post by flightless bird on 2008-02-29
Bizarrely, just as an experiment, I installed xfce4 and it OOwriter works fine in that environment - which is strange I know, considering all the shared libraries. It still won't work under kde and gnome, but at least I have a working production environment

---

