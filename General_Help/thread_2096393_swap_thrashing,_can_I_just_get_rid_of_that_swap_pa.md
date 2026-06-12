---
title: "swap thrashing, can I just get rid of that swap partition?"
date: 2012-12-19
forum: General Help
---

### Post by sdowney717 on 2012-12-19
I have 4gb ddr2 and 4gb swap and the ram never fills up and the OS gets into the swap and really slows things down.

I have ordered 8gb ddr3. What happens if I get rid of the swap partition?

---

### Post by jim_deadlock on 2012-12-19
The first thing you should try is to reduce your swappiness.

Check your current swappiness (default 60 I think):
```
cat /proc/sys/vm/swappiness
```

Then change it to 10
```
sudo nano /etc/sysctl.conf
```

Add this line at the end:
```
vm.swappiness=10
```

CTRL-X to exit/save, then reboot. Then watch your swap and see if it improves. If you remove your swap partition your computer will work fine until you run out of RAM, at which point it will probably freeze and need a reboot. If you NEVER run out of RAM then you should be able to safely remove your swap partition as long as you know the risks. In my opinion it's better to have a swap just in case whatever the circumstances.

PS. If you do decide to remove your swap, don't forget to remove the relevant line from /etc/fstab

---

### Post by orb9220 on 2012-12-19
I'm curious if someone can enlighten me as new and learning. As have 4gb and it rarely uses swap. If I'm doing image editing in darktable and browser,Liberoffice,etc. Will start to see a little swap activity going on. But ram is being used first. 

Isn't better to find out why the ram isn't being used first? Before adjusting swappiness? 
As full blown workload with 6-8 apps running on 3 workspaces is in the 2-3gb range of used ram for me.
.

---

### Post by tgalati4 on 2012-12-19
Keeping swap is a good idea.  The kernel will arbitrarily dump processes when it runs out of memory.  Yes, it will slow down when it hits swap, but then you have a warning to start dumping processes before your machine freezes.  Although rare, kernel lockup is possible when RAM and swap are completely filled.

---

### Post by offgridguy on 2012-12-19
Thanks for this thread, swap is now making sense to me.;)

---

### Post by DuckHook on 2012-12-19
I have my swappiness set to 10 as a matter of course because I believe that I have sufficient memory. However, if you are seeing lots of disk activity, you might want to track it for a bit using *iotop*. Must be run as sudo, but will give you a *top*-type view of disk activity. Esp useful with *-o* option. Will give you nice view of all processes using swap. *iotop* is available from the repositories as *iotop*.

Edit:

Forgot to mention that *iotop* will only work on kernels >2.6.20 But these days, isn't that most installs?

---

### Post by sdowney717 on 2012-12-20
Thanks for these ideas
It is set to 60 
```
scott@scott-P5QC:~$ cat /proc/sys/vm/swappiness
60
scott@scott-P5QC:~$ 

```

---

### Post by Pjotr123 on 2012-12-20
> **sdowney717 said:**
> Thanks for these ideas
It is set to 60 
```
scott@scott-P5QC:~$ cat /proc/sys/vm/swappiness
60
scott@scott-P5QC:~$ 

```

Yes, that's the (unfortunate) default, which is (in my opinion) only fit for servers and the like.

Do what jim_deadlock advised and set the swappiness to 10, which is a much more sensible default for a desktop machine. You can also do this within the graphical user interface, which is somewhat easier:
[https://sites.google.com/site/easylinuxtipsproject/bugs#TOC-Swap-use-swappiness-is-too-high:-Ubuntu-is-too-slow-and-uses-the-hard-disk-too-much](https://sites.google.com/site/easylinuxtipsproject/bugs#TOC-Swap-use-swappiness-is-too-high:-Ubuntu-is-too-slow-and-uses-the-hard-disk-too-much)

Good luck! :)

---

### Post by sdowney717 on 2012-12-20
I can tell it is much better already!

