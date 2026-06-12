---
title: "compiz requirments"
date: 2006-12-31
forum: General Help
---

### Post by Lowfront on 2006-12-31
Can I run compiz with just a intergrated video "card"


I have an x60 with Intel® Graphics Media Accelerator 950

---

### Post by ayoli on 2006-12-31
yes you can, using AIGLX (which is already in Xorg 7.1)

---

### Post by Lowfront on 2006-12-31
alright well I went into the synaptic manager and installed everything compiz.  Where do I start...

Like where is the program in applications or systems?

---

### Post by ayoli on 2006-12-31
try to run from a terminal:
```
gnome-window-decorator && compiz --replace
```
if it works you may want to add this to your startup programms (menu System>Preferences>Sessions, tab Startup progs)
btw, i prefer use beryl (which is a fork of original compiz) here'z a how to about beryl: [http://doc.gwos.org/index.php/BerylOnEdgy](http://doc.gwos.org/index.php/BerylOnEdgy).

---

### Post by Lowfront on 2006-12-31
I really wanted to us compiz because I wanted to just install this theme

[http://www.gnome-look.org/content/show.php?content=44063](http://www.gnome-look.org/content/show.php?content=44063)
and that site has much better themes in general for compiz...


that terminal code didn't work...

---

### Post by ayoli on 2006-12-31
what was the output of terminal ?
which ubuntu version do you use ?
here is a how to for original compiz on edgy: [http://gandalfn.wordpress.com/howto/howto-compiz-aiglx-on-edgy/](http://gandalfn.wordpress.com/howto/howto-compiz-aiglx-on-edgy/)

---

### Post by Lowfront on 2006-12-31
bash: gnome-window-decorator: command not found



edgy


how to change the source.list

mine says its read only

---

### Post by d3v1ant_0n3 on 2006-12-31
To open sources.list as read/write in Gedit, run ```
sudo gedit /etc/apt/sources.list
``` from terminal.

---

### Post by Lowfront on 2006-12-31
how do I configure the xorg config file?

I did this and i think i messed a lot of stuff up answering questions I didn't know, just closed out the window when I realized that wasn't what I wanted.


sudo dpkg-reconfigure xserver-xorg

---

### Post by ayoli on 2006-12-31
```
gksudo gedit /etc/X11/xorg.conf
```

---

