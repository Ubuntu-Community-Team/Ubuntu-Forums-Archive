---
title: "quick time"
date: 2007-07-06
forum: General Help
---

### Post by zig1234 on 2007-07-06
how do install quick time in ubuntu.

---

### Post by bodhi.zazen on 2007-07-06
See this link : [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by eggdeng on 2007-07-06
You don't, because Apple don't want you to. You can however install MPlayer and the mplayer plug-ins which will enable you to view .mov videos. [http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)

---

### Post by zig1234 on 2007-07-06
all right i found that page i need to know if my pc is AMD or power pc to get the download to work it is a dell dimension.

i thought it was amd but when i download the status says the architecture is wrong plz help

---

### Post by eggdeng on 2007-07-06
```
cat /proc/cpuinfo
```
If it's a Dell it will be either Intel or AMD. ```
uname -a 
``` if you need to know which kernel you are using. If you want to go for the quick fix, just download and install Automatix2 ```
sudo apt-get install automatix2
``` and install mplayer, the extra codecs and the mplayer plugin from there.

---

