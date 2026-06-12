---
title: "Why doesn't &quot;search&quot; find anything?"
date: 2006-08-07
forum: General Help
---

### Post by Athanasius on 2006-08-07
Every time I use search nothing comes up, it seems useless.  Deskbar doesn't search for files in my computer, is there something that I am doing wrong?  I also want to search for hidden files.

Are Beagle and Deskbar the same kind of thing?

---

### Post by cantormath on 2006-08-07
> **Athanasius said:**
> Every time I use search nothing comes up, it seems useless.  Deskbar doesn't search for files in my computer, is there something that I am doing wrong?  I also want to search for hidden files.

Are Beagle and Deskbar the same kind of thing?

try this
in terminal
```
sudo find / -name whateveryourlookingfor
```

or
in terminal
```
sudo gnome-search-tool
```

set look in folder to Filesystem if you want to search the whole computer.
Set more options if you want to change how it searchs.

---

### Post by hopstah on 2006-08-07
also, do a ```
sudo updatedb
``` before you search to make sure you get the most recent changes on your disk.

edit:  and don't waste your time on beagle.  it's really buggy right now, and hogs wayyyyy too many resources to make it worthwhile.

---

### Post by hanzomon4 on 2006-08-07
Find is kinda slow, but locate does the trick pretty quick :confused: 
 
```
sudo updatedb
``` ```
locate what_you_want_to_find
```

---

### Post by kbuel on 2006-08-08
i normally do a find and pipe it to grep, then i can use all of greps options when searching... so basically something like this:

find | grep -i whatever

that will do an case insensitive search for "whatever" in the file name.

---

### Post by mlind on 2006-08-08
I use whereis for binaries, slocate for other stuff. 

find is slow if you have to descend to many subdirectories, but offers wide range of different search arguments.

---

### Post by halucard22 on 2006-08-18
Beagle doesn't index anymore. When i create a new file, nothing happens. In the beagle status, I often see Optimize. That's strange !!!

---

### Post by Athanasius on 2006-08-18
I have found Beagle to be useless, I must be doing something wromg.

---

### Post by hopstah on 2006-08-20
i'm in that same camp right now.

---

### Post by GameGod on 2006-08-20
I'm glad I'm not the only one that noticed that Beagle just doesn't find all the files it should for some reason... :(

---

### Post by Roostey on 2006-08-24
I had the same problem where beagle wouldn't update it's indexes.

It turned out that there were several locked files in one of the dirs under ~/.beagle/Indexes.  Deleting the contents of the Indexes directory, then restarting beagled (after killing the stuck beagled and beagle-helper processes) allowed it to finish without errors and now it's working again.

---

