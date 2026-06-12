---
title: "VINO Questions"
date: 2008-04-15
forum: General Help
---

### Post by bc90021 on 2008-04-15
I have some general questions about Vino:

I know how to enable and disable it via gconftool, so I can SSH to my home machine and enable it.  However, I would have expected that it would have been a service to stop and start.  Is that not the case?

If Vino is running, shouldn't I see the box listening on 5900 when I do netstat?

Does anyone have any familiarity with using Vino and SSVnc?  ([http://www.karlrunge.com/x11vnc/ssvnc.html](http://www.karlrunge.com/x11vnc/ssvnc.html))

I've just moved my box over from Gentoo to Ubuntu, and this is the only thing I don't have working yet.

Thanks in advance.

---

### Post by fguilhon on 2008-04-15
When you enable vino, it starts listening on 5900... when disabled, stops listeing. Just like a normal service. I can see it on my machine using ```
netstat -ant
```
As for VNC, you can use vncviewer though SSH using:
```
vncviewer -via home localhost
```
Where home is the dest host (or an alias in ~/.ssh/config) and localhost is the machine name on the dest network.

---

### Post by bc90021 on 2008-04-15
Thank you for your response.  I only see Vino as running when I am actually connected - even if it is enabled and not connected, it does not show up in netstat.

I have simplified things a bit, and have it working without SSH at the moment.

I am not certain what you mean in terms of your steps for running it over SSH.  However, I will continue to research that online.

Thanks!

---

