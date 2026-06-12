---
title: "&quot;Different themes&quot; as root or user?"
date: 2007-10-30
forum: General Help
---

### Post by dmontalvao on 2007-10-30
Hi there!

I have a weird problem, that never happened to me neither on Feisty or Gutsy Beta. If I start an app as root, it will lose the theme config. If I start as a normal user, it is ok.

What's going on here? Is this a bug?

I send u 2 images of Nautilus. The first is run as user (nautilus) the other as superuser (gksudo nautilus).

Thank you for your help!
[IMG]http://ltodi.est.ips.pt/dmontalvao/Nautilusasuser.png[/IMG]
[IMG]http://ltodi.est.ips.pt/dmontalvao/Nautilusasroot.png[/IMG]

---

### Post by Thyme on 2007-10-30
I think you need to copy your "theme" and "icons" folders in you home directory to the "root" directory, cause when you run a program as root, that is its home.

Try making symbolic links so that your don't have to recopy the folders everytime you add a new theme or icons package:

Icons: sudo ln -s ~/.icons /root
Themes: sudo ln -s ~/.themes /root

Hope this works :)

---

### Post by dmontalvao on 2007-10-30
Lol Thyme! Is just that easy? It worked! :)

Thank u so much!

__________________________
A newb is always a noob! :D

---

### Post by Thyme on 2007-10-30
Yeah :) Sometimes we always seem to overlook the simple things ! Anyway man, glad got it soughted out :)

---

### Post by taisao on 2007-11-01
and what is needed if kde is used?

---

