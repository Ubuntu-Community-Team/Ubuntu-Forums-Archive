---
title: "Switching between different languages."
date: 2008-06-12
forum: General Help
---

### Post by OldAlgis on 2008-06-12
Hi,

In the past I used KDE, including kubuntu.  Because of the problems with a laptop, I now installed ubuntu 8.04 with the default gnome desktop. It works surprisingly well, including the KDE applications that I have been accustomed to.

One feature that I can not find in ubuntu gnome desktop is an easy way to switch between different keyboard layouts, in particular between the English and the Lithuanian keyboard layouts.  As Lithuanian does use the "Latin" script with some unique phonetic symbols, the ease of switching is important.

It is easy to do that with KDE, but how do I install KDE on top of ubuntu desktop?

Alternatively, is there an easy way to do this with ubuntu gnome desktop?

Many thanks to many people who share their knowledge and give their time in this forum so generously.

---

### Post by zvacet on 2008-06-12
You can install KDE on top of GNOME with 

```
sudo aptitude install kubuntu-desktop
```

but easier solution is to** right click on panel>add to panel>keyboard indicator>and under groups change keyboard layout**.

---

### Post by housam on 2008-06-12
If you can connect the Internet through the live cd , do sys>> admin. >> language support .it'll download / install the language package.

If not , boot normally and connect to the Internet and then do sys. >> admin. >> software sources . this will download the univers and the multivers packages. then do sys>> admin. >> language support . this will download the languages you need  among other languages. tick the square in front of these languages to start installing them.

after that go for the upper panel and right click >> add to panel >> utilities >> keyboard indicator.>> add.

after that you will find a word 'USA' appears on the panel. right click on it >> keyboard preference >> layouts >> add >> your languages.
this will ease the switch between languages during writing.

Good luck

---

### Post by OldAlgis on 2008-06-12
> **zvacet said:**
> You can install KDE on top of GNOME with 

```
sudo aptitude install kubuntu-desktop
```

but easier solution is to** right click on panel>add to panel>keyboard indicator>and under groups change keyboard layout**.

"zvacet", thank you for pointing me in the right direction. I did choose the easier option, after looking at the reply by "housam".
> **housam said:**
> 
(snip...) 
..Go for the upper panel and right click >> add to panel >> utilities >> keyboard indicator.>> add.

after that you will find a word 'USA' appears on the panel. right click on it >> keyboard preference >> layouts >> add >> your languages.
this will ease the switch between languages during writing.
Good luck

A big thank you to "housam" who gave nicely detailed answer. GUI is allways so hard to document - so much harder than CLI (Command Line Interface).

Having chosen the easy way, I am glad I have the instructions how to install KDE GUI, too.

The "easy way" of using ubuntu GUI works as well as GUI of KDE, with less "eye candy" but just as simply.  

Thank you, both gentlemen, "zvacet" and "housam" for your patience and time. And thank you for this ubuntu forum for being there!

---