[http://publib.boulder.ibm.com/infocenter/lnxinfo/v3r0m0/index.jsp?topic=%2Fliaat%2Fliaattunsetswapiness.htm](http://publib.boulder.ibm.com/infocenter/lnxinfo/v3r0m0/index.jsp?topic=%2Fliaat%2Fliaattunsetswapiness.htm)

> Optional: To set the swappiness value to zero without rebooting, run the following command after you exit the sysctl.conf file:
sysctl -p

you can also change without a reboot. Edit file then the command reloads the sysctl file.

---

### Post by sdowney717 on 2012-12-20
> **Pjotr123 said:**
> Yes, that's the (unfortunate) default, which is (in my opinion) only fit for servers and the like.

Do what jim_deadlock advised and set the swappiness to 10, which is a much more sensible default for a desktop machine. 
Good luck! :)


That would be a very good idea to submit to the developers of Ubuntu.

---

### Post by Pjotr123 on 2012-12-20
> **sdowney717 said:**
> That would be a very good idea to submit to the developers of Ubuntu.

I did. They didn't agree. :p

Note: I wouldn't put it lower than 10, unless you have an SSD for hard drive.

---

### Post by mcduck on 2012-12-20
too low swappiness will actually hurt your performance, as less data is kept cached and more ends being completely dropped from the memory instead.

The small amount of swap use resulting from the normal memory management will not decrease your system's performance, so the only good reasons to avoid that would be if you only had an SSD drive and wanted to maximize it's lifetime, or if you are on a laptop and want to get as long battery life as possible by allowing the hard drive to switch off.

Of course the actual swapping (as in using swap partition to extend the amount of memory available to applications) is slow, but that only happens in a situation where the only other option for the system would be to give the user "out of memory" error and fail to do what you wanted to do. :)

What comes to the OP's swapping, the memory usage shown in the posted image is actually quite high, and depending on what he was actually doing at the time the swapping might easily have been the normal, and preferred, way for the system to work...

---

### Post by sdowney717 on 2012-12-20
I can quickly get to that memory use by opening many tabs in Chrome. I find it quite easy to have 25 to 30 tabs open up by just clicking, especially if using google news or anytime a site will open a new browser tab by a click.

The system is much quieter now and more fluid feeling. If my ram memory is not being fully used, then why should the system offload to the swap? What happens then is the active Chrome window process is forced to use the swap and believe me it is very slow.
It is one reason I decided to go to 8gb ram.

---

### Post by sudodus on 2012-12-20
Interesting discussion in this thread! I'm reading and learning :-)

---

### Post by DuckHook on 2012-12-20
...yes, virtual memory management is a bit of a dark art. One needs the right wand, the right incantations, the right potions... Browser caching in particular is a known memory hog and due to the way Linux memory management works, browser pages are low enough priority that they are often swapped out while lots of system memory is still available. The system is trying to be proactive, and assumes that you will want a portion of main memory reserved for other large programs that you may want to run concurrently (GIMP, LibreOffice, etc). In my experience, it won't start swapping until quite a number of tabs are open, but at a certain threshold, web pages start going to swap. You mention that you routinely have 25 to 30 tabs open. None of my business, but that is an immense number of tabs. Why so many? That sort of overhead will definitely push some pages to swap. If unnecessary, you can definitely save lots of memory by practicing economy of tabs.

---

### Post by dannyboy79 on 2012-12-20
i only have 2GB of DDRII ram and notice with 10+ tabs of chrome open, video editing in kdenlive, and such, my computer gets bogged down. Would I benfit from changing my swappiness to 10 from 60? I am using 64bit Xubuntu 12.04

---

### Post by DuckHook on 2012-12-20
I suspect that your primary bottleneck is RAM, then CPU. Video editing is pretty RAM/CPU-intensive. Combined with 10+ tabs (depending on the sites) and you are just about maxing out your RAM, at which point, it won't matter what your swappiness is set to, as the OS will have no choice but to swap. The type of site is very important: sites like this forum are excellent on resources while script/ad-heavy sites are terrible and just eat up RAM.

