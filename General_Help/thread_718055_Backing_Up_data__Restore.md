---
title: "Backing Up data / Restore"
date: 2008-03-07
forum: General Help
---

### Post by iheartubuntu on 2008-03-07
Ive read several places that linux doesnt have a restore feature like XP does, and that linux is planning something in the distant future. With this in mind, and with me tinkering around on my systems, I want to back up my data, but have been reluctant thus far to do so.

Can someone guide me a bit please? Ive found two programs called "Keep" and also "Simple Backup". Keep looks simple, and Simple Backup looks a bit more robust and might be able to do what I want. Which, frankly, I dont know too much what I want to do here :) I want to back up the stuff in my home directory as well as and programs Ive installed.

I worry about ending up one day at a command prompt at boot up and not knowing what the heck to do to get into my system.

I cam across this... "How to Restore GRUB".. do I need this as part of my backup knowledge?
[http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore](http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore)

and this...

How to Backup and Restore your System...
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

Any thoughts and suggestions would be helpful! Thanks.

---

### Post by LaRoza on 2008-03-07
Windows has a Registry, which is a big binary file that is easily corrupted and everything relies on it (also, one can alter it with regular permissions)

Linux doesn't have that, and relies on text files for configuration settings.

There is a stalled effort to make such a program: [http://ubuntuforums.org/showthread.php?t=678665](http://ubuntuforums.org/showthread.php?t=678665)

Only the package backup and restore script is working at the moment.

It really isn't a problem like it is with Windows, as you should back up any files you edit.

Restoring Grub isn't essential knowledge unless you do a lot of dualbooting and reinstallations of Windows. Backuping up the grub settings should be enough.

---

