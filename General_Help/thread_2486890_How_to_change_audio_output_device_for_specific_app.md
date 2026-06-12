---
title: "How to change audio output device for specific applications"
date: 2023-05-15
forum: General Help
---

### Post by superdanny59 on 2023-05-15
Used to be a feature in old versions of Ubuntu, I am running an application that detects my speakers and headphones as one audio device. I want to play audio from just my headphones but the pulse audio control panel no longer lets you control the output device for specific applications. How do I get this useful feature back?

---

### Post by TheFu on 2023-05-15
Since you didn't say which version of Ubuntu and which DE you are using .... 

Have you tried installing **pavucontrol**?  Run that and you can connect nearly any source (input) to any sink (output).  I suggest starting from the right-most tab and working left.

Using **pactl** or **pacmd**, it is possible to script any specific needs too.

---