It's pretty instructive to see how memory is allocated as you open stuff up. Try opening a terminal and doing:

```
free -s 2
```or, as @Ms. Daisy taught me recently (thanks, Ms. Daisy), for a cleaner look:

```
watch free
```then opening up all of the tabs you are accustomed to, plus editing some video. You'll see your free memory disappearing, then cache diminishing and finally buffers going down, all while swap goes up. You'll get a sense of what threshold values you can stand before your system becomes unbearably laggy.

As for the right swappiness setting, I'm afraid there is no easy rule, since response depends on how every individual uses his/her system. The best way is to experiment with different values and go with the one that feels the best for you.

---

### Post by sdowney717 on 2012-12-20
> **dannyboy79 said:**
> i only have 2GB of DDRII ram and notice with 10+ tabs of chrome open, video editing in kdenlive, and such, my computer gets bogged down. Would I benfit from changing my swappiness to 10 from 60? I am using 64bit Xubuntu 12.04

Easy enough to try and see!

---

### Post by Rebelli0us on 2012-12-20
I have no swap partition or swap file. With 16 GB memory I've had no problems, and I often run 2-3 VMs simultaneously.

---

### Post by dannyboy79 on 2012-12-20
> **DuckHook said:**
> I suspect that your primary bottleneck is RAM, then CPU. Video editing is pretty RAM/CPU-intensive. Combined with 10+ tabs (depending on the sites) and you are just about maxing out your RAM, at which point, it won't matter what your swappiness is set to, as the OS will have no choice but to swap. The type of site is very important: sites like this forum are excellent on resources while script/ad-heavy sites are terrible and just eat up RAM.

It's pretty instructive to see how memory is allocated as you open stuff up. Try opening a terminal and doing:

```
free -s 2
```or, as @Ms. Daisy taught me recently (thanks, Ms. Daisy), for a cleaner look:

```
watch free
```then opening up all of the tabs you are accustomed to, plus editing some video. You'll see your free memory disappearing, then cache diminishing and finally buffers going down, all while swap goes up. You'll get a sense of what threshold values you can stand before your system becomes unbearably laggy.

As for the right swappiness setting, I'm afraid there is no easy rule, since response depends on how every individual uses his/her system. The best way is to experiment with different values and go with the one that feels the best for you.thanks for responding, opening Steam, 5 tabs in chromium, thunar, terminal, and ubuntu software center. this is what it shows
```
             total       used       free     shared    buffers     cached
Mem:       2051060    1754356     296704          0      44616     449516
-/+ buffers/cache:    1260224     790836
Swap:      2050044      21592    2028452

```

system seems snappy so I guess I'll just leave the swappiness setting alone.

---

### Post by sudodus on 2012-12-21
> **DuckHook said:**
> ...
It's pretty instructive to see how memory is allocated as you open stuff up. Try opening a terminal and doing:

```
free -s 2
```or, as @Ms. Daisy taught me recently (thanks, Ms. Daisy), for a cleaner look:

```
watch free
```then opening up all of the tabs you are accustomed to, plus editing some video. You'll see your free memory disappearing, then cache diminishing and finally buffers going down, all while swap goes up. You'll get a sense of what threshold values you can stand before your system becomes unbearably laggy.

As for the right swappiness setting, I'm afraid there is no easy rule, since response depends on how every individual uses his/her system. The best way is to experiment with different values and go with the one that feels the best for you.
Thanks,

I see that the information of ```
watch free
``` is mainly the same as the

[FONT="Courier New"][SIZE="3"]Mem: line and
Swap: line
[/SIZE][/FONT]
of ***top*** :-)

---

### Post by DuckHook on 2012-12-21
> **sudodus said:**
> 
I see that the information of ```
watch free
``` is mainly the same as the

