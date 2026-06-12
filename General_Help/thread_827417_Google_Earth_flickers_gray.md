---
title: "Google Earth flickers gray"
date: 2008-06-12
forum: General Help
---

### Post by questionaire on 2008-06-12
I installed the linux version of Google Earth on my Ubuntu 8.04 but the screen with the earth on it continuously flickers gray blocks.  My graphics card is Radeon 400x I think and under hardware drivers its says that the ATI graphics driver is running.  

so whats up?

---

### Post by executive on 2008-06-13
i have the same problem. using ATI X1400. :(

---

### Post by imon9 on 2008-06-13
did you have compiz on?
if so, you may need to turn compiz (desktop-effect) off.

also,you may want to try install google-earth 4.2 (instead fo the beta 4.3), 4.2 dun have the new feature but it render much better on the average graphic card

---

### Post by petronell on 2008-06-13
Thanks for the advice. I had the same problem and it was compiz. When I disabled the desktop effects all was OK.

daveR

---

### Post by Arborius on 2008-08-24
I have finally signed up because I think I may have something to add here.

I have found that switching back and forth between metacity and compiz to correct Google Earth causes errors and instability. Also when returning to compiz, conky only displays on 1 desktop on my desktop cube.
Below is the error compiz returns when reopening from metacity. Apparently this error is a fairly decent issue all its own.
```

/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

```
Also I believe this issue is related to the problems with compiz and Opengl viewports. I don't know if anyone is making these connections, I'm just trying to brainstorm. I think that this is a localized issue.

I think compiz.real is the file that controls transparency or at least has something to do with it, correct me if I'm wrong. Perhaps there is some sort of error with it, or an error with the files that point to it.

I have a temporary fix that may work better than what I've seen suggested, which was: 

```
 you@yourhouse:~$ metacity --replace 
```

**[COLOR="Red"]MY FIX:[/COLOR]**
I left compiz on, went to System>Preferences>Advanced Desktop Effects Settings, Then Desktop>Desktop Cube>Transparent Cube Tab and adjusted the transparency to 100%. Where Google Earth before was completely unusable, I now only get a few tics and tweaks.

Does anyone else run a transparent cube desktop? If so, this might work for you.

---

### Post by jarl on 2008-11-05
> **imon9 said:**
> did you have compiz on?
if so, you may need to turn compiz (desktop-effect) off.

also,you may want to try install google-earth 4.2 (instead fo the beta 4.3), 4.2 dun have the new feature but it render much better on the average graphic card

I experience the same, 
I am new to ubuntu (just installed 8.10), could you please tell me how to disable compiz.

Jarl

---

