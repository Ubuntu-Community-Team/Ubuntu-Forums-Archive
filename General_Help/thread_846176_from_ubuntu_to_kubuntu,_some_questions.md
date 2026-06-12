---
title: "from ubuntu to kubuntu, some questions"
date: 2008-07-01
forum: General Help
---

### Post by chriskin on 2008-07-01
can i change from ubuntu to kubuntu without format? most probably the answer is yes but i need to know

can i keep the programms i already have? or will they not work perfectly?

will the 12 gbs i have for ubuntu be enough for kubuntu? if not, will the command to download the already installed programms work there? so i can move kubuntu to another disk

my brother had a problem moving files to desktop in kubuntu 8.04 (kde4 remix) is this "problem" universal or is it only on our desktop pc?

is the known problem of sound not coming out from headphones in ubuntu 8.04 while on laptops present on kubuntu as well?

excuse this river of questions, and thank you for any answers you might give :D

* also : is kubuntu worth it? i mean it definitely looks great but is your opinion positive or negative?

---

### Post by morbid_bean on 2008-07-01
you can always type  "sudo apt-get install kde" and it will install it in  your pc without loosing data and it will save all your programs...if you dont like it type "sudo apt-get remove kde"

---

### Post by chriskin on 2008-07-01
is having kde instead of gnome the same as having kubuntu instead of ubuntu?:confused:

---

### Post by morbid_bean on 2008-07-01
Yes, Kubuntu is kde, and ubuntu is gnome

---

### Post by aysiu on 2008-07-01
Last time I checked *apt-get* would not remove all the dependencies of the *kubuntu-desktop*, so *sudo apt-get remove kubuntu-desktop* would remove only an empty pointer package and not all the Kubuntu packages. I would advise you install with *aptitude* instead. Instructions for that are here:
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

Kubuntu is Ubuntu's implementation of KDE. It has particular default programs and Ubuntu artwork (wallpaper, splash screens, etc.) that go with it. If you want a "pure" KDE, you might want to install *kde* or *kde-core* instead of *kubuntu-desktop*.

---

