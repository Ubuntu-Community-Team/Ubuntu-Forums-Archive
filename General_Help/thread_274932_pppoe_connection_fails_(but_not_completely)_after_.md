---
title: "pppoe connection fails (but not completely) after c.a. 30 minutes"
date: 2006-10-10
forum: General Help
---

### Post by cap_gemo on 2006-10-10
Hello, everybody!

  First of all, thanks for your great work on Ubuntu! I tried a lot of distributives: SuSe, Mandrake, Debian, etc., but I only liked Ubuntu.

  The only problem that I have with Ubuntu is my Internet connection. I have a normal ADSL, configured by pppoeconf. And it really works pretty good, but...

  For example, if I chat with people in Gaim-Messenger for a long time, not using other internet-soft, and then after about 30 minutes I open a browser, I can't open any website. It sais, I'm not connected to the internet.

  What I need to do in this situation is poff -a and then again pon dsl-provider. It really sucks. And in another half an hour - the same story.

  What also surprises me, is that even after I use poff -a in this situation, my Gaim is still connected! And I can send messages and receive them!

  Please help me!

  thank you

---

### Post by cap_gemo on 2006-10-12
Someone told me, it could also happen because of the internet-provider. I'm in Germany and my provider is NEFkom. Did anyone have also such problems with this provider?

---

### Post by xbadger on 2007-02-12
Hello man! Finally a post i've searched! I have the same problem! The problem is bought Ubuntu and your provider. Your provider maybe changed the dns verry quickly and pppd can't respond.
Try this;
sudo ifdown eth0
sudo ifup eth0
sudo pppoeconf

It worked for me. I think we should modify something in /etc/ppp/pppoe_on_boot.sh
Maybe someone will give us a good answer.
Cheers!

---

### Post by cap_gemo on 2007-03-03
Say, thanks! I've tried it and it works. Thank you again!

---

### Post by zvacet on 2007-03-03
[http://ubuntuforums.org/showthread.php?t=239815&highlight=rp-pppoe]("http://ubuntuforums.org/showthread.php?t=239815&highlight=rp-pppoe")

---