[FONT=Courier New][SIZE=3]Mem: line and
Swap: line
[/SIZE][/FONT]
of ***top*** :-)

*iotop* is even cooler. Try it with the *-o* switch. Have to download it from the repositories first. Run it with sudo and it gives you a running tally of processes accessing disk, including swap-in (which is what this thread was initially about).

That's the beauty of Linux isn't it? Multiple ways to do the same thing?

---

### Post by sudodus on 2012-12-21
> **DuckHook said:**
> *iotop* is even cooler. Try it with the *-o* switch. Have to download it from the repositories first. Run it with sudo and it gives you a running tally of processes accessing disk, including swap-in (which is what this thread was initially about).

That's the beauty of Linux isn't it? Multiple ways to do the same thing?
I installed ***iotop*** and tested. Yes, I like it :-)

I have been happy with ***htop***, which shows memory used in another way (similar to the GUI system-monitor). What is actually the difference, and what is the most relevant display of the memory used (RAM and swap)?

---

### Post by dannyboy79 on 2012-12-21
i ended up changing my swappiness to 10 and everything does seem snappier! I was trying to play Shank 2 and run Kaazam to capture it and kazam crashed due to "out of memory", that was before I set swappiness to 10. Will have to retry now tonight. I wish I could install more then 2GB but my old AsRock is maxed out

---

### Post by vanadium on 2012-12-21
Lowering the swapiness indeed makes your system "snappier". However, once the need to swap arizes, my experience is that the system may crawl and practically freeze while suddenly trying to accomodate ram to the new demands.

With a higher swapiness, a (relatively) low memory system will feel slower because early on, bit and bytes are already swapped. The likelyhood of having heavy disk trashing, however, is reduced.

It is all very subjective, though, and strongly depending on configurations and use scenarios. The bottom line is that no miracles can be achieved on low memory systems.

---

### Post by DuckHook on 2012-12-21
> **sudodus said:**
> I installed ***iotop*** and tested. Yes, I like it :-)

I have been happy with ***htop***, which shows memory used in another way (similar to the GUI system-monitor). What is actually the difference...

They are both very useful. However, *iotop* shows disk I/O, whereas *htop* shows (and sorts by) cpu usage (at least by default--it can be made to sort by memory: use *-s* switch or <F6>). If you are concerned about swap, *htop* will only give you summary info in its header area whereas *iotop* gives the actual processes doing disk access. It's really only useful for sleuthing, and is a curiosity otherwise.

> ...and what is the most relevant display of the memory used (RAM and swap)?Because *iotop* is written to track interactive I/O usage, it doesn't have anything to say about memory-usage. For memory, use *top*, *htop*, *free*, or other such variants. There are so many ways. You could also use *conky*, as I do, and have a constantly updating picture of your system resources.

