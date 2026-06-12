---
title: "Remove all files in /home/andy/.local/share/Trash/files"
date: 2020-08-28
forum: General Help
---

### Post by raleigh3 on 2020-08-28
I am trying to delete every file and directory in the Trash directory.

I know I can just empty the trash, but this part of a cronjob.

I have this and it works on Most files, but not all.

```
rm -r /home/andy/.local/share/Trash/files/*
rm /home/andy/.local/share/Trash/files/.*

```
It does not remove the directory

.PeaZip

Is there a command that will remove EVERYTHING?

---

### Post by Dennis N on 2020-08-28
You could install **trash-cli** and then use the **trash-empty** command.

---

