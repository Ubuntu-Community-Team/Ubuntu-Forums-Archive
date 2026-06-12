---
title: "Problems with keyboard"
date: 2008-01-10
forum: General Help
---

### Post by Aftermath7246 on 2008-01-10
I just installed Ubuntu and im having trouble with the keyboard. the Question mark key comes out as this when I press it é and É in capital. and whenever I want the at sign it turns into this ". a lot of the other keys are messing up too like the colon semi colon keys and such... brackets and some other stuff.... I tried to switch keyboards but it still happens. Im using Ubuntu 7.04

---

### Post by MartynA on 2008-01-10
Hmm, might be something to do with the keyboard layout you selected on install. What happens if you change the layout on the system?

More info: 

[http://ubuntuforums.org/showthread.php?t=75197](http://ubuntuforums.org/showthread.php?t=75197)

---

### Post by twright on 2008-01-10
hi,
you could try editing the language in the xorg.conf file

edit the file by typing gksudo gedit /etc/X11/xorg.conf into terminal (or just use Ctrl+f2 and type it in there) then scroll down till you see something like this:
```
Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "CoreKeyboard"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "[COLOR=Red]**pc105**[/COLOR]"
    Option        "XkbLayout"    "[COLOR=Red]**gb**[/COLOR]"
EndSection
```then you just need to change the it to the correct details of you keyboard (google can help if you don't know what to put here, you should only need to change the bits in red)

this will change the global language of your system so that it affects all users and the login screen

---

### Post by Aftermath7246 on 2008-01-12
I tried it it didnt change anything... Im thinkin of goin back to windows cause I cant type properly...

---

### Post by twright on 2008-01-12
don't worry,

it is probably fixable

firstly what language is your keyboard, secondly what model PC/laptop do you have

if you google it chances are that someone has already experienced this problem and worked out how to get it working :)

---

### Post by Aftermath7246 on 2008-01-12
The Language is US CA its the Microsoft curve 2000, I have my own custom made PC, I also tried with my other cicero keyboard. Does anybody know how I can edit key symbols customly (question mark) lol

---

### Post by twright on 2008-01-13
this might help:
[http://blog.dotkam.com/2007/06/25/custom-keyboard-layout-in-ubuntu-or-just-linux/](http://blog.dotkam.com/2007/06/25/custom-keyboard-layout-in-ubuntu-or-just-linux/)

---

### Post by Aftermath7246 on 2008-01-13
Thnx man I think that might work... Im going to try it today :)

---

### Post by Aftermath7246 on 2008-01-13
YES I changed it thank you sooo much.

---

