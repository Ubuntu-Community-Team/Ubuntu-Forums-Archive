---
title: "moving files to mp3 player"
date: 2008-02-20
forum: General Help
---

### Post by gorlando on 2008-02-20
I have previously moved audio files and video files to my mp3/4 player but now i get the following:


unable to copy files to /media/disk

You do not have permissions to write to this folder.

what to do..

---

### Post by eggdeng on 2008-02-20
First thing, if it has a lock switch like pen drives have to enable /disable writing, check it's in the open position.
Run ```
ls -l /media 
``` to see what the permissions situation is.

---

