---
title: "Webcam support in Ubuntu"
date: 2005-07-22
forum: General Help
---

### Post by diffuser78 on 2005-07-22
Are there any drivers avaialble in Ubuntu which would help me use my Creative Webcam while chatting  or for any other application ?

Thanks,

Dan

---

### Post by mo_x on 2005-07-22
I have Creative webcam that works with the ov511 driver. It is automatically detected by Ubuntu and work with gnomemeeting or xawtv.

---

### Post by poofyhairguy on 2005-07-24
[QUOTE=diffuser78]Are there any drivers avaialble in Ubuntu which would help me use my Creative Webcam while chatting  or for any other application ?

Thanks,

Dan[/QUOTE]

can you get it to record stuff? Maybe, look at the other post. Can you use it to chat with Windows people on MSN or something like that? Probably not.

Try Gnome Meeting.

---

### Post by diffuser78 on 2005-07-24
[QUOTE=poofyhairguy]can you get it to record stuff? Maybe, look at the other post. Can you use it to chat with Windows people on MSN or something like that? Probably not.

Try Gnome Meeting.[/QUOTE]

Ububuntu didnt detect my creative webcam, any suggestions ?

Dan

---

### Post by mo_x on 2005-07-24
What model is your webcam (mine is CT6840) ?

---

### Post by trash on 2005-07-24
Gnomemeeting would detect my built-in webcam mic but not the webcam video.. I had to get V4L from the universe repository... Ubuntu installl V4L2 by default but it does not work for me.
My cam is a usb logitech quickcam 3000 pro

---

### Post by sethmahoney on 2005-07-26
Has anyone had any luck getting the D-Link DSB-C310 webcam working with ov511?

---

### Post by JPatrick on 2005-07-27
For those who have Creative Webcams ->

[http://opensource.creative.com/](http://opensource.creative.com/)

Home page ->

[http://webcam.sourceforge.net/](http://webcam.sourceforge.net/)

Problem I had:
```
patrick@Titan:~/downloads$ sudo dpkg -i cpia*.deb
Selecting previously deselected package cpia-control.
(Reading database ... 118511 files and directories currently installed.)
Unpacking cpia-control (from cpia-control_0.5.1-2_i386.deb) ...
dpkg: dependency problems prevent configuration of cpia-control:
 cpia-control depends on python (<< 2.4); however:
  Version of python on system is 2.4.1-0ubuntu2.
dpkg: error processing cpia-control (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cpia-control
```

---

### Post by foolsh on 2005-11-13
[http://home.insightbb.com/~foolsh/]("http://home.insightbb.com/~foolsh/")

---

