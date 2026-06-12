---
title: "luckybackup has turned jpegs into txt files"
date: 2019-05-22
forum: General Help
---

### Post by keithmbrown on 2019-05-22
I back files up conscientiously with LuckyBackup, and recently used my backups to recreate my Home Folder on a new computer. I had the impression that all was as it should be, until I went to insert some images into a piece I was writing today, and discovered that many (but NB: not all) of my jpg pictures in Pictures and another folder, and in many of the subfolders (but again, not all) have mysteriously been transformed into text files! Some have been given a .png extension, others retain the .jpg extension but still only open with Mousepad, the text editor. They all contain 0 (zero) bytes, and are therefore blank.  Please could someone explain to me what has happened?  I realise it is impossible to restore them now, but would like to make sure it doesn't happen again.  Thanks in anticipation...

---

### Post by CatKiller on 2019-05-22
Filename extensions are broadly meaningless for determining the file type.

In this case, it seems you've backed up the filenames but not the file contents. Which is, obviously, unfortunate. I've never used that backup software, so I couldn't say what caused the error. Creating the structure before filling it with the contents makes sense as an approach, and possibly it just got interrupted before the second part. 

All of those 0 byte files aren't *text files*, as such, they're just empty. The file manager might as well open them with a text editor as much as anything else, and empty files *are* often used to contain text, eventually, for settings and the like.

---

### Post by keithmbrown on 2019-05-23
Thanks CatKiller for your quick reply! I see your point. There's nothing I can now do, as I reformatted and overwrote the old backups, being so sure that my new system had copied everything correctly, as it always used to. Live and learn!
Incidentally, I discovered after I posted my appeal for advice, that the affected files were almost all screenshots I had made, which were .png files by default - so that corroborates what you said: that I had copied filenames but not contents. Usually I save photos as jpegs, and these were unaffected EXCEPT for some reason a folder of jpegs which I had downloaded from my wife's camera!

---

### Post by CatKiller on 2019-05-23
It's *possible* that it was some kind of permissions thing. I believe that the ability to see what's in a directory - the file names - is dependent on the permissions of the directory, but the ability to read the files - the file contents - is dependent on the permissions of the file. Perhaps the backup software was running as a user that didn't have read permissions on those files.

---

### Post by keithmbrown on 2019-05-27
Thanks again CatKiller!  I think you are on to something here - I do all the backups for both me and my wife, and of course the permissions often stop me in my tracks.  As I said above, one of the folders affected was a download of photos from my wife's camera, which probably, as you suggested, had different permissions.  I will check in future that permissions are correctly set.

---

