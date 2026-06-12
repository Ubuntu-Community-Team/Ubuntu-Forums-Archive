---
title: "QuoteTracker under wine"
date: 2007-04-10
forum: General Help
---

### Post by Mets on 2007-04-10
hey guys,

Right now the only program making me dual boot with Windows is QuoteTracker, a great stock charting program that is free.  I thought I'd try to get it to install it under wine on Ubuntu.  I have wine and winetools installed, along with Internet Explorer as required. The program installs and starts up, but it won't connect to a data stream.  I tried several streams, so basically it just isn't able to connect to the internet through wine.  It is also constantly trying to refresh itself to the point where it can get unreadable. Has anybody got this to work and if so how? I'm running Ubuntu 6.10.

-Mets

---

### Post by BillyBudd on 2007-04-27
I gave up trying to run QT under Wine and am now running it in an Innotek VirtualBox under Ubuntu Edgy.  Works well, though is a resource hog.  All QT features appear to work well.

If you run QT in VBox you need to make sure to shut down QT before you close the VBox XP machine, else sometimes the QT database will get scrambled.

---

