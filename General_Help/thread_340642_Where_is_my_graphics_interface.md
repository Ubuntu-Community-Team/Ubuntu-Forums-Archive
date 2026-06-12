---
title: "Where is my graphics interface?"
date: 2007-01-17
forum: General Help
---

### Post by OOzypal on 2007-01-17
Kubuntu start in command line with no error.

How to start KDE/X/Graphics. I tried kdm no help

I also tried

sudo /etc/init.d/kdm start  -- no help -- kdm manger already started

I tried /etc/init.d/x11-common start still no help

---

### Post by taurus on 2007-01-17
Do you see **kdm** on the list from this command?

```
ps -A
```

---

### Post by OOzypal on 2007-01-17
ps -A| grep kdm

4268 ?  00:00:00 kdm

---

### Post by taurus on 2007-01-17
Then there must be something wrong with X.  What happens when you run **startx** from a console?

---

### Post by OOzypal on 2007-01-17
I get black blank screen.

Then I clicked on ALT-F2 then back ALT-F1 and I saw an error

Backtrace:
XIO fatal IO error 104 (Connection reset by peer)on X server ":0.0"
after 0 request (o known processed) with 0 events remaining

---

### Post by Lucardo Mamones on 2007-01-17
what runlevel are you booting to? have you tried ctrl+shift+F7 it´s the console port that is used by the graphical mode. i think its shift if not try ctrl+alt+f7

---

### Post by taurus on 2007-01-17
From a console/terminal, run

```
sudo dpkg-reconfigure -phigh xserver-xorg
start
```

---

### Post by jocko on 2007-01-17
Are you sure it's not already running? See what happens if you press Ctrl+Alt+F7 (or F1-6).

Otherwise try this:

```
sudo /etc/init.d/kdm restart
```Or:
```
sudo /etc/init.d/kdm stop
sudo /etc/init.d/kdm start
```

Edit: I saw your post with the error message, so I guess it's not this simple...

---

### Post by OOzypal on 2007-01-17
CTRL+ALT+F7 no help.

```
sudo dpkg-reconfigure -phigh xserver-xorg
start
```

gives an error

xerver-zorg postinst warning: overwriting possible-customized configueration
file; back in /etc/X11/xorg.conf.20070117225230

---

### Post by taurus on 2007-01-17
It just means that your original /etc/X11/xorg.conf has been back up to /etc/X11/xorg.conf.20070117225230.

---

### Post by OOzypal on 2007-01-17
ok

```
start
```

does not do anything

---

### Post by taurus on 2007-01-17
> **OOzypal said:**
> ok

```
start
```

does not do anything

I somehow forgot the x at the end...  ](*,) 

```
startx
```

---

### Post by OOzypal on 2007-01-17
```
sudo startx
```

xauth: error in locking authority file /home/hab/.Xauthority

---

### Post by Lucardo Mamones on 2007-01-17
try ```
dpkg-reconfigure --force xserver-xorg
```

---

