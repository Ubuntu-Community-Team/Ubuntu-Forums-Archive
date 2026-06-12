---
title: "Can't start ubuntu"
date: 2008-06-02
forum: General Help
---

### Post by Grandis41 on 2008-06-02
Hello!

Yesterday I decided to try ubuntu for the first time, and I downloaded wubi and installed it as I was told. But when I try to start it I can't get in. After I've chosen ubuntu instead of Windows, the ubuntu loading screen comes. When it is finished it comes some text, that is impossible to read since it dissapears just as quick as it comes. But then it comes this text screen, and it just stays like that.

[IMG]http://img293.imageshack.us/img293/1015/dsc00202js8.jpg[/IMG]

Took a picture of it with my cellphone (hence the poor quality), anyone know what the problem might be?
...or is it just me being a noob ? x)

---

### Post by cprofitt on 2008-06-02
Well...

two options:

1)  X server is not setup 

or

2)  X server did not start properly

Have you tried typing startx at the prompt?

If not please do and post the results (or error code).

Thanks,
PV

---

### Post by Grandis41 on 2008-06-02
Tried "startx" as you said, and ended up with this (yay, another crappy picture)

[IMG]http://img514.imageshack.us/img514/4341/dsc00203wk9.jpg[/IMG]

---

### Post by cprofitt on 2008-06-02
I would do the following:

sudo dpkg-reconfigure -phigh xserver-xorg and see if X can start then.

Let me know.

---

