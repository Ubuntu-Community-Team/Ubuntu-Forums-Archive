---
title: "Corrupted rar"
date: 2008-04-21
forum: General Help
---

### Post by timboellis on 2008-04-21
Is there anyway to recover a corrupted Rar file , it is a file full of all my websites i designed and its over 2 gig

---

### Post by ibuclaw on 2008-04-21
I doubt you'll get the full file back.

But there is a ncurses based terminal app called "photorec" that can recover lost files.
There is also an app called "testdisk" that can recover lost partitions, if you're interested in that too.

But from what you'll recover, most files/filenames will be gobble-dee-gooch.

The larger the file the worse it gets.
Not to forget that you have probably overwritten the data with the Ubuntu Install by now.

But give it a shot.
It's in the repositories.
Open a terminal and type in
```
 apt-get install testdisk 
```
Then run
```
 sudo photorec 
```
It has simple to follow instructions so you won't get too lost.

Regards
Iain

---

