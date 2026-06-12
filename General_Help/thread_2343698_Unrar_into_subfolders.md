---
title: "Unrar into subfolders"
date: 2016-11-18
forum: General Help
---

### Post by thorep on 2016-11-18
Hi! I have alot of folders with rar files. I want to unrar it all, but i want to place the file in the same folder where the rar files is.
Example : i have 4 folders with 4 rar files. I want to unrar into each folder.

I have tried this : unrar x -r -o- *.rar but it just places all the files in the folder im running the command from.

Any tips?

---

### Post by howefield on 2016-11-18
How about ..

```
unrar e sourcepath destination
```

Eg..
```
unrar e Documents/Documents.rar ~/Downloads

RAR 5.30 beta 2   Copyright (c) 1993-2015 Alexander Roshal   4 Aug 2015
Trial version             Type RAR -? for help


Extracting from Documents/Documents.rar

Extracting  /home/hugh/Downloads/editdepends                          OK 
Extracting  /home/hugh/Downloads/get-iplayer modes                    OK 
Extracting  /home/hugh/Downloads/Handy Commands                       OK 
Extracting  /home/hugh/Downloads/ICS - Xboard                         OK 
All OK
```

---

### Post by thorep on 2016-11-18
I dont think that would work, becouse i have multiple folders, and  want the unrared content to be unpacked into the folder it came from.
Example:
Movie/movie1/.rar files
Movie/movie2/.rar files
Movie/movie3/.rar files

I want the unpacked files to end up in the folder where they came from.

---

### Post by howefield on 2016-11-18
Ok, I misunderstood.. this might be better. At the least it worked on a test I've just done. 

```
find Movie/ -name '*.rar' -execdir unrar e {} \;
```

---

### Post by thorep on 2016-11-19
Thanks! Looks like its working.
Are there a way to delete all the rar files after unrar?

---

### Post by oldrocker99 on 2016-11-19
Welcome to the forums!

Simply use rm.```
rm /path/to/rarfile
```

---

### Post by howefield on 2016-11-19
> **thorep said:**
> Thanks! Looks like its working.

You're welcome, feel free to mark the thread as solved in that case.

> Are there a way to delete all the rar files after unrar?

You could add -exec rm {} \; to the end of the command above eg,

```
find Movie/ -name '*.rar' -execdir unrar e {} \; -exec rm {} \; 
```

If you have already done the decompressing, probably just as easy to do a recursive rm as oldrocker99 mentioned.

---

