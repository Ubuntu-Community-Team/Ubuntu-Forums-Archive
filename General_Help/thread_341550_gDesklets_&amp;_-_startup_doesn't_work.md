---
title: "gDesklets &amp; - startup doesn't work"
date: 2007-01-18
forum: General Help
---

### Post by keka on 2007-01-18
Hi, I was wondering if anyone knows what could be the problem of gnome not loading gDesklets at start up.

I used "gdesklets" "gdesklets &" in Sessions, startup.
It works fine when I open it from Accessories. Thanks for your help

---

### Post by MetalMusicAddict on 2007-01-18
Odd. **gdesklets** should be fine. What version of Ubuntu are you using?

---

### Post by keka on 2007-01-18
Ubuntu Edgy, I even see it loading in Splash screen

---

### Post by Dusty545 on 2007-01-18
I've been having the exact same problem myself and have been trying to find a workaround (yes, I know I should have posted).

If I find a workaround I'll post it up.

---

### Post by Heelix on 2007-02-19
any news? i am also experiencing this problem of gDesklets not registering with session. i have  also tried "gdesklets start". 

when i add it to sessions i can see it added to the list, but if i the close sessions and restart it the added command is no longer there.

(gdesklets works fine if started manually)

---

### Post by jongkind on 2007-02-19
Starting Desklets via this script may help:

#! /bin/bash
sleep 5
gdesklets start &

You can run this scrip via sessions-startup.

---

### Post by gkokaisel on 2007-03-03
to run gDesklets at start up:

Go to System > Preferences > Sessions

then

from Startup Programs tab click the add button

then Browse to File System > usr > bin > gDesklets

then click open button
then click close
then ctrl + alt + backup if you want to make sure it worked

---

