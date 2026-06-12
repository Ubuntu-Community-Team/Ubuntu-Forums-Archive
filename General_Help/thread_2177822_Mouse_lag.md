---
title: "Mouse lag"
date: 2013-09-30
forum: General Help
---

### Post by cranerja on 2013-09-30
Hello I'm running Ubuntu 13.04. I have severe mouse lag in games and on desktop (even in windows). I've seen a few suggestions but the commands don't work saying that the directory does not exist. I have switched USB ports and I've switched mice. Any idea on how to fix it?

---

### Post by theDaveTheRave on 2013-09-30
Cranerja, do you have this mouse lag from start up or is it only during game play?

What are your system specs? if your system is seriously slowed down during game play it could be impacting on your mouse.

Do you have access to try the same game on other pcs (similar spec preferable).

You should also find mouse settings for acceleration, resistance and stuff in your settings menu.

---

### Post by didier-amyot on 2013-10-02
I use kubuntu and experience the same problem.  Indeed I have reset my machine with kubuntu 13.10 and it changes nothing.  I have a brand new desktop machine with big specs: intel i7, 16 gig of ram...  I have

---

### Post by theDaveTheRave on 2013-10-03
> **cranerja said:**
>  I've seen a few suggestions but the commands don't work saying that the directory does not exist.

Just re-read your initial post, have you got a link to the pages that you tried.

I'm a bit bemused as to why your mouse should be lagging? unless it is a wireless mouse and you are getting interference somewhere?

from a terminal type in the following
```

lsusb

```
before and after plugging in the mouse

this is what I get with my cordless mouse plugges in...
```

Bus 001 Device 003: ID 13d3:5702 IMC Networks UVC VGA Webcam
Bus 003 Device 002: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
you'll notice the funny code ```
046d:c501
``` this is some sort of hardware / driver detail, if you search for whatever your output is relating to your mouse you may find something.

you should probably try the same thing to get information on the USB driver / hardware using the following
[code]
lshw
[/lshw]
there is a lot of output, and you'll need to run through it to find the detail of your USB controler.

Post the output to this thread, and any result from your research of the details that you get.

David

---

### Post by cranerja on 2013-10-23
I switched my graphics card to an nvidia one and the problem went away (for games at least). The old card must have been bad

---

