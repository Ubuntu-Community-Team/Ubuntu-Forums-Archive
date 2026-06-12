---
title: "NTFS-3G broke XServer"
date: 2007-02-18
forum: General Help
---

### Post by mailcar on 2007-02-18
A true newb...have spent 3 weeks with Ubuntu 6.10, first time using Linux.
So far have dual-boot, beryl working, access windows LAN, most all works fine...here's the problem:

Performed a fresh install, all is working (no beryl this time), so I wanted to add access to a local NTFS drive, so I added thru Synaptic...NTFS-3G & rebooted.

Xserver now errors out & I'm left with the command line. So when I log in as Root, I cannot update root files, noted as read-only & worst yet, when I try "APT-GET remove NTFS-3G" it says that it can't access and write to config files.

I love Linux & would like to be a MS convert, but is Linux this easy to break? With MS quirks & BSOD, you can still always manage to get back into the GUI. I can always do another install (obvious loss of time), but more concerned about long-term stability (also have had better luck with EXT3, where as ReiserFS corrupted on a boot after a normal shut-down???).

Thanks, C.A.  :)

---

### Post by taurus on 2007-02-18
Boot into recovery mode and reconfigure your X again with

```
dpkg-reconfigure xserver-xorg
shutdown -r now
```

You need to know that ntfs-3g is still a beta and beta means that sometimes it works and sometimes it would break your machine.  So, if you want to have a stable machine, stay away from the beta apps.

---

### Post by mailcar on 2007-02-18
Taurus thanks for the info...tried the first line, here was the response:
'Package 'xserver-org' is not not installed and no info is available'

At this point, an install looks like a shorter route than troubleshooting.

Understand the Beta issue...if you see I noted the ResiderFS issue also (on a normal shutdown).

Still curious about the overall stability issue, so have this question:
"Before conducting a package install, do you have to do research on each & every package to be safe?

Hopefully "Fawn" will be a stronger candidate!  Thanks again for your help   :)

---

