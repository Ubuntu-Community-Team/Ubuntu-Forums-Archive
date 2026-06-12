---
title: "Huge memory use"
date: 2006-11-09
forum: General Help
---

### Post by Jasper84 on 2006-11-09
Sometimes when i startup ubuntu the base memory use is a staggering 160Mb, while it is usually 60Mb.
What could be causing it? I use Ubuntu Breezy Badger 5.10 with the Xcfe desktop installed. I can vaguely remember checking that the problem also occured with the Gnome desktop, and i checked that logging in and out of users doesnt help, which didnt suprise me. (which i also still have, but if i log in with Xcfe gnome isnt loaded, right?(atleast if no gnome programs on) )
I have a 800Mb AMD with 250Mb memory. (so 160Mb is not acceptable)

---

### Post by lloyd_b on 2006-11-09
The first question that comes to mind:  How are you getting that "memory used" number?  Does that include cache/buffers, or is it strictly user and system memory?

Having the system use a ton of memory for cache or buffers is nothing to worry about - if you need it for something else, the OS will release it.

If you're actually seeing that large amount of memory used by programs (user or system):

Open a terminal window, and run "top".  When "top" is running, hit <SHIFT> <M> (capital letter "m"), which will cause the list to be sorted by memory usage.  Any memory hogs  running in the system should float to the very top of the list.

Lloyd B.

---

### Post by mbeierl on 2006-11-09
The "top" command can give you information on what's using your memory.  Go to a console (graphic or ctrl-alt-f1 and login) and simply enter top and hit enter.  Once the display is up, hit shift-M (capital M) to sort processes by memory usage.  This will give you a display like so:

```
[FONT="Courier New"]top - 11:44:11 up 47 min,  2 users,  load average: 0.68, 0.66, 0.55
Tasks: 118 total,   3 running, 115 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.5%us,  3.0%sy,  0.0%ni, 95.3%id,  0.2%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1026064k total,  1002084k used,    23980k free,    64884k buffers
Swap:  1550264k total,        0k used,  1550264k free,   511460k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                               
 7475 mark       5 -10  303m 209m 203m S    5 20.9   0:42.66 vmware-vmx                                                             
 4182 root      15   0  483m 122m  15m R    3 12.2   7:09.29 Xorg                                                                   
 6224 mark      15   0  140m  44m  19m S    0  4.5   0:14.72 firefox-bin                                                            
 6005 mark      15   0  151m  37m  19m S    0  3.7   0:26.76 evolution-2.8                                                          
[/FONT]
```

This shows that my program vmware-vmx is using 20% of my memory.  Also that of my 1g memory, nearly half of it (511460k) is filesystem cache.  What is just might be is that a program such as locate was run automatically via cron and just loaded a bunch of memory with filesystem cache.

If your 160m is mainly there, be happy  It'll actually speed up your system - not slow it down.

---

### Post by mbeierl on 2006-11-09
Doh!  Beaten to the punch by lloyd_b!  Great minds - and fools...:)

---

### Post by Jasper84 on 2006-11-13
Thanks, used the top command, but didnt have the 160Mb thing happen yet.
On how i noticed the memory use, I have a sidebar thingy of Xcfe showing memory use, just for the hell of it. I checked it with System Monitor 2.12.1. Probably that app simple has same result as top, but i should learn to use commandline more anyway.
If the memory is going somewhere it shouldnt go again after startup, ill post here again.

---

### Post by aysiu on 2006-11-13
You may want to read this:
[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

---

