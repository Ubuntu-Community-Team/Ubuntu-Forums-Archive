---
title: "RealPlayer Error in Firefox"
date: 2005-03-31
forum: General Help
---

### Post by scottieblues on 2005-03-31
I installed RealPlayer successfully and it runs fine by itself. But when i go to few an embedded file I get the error shown in the screenshot.

The Mozilla plugin page says to make sure to make a sybolic link in the system path.
Where would that be?

Thanks....

[http://img48.exs.cx/img48/6218/realerror1ur.png](http://img48.exs.cx/img48/6218/realerror1ur.png)

---

### Post by scottieblues on 2005-03-31
I got it.

Just had to make a symbolic link to /usr/bin.

Glad to have it working!

---

### Post by bored2k on 2005-03-31
[QUOTE=scottieblues]I got it.

Just had to make a symbolic link to /usr/bin.

Glad to have it working![/QUOTE]
 Weird that wasnt done by itself. RealPlayer asks "install system wide links?". If you said yes, they should have been there.

---

### Post by scottieblues on 2005-03-31
I was thinking that it made the links itself when I installed in Warty. I do remember answering yes, so I'm not sure what happened. It did put the plugin links in the right place though.

---

### Post by purdy on 2005-06-12
I just had to go through the same issues today when I was installing RealPlayer 10 on my install. Like you guys have been mentioning it (sometimes) does take a manual link to the realplayer.bin in your /usr/bin

---

