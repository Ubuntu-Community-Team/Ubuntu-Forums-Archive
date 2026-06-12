---
title: "kaffeine dualview help"
date: 2006-11-11
forum: General Help
---

### Post by 13ojo on 2006-11-11
hi,

i've got ubuntu installed.. well kubuntu + xubuntu anyway.

I've managed to get 2 xservers running, so i can mouse over to the other.

Here-in lies a problem.

I've managed to get my dtv tuner card working in Kaffeine, actually it was EASY! so easy it amazed me.

Thing is, i open kaffeine on the second display, (the TV), and make it go fullscreen, which is nice.

However if i move back onto the primary screen, for web browsing etc, it brings up the horrid kaffeine controls on the top and the bottom, and it doesnt go away till the mouse is over it.


How can i stop this?

---

### Post by 13ojo on 2006-11-12
anyone?

---

### Post by 13ojo on 2006-11-13
*cough*

---

### Post by Rede on 2006-11-13
I have the same problem, but there doesn't appear to be a fix. I'm going to try and get Kaffeine 0.7.1, since I don't want to have to deal with that.

---

### Post by 13ojo on 2006-11-15
whats special about kaffeiene 0.7.1?

---

### Post by esplinter on 2007-04-04
I have the same problem with kubuntu edgy and kaffeine 0.8.3

no solutions?? :confused:

---

### Post by esplinter on 2007-04-06
I have found a solution in order to watch full screen videos on TV.

Im using kmplayer with xine-engine and added this servicemenu in $HOME/ .kde/share/apps/konqueror/servicemenus/displayontv.desktop

[Desktop Entry]
Actions=PlayOnTV
Encoding=UTF-8
ServiceTypes=video/*

[Desktop Action PlayOnTV]
Exec=kmplayer --display :0.1 %F
Name=Play on TV
Icon=kaffeine


so when I want to watch a video on TV I just have to right click on it, an go to actions >> play on TV

the only "problem" is that I havent found the way to launch kmplayer in fullscreen mode from command line so once the video has started playing I have to double click on it to get full screen.

---

