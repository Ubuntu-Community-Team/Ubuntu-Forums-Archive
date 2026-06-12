---
title: "Idle Memory?"
date: 2008-01-19
forum: General Help
---

### Post by SoberWarlock on 2008-01-19
My CPU is never idle. My system is using very little of my ram and I don't want my ram to go to waste. From time to time my Ubuntu machine will randomly freeze and my Hard-Drive won't even react. :(

How can I use more of my Ram?:confused:

[IMG]http://i63.photobucket.com/albums/h144/Jorale_mendoza4/Desktop/Screenshot-SystemMonitor.png[/IMG]

---

### Post by olejorgen on 2008-01-19
Post the output from
```
top -b -n 1 | head -n 20
```
It's seems like somthing is hogging you cpu.

If you want to use more ram, use more/heavier applications :) Your ram is not completely wasted either. The amount shown in your screenshot is only what's used by your applications. Buffers and cache is not included. Larger buffers/cache = faster computer

---

### Post by heindsight on 2008-01-19
If you want to use more memory, run more programs that need more memory.
I don't think the freeze ups you're experiencing are from running out of memory. I'm sure there must be some other cause.

---

### Post by SoberWarlock on 2008-01-19
> **olejorgen said:**
> Post the output from
```
top -b -n 1 | head -n 20
```
It's seems like somthing is hogging you cpu.

If you want to use more ram, use more/heavier applications :) Your ram is not completely wasted either. The amount shown in your screenshot is only what's used by your applications. Buffers and cache is not included. Larger buffers/cache = faster computer

That is so strange....I would have no programs running and leave it idle for 10 minutes but my CPU is still being used. What's up? :confused:

Oh what does that code do?

---

### Post by eolson on 2008-01-19
They are trying to find out why your cpu is freezing.  Top give a lot of information about what is doing what.  Run the command and you will see.   Very informative.

It looks like there is something running in the background,  Top will show what it is.

---

