---
title: "[SOLVED] totem-mozilla keeps crashing in firefox"
date: 2007-03-04
forum: General Help
---

### Post by unebaguettesvp on 2007-03-04
Hey!

I'm having problems with the totem-mozilla plugin in firefox. The video and sound play great in the beginning and then after a little bit of time has passed, I get this error:

Totem could not play 'file:///home/philip/.mozilla/firefox/uyjszwcv.default/Cache/14EB7BD5d01'.
The specified movie could not be found.

I can see the file in the Cache folder in the beginning of the streaming video and then it just disappears. Almost like it was moved somewhere else.

Has anyone seen this before?

Thanks in advance!

---

### Post by vince32 on 2007-03-04
**[FONT="Arial Black"][/FONT]**

I am so tired of firefox working and not working. Totem is not ready for a default media player. I put these repos in  my /etc/apt/sources.list long eneough to apt-get Mozilla-Iceape browser suite. 

deb [http://security.debian.org/](http://security.debian.org/) etch/updates main
deb-src [http://security.debian.org/](http://security.debian.org/) etch/updates main

deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch main
deb-src [http://www.debian-multimedia.org](http://www.debian-multimedia.org) etch main

Remember to disable these once you apt-get Iceape.

Now I have no trouble playing my internet media. Wmv files use mplayer has default not totem.   I am using feisty.

Works for me

Vince32

---

### Post by unebaguettesvp on 2007-03-04
playing wmv files is another problem i have because i am using amd 64 bit architecture.

thanks for the help.

has anyone else seen this problem?

---

### Post by unebaguettesvp on 2007-03-04
fixed it!

it was my cache in firefox. i set it to 1 MB. i changed it to 250 MB and it's working now.

---

