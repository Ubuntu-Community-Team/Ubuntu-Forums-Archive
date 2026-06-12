---
title: "Extracting .rar files : Keep broken files"
date: 2007-06-26
forum: General Help
---

### Post by sunshine12 on 2007-06-26
Hi all,

I would like to know how to keep broken files while extracting .rar files?

For example I started downloading .rar file that contains 500MB video, but that is not finished and stopped at 400MB.
Now I have 400MB .rar file instead 500MB .rar file. Now back in windows using Winrar, If I select "Keep broken files" option while extracting .rar file then It extract whatever is inside the file(upto 400MB). so I can see that much part. so how to do it in archive manager?? Same thing if downloaded 7parts out of 10 and want to see that much part how can we do that???

Thank you

---

### Post by yabbadabbadont on 2007-06-26
In a terminal window, run:
```
unrar x -kb filename.part1.rar
```
Of course, replace "filename.part1.rar" with the correct name of your file.

---

### Post by sunshine12 on 2007-06-26
Thanks a lot....

---

