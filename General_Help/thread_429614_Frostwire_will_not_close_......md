---
title: "Frostwire will not close ....."
date: 2007-05-01
forum: General Help
---

### Post by ginnie6 on 2007-05-01
I have to reboot to get it to shutdown. I close it and it minimizes......I go to system monitor and end it that way and nothing happens. How can I get this program to end? Running Feisty btw.

---

### Post by taurus on 2007-05-01
You can kill it from a terminal.  Look for it PID (first column)

```
ps -A
```
and kill it with

```
sudo kill -9 1234
```
assuming 1234 is the PID for frostwire.

---

### Post by jfinkels on 2007-05-01
> **taurus said:**
> You can kill it from a terminal.  Look for it PID (first column)

```
ps -A
```
and kill it with

```
sudo kill -9 1234
```
assuming 1234 is the PID for frostwire.

or maybe you can do ```
killall frostwire
```

or perhaps you can do ```
pidof frostwire | xargs kill
```

Just a bunch of different ways to do the same thing :D

---

### Post by Roasted on 2007-08-03
So uh, yeah... I just found this thread, did what was said, and frostwire won't close.

I used ps -A and found that Frostwire was 13088

I did

sudo kill -9 13088

didn't work.

---

### Post by Roasted on 2007-08-07
still won't work

---

### Post by Roasted on 2007-08-09
My only means of shutting off firefox are simply logging off and back in. What the... :lolflag:

---

### Post by iAndrew on 2007-08-09
Why would system Monitor not work? It should. Anyways. Either way would work;

But: ```
pidof frostwire | xargs kill
```

Is probably the easiest.

I'm new to Linux coding, but wouldn't it be:
```
pidof frostwire && xargs kil
``` ?.

---

### Post by canadianwriterman on 2007-08-09
There is an option in the Preferences dialogue to shut down when closing. By default, it will stay running if something is downloading or uploading.

---

