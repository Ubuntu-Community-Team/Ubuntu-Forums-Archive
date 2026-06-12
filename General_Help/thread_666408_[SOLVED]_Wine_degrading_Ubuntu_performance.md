---
title: "[SOLVED] Wine degrading Ubuntu performance"
date: 2008-01-13
forum: General Help
---

### Post by Victormd on 2008-01-13
Reasons for installing Ubuntu on my machine include security, performance, great eye candy, and just tired of Windows. I've been using comps. since MS-DOS and went through ALL Windows versions... Always had something to complain about them... performance... I always new that there was something out there that would be able to show me what my comp. was capable of doing, and yes, have known about linux for a loooonng time but only now decided to change... Well, everything is going great except that, due to my X-years with windows, I've acquired quite a software library, mainly graphics stuff... I've been using 3Ds Max since from when it was MS-Dos based... and same with AutoCAD... now days I use them just for fun and am giving Blender a shot! Seems to be very powerful!!! Then of course Photoshop... tried Gimp but still needs some improvements to be competitive... Ok, so here's the thing. I love Ubuntu and don't think about going back to windows any time soon... I dual boot so if I ever need any thing windows specific, I got it... but I'm trying to minimize my windows usage and am playing around with WINE. I've installed a few games and of course, Photoshop. Everything is working fine BUT, seems like my Ubuntu performance (second item on my "reasons list") is degrading and I can only attribute this to WINE. Has anyone else had any issues similar to this? I'm still not very familiar with the linux environment so I can't just look something up to see what linux is loading at startup (which is when this is most noticeable) and change it... If anyone has any comments, observations, suggestions... please, let me know!
Thanks

---

### Post by zvacet on 2008-01-13
Type in terminal

```
top
```

and you will see wich task consume your Ubuntu most.For detailed information type 

```
man top
```

---

### Post by Nexusx6 on 2008-01-13
I seriously doubt that its Wine. Wine is just a translation layer between Windows based commands/calls/and api's into ones Linux can understand and compute. It doesn't start up with the system itself, and as far as I understand, is only active while a program is running through Wine. If you're noticing a slow down still after you've started and closed all programs that use Wine to run on Linux, open a terminal session and type

```
wineserver -k
```
And see if that makes any difference.

You can try checking System Monitor under *System -> Administration* and sort by what is eating the the most CPU resources. 

There's also a thread around these forums in which a poster posted a "How-to" that can significantly cut down on start up time. I haven't been able to find it at the moment, but I do have the link saved on my home computer. I'll edit this post and PM you when I get home and pull the link up :)

---

### Post by Victormd on 2008-01-13
> **Nexusx6 said:**
> I seriously doubt that its Wine. Wine is just a translation layer between Windows based commands/calls/and api's into ones Linux can understand and compute.

This is what I understood about Wine as well. But I only noticed the slow-downs after I installed some apps using Wine...
What does wineserver -k do, kill wine?

I ran the "Top" command and this is my mem usage.
Mem:    963928k total,   833384k used,   130544k free,    91256k buffers
Swap:  1004052k total,        0k used,  1004052k free,   416160k cached

I think this is way to much mem used, 86%, and when I check the System monitor, my CPU usage is spiking at ~50%. The only apps I have open are Firefox and the System Monitor at this time.

I'll be looking forward to check out the link you mentioned.
Thanks

---

### Post by Nexusx6 on 2008-01-13
> What does wineserver -k do, kill wine?
Pretty much.

> I ran the "Top" command and this is my mem usage.
Mem: 963928k total, 833384k used, 130544k free, 91256k buffers
Swap: 1004052k total, 0k used, 1004052k free, 416160k cached

I think this is way to much mem used, 86%, and when I check the System monitor, my CPU usage is spiking at ~50%. The only apps I have open are Firefox and the System Monitor at this time.

You've got me scratching my goatee =/ 
Sys Monitor tells you that your CPU is spiking at ~50%, but isn't showing which program is doing the jumping? It sounds like something has sprung a (memory) leak on you, but thats just a guess. This problem might be  beyond my knowledge of Linux but hopefully someone will come along and help you more. 
You can try installing "Boot Up Manager" from Synaptic which may give you a better look at whats happening at start up. Also, you can check the System Logs under the Administration tab and see if you can catch anything there. If all else fails, you can use Wine to uninstall the programs in reverse chronological order to how you installed them, or uninstall Wine completely for the sake of ruling out what we can.

Getting off work in 3ish hours, so it'll take me atleast that long to get that link you. I'll keep my eye on this thread till then

**EDIT: **
I think its listed as "bum"
> sudo apt-get install bum

---

### Post by Victormd on 2008-01-13
I've installed Boot Up Manager and found that there were some things - laptop related - that I did not need... other than that, nothing seems to be out of place. I'll keep checking to see if something shows up either in Top or System manager...

---

### Post by Nexusx6 on 2008-01-13
Got it: [http://ubuntuforums.org/showthread.php?t=565651](http://ubuntuforums.org/showthread.php?t=565651)

Your sig made me think of a long shot. Do you have Compiz-Fusion on? If you do, turn it off.  A FX5200 is not going to play nice with Compiz and could potentially be a huge source of lag though, again, even if you see improvement it might not be the source of the issue.

Keep us updated :)

---

### Post by Victormd on 2008-01-13
Yes, I have Compiz-Fusion, actually it was the first thing I got going after installing Ubuntu for the first time and haven't turned it off since. That could be the problem, but I've set it up so it doesn't use up too much resources... but you're right, that could be contributing to the problem!
I'll take a look a the link now, thanks!

---

### Post by Victormd on 2008-01-13
Well, after looking at the link you sent, I came to the conclusion that, even though my system is taking a bit longer than it used to, it is still much faster than what people report. From the Grub boot list to full login (with autologin - to the point where I can load apps) my system takes ~45s. Someone mentioned that his login session took around 30sec and that this was a huge improvement. From what I understand, login session is from when he logs in to when he can run an app. If that's the case, my Ubuntu is smokin!!! If not... than I'm trully screwed... hehehe

---

### Post by Nexusx6 on 2008-01-13
Ah, so maybe it was a matter of perspective eh? :P I would still give the method in the link a shot for the sake of having a faster boot up time if you wanted. If you feel like the system is slowing down post boot up you could always try the compiz thing though it sounds like you've configured the load light enough that your card can handle it.

If you feel that there is still a problem, don't hesitate to make another post with a diffrent subject line - for some reason or another, "Halp! My Ubuntu is teh slowxorz!!!11!!evelen!!!" tends to draw a lot of attention :P You can also PM me anytime. 

Take care chief ;)

---

### Post by Victormd on 2008-01-13
Tks dude! I'll be sure to let you know if something comes up!

---

