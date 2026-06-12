---
title: "Ubuntu 13.04 - sometimes can't make screenshot"
date: 2013-08-14
forum: General Help
---

### Post by dsmilgin89 on 2013-08-14
Hello,

I'm using ubuntu 13.04 x64 with unity. I have installed bumblebee support for my nvidia gf310m card. However when I try to make a screenshot (doesn't matter - shutter, default gnome utility, or even my own application in qt) sometimes i get blank file. When I get blank file once I must restart my system because I will be unable to make a proper screenshot. It's unrelated to screen capturing software.

Thank you for any help. (:

---

### Post by Gilad_Pellaeon on 2013-08-14
> **dsmilgin89 said:**
> Hello,

I'm using ubuntu 13.04 x64 with unity. I have installed bumblebee support for my nvidia gf310m card. However when I try to make a screenshot (doesn't matter - shutter, default gnome utility, or even my own application in qt) sometimes i get blank file. When I get blank file once I must restart my system because I will be unable to make a proper screenshot. It's unrelated to screen capturing software.

Thank you for any help. (:

Are you sure it's not saving a screenshot in PNG file format in your home directory? With Lubuntu 13.04 that I use when I hit the Print Screen key it takes a screenshot and saves it to a PNG file. Not sure if that's just Lubuntu specific or if it's like that with all the other *buntu distributions.

---

### Post by dsmilgin89 on 2013-08-14
Yes it saves the screenshot to png file in pictures folder, but as I mentioned sometimes the png file id empty. In my Application witch add an watermark to screenshot only watermark is visible in screenshot file. (;

---

### Post by Gilad_Pellaeon on 2013-08-14
> **dsmilgin89 said:**
> Yes it saves the screenshot to png file in pictures folder, but as I mentioned sometimes the png file id empty. In my Application witch add an watermark to screenshot only watermark is visible in screenshot file. (;

Maybe it's an issue with your video drivers? Because I don't think the screenshot file should be empty/blank.

---

### Post by dsmilgin89 on 2013-08-14
It didn't happened before - both on debian and fedora. So I doubt it is a video driver problem. (:

---

### Post by Habitual on 2013-08-14
I don't use bumblebee, but I do use scrot for "screenies"
I mapped a command ```
scrot -q 50 '/home/jj/Pictures/screenshots/PrintScreen_%m %d %T.png**'
```** to Print key.

HTH.

---

