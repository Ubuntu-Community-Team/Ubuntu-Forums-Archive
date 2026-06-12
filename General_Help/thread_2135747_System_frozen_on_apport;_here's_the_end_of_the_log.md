---
title: "System frozen on apport; here's the end of the log"
date: 2013-04-15
forum: General Help
---

### Post by pwabrahams on 2013-04-15
My system froze overnight, and here's the last few lines of the log:
```
Apr 15 07:26:39 Amanita udevd[9308]: failed to execute '/usr/share/apport/apport-gpu-error-intel.py' '/usr/share/apport/apport-gpu-error-intel.py': No such file or directory
Apr 15 07:26:39 Amanita kernel: [59787.688063] [drm:i915_hangcheck_hung] *ERROR* Hangcheck timer elapsed... GPU hung

```
So I guess that *apport* has something to do with it, but that's not a program that I've ever requested explicitly or know anything about.  The system wasn't entirely dead, since cron jobs were still running and the mouse was alive -- but CapsLock wouldn't turn on the light.

How should I deal with this?

---

### Post by ibjsb4 on 2013-04-15
Apport is suppose to be disabled by default unless your running 13o4.  I have been running into this recently and assume that upgrades are responsible for activating it.  I suggest simply disabling apport.

  [http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=disable+apport&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=disable+apport&sa=Search&cof=FORID:9)

---

### Post by slickymaster on 2013-04-15
See this bug: [Bug #1103061]("https://bugs.launchpad.net/ubuntu/+source/xdiagnose/+bug/1103061")

---

### Post by pwabrahams on 2013-04-15
None of these bug reports seem to match my situation.  However, they did lead me to investigate why the .py file wasn't executing.  It turns out that **python** is not the default application for **.py** files.  In the file associations in System Settings, the listed associations for x-python are kate and Office Writer.  I've changed that and I'll see what happens the next time this error crops up.  Meanwhile, someone should fix that default setting for the file associations.  (I have no idea where that's done.)

---

### Post by slickymaster on 2013-04-15
[http://www.howtogeek.com/117709/how-to-change-your-default-applications-on-ubuntu-4-ways/](http://www.howtogeek.com/117709/how-to-change-your-default-applications-on-ubuntu-4-ways/)

---

### Post by pwabrahams on 2013-04-16
It's clear how a user can fix the default application for **.py** files, which of course should be **python**.  My point is that the user shouldn't have to do that; the *original* default should be **python**.  But I have no idea what program is responsible for setting the original default.

---

