---
title: "deja-dup new target space requirement"
date: 2024-12-01
forum: General Help
---

### Post by JamButty on 2024-12-01
Hopefully someone answers this before the site stops working.
I have always used the default backup program, which i understood to be Deja-dup. Up to now it has been simple.
Since my last backups, the program has been changed and now requires 2X the total required space at the target to be available.
1. this is a real pain and I would hope there is a way to turn this ##$%!@ feature off.
2. It still refuses, even when I comply e.g. I deleted everything on one of my backup disks, giving me 1.7 TB free, which is what the program said was necessary to start, yet it still says the target is too small.

---

### Post by sberla54 on 2024-12-03
Same for me!
I can't find a way to fix this. I'm considering switching to a different backup software.

I just installed Ubuntu 24.04.1 on a new PC, I deleted my old backup folder, and I started a fresh new backup.
I need to backup 1.1 TB of data but DejaDup wants 2.1 TB free, and my NAS only has 2.0 TB free, which were always more than enough and never close to saturation before (on PopOS 22.04).

Root and Home partitions are also far from saturation.

Before deleting my whole old backup folder, I launched DejaDup to re-do a new fresh backup on top of the existing one (which belonged to my previous PC) and the new backup started with no issue, even if I had to stop it because NAS was getting full.

---

### Post by sberla54 on 2024-12-03
Relevant: [https://ubuntuforums.org/showthread.php?t=2497096](https://ubuntuforums.org/showthread.php?t=2497096)
> Deja Dup (Duplicity) can't just make incremental backups for forever. It has to do a second full backup at some point. But it won't have enough space. I'm just suggesting that Deja Dup knows this and is preemptively saying that there's not (won't be) enough room. But who knows. It might be interesting to see if it will back up something with size less than half the size of your backup disk (less several GB to be safe).
> After Googling around, apparently this is the issue. In all the years I've used Deja Dup I've not come across this before, but apparently it does indeed need double the size of the backup otherwise it will stall.
That's space that I do not have. I never appeared to have this issue in 22.04, so it must be something new in the 24.04 version of DejaDup.

This may be worth trying but I don't have much hope about it:
> Duplicity keeps some files in .cache in the duplicity folder. Namely the manifest and signature files. When I want to start over in Duplicity I delete the appropriate sub-folder. Deja Dup also has settings. I have used the dconf-editor to reset settings back to their defaults. I don't know if there are other default settings somewhere. Under org.gnome.deja-dup I believe. Not sure about punctuation there.
> I installed:
dconf-cli
dconf-editor

Opening dconf-editor (with warnings) shows deja-dup settings.

---

### Post by sberla54 on 2024-12-03
At the moment I'm trying Pika Backup: [https://apps.gnome.org/PikaBackup/](https://apps.gnome.org/PikaBackup/)

It's very similar to Deja Dup and it's not complaining about disk space.
I don't like the fact I must install it via Flatpak but I can live the that.

---

### Post by davetheoldcoder on 2024-12-03
DejaDup is simple to use, but my preference is [BackInTime]("https://github.com/bit-team/backintime"). It's basically the same as my former backup software [RSnapshot]("https://github.com/rsnapshot/rsnapshot"), but BackInTime has a GUI, while RSnapshot uses a text configuration file.

---

### Post by sberla54 on 2024-12-05
Thank you, mate!
So far I'm happy with Pika Backup, it's simple and it just does the job :)

---

