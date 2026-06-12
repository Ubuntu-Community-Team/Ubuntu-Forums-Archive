---
title: "Increased Memory Usage in Gutsy"
date: 2007-10-20
forum: General Help
---

### Post by smartbei on 2007-10-20
Upgraded to Gutsy yesterday, generally happy - system feels faster, etc. One thing I have noticed is that my program memory usage seems to have skyrocketed. Under Feisty, I would get to maybe 500mb with a bunch of applications - under Gutsy it is over 700mb, and what is worse is that when I close all the applications, it remains above 500mb. Why is that?

When I just turn on the computer, System Monitor shows around 150-180mb of 'user' memory usage, and as I write this now (the computer has been on 12 hours or so under reasonable use) it shows 599mb of 'user' memory usage, with only firefox open.

What I also don't understand is the relationship between the memory shown taken up by processes under the 'process' tab and the memory shown used under the resources tab. Under processes, if I add it all up, I get to around 150mb.

Thanks in advance for answering/explaining. I may well be misunderstanding something basic here, don't hesitate to point it out :D.

---

### Post by smartbei on 2007-10-20
[Sorry about the near-instant double post, but it seems appropriate]

Well, switching to no visual effects (I was on Normal) brought down memory usage by over 350mb. From around 600mb to 250mb. I am guessing there is a memory leak of some sort in Compiz... Anyone else have similar experiances?

---

### Post by mbeierl on 2007-10-24
Yep:

[http://ubuntuforums.org/showthread.php?p=3620881#post3620881](http://ubuntuforums.org/showthread.php?p=3620881#post3620881)

My visual effects are eating up > 1gb of physical memory and climbing constantly.  Restarting X does not free the memory - only a reboot does.

---

### Post by mbeierl on 2007-10-24
Hmmm.  I just realized that I chose to try out 64bit Gutsy.  So I just did a manual install of the latest 64bit nVidia driver (x86_64-100.14.19) and now my compiz seems to be holding steady...

---

### Post by mbeierl on 2007-10-25
Okay, maybe not:
```

Mem:   3096320k total,  2941184k used,   155136k free,    16560k buffers
Swap:  1550264k total,   564848k used,   985416k free,   293696k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                               
23772 mark      20   0 **1765m 1.4g 1.4g **S    2 46.4  68:25.52 /usr/bin/compiz.real --ignore-desktop-hints --replace --loose-binding -

```

**1.4GB** ?!?  Something is seriously wrong here, folks!

---

### Post by mbeierl on 2007-10-26
Before killing compiz:
```

Mem:   3096320k total,  **2997924k** used,    98396k free,    33560k buffers
Swap:  1550264k total,      128k used,  1550136k free,  1103832k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                               
16101 mark      20   0  **974m 710m 686m** S    0 23.5   2:52.05 compiz.real                                                            
 4179 mark      20   0 1578m 481m  35m S    3 15.9   2:47.15 java                                                                   
15816 root      20   0  252m 163m  81m S    0  5.4   3:22.88 Xorg                                                                   
17009 mark      20   0  718m 137m  29m S    0  4.6   2:10.85 firefox-bin                                                            

```
After:
```

Mem:   3096320k total,  **3010540k** used,    85780k free,    34232k buffers
Swap:  1550264k total,      128k used,  1550136k free,  1114044k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                               
 4179 mark      20   0 1580m 485m  35m S    1 16.1   2:49.15 java                                                                   
15816 root      20   0  280m 182m  70m S    1  6.0   3:26.25 Xorg                                                                   
17009 mark      20   0  718m 137m  29m S    0  4.6   2:11.12 firefox-bin                                                            
17127 mark      20   0  **333m  87m  67m** S    1  2.9   0:01.52 compiz.real                                                            

```

So, killing compiz and restarting it made the process go from 810M to 87M in resident memory, but the total amount of physical memory used did not go down? :confused:

Things that make you go hmmm...

---

### Post by zaphod777 on 2007-10-26
Doh! I think this needs to be brought to someones attention. That is pretty bad.

---

### Post by mbeierl on 2007-10-26
A full X restart (ctrl-alt-backspace or gdm restart) DID free up the memory, so I suspect it's lost somewhere amongst X, compiz and the nvidia driver.

---

### Post by fjgaude on 2007-10-26
I can't say for sure, but Linux quickly uses all the physical memory there is, mostly into cache for any program that used any memory. For speed in returning to the program. After all the memory is used and another new program needs some, then it released what the new one wants. "Unused memory is wasted memory."

---

### Post by anaconda on 2007-10-26
The real question is does it use swap!

Because nowadays using all the RAM that is available (even unneeded) is considered just proper, efficient use of RAM. The unneeded RAM is releaced as soon as it is needed. 

This is one way to make your machine faster. eg. if you start a kde application and load the KDE-libraries to RAM why should that ram be freed when you stop using the kde application? You just might start another kde application next, and if the libraries are already in your ram then kde-programs will start that much faster.  

But if you start other programs and ram is needed THEN the memory is released. Not before.

If it really eats memory then the swap will be used also. The cache wont use swap..

---

### Post by mbeierl on 2007-10-26
Thanks.

If this were cache memory, your statements would be correct.  However this is a program that is taking physical memory away from the cache, and growing unbounded.  (Yes, I have let it go well into swap to the point of being unusable.)

So, this one program (compiz) is taking up 1g of physical memory.  When I close any other program, the memory that the program was using is immediately released and is available for other programs or the cache to use up.

When I close compiz, it is no longer taking up 1g of memory.  In fact no program is.  Compare the numbers from the two postings:

Cache before: 1103832k
Cache after: 1114044k

So, the physical memory in use did not go to cache.  It is effectively "leaked" in the OS.  Trust me, this is not a good thing.

---

### Post by fjgaude on 2007-10-26
Does system monitor show this? I use Compiz and it gives me no trouble with memory useage. I'm also running VMware Server on the same box, with 2 GB of RAM.

You likely have a different setup, and Gutsy doesn't like something about it. A bug report seems a way to go.

---

### Post by mbeierl on 2007-10-26
Gutsy, 64bit, latest nvidia drivers, compiz with full effects.

System monitor, top, ps ... they all show it.

---

### Post by smartbei on 2007-10-27
On my computer, all that is needed to free up the memory is System > Preferences Appearance > Visual Effects > None. After which you can go turn it back on and memory usage will be reasonable. No need to kill gdm.

It does however slowly increase just as before...

---

### Post by mbeierl on 2007-10-27
Hey, great workaround!

Now, (I can't believe I'm saying this about Linux!!!) how do I do this from a command line, I wonder?  I'd love to do this just prior to hibernating, but clicking through menus is just too painful for me ;)

---

### Post by IllegalCharacter on 2007-11-01
> **fjgaude said:**
> After all the memory is used and another new program needs some, then it released what the new one wants. 
I don't think this is true, not from my knowledge of the Linux kernel but from experience. When running a "normal" setup with aMSN, Firefox with 3 or 4 tabs open and Azureus running, most of my memory is being used. If I open an IDE to do some work, the system slows to a crawl. The desktop effects are choppy and programs stop responding. Even if I then close everything, the memory used drops to about 500mb (out of 1GB). Would anybody know why? When I did all this under Feisty (minus the desktop effects) the system ran fine and was incredibly responsive.

I've noticed that anything Java really slows down the system. Maybe this is part of the problem? I've had problems with Java since I first installed Gutsy.

---

### Post by mbeierl on 2007-11-01
There are many reports of the nvidia module leaking memory

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/151168](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/151168)

