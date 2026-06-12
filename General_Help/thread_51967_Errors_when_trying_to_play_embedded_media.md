---
title: "Errors when trying to play embedded media"
date: 2005-07-25
forum: General Help
---

### Post by zarathustra on 2005-07-25
I get this error message pop up:

> Totem could not play 'fd://0'.

No URI handler implemented for "fd://0"

No idea what it means :(

---

### Post by Xian on 2005-07-25
It sounds like you need some codecs but hard to say which ones based on the information provided. You could start by making sure that you have the totem-xine pkg installed.

---

### Post by zarathustra on 2005-07-25
[QUOTE=][/QUOTE]
 I have all the required codecs installed, as well as totem-xine.

---

### Post by foolosophy on 2005-12-08
Hey, I just had the same problem, when trying to listen to a radio programme over the net (firefox). I have the latest java, and I guess I have all the audio codecs needed. Were you able to solve the issue? (Since your post is from march...)
-------------------------
EDIT:I got it working.. i updated Java plugin for firefox, and also installed totem-xine pkg.

Still.. the audio (a .wma) wouldn't start embedded in firefox. My solution: I opened the source code of the webpage (ctrl+U) and found the .wma source. I copied that link (something that started with a "mms://") and opened with totem (as an url).

---

