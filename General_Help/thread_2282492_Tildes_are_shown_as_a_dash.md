---
title: "Tildes are shown as a dash"
date: 2015-06-14
forum: General Help
---

### Post by Shiryu on 2015-06-14
With most fonts, when the size is less than 11, tildes (ã &#7869; &#297; õ &#361; ñ) are shown as a dash. Consequently, I cannot distinguish tilde (ã) from macron (&#257;).

This problem occurs on Firefox (tildes are dashes on Gmail), but it does not occur on Libre Office using the same fonts and the same size. Furthermore, this problem does not occur on Firefox on another distro.

I am using Lubuntu 14.04.

---

### Post by llamabr on 2015-06-14
Patient: Doctor, doctor, it hurts when I do this
Doctor: Well, don't do that.

How about you keep your font size greater than 11?

---

### Post by Shiryu on 2015-06-14
The font size is defined by the web page that I load, therefore I cannot change it.

---

### Post by Holger_Gehrke on 2015-06-15
> **Shiryu said:**
> The font size is defined by the web page that I load, therefore I cannot change it.

Actually, you can. ctrl-+ to enlarge, ctrl-- to reduce and ctrl-0 (thats zero, not capital 'o') to reset. Additionally you could set up a user css file for your browser to override settings on web pages, but that's probably overkill ...

---

### Post by Shiryu on 2015-06-18
This is a known bug:
[https://bugs.launchpad.net/ubuntu/+source/freetype/+bug/839189](https://bugs.launchpad.net/ubuntu/+source/freetype/+bug/839189)
[https://bugs.launchpad.net/ubuntu/+source/freetype/+bug/655619](https://bugs.launchpad.net/ubuntu/+source/freetype/+bug/655619)

It is partially improved by deleting all files with "10-hinting" in the name located in /etc/fonts/conf.d/ and adding a file with the following content:
> 
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<match target="font">
 <edit name="hinting" mode="assign">
  <bool>true</bool>
 </edit>
 <edit name="autohint" mode="assign">
  <bool>false</bool>
 </edit>
 <edit name="hintstyle" mode="assign">
  <const>hintfull</const>
  </edit>
</match>
</fontconfig>

---