For example, if your system is swapping out web pages while RAM is still free, *htop* won't show this directly. It will show swap being used, and RAM still free, but such high-level summary info won't show *which* process is doing the swapping. *iotop* will show that it's *firefox* or *chromium* that is actually swapping, but won't show memory usage or summary (that's not what it was designed for). I'm sure that an experienced system admin would go about it much more efficiently and probably use tools I'm not even aware of, but I don't know them, so am stuck with using a combination of the easy tools. If any sysadmins care to pipe in, I'm always happy to learn.):P

---

### Post by sudodus on 2012-12-21
> **DuckHook said:**
> They are both very useful. However, *iotop* shows disk I/O, whereas *htop* shows (and sorts by) cpu usage (at least by default--it can be made to sort by memory: use *-s* switch or <F6>). If you are concerned about swap, *htop* will only give you summary info in its header area whereas *iotop* gives the actual processes doing disk access. It's really only useful for sleuthing, and is a curiosity otherwise.

Because *iotop* is written to track interactive I/O usage, it doesn't have anything to say about memory-usage. For memory, use *top*, *htop*, *free*, or other such variants. There are so many ways. You could also use *conky*, as I do, and have a constantly updating picture of your system resources.

For example, if your system is swapping out web pages while RAM is still free, *htop* won't show this directly. It will show swap being used, and RAM still free, but such high-level summary info won't show *which* process is doing the swapping. *iotop* will show that it's *firefox* or *chromium* that is actually swapping, but won't show memory usage or summary (that's not what it was designed for). I'm sure that an experienced system admin would go about it much more efficiently and probably use tools I'm not even aware of, but I don't know them, so am stuck with using a combination of the easy tools. If any sysadmins care to pipe in, I'm always happy to learn.):P
You know enough to help me get several steps forward :-)

Thanks a lot

---

### Post by sdowney717 on 2012-12-21
More and more now systems are starting to come with lot more memory. Once you get to 8gb or higher, swap wont be needed, I think for 90% of people or programs.
So then set the value to zero.

I think a rethink ought to be done on this, perhaps this value could auto adjust itself depending on installed memory or user habits. For my use with Chrome browser and lots of tabs, I think the system as designed let me down. I was struggling with this for a long time.
I am very happy you told me how to fix this. And I have adjusted all my ubuntu installs setting to 10.
I plan to show this to my brother, who has become an Ubuntu convert. Windows 7 was being hijacked exploits on him, I never seen that myself.

It is so funny, he used to love Windows, now thinks its crap.

---

### Post by Pjotr123 on 2012-12-21
> **sdowney717 said:**
> 
So then set the value to zero.

I wouldn't do that, not even on an SSD. Too extreme. A swap on a platter hard disk should never go below a swappiness of 10, or in extraordinary cases 5. Even with an SSD I advise a swappiness of 1.

These values are in my opinion a sensible and reasonable compromise, which should guarantee a stable and reliable system for nearly all usage profiles.

---

### Post by LewisTM on 2012-12-21
To improve things further (a maybe make the subject more complicated), you can use zRAM. Just install zram-config and let it do its thing, no need to reboot.

When memory gets low and Linux starts to page out, zRAM puts the memory pages in compressed RAM instead. When memory can no longer be compressed, it uses disk swap. It's the most efficient memory management scheme. Compressing RAM incurs much less performance drain or device wear than writing to disk. It also eliminates spurious disk writes due to an overzealous swappiness. A swappiness of 60 works fine with zRAM, no need for tweaking. 

Cheers!

---

### Post by Pjotr123 on 2012-12-21
> **LewisTM said:**
> To improve things further (a maybe make the subject more complicated), you can use zRAM. Just install zram-config and let it do its thing, no need to reboot.

When memory gets low and Linux starts to page out, zRAM puts the memory pages in compressed RAM instead. When memory can no longer be compressed, it uses disk swap. It's the most efficient memory management scheme. Compressing RAM incurs much less performance drain or device wear than writing to disk. It also eliminates spurious disk writes due to an overzealous swappiness. A swappiness of 60 works fine with zRAM, no need for tweaking. 

Cheers!

A useful addition to the discussion, but I'd like to qualify this a bit:
[https://sites.google.com/site/easylinuxtipsproject/speed#TOC-For-512-MB-RAM-or-less:-enable-zRam](https://sites.google.com/site/easylinuxtipsproject/speed#TOC-For-512-MB-RAM-or-less:-enable-zRam)

That's at least how I view the best use of zRam. :)

---

### Post by sudodus on 2012-12-21
> **LewisTM said:**
> To improve things further (a maybe make the subject more complicated), you can use zRAM. Just install zram-config and let it do its thing, no need to reboot.

When memory gets low and Linux starts to page out, zRAM puts the memory pages in compressed RAM instead. When memory can no longer be compressed, it uses disk swap. It's the most efficient memory management scheme. Compressing RAM incurs much less performance drain or device wear than writing to disk. It also eliminates spurious disk writes due to an overzealous swappiness. A swappiness of 60 works fine with zRAM, no need for tweaking. 

Cheers!

I found some descriptions of xzRAM on the internet. It  looks almost too good to be true ;-)

Are you using it now? Have you found any draw-back? What happens when you close some programs and don't need much RAM - will standard RAM usage be enabled again?

*Edit*: I saw your post afterwards, [Pjotr123]("http://ubuntuforums.org/member.php?u=141824"), and you answered one important question.

---

### Post by LewisTM on 2012-12-21
I have found that zRAM is like ABS brakes: never hurts, rarely used, but can be a life saver. I never saw a performance hurt with it. You sometimes see the CPU usage go up for a few seconds while it compresses but the process is set to very low priority so you don't notice any slowdown. With today's overpowered CPUs it's very fast.

zRAM has been around for a while (since kernel 2.6), I don't think it should be qualified as experimental anymore.

Since it acts like swap, Least Recently Used (LRU) memory pages are compressed first. When they are needed, they are restored to normal RAM. Decompression is extremely fast, much faster than compression.

Anyways, try and find out. It's not miraculous but it tends to make the system run smoother.

---

### Post by sudodus on 2012-12-21
> **LewisTM said:**
> I have found that zRAM is like ABS brakes: never hurts, rarely used, but can be a life saver. I never saw a performance hurt with it. ...
Anyways, try and find out. It's not miraculous but it tends to make the system run smoother.

Thanks, I will try and find out :-)

