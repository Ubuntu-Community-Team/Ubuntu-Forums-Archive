---
title: "opening multiple files from cli"
date: 2007-08-04
forum: General Help
---

### Post by phillips321 on 2007-08-04
Hi guys,

i would like to open all of the following files with gedit:
```
phillips321@LinuxDesktop:~/Pictures$ find -name images.html
./Gordie's Pics/images.html
./Laura and Dale 060908/images.html
./Star vs C&G 070201/images.html
./Sid/images.html
./Florida/images.html
./Other/images.html
./Camping/images.html
./Meal 060816/images.html
./Brecons 070419/images.html
./Damaged Cae/images.html
./Family/images.html
./Microsoft Clip Organizer/images.html
./Brecons 070604/images.html
./OldBoys 061231/images.html
./Graduation 060908/images.html
./Sandy/Originals/images.html
./Sandy/Vids/images.html
./Sandy/images.html
./Random 060925/images.html
./Holiday Spain/images.html
./Prinknish Abbey 060717/images.html
./Camera/images.html
./Me/images.html
./Mates and Pissed/images.html
./Bevs Bday 060901/images.html
./Drayton Manor 060710/images.html
./Florida 061020/images.html
./Nala/images.html
./play/images.html
./Fish/images.html
./Brecons 060829/images.html
./RosieandDixon/images.html
./Uni Lads/images.html
./WallPapers/images.html
./Cruise/images.html
./Gemma/images.html
./Bodmin 061009/images.html
./Horse Riding/images.html
phillips321@LinuxDesktop:~/Pictures$

```
i have tried the following but neither seem to work
```

phillips321@LinuxDesktop:~/Pictures$ gedit | find -name images.html
phillips321@LinuxDesktop:~/Pictures$ find -name images.html | gedit

```

any ideas?

cheers

---

### Post by Paul S on 2007-08-04
try

```
find ~ -iname '*images.html*' -exec gedit {} ';'

```

hth

---

### Post by phillips321 on 2007-08-04
magic that worked, cheers for that A++++ :)

What i wanted to do was simply remove all of the crap that Konqueror "Create Image Gallery" added in.

You know of any other better tools for creating galleries?

I don't want to do it on the fly like gallery(2).

Cheers

---

