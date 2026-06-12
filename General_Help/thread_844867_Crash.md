---
title: "Crash"
date: 2008-06-30
forum: General Help
---

### Post by carl_pr on 2008-06-30
I just installed ubuntu, i didnt knew it was so easy. I was thinking i was going to had a bad time updating and finding drivers but it find the nvidia drivers automatically and updates. Its great.

The only issue im having is that after a hour or two some programs start to mess up (happen with firefox and totem player) they crash and after a while i cant click or do anything. The screen freeze. I dont know the cause. Ive been using only firefox and pidgin.

---

### Post by iaculallad on 2008-06-30
> **carl_pr said:**
> I just installed ubuntu, i didnt knew it was so easy. I was thinking i was going to had a bad time updating and finding drivers but it find the nvidia drivers automatically and updates. Its great.

The only issue im having is that after a hour or two some programs start to mess up (happen with firefox and totem player) they crash and after a while i cant click or do anything. The screen freeze. I dont know the cause. Ive been using only firefox and pidgin.

With your Firefox, are you trying to open web pages loaded with flash files?

---

### Post by carl_pr on 2008-06-30
> **iaculallad said:**
> With your Firefox, are you trying to open web pages loaded with flash files?


yea, right now i was trying to watch a video on youtube and firefox crashed. 

By the way is there something like windows ctrl + alt + del in case i cant restart ubuntu by clicking in the power icon?

---

### Post by iaculallad on 2008-06-30
> **carl_pr said:**
> yea, right now i was trying to watch a video on youtube and firefox crashed. 

By the way is there something like windows ctrl + alt + del in case i cant restart ubuntu by clicking in the power icon?

Try to use GNASH instead of Adobe's proprietary flash. It's available in the repo.

```
sudo apt-get install gnash
```

For the Ctrl+Alt+Del key combo, try pressing Alt+F2 and input "gnome-system-monitor" (w/o the double quote) and press enter. That would launch the System Monitor application where you can kill unresponsive processes/apps.

---

### Post by katiad on 2008-06-30
> **carl_pr said:**
> By the way is there something like windows ctrl + alt + del in case i cant restart ubuntu by clicking in the power icon?


Another helpful key combination is ctrl + alt + backspace. This will kill and restart X, the graphic windowing system. Sometimes, when a freeze happens, this will solve your problems without having to do a hard reboot.

---

### Post by carl_pr on 2008-06-30
ok thanks that ctrl alt <-- is going to be helpful.


This happened again, i was installing some open office things then while i waited i put a dvd. totem player crashed. i intalled amarok and when i open it it crashed. Then i enter a dvd with backup things like pictures and the window crashed. Then the whole screen froze and i cant even use ctrl alt F2. havnt try yet with backspace.


This usually happen after a few hours of logging in ubuntu.

---