---

### Post by DuckHook on 2012-12-21
> **sudodus said:**
> I found some descriptions of xzRAM on the internet. It  looks almost too good to be true

I imagine that it *is* too good to be true; or rather, it is not the "solution" that those short on RAM might anticipate. As I see it, problem is threefold:

1. Those short on RAM tend to have very old CPUs as well. Therefore, not only are they RAM challenged, but don't have a lot of processor cycles to spare for compression/decompression either.

2. More importantly, the only way zRAM can work is by reducing conventional RAM space even further. This is not a big deal if you have, say 1GB where half can be allocated to zRAM and the OS can be quite happy with the remaining half, but for those on 512KB or less, you are now layering a two-way compression process onto practically every memory operation. Don't see how that results in a net gain for the already RAM challenged.

3. Most of all, I'm always worried about fragility: layering far too much onto an OS that's already awfully complex. What if the user decides to run a VM? Are we now talking about a whole VM run almost entirely in compressed space? No longer just encoding/decoding data, but all of the precision- and time-critical system stuff that needs to be handled delicately yet meticulously? This technology reminds me of disk compression, which I used when it first came out and HDDs were stupidly expensive. I lost a lot of data on multiple occasions to that technology--it's much harder to recover from file corruption on a compressed drive than an uncompressed one. With HDD storage now so absurdly cheap, does anyone compress their HDDs anymore?

I fear that RAM compression is the same thing. Short-term gain for long-term pain. Wouldn't you rather just spring the price of a lunch for more RAM? 2 extra GBs does wonders on an old machine and makes all of the workarounds academic. I'm the first to admit, though, that I've never tried it. Would be happy to be proved wrong.

Edit:

> **LewisTM said:**
> I have found that zRAM is like ABS brakes: never  hurts, rarely used, but can be a life saver. I never saw a performance  hurt with it. You sometimes see the CPU usage go up for a few seconds  while it compresses but the process is set to very low priority so you  don't notice any slowdown. With today's overpowered CPUs it's very fast.

zRAM has been around for a while (since kernel 2.6), I don't think it should be qualified as experimental anymore.

Since it acts like swap, Least Recently Used (LRU) memory pages are  compressed first. When they are needed, they are restored to normal RAM.  Decompression is extremely fast, much faster than compression.

Didn't see this post. Interesting. May try it out as suggested.

@LewisTM: do you run it with a VM? If so, ever notice anything wonky?

---

