---
title: "I have a font problem"
date: 2017-06-01
forum: General Help
---

### Post by bask185 on 2017-06-01
I am using a 16.04 Ubuntu PC to build a Qt application. Last week I finished the translation part of my assingment. The application can also succesfully make  Chinese and Thai translations.

Problem: I am cross-compiling this app for the Raspberry Pi 3, and she does not want to learn to learn Chinese or Thai. 

I found the folder in which the application picks it's fonts.

 /usr/local/qt5pi/lib/fonts

If I remove all but one font in that folder, the app takes over that font. And the app has no text at all when this folder is empty. The folder contains the dejavu fonts. I do not know how the app picks which font out of that folder, it does not simply pick the top one. I also cannot tell if the app picks a different font out of the folder when one is incomplete.

I am looking for suitable Chinese and Thai Fonts which I can put in that folder. Preferbly I'd like a one single font file which has a symbol for about every possible UTF-8 code.

Which fonts should I get?

---

