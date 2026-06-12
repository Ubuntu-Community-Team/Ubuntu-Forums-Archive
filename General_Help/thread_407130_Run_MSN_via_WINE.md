---
title: "Run MSN via WINE ?"
date: 2007-04-11
forum: General Help
---

### Post by Kizilbas on 2007-04-11
Hello how can I firstly install Wine and then install msn & run it in wine?
(I want the original msn, not amsn kmess or GAIM)

Can u show me from where to download & how to install wine & msn

& then run msn in wine


**_Cam driver + cam installation_**

Then after doing all that how can I use Wine to install my web camera drivers? The drivers and installation of the webcam is on a CD that came with my webcam.

The Webcam:

This is very urgent and must be done before 1am, please help me pls !
I thank everyone who helps me solve this from now on :)

---

### Post by machoo02 on 2007-04-11
To install Wine, I'd recommend the latest version:```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/edgy.list -O /etc/apt/sources.list.d/winehq.list
sudo aptitude update
sudo aptitude install wine
```
Replace edgy with dapper in the second line if you happen to be using it.

As for using the regular MSN in Wine, you might not have that much luck...check out its page at the [Wine AppDB]("http://appdb.winehq.org/appview.php?iAppId=127").  Why not use one of the native chat clients?

I can't help you with your webcam...try searching for the make/model here on the forums, or posting a little more information about it.

---

