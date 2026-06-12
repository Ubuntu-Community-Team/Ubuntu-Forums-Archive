---
title: "Copying directories"
date: 2006-12-20
forum: General Help
---

### Post by Valinski on 2006-12-20
Hi i'm quite new to ubuntu and am having a problem copying a directory. Ive copied files in the past but when i try to copy the directory in question it says "Ommitting Directory". 

This is what i have typed: 

[email]dave@dave-desktop:~/Desktop/flightgear/w010n50.tgz[/email]_FILES/Terrain$ sudo cp w010n50 /usr/share/games/FlightGear/Scenery/Terrain
cp: omitting directory `w010n50'

Any help would be appreciated! 

Thanks

---

### Post by tkjacobsen on 2006-12-20
use "sudo cp -r ,,,," to copy recursively. This will do the job, I think.

---

### Post by Valinski on 2006-12-20
Yeah that worked great thanks a lot mate! :)

---

### Post by majoridiot on 2006-12-20
```
cp -ar <directory> <destination>
```

is probably more what you want... the -a also preserves all attributes and permissions.

---

