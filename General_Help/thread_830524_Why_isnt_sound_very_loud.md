---
title: "Why isnt sound very loud?"
date: 2008-06-15
forum: General Help
---

### Post by morbid_bean on 2008-06-15
When im trying to play music its not very loud... ill have the volume on the speakers all the way up...volume on the media player and volume on ubuntu.......and its at a litenable state but it just dosnt seem to go very loud....i have checked connections everything is ok.  Im using ubunut 8.04

---

### Post by shakabra on 2008-06-15
If you are using ALSA then open a terminal and type "alsamixer" without the quotes.  set all of those settings to 100% and that should fix your prob.  I don't know the command name in pulse but it shouldn't be hard to figure out on google.

---

### Post by windoze87 on 2008-06-16
do everything the previous poster recommended, except this: when you run alsamixer in terminal, DO NOT set PCM volume to 100%. If you ever go to crank your music and dance around while cleaning your house, you will most likely blow your speakers... i blew a fine quality set of Altec-Lansings when i used Windows by setting the PCM volume to 100. Set the PCM volume to 50% and everything else to 100% and you should be fine

---

### Post by morbid_bean on 2008-06-16
Did just that ...but nothing happens...anything else?

---

