---
title: "Which Software: File Recovery"
date: 2006-12-04
forum: General Help
---

### Post by charlie. on 2006-12-04
I'm looking for software to recover deleted files on a memory stick. I presume that the "delete" just removed records in the file allocation table and the user has promised me that she never wrote any new data to the device after she deleted the data she wants me to recover.

Naturally, I'm looking for something that will run on my nice, shiny Ubuntu Edgy workstation.

Any suggestions would be greatly appreciated. Thank you.

---

### Post by charlie. on 2006-12-05
This is, honestly, the first question I've asked on these forums that has not received an answer within about 18 hours. I'm not sure whether that should be taken as a compliment to this awesome community or an indication of the difficultly of the proposed file recovery.

*BUMP*

---

### Post by RAOF on 2006-12-05
What sort of file system is on the stick?  That'll determine what tools (and whether it's actually possible or not) you can use to recover the files.

EDIT: It seems like the **magicrescue** package might contain the tools you're after, regardless of file system.

---

### Post by charlie. on 2006-12-05
The file system is FAT-16.

I've dug around a bit and managed to make a raw copy of the card with dd. I fiddled around with the Sleuth Kit, but it could not go into the directory that was deleted because it said that the first cluster was allocated. I then tried an app called foremost, which actually did recover a few of the jpg files on the disk, but not very much.

Thanks for the suggestion, I'll try magicrescue.

---

### Post by charlie. on 2006-12-05
Where is this "magicrescue" package? I can't find it.

---

### Post by Sef on 2006-12-05
Try [Trinity Rescue Kit]("http://trinityhome.org/Home/index.php?wpid=1&front_id=12").

---

