---
title: "how to install ms fonts into ubuntu 17.10"
date: 2018-03-14
forum: General Help
---

### Post by seekertom on 2018-03-14
I am using libreoffice 5 on ubuntu 17.10. I copied a folder called fonts from my xppc \windows to sd, then copied the folder with about 200 fonts into my downloads folder on my ubuntu pc.

How do I get them where they need to be so they show up in writer fonts list?

thanks! st

ps, just wondering howcome all my google search results for this how-to...  are ancient, 2011, - 2015 etc? am i the only one these days that hasn't figured it out?:confused:

pss fonts are .fon, .TTF, .ttf

---

### Post by kannanmanism on 2018-03-15
try installing "msttcorefonts" via terminal "sudo apt-get install msttcorefonts " or Synaptic Package Manager. 
Then ms fonts should work fine

---

### Post by kurt18947 on 2018-03-17
.ttf fonts can be installed two ways. If you want to only make the fonts available to a single user, you can create a .fonts folder in your home folder and copy the .ttf files there. If you want to make them available to all users, you can copy them to /usr/share/fonts. I have a few folders there - opentype, truetype, type1 and X11.

---

