---
title: "outputting to a tv?"
date: 2007-07-27
forum: General Help
---

### Post by ELD on 2007-07-27
Hi just wondering how exactly in ubuntu you can get the output from my laptop onto my tv, my brother can do it on his under vista, just wonderinf if it ispossible in ubuntu?

---

### Post by tgm4883 on 2007-07-27
> **ELD said:**
> Hi just wondering how exactly in ubuntu you can get the output from my laptop onto my tv, my brother can do it on his under vista, just wonderinf if it ispossible in ubuntu?

Do you have some sort of TV out port (ie svideo).

---

### Post by ELD on 2007-07-28
Yes i have the port, and connected it all up exactly how my bro does with his vista laptop, do i need a program for ubuntu to do it?

---

### Post by MrHippocampus on 2007-07-28
The first thing to find out is what graphics card you are using and what driver. The instructions are different for each type of graphics card.

---

### Post by fragos on 2007-07-28
If you have an Nvidia chipset the package you want is nvtv from the Ubuntu repositories.

---

### Post by mykrob on 2007-07-28
what about intel video?

---

### Post by ELD on 2007-07-30
I have integrated intel stuff?

---

### Post by mykrob on 2007-08-01
sorry, i was asking about using the S-video out if you have integrated intel video. My laptop has this chipset.

---

### Post by sr20ve on 2007-08-01
I connect my laptop to my TV via a VGA cable. The one thing I found out when first hooking it up is that you have to have the TV connected when you start X.

So if you're connecting your TV and you're already logged into a session, just hit ctrl-alt-bkspc to start a new session and it should pick up the TV.

---

### Post by fragos on 2007-08-01
S-video uses a small round connector with pins inside it.  They are similar to the PS/2 connectors that have been used for mice and keyboards, but larger.  You may have one on your TV  or DVD player.  If you have that connector on your PC you're good to go.  Some HDTVs have VGA or DVI connectors and can be used as monitors.

---

