---
title: "Font"
date: 2008-05-27
forum: General Help
---

### Post by andrecamp on 2008-05-27
Hello,

How do you install windows fonts on Ubuntu?
I just left Windows and I really need fonts because I was into graphical designing and stuff...

---

### Post by mano cazalet on 2008-05-27
hello you can install msttcorefonts package with Arial, Comic Sans MS, Courier, Times New Roman, etc

```
sudo apt-get istall msttcorefonts
```

and also check this couple of links:

[http://ubuntu.wordpress.com/2007/09/16/installing-vista-fonts-in-ubuntu/](http://ubuntu.wordpress.com/2007/09/16/installing-vista-fonts-in-ubuntu/)

[http://www.oooninja.com/2008/01/calibri-linux-vista-fonts-download.html](http://www.oooninja.com/2008/01/calibri-linux-vista-fonts-download.html)

[https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts)

[http://ubuntusite.com/fix-get-best-firefox-font-linux/](http://ubuntusite.com/fix-get-best-firefox-font-linux/)

---

### Post by andrecamp on 2008-06-01
All the other programs that come with Ubuntu have no font problems but Photoshop which is running through Wine can't seem to access the fonts. :S

What do I do?

---

### Post by andrecamp on 2008-06-05
Can someone PLEASE help. The wine programs can't access the fonts.

---

### Post by leemid on 2008-06-05
> **andrecamp said:**
> Can someone PLEASE help. The wine programs can't access the fonts.

I'm going to try this tomorrow so I'm not sure if it'll work. But... go to Applications -> Wine -> Browse C: Drive, and navigate to the windows\fonts\ folder and copy the font files there (these files are probably located at */usr/share/fonts/truetype*).

I'm guessing Photoshop will be able to use them. It's probably because Photoshop doesn't know it's running on Linux, so doesn't know where to look for the fonts you have installed.

Hope this works.
Lee

---

### Post by andrecamp on 2008-06-05
It still doesn't work. It says it can't find the default system font.

---

### Post by VMC on 2008-06-05
Here is a discussion on the subject, at Wine forums: 
[http://www.wine-forum.org/showthread.php?t=160](http://www.wine-forum.org/showthread.php?t=160)

---

