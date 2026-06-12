---
title: "So many .goutputstream-* files in ~/... but WHY?"
date: 2015-04-27
forum: General Help
---

### Post by t0p on 2015-04-27
When I look at my home directory, with hidden files visible, I see multitudes of .goutputstream files (eg .goutputstream-HQVUOX).  I take it these files are created when I look at some graphical output or somesuch and are safe to delete?  More importantly: can't I have them written to /tmp, so they'll automatically disappear on reboot?  All these files in my home directory make it very difficult to locate other "hidden" files that I might need to find; and their existence is so irritating!

Is there anything I can do about them, other than periodically deleting them manually?  I know typing
```
rm .goutputstream*
```
is trivial... but why do they go into /~ anyway?  Grrr...

Running Ubuntu 12.04.  I know this is logged as a bug on Launchpad - but still no cure?  If I knew how to, I'd squash this bug as a matter of urgency.  It's expensive throwing laptops and/or monitors through windows in frustration...

---

### Post by dino99 on 2015-04-27
some time ago (long ago) i also had such mysterious files, but never found what was creating them (probably a plugin somewhere, or java) now my system run without java and they never came back, so ... but i've also deactivated scripting into the browser

---

### Post by mc4man on 2015-04-27
longstanding bug with many theories, ect.
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/984785](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/984785)
No longer an issue with recent buntu's, I guess still happens in 12.04

---

### Post by ajgreeny on 2015-04-27
I had that very problem when I was using Xubuntu 12.04 and I added the command ```
bash -c "rm .goutputstream*"
``` to the listed autostart-applications to remove any such files at the start of each session login.

Those files are just an annoyance, and do not cause any real problems, but like you I wanted to get rid of them anyway.

---