### Post by Pjotr123 on 2012-12-21
Well, I did try zRam myself, and I wouldn't advise it under normal circumstances. But in some cases it might be useful:
[https://sites.google.com/site/easylinuxtipsproject/speed#TOC-For-512-MB-RAM-or-less:-enable-zRam](https://sites.google.com/site/easylinuxtipsproject/speed#TOC-For-512-MB-RAM-or-less:-enable-zRam)

That's my point of view. :)

---

### Post by DuckHook on 2012-12-21
> **Pjotr123 said:**
> Well, I did try zRam myself, and I wouldn't advise it under normal circumstances

Did your computer actually blow up or did you just stop because you didn't like that nagging feeling that it was about to do so at any moment? If something went wonky, would you mind telling us what it was? And roughly what hardware config were you running? I'm really all curiosity on this one.

---

### Post by LewisTM on 2012-12-21
I run zRAM on 3 systems, all with various VMs, all rock stable.
I too would like to hear about real-world issues with it. So far, I've only heard complaints from "theorists" who don't like the idea.

zRAM doesn't steal you RAM. You data is still in memory, only in compressed form. It's infinitely better than running software off hard drive space. Unless you know you will NEVER exceed your RAM capacity. Then you can turn off swapping. And risk running into a brick wall someday...

---

### Post by sudodus on 2012-12-21
> **duckhook said:**
> did your computer actually blow up or did you just stop because you didn't like that nagging feeling that it was about to do so at any moment? If something went wonky, would you mind telling us what it was? And roughly what hardware config were you running? I'm really all curiosity on this one.
+1

---

### Post by Pjotr123 on 2012-12-21
Right enough; some adstruction is in place.

I've noticed that performance actually dropped noticeably by zRam. Not by much, but noticeably. The system simply felt a little more sluggish than before. On my HP Mini 110-3000 netbook with 2 GB RAM and an Intel Atom 450 CPU. OS: 64-bit Xubuntu 12.10. Length of experiment: couple of days. No hard performance data available, just my impression.

On the other hand, I've had reports from people whom I trust to be reliable, who have used zRam mostly in situations with little RAM (1 GB or less), and who were much more positive. With also a swappiness that was lowered to 10. One of these people even reported massive slowdowns with zRam and a swappiness of 60, and good results with zRam and a swappiness of 10.

Note also the reactions of these mailers in the Debian developers mailing list, who claim negative real world experience:
[http://lists.debian.org/debian-devel/2012/01/msg00217.html](http://lists.debian.org/debian-devel/2012/01/msg00217.html)
(in particular Rainer Dorsch and Thomas Goirand)

That's all the real world experience I've had with zRam, directly and indirectly. Then there's also the experimental status of this module and the theoretical disadvantage of adding an extra layer of complexity. All this combined was enough to make me advise zRam only in specific circumstances.

Personal opinion folks, not God's own truth. For what it's worth. :)

---

### Post by sudodus on 2012-12-21
Thanks for sharing your experience about zRAM, [Pjotr123]("http://ubuntuforums.org/member.php?u=141824") :-)

---

