---
title: "Digikam5 hangs on creating slideshow list"
date: 2017-03-12
forum: General Help
---

### Post by Ralph L on 2017-03-12
I am running Xubuntu 16.04 with the latest updates.  I installed digiKam 4 from the normal 16.04 repository and digiKam5 (Version 5.4.0) from ppa:philip5/extra. I just updated my system so I should have the latest version of digiKam 5.4.0.  I cannot get digiKam5 to build a Slideshow List.  I go to Main menu>View>Slideshow>Presentation and select the "+" button to add photos from my albums.  This causes digikam to hang up and I must drop it or xkill it.  I am using an Sqlite database created under digiKam 4.  Does anybody know how to fix this problem??  Does anybody else have this problem with dgikam5?? DigiKam 4 works fine creating lists.

Any help appreciated......

---

### Post by Ralph L on 2017-04-01
DigKam 5.5.0 solved the problem.```
sudo add-apt-repository ppa:philip5/extra
sudo apt-get update
sudo apt-get install digikam5
```

---

