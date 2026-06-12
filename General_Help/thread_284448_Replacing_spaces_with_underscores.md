---
title: "Replacing spaces with underscores"
date: 2006-10-25
forum: General Help
---

### Post by justin on 2006-10-25
Essentially I am trying to mass rename a folder, all its subfolders and files so that spaces are replaced with underscores. Is there an easy way of going about this? I read about krename, but I use gnome.

---

### Post by Ramses de Norre on 2006-10-25
I think this might work: I'm not able to test it right now so I'm not totally sure.
```
cd /parent/folder/
find . -depth|rename 's/\ /_/'
```

---

### Post by justin on 2006-10-25
That command replaced on the first space in the filename, getting close though. ;)  Any other suggestions?

---

### Post by Ramses de Norre on 2006-10-25
Ow I forgot something, this should do:
```
cd /parent/folder/
find . -depth|rename 's/\ /_/g'
```

---

### Post by justin on 2006-10-25
I love you.

---

### Post by justin on 2006-10-25
hmm, another snag.

if for example, i want to rename usbdisk/my music/name of artist/album name/song title.mp3

and i run the command 'find . -depth|rename 's/\ /_/g'' in /usbdisk

it will rename 'my music', 'name of artist', and 'album name', but it will not rename the mp3. 

it will work however if i go to the the album folder containing the mp3s and run the command. problem is, i have a ton of different artists and albums, which will make this very time consuming. any way i can edit the command so i can just run in from the parent folder?

---