This is not a normal thing, and in my case restarting compiz or changing desktop effects does NOT release the lost memory.

I have no choice but to run compiz with --indirect-rendering or my system's toast.  All I can say is now that ATI has gone open source I hope nvidia feels the heat and does something about their buggy closed software.

If I could, I'd be replacing my video card with an ATI right now - but this is an onboard video in a laptop.  Not easily done :(

---

### Post by IllegalCharacter on 2007-11-01
So I guess I'll have to wait until Nvidia releases something that fixes this leak. It appears to be with either compiz or the new drivers, as I've never had an issue with memory until Gutsy. In fact I would say that the performance of the 3D games on Ubuntu such as sauerbraten or Neverwinter Nights has improved with this new driver.

[quote=mbeierl]All I can say is now that ATI has gone open source I hope nvidia feels the heat and does something about their buggy closed software.[/quote]
I hate to say it but they will probably feel the heat like us Canadians do on a sunny January morning. The current Nvidia drivers for Linux are far superior to the ATI ones (I can say this from personal experience using both on various cards) and even with ATI's drivers now being open-source, I think it will be several months at least before we see anything worthwhile come along (probably after Hardy Heron comes out). By the time the ATI drivers are comparable, it's likely that the current issues with the nvidia drivers (there are very few as far as I can tell) will have been resolved. There's also the lack of incentive for them to provide better drivers, they already have the reputation among Linux users as the better of the two and until that gap shrinks a considerable amount, there will be no heat to be felt.

