---
title: "Date Stamps on Files and Folders"
date: 2007-03-15
forum: General Help
---

### Post by gavinjb on 2007-03-15
Hi,

I have somehow managed to change the date stamp on loads of photos I have taken, this means that when viewing them in Picasa they are all showing in 2007 rather than in the years I have taken them, does anyone know an easy way I can change the date stamp on these files (if possible at folder level, filtering down to sub folders), I am looking at preferable a gui, but anything which can enable me to get all my files organized again will help.

Thanks,


Gavin,

UPDATE: Just tried the touch command (touch -t199908010815 filename) but it made no difference

---

### Post by peabody on 2007-03-15
> **gavinjb said:**
> 

UPDATE: Just tried the touch command (touch -t199908010815 filename) but it made no difference

It should have made a difference if you used it correctly.  I can't speak for Picasa because I don't use it.  Is it possible that it stores its dates somewhere else and doesn't rely on the filesystem for the information?

What does the ls -l command return?

---

### Post by gavinjb on 2007-03-15
Hi,

found my problem with touch I was doing it right, but for some reason when I was right clicking on a file and selecting properties it was not showing me the updated details until I refreshed the folder in kde.

Didn't fix the problem with Picasa but found an option where I can change the date for folders.  

Does anyone know of a better Photo Organizer, I have tried both F-Spot and DigiKam and neither gives me the flexibility I would like, but then I am comparing them to IMatch on Windows


Thanks,


Gavin,

---

