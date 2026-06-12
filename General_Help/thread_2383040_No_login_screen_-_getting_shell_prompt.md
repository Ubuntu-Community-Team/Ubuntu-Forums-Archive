---
title: "No login screen - getting shell prompt"
date: 2018-01-20
forum: General Help
---

### Post by bizres on 2018-01-20
Hello,

My Ubuntu installation has suddenly stopped working.

Now when booting up, the whole process completes but just before the login screen, it ends up with a message
> BusyBox v1.22.1 (Ubuntu 1:1.22.0-19ubuntu2) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) 
[ATTACH=CONFIG]278250[/ATTACH]
The worst part is, I can't even access my data from a live medium as it's an encrypted volume.

Would really appreciate some help on this, pls.

---

### Post by ajgreeny on 2018-01-20
I can not help with encryption but the one time I had that busybox problem, many years ago, it was solved by running fsck on the volume from a live Ubuntu system.

Whether encryption will mean this is impossible to run, I have no idea, but it is worth a try.
It also leads me to say yet again how important backups are, particularly on encrypted systems; do you have any backups?

---

