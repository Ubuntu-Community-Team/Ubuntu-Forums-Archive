---
title: "Ubuntu swapped CAPS LOCK and CTRL on my keyboards"
date: 2016-07-11
forum: General Help
---

### Post by alacis on 2016-07-11
After 2 years of using 14.04, this morning Ubuntu unilaterally(?) swapped the CAPS LOCK and Left CTRL on my keyboards.

Keyboard_**S**_ explained: I have the lap-top keyboard with the little flat keys, and a separate large keyboard that I use for touch-typing.

Both of the keyboards have changed, so the problem is not the keyboards, but some Ubuntu system definition.

Please see the attached screenshot.

***Funny note***: when I press the CTRL key, now assigned to the CAPS LOCK key, the CAPS LOCK light comes on as required!

How do I change these back, please???

---

### Post by QDR06VV9 on 2016-07-11
Make a text file name "ctrlcapswap"
You can save it in your home directory as ".swapctrlcaps" without the quotes note the "." it is needed.
```
!
! Swap Caps_Lock and Control_L
!
remove Lock = Caps_Lock
remove Control = Control_L
keysym Control_L = Caps_Lock
keysym Caps_Lock = Control_L
add Lock = Caps_Lock
add Control = Control_L
```

(The above comes straight out of the xmodmap man page). Then input the command in the terminal:

```
xmodmap ctrlcapswap
```

will swap your capslock and left control keys. 
To make it persistent...add the text file to your Startup Applications.

---

### Post by alacis on 2016-07-12
But what caused this after 2 years of operation?

---

### Post by QDR06VV9 on 2016-07-12
I do not know.
I have only heard of it happening.... but never on my machine.
Sorry I do not have an answer for you for that.
But may I ask if this work around sorted you out?

---

