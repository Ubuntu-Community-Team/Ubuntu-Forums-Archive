---
title: "Trackerd memory leak -- pretty bad one"
date: 2007-11-28
forum: General Help
---

### Post by quoderat on 2007-11-28
Hi. Been using Ubuntu since way back, but am now on Gutsy Gibbon 64-bit. 

My problem is that the process trackerd has an enormous memory leak. If I leave it on for a full day, it consumes over one GB of memory. I noticed that it seems to gain .1MB of memory every 30 seconds or so.

Does anyone have any solutions to this, or suggestions?

Please note that I cannot disable it, as I have 2.5TB of mixed media that is not organized, and never will be, and I need to be able to search it. 

The amount it's indexing is not the problem as even when I set it to index only my home folder, which has nothing in it, the memory leak still occurs.

---

### Post by volfro on 2007-12-06
I'm experiencing the same problem. Fortunately for me, the search features are more convenience than necessity; I can do without.

But, tracker automatically starts with Gutsy, and the memory leak for me  is pretty bad. It's easy enough to disable through the sessions manager, but it shouldn't be there with a bug like this.

I should note that I'm also on Gutsy x64.

---

### Post by firoozyves on 2007-12-07
If you still want to use trackerd, make the following changes to the tracker _preferences_ (Gutsy). I have not have any problem since.

You can change the tracker preferences in System; Preferences; Indexing Preferences.

On the General tab:

**Mark** Enable indexing
**Unmark** watching

on the Performance tab:

Indexing speed: **0**
Select **Minimize** memory usage

A Son service.

---

