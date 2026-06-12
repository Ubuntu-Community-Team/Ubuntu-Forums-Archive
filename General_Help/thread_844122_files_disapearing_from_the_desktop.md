---
title: "files disapearing from the desktop"
date: 2008-06-29
forum: General Help
---

### Post by eival on 2008-06-29
ive noticed this issue happening quite frequently where files and folders on my desktop will disapear after i change it(either by renaming it, or simply moving it to another area of the desktop)and the only way to get it back is by doing
Places > Search for Files > Look in folder (my username)

the files wont show up if i search only the desktop folder, which is strange cause...

the search results always show the file in my desktop directory. then i have to click+drag it back to the desktop so i can see it visually and access it like normal.


anyone else know about this issue and is there a fix cause ive actually lost quite a few files in the past since installing Ubuntu but it wasnt till just now that i pinpointed that the files werent deleted but somehow hidden but also the only way to find them is to remember the name of the file/folder, otherwise its lost forever in the partition somewhere:(


im using Hardy Haron 64bit version

---

### Post by ghostdog74 on 2008-06-29
try finding through your terminal.
```

find / -name "your_file_name" -print

```
and see where it lands.

---

