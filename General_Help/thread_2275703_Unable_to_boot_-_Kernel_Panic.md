---
title: "Unable to boot - Kernel Panic"
date: 2015-04-27
forum: General Help
---

### Post by hanz2 on 2015-04-27
I was editing some files yesterday, and i started getting permission denied, so i restarted the server, apon restarting it, i've received the error:

[B][I]run-init: /sbin/init: No such file or directory
Kernel Panic - Not syncing: Attempted to kill init! Exit code: 0x00000100[/I][/B]

Any suggestions? I believe I still have all my system files.. lib, lib64, dev, etc..

When I try to boot into recovery mode, I get the same error.

Any help would be appreciated.
[COLOR=#AFAFAF][FONT=Roboto]

[/FONT][/COLOR]

---

### Post by twtduck.ii on 2015-05-12
First, please let us know which files you were editing (many system files shouldn't be edited) and perhaps we could work together to figure out what went wrong. 

If the files you were working on were irrelevant, you should browse your hard drive without trying to boot it. If there is a file (or folder) called /sbin/init, then you should probably restore your kernel from a backup or reinstall it. If not, then try and see if you could have misplaced it into a different place. If you still can't find it, try and see if any backups have it. You mentioned that you were using a server, so you should have some backups around (if you don't make backups, I strongly suggest you do. They really help with these situations a lot). 

Let me know if you have any questions!

---

