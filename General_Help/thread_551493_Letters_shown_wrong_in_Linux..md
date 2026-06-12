---
title: "Letters shown wrong in Linux."
date: 2007-09-15
forum: General Help
---

### Post by _sAm_ on 2007-09-15
Hi, I need help with my files. 

I got a new external hard drive witch I in Windows XP converted to NTFS, with Norton Partition. When this was done I transferred all my music and other file to this drive. Lots of the music files comes from Scandinavian artist, and so the names are written in that language. That means letters as ö, æ, å are in the file names. This was before I started using Ubuntu.

I decided to turn this drive into the ext3 file system, and did so with geparted after moving all the music back to an internal hard drive. The problem showed up when I transferred the files back; all the letters(as ö, å and so on) are now displayed as a black box with an ? in it. I run Windows Xp in dualboot, and when I mount this disk to Windows all the letters are shown correctly. 

Is it possible to fix this in some way? It is to many for me to do it manually. 

I will be very happy for any help!

---

### Post by por100pre1 on 2007-09-15
Check if renaming all files with Audio Tag Tool can do the trick:

```
sudo aptitude install tagtool
```

Be sure to try with some files first, until you get to do it the way you like it. :)

---

### Post by Sef on 2007-09-15
Have you enabled those language?  (System > Administration > Language Support)

---

### Post by Oki on 2007-09-15
...........

---

### Post by mali2297 on 2007-09-15
> **Oki said:**
> 
tagtool is not an option, there is nothing wrong with the tags - but how the files are shown in Nautilus.


If you try to manually rename a file with å, æ, ö etc, doesn't it work?

If it does work, you can more systematically recreate the file names from the tags by tools like* Audio Tag Tool* or *Ex Falso*. However, I would suggest that you convert the letters to a:s and o:s.

---

### Post by Oki on 2007-09-15
.................

---

### Post by por100pre1 on 2007-09-15
Let me clarify this. Moving some files to other systems has messed many of my files in the same way you mentioned (I use Spanish characters, é, ñ, etc.). When the tags are fine, renaming the files has worked for me. :)

---