[Edit:] Actually I checked this out, and the ATI drivers are NOT open-sourced.
[http://ati.amd.com/products/catalyst/linux.html#4](http://ati.amd.com/products/catalyst/linux.html#4)
They cannot legally make the drivers open-source.

---

### Post by mbeierl on 2007-11-01
Woo-hoo!  Montreal - the home of Nikki Yanofski the jazz singing sensation!

Ya, you're right, it'll be cold for a while yet.  I also must admit the latest driver is slicker/faster, but the memory leak is just so huge!

I've also still got quite a few redraw problems, but no more black windows :)

---

### Post by IllegalCharacter on 2007-11-02
Oh god, yes the black window bug is gone. I would not have waited for Gutsy to use Compiz Fusion (or Beryl for that matter) had there been no black window bug.

It also fixed a bug for me that when I was in a game, it would sometimes stop rendering anything 3D but not the 2D GUI elements.

The only problem I've noticed is the memory leak. It's not one that makes the system overly unusable, you just have to restart now and then - a lot like I did when I used Windows!

---

### Post by smartbei on 2007-11-03
IllegalCharacter: Instead of restarting, try turning off the visual effects and then turning them back on. That fixes the problem for me.

---

### Post by IllegalCharacter on 2007-11-03
How do I turn them off in Gutsy?

---

### Post by Pevichaey5 on 2007-11-03
hi

sorry if i'm wrong, but i'm sure linux uses as much RAM as possible for disk caches

i was a suse 10.2 user from march until a couple of weeks ago and all my RAM was used up within about 30 minutes

cheers

---

### Post by IllegalCharacter on 2007-11-03
If it does, then it's a new feature for me. Under Feisty when I'd run a certain set of programs, it'd use less than half of my RAM (according to the System Monitor). Under Gutsy when I don't have any programs open then over half of my RAM is in use. Once I get a bunch of programs running that use the rest of that memory, the system slows to a crawl. Shouldn't whatever Linux is doing free the disk caches so that the other things don't go so slow? Usually I have to Ctrl-Alt-Backspace to do anything which is bad if I'm doing work.

---

### Post by smartbei on 2007-11-03
> **IllegalCharacter said:**
> How do I turn them off in Gutsy?

System => Preferences => Appearance => Visual Effects => None

---

### Post by Pevichaey5 on 2007-11-03
> **IllegalCharacter said:**
> If it does, then it's a new feature for me. Under Feisty when I'd run a certain set of programs, it'd use less than half of my RAM (according to the System Monitor). Under Gutsy when I don't have any programs open then over half of my RAM is in use. Once I get a bunch of programs running that use the rest of that memory, the system slows to a crawl. Shouldn't whatever Linux is doing free the disk caches so that the other things don't go so slow? Usually I have to Ctrl-Alt-Backspace to do anything which is bad if I'm doing work.

hi

well if it is, you can change the indexing 

System>>Preferences>>Indexing Preferences

then click the performance, but reading this again, people are thinking it is something else

hope this helps
cheers

---

### Post by Superdarion on 2008-04-03
Well, as soon as X starts (the only thing that I load on startup is compiz) half my RAM is gone. That is, half of 1gb. I have the system monitor on one of my panels for quick references at all times and the green bar never goes below half full (or half empty? haha). With aMSN, Amarok, firefox and azureus open, most of the ram is totally gone.

By this time, the system monitor reports 38% by programs, 61% by cache. Then I tried opening Kaffeine, aMule and Gimp, just to see it react. The monitor stays the same (38/61) and the swap is not yet used.

Now I proceed to open Open Office's "excel" and "word", then k3b. The monitor now changes to a neat 50/50, so the cache goes down a bit and the user memory increases. The swap is still unused and I think that I've made my point so far, which is good 'cause I ran out of programs to open, haha.

I also thought I had a memory leak somewhere, probably related to compiz or something, but after I read this thread I figured I could do a little experiment to see if what some people have been telling about the system not innecessarely freeing cache was true and it seems to me that it is:

I start with a 18/30 memory usage (user/cache). After a few programs it goes to 38/61. Then to 50/50 and the swap remains unused, so the cache keeps as much as he has until a program asks for some, then he releases and the program obtains. The user remains unaware of this since the monitor never shows the released memory.

Just for the sake of the argument I now close all programs and the monitor goes to 38/44. I guess this definitely proves my point and most certainly makes me feel better.

Oh, and my system was never slow during this little experiment. All programs kept opening as if no other program was around to waste precious RAM.





-No swaps were harmed during the course of this experiment.

---

