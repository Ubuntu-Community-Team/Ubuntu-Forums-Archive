---
title: "Getting Data Files off of a DVD+R"
date: 2007-12-08
forum: General Help
---

### Post by OvenMitt Bandit on 2007-12-08
I have a DVD+R with a bunch of data files on it that was burned on a friend's Mac. Now on my computer (running Gutsy), these files are shown as being protected, and they can't be accessed at all. Is there a program or something that can forcibly rip those files off of the DVD+R?

---

### Post by ekravche on 2007-12-08
It's a permissions problem. If you run
```
sudo nautilus
```

and then navigate to your dvd drive then you should be seeing the files as non readonly

---

### Post by OvenMitt Bandit on 2007-12-08
Alright, awesome, but that only half worked. I can read the files, but I can't copy them off of the disc. Whenever I try to change a file's permissions, it crashes.

---

