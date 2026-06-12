---
title: "general problems"
date: 2013-02-05
forum: General Help
---

### Post by s7c on 2013-02-05
hello there, i'm new to ubuntu world(12.10, 64-bits) and don't have any background into the field but being sick of windows i decided to give it a try...for my pleasant surprise i was able in last 3 weeks to make it work most of my windows programs.  but i experience so problems which i will try to describe them below and hopefully with your help i will solve them:

1-being a soccer fan i watch champions league and i didn't find a way yet to do that using ubuntu. most of the sites requires internet explorer browser and sopcast in order to be able to access the video.so i've installed IE8 through wine and of course sopcast too but i still can't make it work using the sites i know, or i get that some player is missing or it says i still need to install sopcast which is running ok or on other site where i need to download like a toolbar with channels i get "MIME Type: application/x-msdownload description: Unknown". 

2-i installed iTunes using this link: [http://freshtutorial.com/install-itunes-ubuntu-linux/](http://freshtutorial.com/install-itunes-ubuntu-linux/) but it's working somehow like in a demo version and is not at his full cappacity, not being able to acces my iphone if it is recognize it. 

3-i didn't found a driver to be able to use finger scanning for my lenovo ThinkPad and i didn't found the right way to install the Brother scanner even i didn't found problems in installing the driver for printer.

4-for some reason sometimes when i use netflix or i open some youtube videos for example it doesn't seems to work, somehow the frames are not coming example like it should but fater i while or maybe if i reload verithing it seems to work. it found that strange...

k, that's all for now :)

---

### Post by dcottingham on 2013-02-05
Lot of issues here. Just to pick one out to get started, I found this post at a forum at Lenovo's website:
[http://forums.lenovo.com/t5/Linux-Discussion-Knowledge-Base/Configuring-Fingerprint-reader-in-Linux-Thinkpad-General/ta-p/522271]("http://forums.lenovo.com/t5/Linux-Discussion-Knowledge-Base/Configuring-Fingerprint-reader-in-Linux-Thinkpad-General/ta-p/522271")
You could see if that helps.

---

### Post by lovevn on 2013-02-05
You can try following guide to install Sopcast:
- Add ppa:  
```
 sudo add-apt-repository ppa:ferramroberto/sopcast
```
- Update and install:
```
 apt-get update 
```
```
 sudo apt-get install sopcast-player sp-auth 
```
then use :popcorn:


You can see here: [http://ubuntuforums.org/showthread.php?t=154454](http://ubuntuforums.org/showthread.php?t=154454)

---

### Post by QIII on 2013-02-06
s7c

If you get back to this, it might be worth your while to have a look at [this]("https://help.ubuntu.com/community/PPA") for some explanation of PPAs.

---

### Post by s7c on 2013-02-06
> **dcottingham said:**
> Lot of issues here. Just to pick one out to get started, I found this post at a forum at Lenovo's website:
[http://forums.lenovo.com/t5/Linux-Discussion-Knowledge-Base/Configuring-Fingerprint-reader-in-Linux-Thinkpad-General/ta-p/522271](http://forums.lenovo.com/t5/Linux-Discussion-Knowledge-Base/Configuring-Fingerprint-reader-in-Linux-Thinkpad-General/ta-p/522271)
You could see if that helps.
thank you it seems it works, i got a message though like the key ring didn't get unlocked and i had to enter my password after. not sure what that means but i look further to fix it.

---

### Post by s7c on 2013-02-06
> **lovevn said:**
> You can try following guide to install Sopcast:
- Add ppa:  
```
 sudo add-apt-repository ppa:ferramroberto/sopcast
```- Update and install:
```
 apt-get update 
``````
 sudo apt-get install sopcast-player sp-auth 
```then use :popcorn:


You can see here: [http://ubuntuforums.org/showthread.php?t=154454](http://ubuntuforums.org/showthread.php?t=154454)
hi there, i did that already successfully as i said. but my problem is i still can't access those sites for some reason.

---

### Post by s7c on 2013-02-06
> **QIII said:**
> s7c

If you get back to this, it might be worth your while to have a look at [this]("https://help.ubuntu.com/community/PPA") for some explanation of PPAs.
;-)

---

### Post by travalon on 2013-02-07
Try replacing itunes with Amorak

---

### Post by s7c on 2013-02-08
> **travalon said:**
> Try replacing itunes with Amorak
thank for the idea but i don't need the iTunes necessary for music, i use it for i use it more for iPhone backup and stuff like that...

---

### Post by s7c on 2013-02-11
any other ideas mainly to solve point 1 of my requests? if not i will need to reinstall W...

---

### Post by Bufeu on 2013-02-11
> **s7c said:**
> any other ideas mainly to solve point 1 of my requests? if not i will need to reinstall W...
You can't run Windows applications on a Linux-based OS. Linux does not use DLLs.

---

### Post by s7c on 2013-02-13
ok, i tried to install w7 but it seems like i can't when i already have ubuntu installed. windows needs to be the boss and in order to install i need to format my hard ntfs and of course lose ubuntu ...this stuff is getting better and better.

---

