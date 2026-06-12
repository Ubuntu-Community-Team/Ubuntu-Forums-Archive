---
title: "Insert permission as root"
date: 2014-04-08
forum: General Help
---

### Post by alfirdaous on 2014-04-08
Hello everybody,

Even though I am a root, I cannot insert text and save it using vim:

```

"file" [readonly] 1L, 68C

```


OR:

```

"file"
"file" E212: Can't open file for writing
Press ENTER or type command to continue

```

Even if I would like to change the file system:

```

chmod: changing permissions of `file': Read-only file system

```
Thanks for your help

---

### Post by hardkhora on 2014-04-08
Just looking at your code, have you tried using ```
sudo
``` before your commands?

---

### Post by Impavidus on 2014-04-08
It appears that the entire file system has been mounted read-only. In recovery mode the file system is mounted like that by default and it is also remounted read-only in case of I/O errors to the drive. Are you in recovery mode or did you get an I/O error, or any other reason for the file system to be in ro mode?

---

### Post by hardkhora on 2014-04-08
Nice work Impavidus, I totally missed that when looking at the post.

---

### Post by alfirdaous on 2014-04-09
Well, I rebooted the system and now it works fine, thanks everybody

---

### Post by Impavidus on 2014-04-09
If it suddenly went read-only it's best to check at least the smart status of your hard drive (search for disk tools). It may be nothing, but if you got an I/O error you could have a bad drive. Make sure you have backups, but that goes always.

---

### Post by hardkhora on 2014-04-10
As pointed out, make backups...always make backups. Flickr gives you 1 TB of space for free for photos and video files (up to 1 GB)...just saying.

---

### Post by alfirdaous on 2014-04-18
Well, I've got this error again:

```

mv: cannot remove `Downloads/Medias/002.mp3': Read-only file system

```

---

### Post by Danger_Monkey on 2014-04-18
[COLOR=#000000]_I_&#8203;mpvadius is correct, something bad is making the disk go to RO.  You may want to boot from a live CD and use fsck to check the partition for bad sectors, etc.[/COLOR]

---

