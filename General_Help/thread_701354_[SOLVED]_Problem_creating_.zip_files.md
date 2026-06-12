---
title: "[SOLVED] Problem creating .zip files"
date: 2008-02-19
forum: General Help
---

### Post by nyorondesu on 2008-02-19
I'm trying to create a .zip file of a folder with a multitude of sub-folders, some of which are empty, but all of which must remain in-tact. I've tried just right-clicking in Nautilus and using the "Create archive" button, but this removes empty folders. Then I tried making it in File-Roller with the same result. Apparently, you can create .zip files with WinZip that don't remove empty folders, is there any way to do this in Ubuntu?

---

### Post by cdenley on 2008-02-19
Seems to work for me using gutsy.
[ATTACH]60117[/ATTACH]

---

### Post by Shippou on 2008-02-19
You can install wine then install winzip or winrar.

Alternatively, you can download Ark then compress it into .tar or .bz2... (I don't know if it also compresses empty folders).

Hope this solves your problem.

But then just a curious question: why would you want to compress empty folders?

---

### Post by oldos2er on 2008-02-19
Are you averse to the terminal? Type "zip" in a terminal to see your options. Just for test purposes, I created a zip file with directories intact by using "zip [name of zip file] -r9 [/files/to/be/zipped]"

---

### Post by nyorondesu on 2008-02-19
> **oldos2er said:**
> Are you averse to the terminal? Type "zip" in a terminal to see your options. Just for test purposes, I created a zip file with directories intact by using "zip [name of zip file] -r9 [/files/to/be/zipped]"
Okay, that worked. Thanks!

Also, I had to keep the empty folders because it's part of an assignment for a really stupid computer course.

---

### Post by oldos2er on 2008-02-19
You're welcome--glad it worked.

---

