---
title: "[SOLVED]  Putty and X11 forwarding, help please"
date: 2017-05-28
forum: General Help
---

### Post by rob141 on 2017-05-28
Hello everyone i have a question about putty and X11 forwarding but i dont know if what i want to do is actually possible


First of all, i have done already the X11 forwarding with putty but it does not do what i really want to do.

Let me explain.

I have two machine running on ubuntu, lets call them PC-A and PC-B

When i open putty on PC-A to connect to PC-B that works ok, then from the command prompt within putty ( where i am actually inside PC-B), i do:  sudo startx

that does start the x windows but it open the xwindow of PC-B 

what i would like to do is when i do startx, it would actually forward the xwindow of PC-A onto PC-B.  

In the filed of:  X display location in the X forwarding in putty i have written localhost: 0.0  but i have also tried to put the ip adresse of PC-A then : 0.0  but i still got the exact same result, still open the xwindow of PC-B

Is it possible to really forward the xwindow from PC-A onto PC-B when using putty on PC-A to connect in PC-B instead of just opening the xwindow of PC-B when connected on it ?

Thank you in advance for your help   ;)

---

### Post by steeldriver on 2017-05-28
First, never run startx with sudo

Second, AFAIK X forwarding can only connect remote X *clients *to a local server - there's no mechanism that I know of to forward from an X server to another X server. The closest you will probably be able to come is to start a "panel" client.

However if you want an entire remote session it will almost certainly be easier to use VNC or x2go etc. which are designed to do that

---

### Post by rob141 on 2017-05-28
Thank you very much for your reply. I had thought about VNC but i was just wondering if it would have been possible to do the same with putty. 

Thank you again for the clarification  ;)

---

