---
title: "Problems transferring mp3's to my player"
date: 2007-08-31
forum: General Help
---

### Post by C E Jones on 2007-08-31
Hi all,

I just got a Sansa Express 1GB mp3 player and Ubuntu isn't letting me copy my music files onto the player's flash drive. It sees the drive without a problem and I'm able to do other things like delete files from it, but I can't add anything! :confused:

The error message I get reads: "Error: 'invalid parameters' while copying [filename]"

Any suggestions would be much appreciated, thanks!

---

### Post by jackocleebrown on 2007-08-31
Hey,

It might just be the filenames of the files you are trying to copy to the mp3player. Most likely the flash drive on the player is formatted to FAT16 and will not support as many filename characters than a linux ext3 drive.

Jack

---

### Post by C E Jones on 2007-08-31
Thanks Jack, you were right. I renamed the files and transferred them without a problem!

CEJ

---

