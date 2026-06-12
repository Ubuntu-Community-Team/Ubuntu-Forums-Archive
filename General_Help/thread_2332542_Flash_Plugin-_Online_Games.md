---
title: "Flash Plugin- Online Games"
date: 2016-08-01
forum: General Help
---

### Post by sasafrass452 on 2016-08-01
Some web games I used to play require the newest version of the flash plugin. I know that linux is no longer supported by adobe other than security updates. Is there an alternative that will allow the games to work?

---

### Post by QDR06VV9 on 2016-08-01
Try This:
```
sudo apt-get install pepperflashplugin-nonfree
sudo update-pepperflashplugin-nonfree --install
```
And what browser are you using?

---

### Post by sasafrass452 on 2016-08-01
Apparently, that's for chrome only. I use Firefox. Any suggestions?

> **runrickus said:**
> Try This:
```
sudo apt-get install pepperflashplugin-nonfree
sudo update-pepperflashplugin-nonfree --install
```
And what browser are you using?

---

### Post by QDR06VV9 on 2016-08-01
> **sasafrass452 said:**
> Apparently, that's for chrome only. I use Firefox. Any suggestions?
Not just for Chrome I have Seamonkey with this version of Flash "You have version 22,0,0,209 installed"
But I just do not use firefox and completely uninstall it.
Have a look here to install Freshplayer and if installed correctly you will or should see the same version I show.
[http://www.pcworld.com/article/2993902/browsers/how-to-get-the-latest-version-of-flash-on-firefox-for-linux-after-adobes-abandonment.html](http://www.pcworld.com/article/2993902/browsers/how-to-get-the-latest-version-of-flash-on-firefox-for-linux-after-adobes-abandonment.html)

---

### Post by sasafrass452 on 2016-08-01
Well, I tried it, but it didn't work. Maybe I did something wrong? HELP!

> **runrickus said:**
> Not just for Chrome I have Seamonkey with this version of Flash "You have version 22,0,0,209 installed"
But I just do not use firefox and completely uninstall it.
Have a look here to install Freshplayer and if installed correctly you will or should see the same version I show.
[http://www.pcworld.com/article/2993902/browsers/how-to-get-the-latest-version-of-flash-on-firefox-for-linux-after-adobes-abandonment.html](http://www.pcworld.com/article/2993902/browsers/how-to-get-the-latest-version-of-flash-on-firefox-for-linux-after-adobes-abandonment.html)

---

### Post by QDR06VV9 on 2016-08-01
What dose this report from the terminal
```
apt-cache policy adobe-flashplugin
```

Paste back here.
And did you restart Firefox?

---

### Post by sasafrass452 on 2016-08-01
Ok, I had some other plugins installed, in an attempt to make the games work. I also had the old flash installed. I removed them all, leaving an up to date version of flash, & now the games work!!! Thanx for your help!!!

---

### Post by QDR06VV9 on 2016-08-01
Good to hear...enjoy:)

---

