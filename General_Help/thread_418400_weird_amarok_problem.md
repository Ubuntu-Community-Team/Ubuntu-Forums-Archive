---
title: "weird amarok problem"
date: 2007-04-22
forum: General Help
---

### Post by r0ck80y on 2007-04-22
Hi,

This happened just today...I was listening to some music on amarok as i always do, but this time i ran out of space on my home drive. I deleted some stuff but soon within minutes i was out of space again !! I freed about 100mb again and i saw the disk space reducing at a uniform rate. I shutdown amarok and things settled. Now i have just about 60mb left :( :(

What was happening with amarok? any ideas? :confused:

---

### Post by djgrandmarquis on 2007-04-22
Are you using SQLite? MySQL? That's the first place I'd look. Not sure though.

---

### Post by r0ck80y on 2007-04-22
ya..database is managed by SQlite..but that was always being used and such a problem had never occured until today. But i had more than 500mb of disk space...now its 60mb..where are all the files that took up all that space. 
.kde/share/apps/amarok --> 41 mb
/usr/share/apps/amarok --> 3 mb
/tmp --> 70 mb

:confused:  :confused: 
400mb space used up but where??

---

### Post by djgrandmarquis on 2007-04-22
There are some useful commands for listing disk usage...

```
du -h
```

Or try sorting them by size

```
du | sort -n
```

Maybe that will unearth something.

---

