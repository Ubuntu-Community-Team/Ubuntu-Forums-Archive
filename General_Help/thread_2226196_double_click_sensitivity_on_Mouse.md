---
title: "double click sensitivity on Mouse"
date: 2014-05-25
forum: General Help
---

### Post by sumbitch212 on 2014-05-25
I want to increase sensitivity on the double click on my mouse. I cant even double click folders to open. Which i would like too. Double clicking files and other stuff is also slow to respond. Ive tried all the tips i could search on google. So, if you have another one im all ears. Thanks! (but i love this operating system. Its amazing!)

---

### Post by sammiev on 2014-05-25
> **sumbitch212 said:**
> I want to increase sensitivity on the double click on my mouse. I cant even double click folders to open. Which i would like too. Double clicking files and other stuff is also slow to respond. Ive tried all the tips i could search on google. So, if you have another one im all ears. Thanks! (but i love this operating system. Its amazing!)

If you already went into the settings and adjusted the mouse settings you may to try another mouse. I had much the same problems and a new mouse saved the day. Remember a $5.00 mouse is just that and can be fixed by using a $5.00 mouse trap.

---

### Post by brian_woods on 2014-05-26
I think there is no other option besides control panel settings or mouse settings, try again to adjust the settings hope you will solve your problem.

---

### Post by PotatoHead007 on 2014-05-26
Are you sure you have tried to change the settings at Dash>System settings>Mouse and Touchpad? There is an option for changing the double-clicking speed.

---

### Post by sumbitch212 on 2014-05-26
yeah, i did all that stuff. Also did some terminal stuff. nothing works. maybe a new mouse will help. thanks

---

### Post by sumbitch212 on 2014-05-26
cant double click a song to start in Rhythmbox. is there a plug in that allows you to play selected song without double clicking? 
i dont think my mouse is the problem as db click is fine on other things.

---

### Post by sumbitch212 on 2014-05-26
ok, im starting to notice that double click ability changes from app to app in ubuntu.

---

### Post by tgalati4 on 2014-05-26
Perhaps you are getting interference with the X server.  Do the following:

1.  Look for errors in dmesg:  (open a terminal)

```
dmesg | tail -40
```

2.  Look for errors in the system log:

```
less /var/log/syslog
```

"q" to quit.

3.  Look for errors in .xsession-errors  (This is where local, by-user errors are captured, as opposed to system errors)

```
cd
less .xsession-errors
```

4.  Finally look for global X-server (graphics server which also controls input devices) errors.

```
less /var/log/Xorg.0.log
less /var/log/Xorg.1.log
```

Post any murine errors.

Try another mouse and see if the behavior is the same.

---

### Post by sumbitch212 on 2014-05-27
thank you. ill have to come back to this . I appreciate your help!

---

### Post by grumblebum2 on 2014-05-27
Starting to sound more like a sticky mouse button.
Use "Test Your Settings" button in Mouse and Touchpad.

---

