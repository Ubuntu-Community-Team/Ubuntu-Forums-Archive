---
title: "[ubuntu] pidgin offline messages don't work"
date: 2014-09-29
forum: General Help
---

### Post by asasdsadsadsad on 2014-09-29
hi,

I use the current ubuntu and pidgin version and normally offline messages works (works on my windows machine), but in the ubuntu system i don't get offline messages.
Anyone have any ideas?

---

### Post by D2theW on 2015-02-21
I am having the same issue in 14.04 using Google Talk.  I know I'm missing messages, because when I turned on the wi-fi for my tablet, the messages sent while I'm offline get downloaded to the app.

I tried the instructions found here under "Auto logout on suspend", but it did not fix things:
  [https://wiki.archlinux.org/index.php/Pidgin](https://wiki.archlinux.org/index.php/Pidgin)

I tried testing out by:

[LIST=1]
[*]Opening up the terminal
[*]```
$ purple-remote setstatus?status=offline
```
[*]Having somebody send me a message
[*]```
$ purple-remote setstatus?status=available
```
[/LIST]

Pidgin reports nothing and only reports new messages sent while my status is set to available.

---

