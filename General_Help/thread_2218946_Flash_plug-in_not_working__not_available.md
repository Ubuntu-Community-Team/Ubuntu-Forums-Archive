---
title: "Flash plug-in not working / not available"
date: 2014-04-22
forum: General Help
---

### Post by Odense on 2014-04-22
I am running Ubuntu 14.04 LTS on a Samsung RV510.

The procudure Ubuntu suggests at the top of the warnings:
[https://wiki.ubuntu.com/Chromium/Getting-Flash](https://wiki.ubuntu.com/Chromium/Getting-Flash) is working

---

### Post by slickymaster on 2014-04-22
Linux Adobe Flash will stop working on Chromium because Chromium will soon stop using the Netscape Plugin API. To get Flash working in Chromium it's the pepperflashplugin what you have to install. To achieve it, just run the following in a terminal window:```
sudo apt-get install pepperflashplugin-nonfree
sudo update-pepperflashplugin-nonfree --install
```

---

