---
title: "batch permissions change"
date: 2007-10-14
forum: General Help
---

### Post by mikeize on 2007-10-14
trying to get my wife acclimated to ubuntu, and we plugged her ipod in, and setup amarok to use it.  While trying to edit tags on her songs/albums, we got permission errors.  She has a huge collection of music, so how can I change the owner and/or permissions for every song in every folder in /home/hername/Music directory?  I've tried gksudo nautilus to change folder permissions, but it doesn't effect the files within.  I even tried selecting all files w/in a folder, but I can't change owners/users that way.  Somebody spare the code?

-mike

---

### Post by geirha on 2007-10-14
```

sudo chown -R hername /home/hername/Music   # hername will own all directories and files inside and including the Music dir
sudo chgrp -R somegroup /home/hername/Music # somegroup have group ownership on all files and dirs
sudo chmod -R ug+rw /home/hername/Music     # owner and group will have read and write access
```

The commands are explained in detail in their man-pages. so do ```
man chown
man chgrp
man chmod
```
to see what more you can do

---

### Post by mikeize on 2007-10-14
Excellent, thank you very much!  I did like you said, and tested some files...  it works.  I'll try to remember this trick, as I'm sure I'll need it again!

-mike

---

