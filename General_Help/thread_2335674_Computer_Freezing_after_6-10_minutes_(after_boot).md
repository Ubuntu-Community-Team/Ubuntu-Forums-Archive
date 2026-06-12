---
title: "Computer Freezing after 6-10 minutes (after boot)"
date: 2016-08-31
forum: General Help
---

### Post by xieem on 2016-08-31
Hi everybody,

this is my first time posting on this forum, I am a new user of Ubuntu and by far I really enjoyed the operating system but problems started to appear after several recent updates.

It came to my attention that my computer is freezing 6-10 minutes after booting up. I have no idea where to look for the problem and it's becoming problematic.

I already disabled CSM in the BiOS but didn't help me out much.

The specifications for my computer are

Asus Z170I Pro Gaming  
Corsair CS650M 
Intel Core i7 6700K  
Corsair Hydro Series H55
Kingston HyperX Fury 16 GB DIMM DDR4-2666
Samsung 850 EVO SSD M.2 120 GB  
Cooler Master Elite 130  
Asus STRIX-GTX960-DC2OC-4GD5   

I added latest DMESG output => [http://pastebin.com/x80aQNKT](http://pastebin.com/x80aQNKT)

I know this is like searching for a needle in a haystack but please ask me question so we can find and hopefully solve this issue.

I have to add that when working in terminal (so using CLI) the freezing happens later in time, but when I for example when I am using the GUI and try to install a .deb package it freezes basically 10-15 seconds after execution. 

Thanks in advance

---

### Post by Gatorade on 2016-08-31
I had a somewhat similar problem, which turned out to be the graphics card.
Maybe the update installed a different driver for the graphics card and that's causing the crashes.
The problem I had was with Linux Mint, but it does kinda sound like the same thing you're going through.

---

### Post by TheFu on 2016-08-31
[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)  dmesg isn't the only place to look.
I'd use **grep** to search all the log files for warnings or errors.  Something like **egrep -i 'warn|error' /var/log/*g | more** is the command I'd use.

Don't see anything in your dmesg dump.  Please try to show the relevant parts only.

It is common for a GUI freeze to appear like an OS freeze, when it isn't really the entire OS.  If it happens again, can you ssh in from another machine and look at the log files?  That's what I would do.  Computer lockups are almost always hardware issues. A failing GPU or PSU might not show anything in the log files, but pretty much everything else will.

Directly installing .deb packages can break all sorts of things, mainly repo dependencies - usually not immediately, but over the next 4-12 months. Beware. It is best to stay within the Canonical repos, especially when new to Linux/APT.

IMHO.

---

### Post by xieem on 2016-08-31
@TheFu

Thanks for the reply, sorry for posting the whole message.

When the freeze happens I am not able to ssh to the box, so taking a look at the log files is impossible.

@gatorade

I am suspecting the GFX card as well, the problems started to appear after an update (approx 6 weeks ago). Due to the fact I was travelling I couldn't take a closer look at this issue. How did you fix it?

Thanks for the reply!

---

### Post by TheFu on 2016-09-01
Can you swap the video card with an older one?

---