### Post by DuckHook on 2012-12-21
> **Pjotr123 said:**
> Note also the reactions of these mailers in the Debian developers mailing list, who claim negative real world experience:
[http://lists.debian.org/debian-devel/2012/01/msg00217.html](http://lists.debian.org/debian-devel/2012/01/msg00217.html)
... Then there's also the experimental status of this module and the theoretical disadvantage of adding an extra layer of complexity.

Yours are exactly my concerns too. Thanks for the link.

> For what it's worth.Worth plenty. Much appreciated.

---

### Post by rnerwein on 2012-12-22
> **sdowney717 said:**
> I have 4gb ddr2 and 4gb swap and the ram never fills up and the OS gets into the swap and really slows things down.

I have ordered 8gb ddr3. What happens if I get rid of the swap partition?
hi
looks like a new version of the book: the never ending story
but the answer is very easy. see the third post from tgalati4 and every body gots the answer
cheers

---

### Post by sdowney717 on 2012-12-22
> **rnerwein said:**
> hi
looks like a new version of the book: the never ending story
but the answer is very easy. see the third post from tgalati4 and every body gots the answer
cheers

It has likely happened to me locking up from oom.

If you have enough ram then swap wont be needed as the ram wont fill up. You can fill up with 4gb ddr and 4gb swap, I have seen it close to overflowing on my system. Swap just exists to offload from ram, so more ram means less need for swap, and an overabundance excess of ram means swap is just a waste of your time slowing the system down as it swaps.

As system with 16 or 32gb ram could eliminate swap. And that is where the systems are heading now. Newer motherboards are all supporting this level of ram and with 64 bit os. I have been not hearing the system swapping on me with swappiness set at 10. It is pleasantly quiet.

Ubuntu should adjust swappiness on the boot, if lots of ram turn it way down. If you had 16gb ram, and swapiness at stock 60, I bet it will swap out to disk even if ram only using a couple gb.

---

### Post by Pjotr123 on 2012-12-22
> **sdowney717 said:**
> As system with 16 or 32gb ram could eliminate swap.

No. Reason: suspend-to-disk. :)

---

### Post by sdowney717 on 2013-01-10
Even 8gb is not enough ram!
It is back to swapping tonight.
I am doing a grep on the entire drive.
Then left it for a few hours. Come back and the drive is thrashing and clicking away. Thing is barely responding.

I am into 1.4 gb of the swap. The experience is like being stuck in the mud.
I have noticed if the computer gets into the swap it is worthless to use.
Like typing and it lags seconds behind, open file manager, shows white screen for 10 seconds, programs dont want to close.  What good is swap if it makes it so bad you can hardly use the PC at all. I think I would rather have it lock up.

---

### Post by jim_deadlock on 2013-01-10
Check the processes tab to see what's eating up all the RAM, it must be something horrendous.

---

### Post by sdowney717 on 2013-01-11
I rebooted this am as it was not responding well.
I then restarted kdenlive video render, 26 1gb clips, process being done onto an NTFS partition.
After 30 minutes, system becomes unbearably slow.

check memory and it is using 2.5gb swap.

I was rendering in ext4 partitions and did not notice this terrible bogging down.

---

### Post by jim_deadlock on 2013-01-11
Well that solves the mystery doesn't it. Your RAM is maxed out so the swap is being used, as it was designed to do. Swapping is slow, there's no getting around it. If it bothers you then you can either a) get more RAM or b) modify the way you're using your software.

---

### Post by sudodus on 2013-01-11
The linux driver for ntfs is less efficient than the driver for ext[234] file systems. Maybe both regarding cpu and ram.

So to work efficiently, use ext file systems.

---

### Post by sdowney717 on 2013-01-13
It could be so, I may test when I get time.
Idea was to render files on NTFS then network share gigabit ethernet to downstairs win7 pc vs copy files to local pc.

---

### Post by sudodus on 2013-01-13
> **sdowney717 said:**
> It could be so, I may test when I get time.
Idea was to render files on NTFS then network share gigabit ethernet to downstairs win7 pc vs copy files to local pc.
You can make win7 read ext files :-)

[[COLOR="Red"]http://sourceforge.net/projects/ext2fsd/[/COLOR]]("http://sourceforge.net/projects/ext2fsd/")

---

### Post by sdowney717 on 2013-01-13
I used that once to see its capability.
I use ext4 now.

I bought another 1tb drive and split it in half, one side ntfs, one side ext4. I can move the finished files onto ntfs so windows can see them.

Normally I render a single 26gb file and that can take 1 to 2 hours. And it uses 2gb ram. 

If you capture video off tape, kino and kdenlive default to 1gb sized clips. So turn dvgrab parameter size=0, and you capture into one huge file. One huge file edits fine in the editor as does 26 one gb files. I would rather loads one clip vs 26 clips for convenience sake.

It could be the rendering putting together 26 clips into one is the problem not the ntfs driver. Someday I will test that idea.

---

