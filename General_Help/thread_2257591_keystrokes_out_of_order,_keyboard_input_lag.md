---
title: "keystrokes out of order, keyboard input lag"
date: 2014-12-20
forum: General Help
---

### Post by fizikz on 2014-12-20
Since upgrading to Ubuntu 14.04LTS, sometimes when I type (eg, into search box or address bar of a browser), the input lags my typing and when it does finally appear on screen, there are several characters out of the order in which I typed them. The lag is not always present. 

Initially I thought I might be making a lot of typos, but no, it really does come out scrambled sometimes, and only when there is the lag between keystrokes and their appearance on screen. Any ideas how to fix this? It did not used to happen before on the same hardware (Asus G1 laptop), and it's highly irritating!

---

### Post by loki.verloren on 2015-02-25
i also have a similar problem though i haven't got as clear an idea which configuration might be causing it, but i have had this happen in 14.10 and also 15.04 beta particularly i think the gnome shell is the common factor. what appears to be happening is that keypresses, which i know from my beginning study of gtk/gdk/glib/etc programming that events are supposed to have timestamps and what is clearly happening is - there is always lag of about half a second between keypress and response, and sometimes, especially in the gnome shell clutter overview search, i can type perfectly normal speed for me (60-80wpm) but the order the characters come out can be completely out of order, i might type 'tweak' and it comes up with waket or something equally garbled. the lag is annoying, but tolerable, but getting keypress sequence out of order is intolerable. the problem is worse when the system is heavily loaded, particularly, for example, when tracker is on. i have not changed any deep settings particularly, there definitely seems to be some problem with keyboard input especially with event time sequencing when there is high latency. i haven't got any solutions. oh, it also happens quite bad especially in chromium, i think sometimes it is the biggest cause of high latency.

---

### Post by fizikz on 2015-02-25
I'm using gnome classic (no effects, metacity), so it's not specific to gnome shell.

---

