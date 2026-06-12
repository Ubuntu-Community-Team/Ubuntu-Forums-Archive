---
title: "IRiver IFP-899, not writeable?"
date: 2008-01-27
forum: General Help
---

### Post by Coralin on 2008-01-27
Hello; I'm fairly new to the Linux community, and everything is going quite well, thanks to these forums, except for one problem that I just can't seem to find a solution for: When I connect my unlocked Iriver IFP-899, with the UMS firmware, it mounts, showing an iPod-ish icon on the desktop. I can open it, copy and play the files already on it, but when I try to delete them from the drive or add any new files, it claims to be a read-only filesystem. Another thread offered the suggestion of unmounting, and remounting as a writeable filesystem... but I have no idea how to do that. I can unmount it no problem, but don't know how to remount it as writable... Any suggestions?
Thanks in Advance!

---

### Post by Coralin on 2008-01-27
I hate to bump, but does anyone have any suggestions? I REALLY don't want to have to use my MS partitions to handle MP3 player woes...

---

### Post by dandoze on 2008-02-20
I'm no guru on this matter, but I would say type "mount" as root to see what type of file system it is mounted as and what options are active (like "ro") and then make an /etc/fstab entry similar to a cdrom.  Even better, plug in a thumb drive that works fine read-write and see what it is listed as in the "mount" output.  If in doubt, post your "mount" output and your /etc/fstab and maybe somebody can make a more specific suggestion.

I have the same mp3 player and a linux box on my desk.... maybe i'll just try it myself...

---

### Post by Coralin on 2008-02-21
It's actually quite odd... it seems to have fixed itself somehow? :confused:

---

