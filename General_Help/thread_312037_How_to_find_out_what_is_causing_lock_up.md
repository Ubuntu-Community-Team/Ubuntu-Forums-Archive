---
title: "How to find out what is causing lock up?"
date: 2006-12-03
forum: General Help
---

### Post by spelingchampeon on 2006-12-03
I am running 6.06. I have set this PC up as an MP3 server, and ONLY when I am running XMMS, my PC will lock up (the last digital bit is replayed over and over until the PC locks up). Again, this only happens when I am running XMMS..but I have no clue as to how to find out what happened. The system log is of no help that I can determine. Can anyone help out?

Thanks

---

### Post by loell on 2006-12-03
you cad do a trace, by doing

```
strace xmms
```

---

### Post by spelingchampeon on 2007-01-27
Same situation here with trying to figure out where I am locking up. 

Since the post above, I have reformatted and installed Ubuntu 6.10. I installed a new sound card (Creative).. and have  found out quite a few things:

1. The problem above is a little off the mark. My problem appears when XMMS is running, as a result of starting up Streamtuner. To be sure it was or was not XMMS, I put a bunch of MP3 songs on this PC, and ran XMMS for over 24 hours with no freezes. 
2. Streamtuner will freeze the PC...sometimes after 5 minutes, other times it will run for a couple of hours, but it always locks up. 
3. Streamripper seems to speed the lock up process, but during evaluation periods, I figured that Streamripper is not the culprit. 
4. STRACE is a good tool, but only runs for a short period of time, or it appears that way. For instance, last night, I started STRACE which with: *strace -t -o me3.txt streamtuner*, and waited for the lockup. After 15 minutes, the PC locked, and I had to reboot.. only to find my text file capturing the processes only lasted 35 seconds. The previous STRACE ran for 8m 29s.. and the one before that 1m 8s. Needless to say, none of the lock ups were captured, at least that I would understand. 

I am at a total loss, since the same thing has been happening ever since using Ubuntu (5 and 6). I've upgraded my MB, CPU, memory, sound card and hard drive. I really like Ubuntu... the look and feel is great, plus it has many benefits...however, the main reason I am using this PC is for music/mp3's. Any ideas?

My spec: 
AMD 2000+ cpu
PC Chips 810LMR mb
512M sdram 
WD 80G hd
Power Man 240W ps (this is a flex box, and the only peripherals are cd rom, hd and now the sound card)

---

### Post by spelingchampeon on 2007-01-31
Welp, since no one seems to have any ideas... how about this...

 Does anyone know of another Linux OS that runs Streamtuner-ripper and XMMS without locking up?

---

### Post by spelingchampeon on 2007-02-21
I'm going to answer my post with my fix. 

Since my last post, I built another machine with a different motherboard, and never had a lockup with Streamtuner....hmmm

SO.. I bought a ECS K7SOM+ motherboard and 768meg DDR266 memory. 

Its been running and running and running with NO lockups. 

Maybe the PC Chips mb just isnt meant for Streamtuner.....

---

### Post by teaker1s on 2007-02-21
pass but in terminal type ```
top
``` you will see top resource hog at top,if it's running when crash happens you'll know what caused it.
secondly under system tab on gnome desktop there is syslog which will have records of events

---

### Post by spelingchampeon on 2007-02-24
When I checked the old PC, most of the times, XMMS was utilizing the most.. and the system log had no information whatsoever..just your normal bootup processes. STRACE didnt do much for me either... thats why I was starting to suspect a MB-memory issue. This new MB has been running for 5 days now, with no hiccups. 

Later

---

### Post by teaker1s on 2007-02-25
did you try memtest in grub to check memory as well

---

