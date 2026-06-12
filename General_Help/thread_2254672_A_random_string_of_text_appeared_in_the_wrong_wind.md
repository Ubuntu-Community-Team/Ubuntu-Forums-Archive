---
title: "A random string of text appeared in the wrong window. What just happened?"
date: 2014-11-29
forum: General Help
---

### Post by Drekidegga on 2014-11-29
So I was trying to troubleshoot a network problem. I had reason to suspect that I might be getting DDOSed. So I was looking for some information about how my router firmware (DD-WRT)  handles random unsolicited requests. What happened next is something I didn't think possible. I had a terminal emulator window open running "ping google.com". Then suddenly a some text from my browser window shoewed up in my terminal emulator window. I will post a screenshot of it.  [https://i.imgur.com/x40Gb4K.jpg](https://i.imgur.com/x40Gb4K.jpg)  Also you will notice that the XFCE4-screenshooter doesn't know how to take a screenshot of two monitors with two different resolutions.  What caused the text from one window to bleed into a terminal window like that? How is that even possible?

---

### Post by Vaphell on 2014-11-29
you probably middle clicked in terminal window.
Anything you select and have highlighted lands in a copypaste buffer that can be pasted with middle click. Very handy.

You can see contents of that buffer using let's say *xsel -po* in terminal. Select some text anywhere and without losing highlighting run that command.

---

### Post by Drekidegga on 2014-11-29
That must be it. Thanks for the swift reply.

---

### Post by JKyleOKC on 2014-11-29
Very useful trick to know! However "xsel" is not installed by default on all current systems. Looks as if it might be something nice to add though...

---

