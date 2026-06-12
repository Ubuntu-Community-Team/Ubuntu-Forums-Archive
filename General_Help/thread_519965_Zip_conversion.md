---
title: "Zip conversion?"
date: 2007-08-07
forum: General Help
---

### Post by upthelum on 2007-08-07
Is it possible to convert a .zip file into a .tar.bz2 extension? 
I ask because i downloaded a pretty cool bootsplash which is a zip file and my settings manager wont install it unless it's a .tar.bz2 file, although some .tar.gz files work also. I tried renaming it but it didn't work. Can anyone recommend a program to do this in Ubuntu if there is one?
Thanks in advance...

---

### Post by eggdeng on 2007-08-07
Extract the file by clicking on it and choosing extract in the dialogue window. To compress in the new format, cd to the directory where the file is located and run ```
bzip2 file_name
``` This will compress the file as file_name.bz2 and delete the original.

---

### Post by upthelum on 2007-08-07
Hey thats good but i tried that and the file converted to .bmp.bz2, which isn't working. :sad:

---

### Post by eggdeng on 2007-08-07
bmp.bz2 is legit, but I thought it was strange you wanted a compressed file for a settings manager. Are you sure that what you need is a bz2? Check your sources because splash screens are usually .png or jpg.

---

### Post by nick_h on 2007-08-07
I think you need a compressed tar file. Try:
```
gunzip file.zip
tar cvjf <dir>
```
where <dir> is the directory you unzipped the archive

---

