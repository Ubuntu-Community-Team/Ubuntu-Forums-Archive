---
title: "VNC connection refused on headless 18.04 ??"
date: 2018-08-22
forum: General Help
---

### Post by rr4711 on 2018-08-22
I have a similar problem. I want a dummy monitor with a custom resolution (let's say 1920x1080) when there is no physical Monitor connected at boot-up, and if a monitor is connected it should use the native resolution of the screen (which is lower, we have some quite old HW, but it's a certification issue and we cannot use different one). Doesn't need to be hot-pluggable, a reboot when I attach the screen would be ok.

What is the best approach here? VNC is a must, I don't want to use remote X session via SSH Tunnel for instance.

Markus

---

### Post by slickymaster on 2018-08-22
Moved to a thread of its own.

Please don't hijack other people's threads. Not only it dilutes community effort but it's also the wrong way to get the proper and adequate help to your problem.

---

### Post by HermanAB on 2018-08-22
You should use the right tool for the job and VNC is almost never the right one.  So you should read up on how X, VNC and OpenSSH work and then decide which tool to use.  By that time, you will also know enough to make it work.

---

