---
title: "using rm recursively in a right way"
date: 2008-02-29
forum: General Help
---

### Post by nlz on 2008-02-29
My flash disk goes into windows PC's a lot, that's why i have to delete a lot of viruses every day. Mostly just from the root. Now something irritating has happened. A virus was active on my flashdrive that created a file in every directory with the name of the directory (eg documents.exe in document, libarary.exe in library). Clamav doesn't recognise these executables as viruses, so i want to remove them manually, but since i have 154 folder in my USB stick, i don't want to go into every dirctory, so i wanted to use a rm command to remove the files

i tried
 ```
 rm -r *.exe 
```

but it didn't work. What code should ik use to remove all executables from my flash? There are no other exe-files on my flash that i don;t want to be removed

---

### Post by kpkeerthi on 2008-02-29
```

find /media/sdb -name *.exe -exec rm '{}' ';'

```

/media/sdb is where your flash is mounted. You can find it by running **mount** command.

EDIT: Oh.. btw.. be **extra cautious** with that command and **double check your flash's mount point**.

---

### Post by Mr. C. on 2008-02-29
Change the find command to be safer and more efficient:

```
find /media/sdb -name "*.exe" | xargs rm -f
```

You want to 1) avoid shell filename expansion of * in case any .exe files exist in the current directory, and 2) send clusters of filenames to one or two **rm** commands instead of fork/exec'ing a new **rm** process for each file.

MrC

---

### Post by nlz on 2008-02-29
many thanks, everything worked out nicely!

---

### Post by nlz on 2008-02-29
hmmm but it didn't seem to have worked out with the files in the directories which consisted of two names. So was there a file named ' ethiopie voorbereidingen.exe ' still in the directory ethiopie voorbereidingen. The same was true for the directory ' logo's '.
Maybe because space and ', are normally excluded in directory and file names?

---

### Post by banewman on 2008-02-29
If there is a space in the file name enclose the file in parenthesis 
e.g. "ethiopie voorbereidingen.exe '"
:)

---

### Post by Mr. C. on 2008-02-29
Use the find -print0 and xargs -0 options to protect characters that would need to be quoted from shell word splitting:

```
find /media/sdb -name '*.exe' -print0 | xargs -0 rm -f
```

MrC

---

