---
title: "Why is firefox acting frenzy it is killing every site's font/image"
date: 2013-07-16
forum: General Help
---

### Post by amandatech on 2013-07-16
Hi I am using firefox 22 on ubuntu 13, I am seeing very small or very large fonts on every site, images on facebook are thrown out of box what should I do, 
I have installed msttfonts but it did not help me.  I am also using gnome desktop environment

please help me I am really frustrated.

[http://i.imgur.com/Ke4AkY0.png?1](http://i.imgur.com/Ke4AkY0.png?1)

---

### Post by BreezyBrooke on 2013-07-16
Lets try to fix the fonts. First install unity tweak tool.
```
sudo apt-get install unity-tweak-tool
``` 
Open the app, click on the fonts icon and change to your hearts content. I find if you put the fonts on the left side as 10pt, and the ones on the right side as 11pt, it makes for a nice, crisp look.

Also, adding the libfreetype ppa and updating your computer with it makes them look even better.
```
sudo add-apt-repository ppa:teppic74/freetype-latest && sudo apt-get update && sudo apt-get dist-upgrade
```
Don't worry, dist upgrade gives you the latest 13.04 packages, it dosen't upgrade to 13.10 like it suggests in the command.

---

