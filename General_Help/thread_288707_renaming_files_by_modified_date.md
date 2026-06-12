---
title: "renaming files by modified date"
date: 2006-10-30
forum: General Help
---

### Post by mzilhao on 2006-10-30
i want to make a bash script to automatically copy files from my digital camera and then renaming them according to their date.

the jpeg files are easy, i just have to do 
```
jhead -nf%Y-%m-%d--%H.%M.%S *.jpg

```
and jhead renames all the files with the date on the EXIF data, exactly like gThumb.

problem is, i sometimes have some avi video files on my camera, and they don't have EXIF data. so, neither gThumb nor jhead will work.

i'd like to make a script to rename the avi files according to their modification or creation date...

any ideas?

thanks in advance

---

