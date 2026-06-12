---
title: "per user window manager"
date: 2007-05-17
forum: General Help
---

### Post by dunkyp on 2007-05-17
is it possible to set the default window manager for each user i.e Bill has iceWM, Nancy has GNOME and Andy has KDE. As opposed to choosing the session at login:)

---

### Post by Psicolonia on 2007-05-17
I'd like that too... even though i'm the only user of my machine that may change so... that would be nice...

---

### Post by aysiu on 2007-05-17
Use KDM for your display manager instead of GDM

---

### Post by dunkyp on 2007-05-17
I'll give it a shot thanks a lot :)

---

### Post by aysiu on 2007-05-17
Please do report back on this. I'm just going on memory here (as I don't use KDM any more), but I recall KDM remembering the session you last used and, unlike GDM, not constantly confirming (Just for this session? Or make default?).

---

### Post by dunkyp on 2007-05-18
urgh I think I wrecked my install I'm trying to work it out but I have no login screen I have to use startx

---

### Post by aysiu on 2007-05-18
Are you using KDM or GDM?

If you're using GDM, try ```
sudo /etc/init.d/gdm restart
```

If you're using KDM, try ```
sudo /etc/init.d/kdm restart
```

---

### Post by dunkyp on 2007-05-18
I'm on gdm but when I did what you said it just said it had restarted but I still didn't have a login screen.. edit:working now

---

### Post by aysiu on 2007-05-18
Have you tried pressing Control-Alt-F7 after it says GDM is already restarted?

---

### Post by dunkyp on 2007-05-18
I'm trying to get kdm though but it's just not working :'(

---

### Post by aysiu on 2007-05-18
Okay. Let's take it one step at a time. First, let's remove GDM: ```
sudo apt-get remove gdm
``` Then, let's install KDM: ```
sudo apt-get install kdm
``` Double-check that KDM is the default display manager: ```
cat /etc/X11/default-display-manager
``` The output should read ```
/usr/bin/kdm
``` If it doesn't, let me know. Finally, do ```
sudo /etc/init.d/kdm stop
sudo /etc/init.d/kdm restart
``` If you're not immediately taken to the login screen, press Control-Alt-F7

If that doesn't work, well... we'll cross that bridge at that time.

---

### Post by dunkyp on 2007-05-18
it took me to an ubuntu shutdown start up loading bar thingmie

---

### Post by aysiu on 2007-05-18
And just stays there? Never a login screen?

---

### Post by dunkyp on 2007-05-18
yeah I think I'm just going to give up for the moment :( but I'll try again later

---

### Post by aysiu on 2007-05-18
What happens if you're at the frozen login screen and you press Control-Alt-Backspace?

---

### Post by dunkyp on 2007-05-19
nothing :( don't worry about it I'm just gonna leave it I'll try fix it next time I do a clean install

---

### Post by Cene on 2007-05-19
Just a hint: This can be done in gdm too with .xsession file. Just select the "execute x start script" or something for the default session.

---

### Post by dunkyp on 2007-05-19
cheers

---

