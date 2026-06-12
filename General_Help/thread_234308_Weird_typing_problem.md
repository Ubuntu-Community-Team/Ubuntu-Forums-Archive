---
title: "Weird typing problem"
date: 2006-08-11
forum: General Help
---

### Post by GazzaK on 2006-08-11
I have a bit of a text problem, typing the ´ key once does nothing, but if I follow it by a aeocl etc I get a áéó&#314;&#263;, this is great but if I want to type say i´m I have an extra key press and words which need a ´s, like say Gary´s come out like Gary&#347;, how do I disable this behaviour?

It seemed to appear after messing about with xorg.conf, but I have restored my old xorg.conf

---

### Post by steve.horsley on 2006-08-11
Dumb question - have you restarted X since restoring the config? That's all I can think of.

---

### Post by tomtom_in_eire on 2006-08-11
ok, one thing you can try is:```
sudo dpkg-reconfigure xserver-xorg
```
It will prompt you again for all the xorg settings, including the keyboard layout. Make sure you select uk.

---

### Post by GazzaK on 2006-08-11
It is something to do with the keyboard opeions in System>Preferences>Layouts, I have ¨United Kingdom International (with dead keys)¨ - if I try to choose any other UK keyboard, I do not get  any in the list, if I click the reset to defaults button, it reverts to uk, but then shift and 3 gives a 3 not a £...

---

### Post by GazzaK on 2006-08-11
oh and yes I´ve restarted X a number of times and tried a ¨sudo dpkg-reconfigure xserver-xorg¨ selecting uk.

---

### Post by GazzaK on 2006-08-11
[https://launchpad.net/distros/ubuntu/+source/xkeyboard-config/+bug/44014](https://launchpad.net/distros/ubuntu/+source/xkeyboard-config/+bug/44014)

**in System>Preferences>Keyboard**
1. add any US keyboard
2. remove UK keyboard
3. add first UK keyboard
4. remove US keyboard
5. set UK keyboard to default

Shift+3=£ now :)

---

