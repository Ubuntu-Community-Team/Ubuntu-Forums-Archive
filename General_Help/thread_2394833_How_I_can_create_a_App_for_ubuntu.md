---
title: "How I can create a App for ubuntu?"
date: 2018-06-22
forum: General Help
---

### Post by 123highland on 2018-06-22
hello I am new here I would like create a App for ubuntu I would like create a Calculate simple before of create this question I was reach about this theme and I found this video : [https://www.youtube.com/watch?v=sO8hiPreNBg5](https://www.youtube.com/watch?v=sO8hiPreNBg5)


but i did not understand anything , any could help me or orient me about the development of app for ubuntu main?

---

### Post by dragonfly41 on 2018-06-22
Unfortunately the first tutorial you selected (date 2012) refers to an obsolete package - Quickly.

It will be a gamble recommending a starter pack for you since there are many to choose from and much depends on your future plans and your current level of knowledge.

However I will suggest that you try Qt5 community version.

[https://www.qt.io/](https://www.qt.io/)

and later [https://riverbankcomputing.com/software/pyqt/intro](https://riverbankcomputing.com/software/pyqt/intro)

After installation you will see under Programming the launcher Qt Creator.

This is a GUI for designing the layout of your app.  There are examples given in the installation.

---

### Post by deadflowr on 2018-06-22
It takes a long journey to get an app into Ubuntu main or any of Ubuntu's repositories.
[https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages]("https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages")

In the mean time you can either create snap packages:
[https://docs.snapcraft.io/snaps/intro]("https://docs.snapcraft.io/snaps/intro")
[https://tutorials.ubuntu.com/tutorial/create-your-first-snap#0]("https://tutorials.ubuntu.com/tutorial/create-your-first-snap#0")
[https://docs.snapcraft.io/build-snaps/]("https://docs.snapcraft.io/build-snaps/")
[https://docs.snapcraft.io/build-snaps/your-first-snap]("https://docs.snapcraft.io/build-snaps/your-first-snap")
(These, as shown in the docs linked, can be published and would then be available to other users almost instantaneously.)

or create PPAs:
[https://help.launchpad.net/Packaging/PPA]("https://help.launchpad.net/Packaging/PPA")

---

### Post by diegogermangonzalez on 2018-06-22
> **123highland said:**
> hello I am new here I would like create a App for ubuntu I would like create a Calculate simple before of create this question I was reach about this theme and I found this video : [https://www.youtube.com/watch?v=sO8hiPreNBg5](https://www.youtube.com/watch?v=sO8hiPreNBg5)


but i did not understand anything , any could help me or orient me about the development of app for ubuntu main?

It all depends on the programming language you choose
A good alternative is Builder, the GNOME application builder. You can install it from the Software Center
Then you can create the snap package by following the tutorial that you were told in the previous post

---

