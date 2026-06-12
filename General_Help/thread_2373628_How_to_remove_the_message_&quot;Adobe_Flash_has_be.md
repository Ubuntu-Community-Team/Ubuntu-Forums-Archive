---
title: "How to remove the message: &quot;Adobe Flash has been blocked because it is out of date&quot;"
date: 2017-10-08
forum: General Help
---

### Post by aneblanc on 2017-10-08
A month ago I started getting the message "Adobe Flash has been blocked because it is out of date". I run Ubuntu 16.04 and Chromium. 
I checked Askubuntu. Someone has the same problem but (s)he di not get any answer: [https://askubuntu.com/questions/947363/ubuntu-16-04-3-chromium-get-rid-of-adobe-flash-player-was-blocked-because-it-wa](https://askubuntu.com/questions/947363/ubuntu-16-04-3-chromium-get-rid-of-adobe-flash-player-was-blocked-because-it-wa)
There is an option to run flash once: "Run this time" and it works very well.

Any idea what I should do?

---

### Post by deadflowr on 2017-10-08
What does your 
```
apt show adobe-flashplugin
```
show?

---

### Post by Impavidus on 2017-10-08
Or```
apt show flashplugin-installer
```depending on how you installed flash.

---

### Post by efflandt on 2017-10-08
If you installed it normally from the repos (flashplugin-installer) or restricted-extras, it probably means that your system is due for updates if you have not done that lately. Does your system automatically check for updates and do you do them? You should be able to find out which version you have from Firefox add-ons or using dpkg-query:```
~$ dpkg-query -l flash* | grep ii
ii  flashplugin-installer  26.0.0.137ubuntu0.16.10.1 amd64        Adobe Flash Player plugin installer
```OK I know that Ubuntu 16.10 is no longer supported, but I intend to do something about that soon. **Current flash version is 27.0.0.130**, see [http://get.adobe.com/flashplayer/about/](http://get.adobe.com/flashplayer/about/) for current flash version.

---

### Post by Yellow Pasque on 2017-10-08
What does this output?:
```
sudo update-pepperflashplugin-nonfree --status
```

If it shows mismatching vesion, try manually updating:
```
sudo update-pepperflashplugin-nonfree --verbose --install
```

---

