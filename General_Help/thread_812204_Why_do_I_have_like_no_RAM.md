---
title: "Why do I have like no RAM"
date: 2008-05-29
forum: General Help
---

### Post by Lichig0 on 2008-05-29
When I first started using Linux(Ubuntu) I used to use half the Memory that Windows used. But recently I have been Running low on memory. Like not cached memory, used Memory, 87% used memory. I have about 1 gig of RAM(I'm assuming thats what the memory is) and the graph just doesn't go down anymore, and there isn't anything using it, it's just being used... I wish I knew what is going on, and I have probably just a few hours before I have to log out before I run out of memory...any help....like maybe is there a way to "recover" RAM...or just simply fix the problem

---

### Post by Tom--d on 2008-05-29
go onto System monitor and go on view > all proccess. Then go to the processes tab. > sort by ram. and post a screen shot of it.

And post it in here. 

Then we shall see whats using your ram.

---

### Post by Lichig0 on 2008-05-29
[http://i159.photobucket.com/albums/t138/sords4/Screenshot.png](http://i159.photobucket.com/albums/t138/sords4/Screenshot.png)

---

### Post by wootah on 2008-05-29
Please post results of *free -m*

---

### Post by BlueSkyNIS on 2008-05-29
That's one small screenshot! Make it bigger, please #-o

---

### Post by Lichig0 on 2008-05-29
Ummm, I don't know how to make it bigger, and I had to restart like 5 min ago because I ran out of memory, so I have quite a bit free right now compared to before but I garentee it'll get back up there.

the free -m right now is 

             total       used       free     shared    buffers     cached
Mem:           947        765        181          0         13        232
-/+ buffers/cache:        519        428
Swap:         2776         50       2726

---

### Post by chrisccoulson on 2008-05-29
> **Lichig0 said:**
> Ummm, I don't know how to make it bigger, and I had to restart like 5 min ago because I ran out of memory, so I have quite a bit free right now compared to before but I garentee it'll get back up there.

the free -m right now is 

             total       used       free     shared    buffers     cached
Mem:           947        765        181          0         13        232
-/+ buffers/cache:        519        428
Swap:         2776         50       2726

Looks pretty normal to me. You're not running out of memory - it is being used for cache. Check out [http://gentoo-wiki.com/FAQ_Linux_Memory_Management]("http://gentoo-wiki.com/FAQ_Linux_Memory_Management") for an explanation of how Linux memory management works:)

---

### Post by BlueSkyNIS on 2008-05-29
> **Lichig0 said:**
> Ummm, I don't know how to make it bigger, and I had to restart like 5 min ago because I ran out of memory, so I have quite a bit free right now compared to before but I garentee it'll get back up there.

Maybe Firefox is eating your memory? Also, don't be too excited about low free memory, linux is just cashing your files :)

---

### Post by Lichig0 on 2008-05-29
I'll post again when I'm running low on memmory again, I'm also pretty sure it's not cached memory either, because when I restarted it was like 89% used by programs and 8% cache. And also Firefox was only using 57 MB

---

### Post by ramjet_1953 on 2008-05-30
I second what was mentioned above.

Linux is set up to USE spare memory for cache, as the philosophy behind it is that unused memory is a waste.

If you put the [COLOR="Blue"]System Monitor apple[/COLOR]t on your toolbar, by right clicking on a vacant space and then click Add to Panel, you will be able to choose it from the list. Just configure it to monitor you RAM. Dark green is used RAM and light green is cached RAM.

ps You can also see if a particular application is hogging memory or CPU time by typing [COLOR="Red"]top[/COLOR] in a terminal.

Regards,
Roger :cool:

---

### Post by wootah on 2008-05-30
> **chrisccoulson said:**
> Looks pretty normal to me. You're not running out of memory - it is being used for cache. Check out [http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management) for an explanation of how Linux memory management works:)

Vista tried doing that but failed :)

---

### Post by yaknowwat on 2008-05-30
it may be that an application you are using is allocating a chunk of memory for itself and not freeing it up after you close it.

With Virtualbox 1.5.8 there seemed to be bug where if i saved the machine state the memory allocated for the virtual machine was not free'd the bug seemed to have went away with Virtualbox 1.6 though.

Possibly an application you have is causing a similar effect.

Also nautilus in 7.10 has a memory leak [i think it was caused from badly caching sound previews on mouse over] (nautilus would start to take up +200 MiB of RAM at times. solved with a simple killing of nautilus though.) from what i remember and was never patched in 7.10. The memory leak doesn't exist in 8.04 though.

So you know nautilus should only be using around 15-30 MiB ram it varies.

---

### Post by wootah on 2008-05-30
> **yaknowwat said:**
> it may be that an application you are using is allocating a chunk of memory for itself and not freeing it up after you close it.

With Virtualbox 1.5.8 there seemed to be bug where if i saved the machine state the memory allocated for the virtual machine was not free'd the bug seemed to have went away with Virtualbox 1.6 though.

Possibly an application you have is causing a similar effect.

Also nautilus in 7.10 has a memory leak [i think it was caused from badly caching sound previews on mouse over] (nautilus would start to take up +200 MiB of RAM at times. solved with a simple killing of nautilus though.) from what i remember and was never patched in 7.10. The memory leak doesn't exist in 8.04 though.

So you know nautilus should only be using around 15-30 MiB ram it varies.

Mine sits around 24 MiB residential and 99 MiB Virtual. Guess that seems right. I don't do the whole sound preview thing though.

---

### Post by yaknowwat on 2008-05-30
> **wootah said:**
> Mine sits around 24 MiB residential and 99 MiB Virtual. Guess that seems right. I don't do the whole sound preview thing though.

Yeah thats good. 

By chance do you use desktop effects?

---

### Post by wootah on 2008-05-30
No sir, not at that moment. My X is sitting pretty high though (74 MiB res, 233 MiB virt). It makes me wonder what X is really doing :(

---

### Post by Lichig0 on 2008-05-30
> **ramjet_1953 said:**
> I second what was mentioned above.

Linux is set up to USE spare memory for cache, as the philosophy behind it is that unused memory is a waste.

If you put the [COLOR="Blue"]System Monitor apple[/COLOR]t on your toolbar, by right clicking on a vacant space and then click Add to Panel, you will be able to choose it from the list. Just configure it to monitor you RAM. Dark green is used RAM and light green is cached RAM.

ps You can also see if a particular application is hogging memory or CPU time by typing [COLOR="Red"]top[/COLOR] in a terminal.

Regards,
Roger :cool:
Yea, see the thing is I know that. And its USED memory not cached memory. I very aware of the difference.

---

### Post by sweeneytodd on 2008-05-30
the system can apparently be run with only 64mb memory, sounds like its just not reusing memory, strange? could it be u reckon, some program trying to access cache, and the system is saying no or something, have u got some sort of memory optimization program or something, if so, maybe uninstall it

---

### Post by Lichig0 on 2008-05-31
> **sweeneytodd said:**
> the system can apparently be run with only 64mb memory, sounds like its just not reusing memory, strange? could it be u reckon, some program trying to access cache, and the system is saying no or something, have u got some sort of memory optimization program or something, if so, maybe uninstall it

Ummm, none that I know of

---

### Post by Lichig0 on 2008-06-01
> **yaknowwat said:**
> Yeah thats good. 

By chance do you use desktop effects?

Yea...

---

### Post by Lichig0 on 2008-06-08
top - 19:21:25 up 1 day,  4:04,  2 users,  load average: 1.22, 0.64, 0.54
Tasks: 137 total,   2 running, 135 sleeping,   0 stopped,   0 zombie
Cpu(s): 29.0%us, 15.2%sy,  0.0%ni, 55.8%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    970304k total,   948136k used,    22168k free,     5492k buffers
Swap:  2843464k total,   256756k used,  2586708k free,    90428k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 6032 root      20   0  112m  32m  18m R   42  3.4  35:49.49 Xorg               
22561 mark      20   0 41516  21m  12m S   40  2.3   0:09.70 gnome-system-mo    
 6509 mark      20   0  743m 651m 645m S    1 68.8 138:04.24 compiz.real        
22592 mark      20   0 82756  22m  11m S    1  2.3   0:00.86 gnome-terminal     
 6683 mark      20   0 74252  27m 8744 S    1  2.9  13:13.72 gweather-applet    
 5741 icecast   20   0  4376  792  664 S    1  0.1   0:56.39 icecast            
 6442 mark      20   0 15884 4432 3904 S    1  0.5   1:05.15 gnome-screensav    
 6677 mark      20   0 25628 8956 7432 S    1  0.9  10:10.49 multiload-apple    
 6309 mark      20   0 42572 6604 5992 S    0  0.7   0:17.58 gnome-settings-    
22567 mark      20   0  189m  54m  20m S    0  5.8   0:04.54 firefox            
    1 root      20   0  2844  508  456 S    0  0.1   0:01.40 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.58 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.02 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:04.38 ksoftirqd/1

[http://s159.photobucket.com/albums/t138/sords4/?action=view&current=Screenshot-SystemMonitor.png](http://s159.photobucket.com/albums/t138/sords4/?action=view&current=Screenshot-SystemMonitor.png)

91% used by programs
4% in use as cache

---

### Post by Bushwack on 2008-06-08
> 6509 mark 20 0 743m 651m 645m S 1 68.8 138:04.24 compiz.real 

It looks like compiz (Desktop Effects) is leaking memory on you.

Disabling desktop effects and then turning them back on when you start to run low on memory should clear up the issue.

I'm not sure why compiz is leaking memory (and eating cpu time by the looks of it), but it may be a known issue with certain plugin.  I would search to see if any of the plugins you use are known to cause issues and then try disabling them.

---

### Post by Lichig0 on 2008-06-08
> **Bushwack said:**
> It looks like compiz (Desktop Effects) is leaking memory on you.

Disabling desktop effects and then turning them back on when you start to run low on memory should clear up the issue.

I'm not sure why compiz is leaking memory (and eating cpu time by the looks of it), but it may be a known issue with certain plugin.  I would search to see if any of the plugins you use are known to cause issues and then try disabling them.

OMG Thank you! I reloaded the window manager using Compiz Fusion Icon and I went from 91% to 20%

I'll look into what might be leaking memory.

---

### Post by markbuntu on 2008-06-08
I agree. I am looking at my sys monitor right now and my compiz.real is at about 10MB. If you have atlantis or anything else running behind a transparent desktop that will use huge amounts of memory. It did for me.

sys monitor in the panel is really a good thing to have along with force quit to kill off misbehaving programs.

---

