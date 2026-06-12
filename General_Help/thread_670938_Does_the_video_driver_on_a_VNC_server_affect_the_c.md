---
title: "Does the video driver on a VNC server affect the client?"
date: 2008-01-18
forum: General Help
---

### Post by dwasifar on 2008-01-18
I just set up VNC on my home server to administer it without going down into the basement.

In the process I discovered that I had to disable the proprietary nvidia driver and use the nv driver instead, because the machine would not boot headless with the nvidia driver installed.  (It needed a monitor attached to boot; the monitor could be powered off, but it had to be connected.  Weird.)

After reverting to the nv driver on the server, I could swear my image quality in the client vncviewer window suffered.  Am I imagining it?

---

### Post by samosamo on 2008-01-19
Funny, I've been using a headless server for years and I've cursed VNC every day because I thought it was the connection that was slow.  Turns out the video driver DOES matter.  I switched it from vesa to ATI and its like I'm actually sitting at the computer.

---

### Post by amo-ej1 on 2008-01-19
vnc only 'reads' what appears on the screen and transfers that over the network. So the better/faster things appears on the screen the better vnc will work (shifting the bottleneck to the network). Take a silly example, putting your x-server to a small resolution and a low color depth won't enable you to use vnc at a high resolution. So yes, it does matter ;)

---

