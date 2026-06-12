---
title: "VNC java problems"
date: 2007-05-19
forum: General Help
---

### Post by short4lif2 on 2007-05-19
I am having problem with the vnc-java client connecting to my desktop.  When I start my server, I just use the following command
```
vncserver :1
```

This would mean that when connecting to the Java applet, I would have to go to [ip]:5801.  I have ports 5801, 5901, 5900 and 5800 open.  (the second two are for windows vnc.)  For some reason, when I go to [ip]:5801, the applet loads fine, but once I connect, things get weird.  I am presented with a screen matching my 2560X1024 resolution (two screens) which would indicate that something is working properly, but i just get a large grey screen and an X where the cursor should be.  Is this a problem with the java applet, or the server?  I think it is the applet because the server is clearly running, otherwise i would just not be able to connect at all.

---

### Post by mbradlcu on 2007-05-20
just curious,, what happens if you set a smaller size,, eg:
```
vncserver -geometry 1024x768 :1
```

---

### Post by short4lif2 on 2007-05-20
Apparently that made the server not want to even start!

```

danny@box:~$ vncserver -geometry 1024X768 :1
vncserver: geometry 1024X768 is invalid
danny@box:~$

```

---

### Post by mbradlcu on 2007-05-21
make sure the "X" is a "x", don't you just love the little things at times ; )

---

