---
title: "No Playback in audacity"
date: 2007-04-29
forum: General Help
---

### Post by Fireblend on 2007-04-29
Hey, I have trouble using audacity; whenever I try playing anything after loading it, it gives me the error message 
> Error while opening sound device. Please check the output device settings and the project sample rate

---

### Post by stmiller on 2007-04-30
Ubuntu contains the old Audacity, for some reason (It is only compatible with OSS).

Install alsa-oss to install a compatibility layer.

---

### Post by LegoAddict on 2007-05-15
I'm glad I found someone else with this problem.  I can't get Audacity to work even with AOSS.  It's a pain in the neck to get it to work.  It's really annoying as every time I want to use Audacity I need to switch to Windows.

Exact same problem

---

### Post by smeashy on 2008-06-28
Though i am still fairly new to Ubuntu, i did find a suitable solution to this.

Quite simply, make sure the active device in your volume control settings (double click the speaker icon in panel) is the same as the one being used in the audio preferences in Audacity.

Reconciling the mismatch sorted the problem out completely.

---

