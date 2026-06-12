---
title: "wx not displaying nicely"
date: 2005-10-31
forum: General Help
---

### Post by pickarooney on 2005-10-31
I'm trying to install the necessary components for, amongst other, bittornado, which uses wxWindos/wxWigets. The program runs, but the UI is all an ugly, dull grey with badly-formed fonts. I installed everything I could find using sudo apt-cache search wx but no luck.

---

### Post by pickarooney on 2005-10-31
Strangely, xMule looks terrible (grey with crappy fonts) while aMule looks normal. If anyone knows the basic difference between the GUIs of these programs, it might help me find what's missing.

---

### Post by pickarooney on 2005-11-01
I was missing wxcommon, but after installing it and running bittornado again, the display is still wrong. I have a feeling I had the same problem when I first installed it (and xMule) on mandrake, but can't remember how I fixed it. :(

---

### Post by temcat on 2005-11-01
[QUOTE=pickarooney]I'm trying to install the necessary components for, amongst other, bittornado, which uses wxWindos/wxWigets. The program runs, but the UI is all an ugly, dull grey with badly-formed fonts. I installed everything I could find using sudo apt-cache search wx but no luck.[/QUOTE]

AFAIK these UI problems are not "fixable" currently, because for some reason devels started recently to compile wxWidgets against GTK+ 1.2 ("ugly, dull grey with badly formed fonts") and not GTK+2 (nice look with beautiful antialiased fonts).

---

### Post by pickarooney on 2005-11-01
[QUOTE=temcat]AFAIK these UI problems are not "fixable" currently, because for some reason devels started recently to compile wxWidgets against GTK+ 1.2 ("ugly, dull grey with badly formed fonts") and not GTK+2 (nice look with beautiful antialiased fonts).[/QUOTE]

Do you mean the people who make the .deb packages for Ubuntu compile them against GTK1.2? If so, would compiling from source be a better option?
(I know there's nothing wrong with the actual code of the programs, as I've had them display correctly on my previous system.)

Unfortunately it seems Ubuntu ships without even the most basic tools for compiling, which is a mystery to me, considering all the extra bells and whistles it does have.

BTW, if anyone has an easy guide to installing the tools necessary for compiling from source, I'm all ears :)

---

### Post by bored2k on 2005-11-02
BitTornado can be fixed. Install python 2.6 libs and use the source package.

---

### Post by pickarooney on 2005-11-02
[QUOTE=bored2k]BitTornado can be fixed. Install python 2.6 libs and use the source package.[/QUOTE]

Works, thanks :)

---

