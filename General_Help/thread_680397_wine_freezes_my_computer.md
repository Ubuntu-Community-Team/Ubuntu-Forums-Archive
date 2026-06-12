---
title: "wine freezes my computer"
date: 2008-01-27
forum: General Help
---

### Post by ToeToe on 2008-01-27
When I try to run any of the wine features my computer completely freezes.  I'm using wine v0.9.56 and Ubuntu 7.10. I used the instructions on this site to install it. [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
If anyone knows why it might be doing that please let me know. I'm still a newb to Ubuntu though. I just know the bare basics pretty much. I kinda know how to use terminal though. Any help is appreciated.

---

### Post by Greg T. on 2008-01-27
Wine tends to suffer from more than its share of regressions. You could try downgrading to an earlier version (I'm using 0.9.46).

You also can try [wine-doors]("http://www.wine-doors.org") to help automate some of the setup hassles that are otherwise involved with Wine. 

At the least, I suggest deleting (or renaming) your .wine folder in your home directory, as this will eliminate any problematic configuration changes you may have made.

---

### Post by ToeToe on 2008-01-27
Thanks I'm going to try and use the wine door you just said but the thing with deleting the wine folder is i can't find anywhere. Yeah that might be why it doesn't work.

---

### Post by steveneddy on 2008-01-27
It's a hidden folder in your /home.

Open /home and hit** ctrl + H**

to show hidden files.

It will be .wine - notice the (.) before wine - means a hidden file.

:popcorn:

---

### Post by ToeToe on 2008-01-27
ok thanks i didn't think there was hidden folders in ubuntu. I tried to use the wine door and that locked up my computer too.

---

### Post by ToeToe on 2008-01-27
so should i delete all of the .wine folders or just .wine.

---

