---
title: "Feisty Running-  Extremely Slow"
date: 2007-08-07
forum: General Help
---

### Post by lonecold on 2007-08-07
I have recently come back to Ubuntu again lol now that I think I can finally leave Windows but can I? No. 

Normally for me in the past Ubuntu has run sooo smooth compared to windows but since installing Feisty it is **TERRIBLY** slow! Applications are continuously stuttering and taking a long time to respond, I can't play music properly because if I click anything in another application - such as a link in firefox, it makes my music in the background begin to stutter.

I have already done some looking into this and my first reaction was to check my CPU usage and RAM usage. So I did:

```
top
```

In terminal, and CPU usage was showing fine but my RAM off the scale. I had a problem like this in the past and it was due to a memory leak in one application, however I don't think a memory leak is the case this time as it has been doing this since I have first installed it or maybe it is I don't know. Anyway, here is the result from the top command sorted by memory:

[IMG]http://i10.tinypic.com/5yx1w6o[/IMG]

So I have like 1gb RAM and if those results are correct, almost all of that is being utilized but I looked at the processes and can't understand what is using it all :S.

If anyone could help with this I would be so grateful, as it is really causing me problems at the moment. It's like running Windows XP on a 500mhz Pentium 3 lol.

---

### Post by lonecold on 2007-08-07
Anyone please? Tried different things and looked around the net but can't find what is the problem :'(

---

### Post by RedSquirrel on 2007-08-07
I wouldn't worry too much about the RAM usage. That can be reclaimed as a lot of it is in buffers + cached.

The only suggestion I have off the top of my head is to make sure you're using the appropriate video drivers for your system.

---

### Post by bogolisk on 2007-08-07
It seems to me that you load to much crappy software:
[LIST]
[*] firefox grabbed a total of 94M RSS. check what extensions you selected. Disable some flash. Too many tabs with many flash in each of them will grab a lot of memory and cpu.
[*] mono programs like banshee: What ever some says, interpreted/JITed code is sill far less efficient than native compiled code. Almost all modern CPUs were designed and optimized for compiled C code, that's why compiled code run more efficiently.
[*] wish: avoid tcl like plague! "tcl considered harmful! - Richard Stallman". Whether you hate or like the man, he did wrote the original gcc and gdb, so he knows a thing or two about software.
[*] applets: watch for python-based applets, many are known to be memory/cpu hogs. It's not python per-se, but badly written python applets can still looks good and tempting.
[/LIST]

---

### Post by hikaricore on 2007-08-07
Ram shouldn't be an issue, it looks like the OP has 1GB of ram.

What video card are you using, and have you properly installed the drivers?

Also I don't know if it still exists, but there was a weird bug that had to do with the /etc/hosts file being improperly formated at one time which caused a system-wide slowdown for some users.  Just thought I'd mention it.

---

### Post by lonecold on 2007-08-08
I tried the /etc/hosts fix and not much seems to have happened. The TCL thing is for aMSN which I think uses TCL.

My graphics card is nVidia GeForce FX5200, and I have nvidia drivers installed. 

I booted up before and at first the system is fine, but I kept running top in the background to monitor and the ram usage just keeps going up and up and up the longer the PC is on. 

I don't think there is a problem with firefox, it doesn't seem to vary that much if I have more tabs than less open, and the only extension I have installed is the StumbleUpon extension - which causes no problems on my Windows system so I don't see why it would on Ubuntu but I dunno :confused:


Maybe this is just something I will have to put up with :(

But thanks for the help anyway

---

