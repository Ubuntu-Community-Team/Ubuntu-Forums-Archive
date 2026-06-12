---
title: "Ubuntu standard backup program"
date: 2018-10-11
forum: General Help
---

### Post by enzo1337 on 2018-10-11
hi! i have a question about the ubuntu backup program that comes with it that one with like the black vault anyway i have autobackup to network drive turned on and the first question is is that the backup folder is just full off random files i gues that is because is a backup and restore program so its get normal when you do restore right?. and the second question is that the program has keep old files forever setting on but the folder doesnt seem to take up more space or mayby taking upp a little bit more space every time its backup im not sure,  but mayby thats is also because is a backup and restore program idk can someone explain to me?

---

### Post by deadflowr on 2018-10-11
First question: Yes 
Second question: Backups (known as deja-dup) uses incremental backups, so the first backup is a full backup and all subsequent backups (for a set period, default being 90 days) only backup whatever has changed since the last backup.
The one major downside is that the backups require that all backups from the first full backup to the last incremental backup are uncorrupted. If any backup is corrupted then every backup after the point of corruption is lost.

More here: [https://wiki.gnome.org/Apps/DejaDup/HowItWorks]("https://wiki.gnome.org/Apps/DejaDup/HowItWorks")

---

### Post by enzo1337 on 2018-10-11
okay thanks so much!

---

