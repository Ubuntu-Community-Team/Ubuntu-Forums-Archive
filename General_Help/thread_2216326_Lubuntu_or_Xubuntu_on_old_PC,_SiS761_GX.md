---
title: "Lubuntu or Xubuntu on old PC, SiS761 GX?"
date: 2014-04-11
forum: General Help
---

### Post by POBRA on 2014-04-11
Hello,i'm a new user and I have one question.I have an old pc with this specs: **AMD Sempron 3000+ 1.8ghz,512mb ram DDR 160 mhz,40 gb HDD,SiS761 GX integrated graphics with 32mb of memory...And which lightweight system of ubuntu family ?? Lubuntu or Xubuntu ?** I already have **xfce desktop Mint 13 XFCE and very often its freeze...**Please answer and help me of course i'm waiting for LTS release of this systems...And one more thing,i'm still going to high school and live in Bosnia And Herzegovina so please sory about my langunage mistakes :D:D

---

### Post by sudodus on 2014-04-11
Welcome to the Ubuntu Forums :-)

I would recommend ***Lubuntu*** for your computer with only 512 MB.

See this link for more details about old hardware and tips about your SIS graphics chip.
[URL="http://ubuntuforums.org/showthread.php?t=2130640"]
Old hardware brought back to life[/URL]

---

### Post by sudodus on 2014-04-11
With a graphics chip or card from SIS then the installation of 13.10 goes like this:

Install a [minimal ISO]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall").
After a reboot run the following commands one at a time:

```
sudo apt-get install software-properties-common 
sudo add-apt-repository ppa:dtl131/mediahacks
sudo apt-get update
sudo apt-get install lubuntu-desktop
sudo reboot now 
```
Thanks to Temüjin for the fix.

14.04 installs without adding the PPA, but it is still being developed as 'Trusty Tahr'. It will be released during this month.

---

### Post by POBRA on 2014-04-11
> **sudodus said:**
> With a graphics chip or card from SIS then the installation of 13.10 goes like this:

Install a [minimal ISO]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall").
After a reboot run the following commands one at a time:

```
sudo apt-get install software-properties-common 
sudo add-apt-repository ppa:dtl131/mediahacks
sudo apt-get update
sudo apt-get install lubuntu-desktop
sudo reboot now 
```
Thanks to Temüjin for the fix.

14.04 installs without adding the PPA, but it is still being developed as 'Trusty Tahr'. It will be released during this month.
i didn't want 13.10 i want 14.04 and I waiting for that...Could I install 14.04 without these commands ?? just to download the installation of 700 or more megabytes(from lubuntu site) and install that??

---

### Post by sudodus on 2014-04-11
I did not try it with SIS graphics, but I would rely on the writer of those instructions.

-o-

It is simpler with Trusty.

You can get Trusty now, but it might to break on the path to the final release. If that is OK for you, welcome as a tester of the next Lubuntu version :-)

You get the current daily build of Lubuntu via this link

[http://iso.qa.ubuntu.com/qatracker/milestones/308/builds/66434/downloads](http://iso.qa.ubuntu.com/qatracker/milestones/308/builds/66434/downloads)

---

### Post by sudodus on 2014-04-11
I did not try it with SIS graphics, but I would rely on the writer of those instructions.

-o-

It is simpler with Trusty.

You can get Trusty now, but it might to break on the path to the final release. If that is OK for you, welcome as a tester of the next Lubuntu version :-)

You get the current daily build of Lubuntu via this link

[http://iso.qa.ubuntu.com/qatracker/milestones/308/builds/66434/downloads](http://iso.qa.ubuntu.com/qatracker/milestones/308/builds/66434/downloads)

---

