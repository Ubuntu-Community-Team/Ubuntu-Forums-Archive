---
title: "How do I confirm Ubuntu is running &quot;full speed&quot;?"
date: 2006-10-08
forum: General Help
---

### Post by RayH on 2006-10-08
I've been playing with Ubuntu on and off for a year, and have always wanted to have a dedicated Linux station, but I lack the skills to make Ubuntu run 100% and end up going back to Windows everytime.  Anyway, I have a fresh Ubuntu 6.06 build and even setup XGL/Beryl (which is very pretty) but before and after the XGL/Beryl setup, the system was choppy.  By other threads on the forum, it seems like I have enough horsepower to run everything, so could  you guys point me in the right direction on how to make sure everything is setup right?  Here is some basic info:

System:  AMD +2600 w/1GB Ram, 40GB hard drive, MSI 6570e MB and Nvidia Geforce4 MX440-8x card (64mb).

Linux OS Build Info:  2.6.15-27-686, Updated Nvidia driver (not sure how to verify version, but nvidia is indicated in xorg.conf).  

I think part of the delay is from video, if I run glxgears, I'm getting around 450fps, but the gears are quick for a second, and then very choppy.  Also, the system gets worse the longer that I have it running.  If I reboot, it's a little quicker for a while, then becomes slow again.  System Monitor shows an average of 80+% cpu, but the biggest cpu hog only shows 3% usage.  Memory used is only 240mb out of 1GB.

Thanks for your help.  I would eventually like to load VMWare to run W2K and my remaining windows programs within Linux if possible.

---

### Post by LORD_PoLvO on 2006-10-08
yeah this sounds like a problem with your nvidia driver not the system system itself ( i run amd athlon xp 2600+ 512 mb ram and used to use a geforce 4 mx 440 i have a 6600 now)

but yeah from the soudns of your glxgears its the driver thats the problem 

what nvidia driver version are you currently using??i sugest reinstalling your nvidia driver again which can be downaloded from 

[http://www.nvidia.com/object/linux_display_ia32_1.0-8774.html]("http://www.nvidia.com/object/linux_display_ia32_1.0-8774.html")

if you dont know how to install ask me and i will help or there are lots of tutorials on the subject in this verry forum

---

### Post by RayH on 2006-10-08
Thanks for the quick reply.  I bet you're right, I think I assumed that the NVidia drivers were updated when I followed the directions for XGL/Beryl.  I'm installing the drivers via your link now.  Already running into dependencies, which I'm resolving.  Thanks for the offer of personal help, I'll get as far as I can by myself (I learn great that way) and will post my results when I'm done (including new glxgear numbers).

---

### Post by RayH on 2006-10-08
Okay, some progress.  I installed the dependencies and it performed the install.  Started gdm and it appeared to be noticeably faster, at least at first.  Ran glxgears, and it's a little slower, around 300fps.  So I rebooted, and now x server fails to load.  Tried copying xorg.conf.backup_* back to xorg.conf and it still fails.  I'm searching the forum now on how to fix it, but if you know the exact fix, feel free to post.  Thanks for your help so far!

---

### Post by RayH on 2006-10-08
I tried the various ways to restore the gui (dpkg-reconfigure xserver-xorg with vesa and vga) with no luck, so I'm doing a fresh reinstall.  Since I'm doing a fresh reinstall, is there a specific order that I should update everything?  For instance, if I want to run the 686 kernel, I assume that I should update that before I install the Nvidia driver?  Should I update anything else before doing so?

---

### Post by podunk on 2006-10-08
I'm not siure - but isn't the 686 kernel for Intel P4's? I'm using the k-7 for my Sempron.

Beryl and compiz is indeed very pretty - but on my computer with an older card it really does slow things down. This is very bleeding edge stuff.

I found the program 3ddestop in the package manager. It gives some of the effects of compiz without the overhead.

I never thought about a benchmark. On every machine I've set up on Ubuntu was just so visably faster that the thought never occured to me.

---

### Post by tommcd on 2006-10-09
Yes, the k7 kernel is for Athlon CPUs. It is possible to use the 686 kernel though. I use the k7 kernel for my AMD athlon64 CPU. I don't notice any increase in performance over the default 386 kernel though. 
For the nvidia driver, you should be able to use the driver from the repos:
[https://help.ubuntu.com/community/Latest_Nvidia_Dapper?highlight=%28nvidia%29%7C%28latest%29](https://help.ubuntu.com/community/Latest_Nvidia_Dapper?highlight=%28nvidia%29%7C%28latest%29)
Use method #1 (easiest).
Or, for the short and sweet how-to:
[http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Dapper#How_to_install_Graphics_Driver_.28NVIDIA.29)
The gforce4 mx440 is listed as compatible:

[http://doc.gwos.org/index.php/Nvidia](http://doc.gwos.org/index.php/Nvidia)
Hope this helps.

---

### Post by RayH on 2006-10-09
Thanks guys.  I stumbled upon all this stuff as well last night during my forum searches.  I now have a fresh 6.06 install with the NVidia drivers installed per your link (method 1), and also have the K7 kernel installed.  I installed XGL/Beryl and it was running better, for a while.  Glxgears posts roughly 340fps in beryl and around 250 in metacity, and the gears are visibly very choppy, but general redraw is fairly quick.  One problem I noticed is that loading Firefox slows the system down considerably, regardless of CPU load and memory usage never goes over 320mb out of 1gb.  I tried Opera and it's marginally better but not by much.  I wonder if I need drivers for my chipset for proper support?  As a baseline, I'm going to do an identical install on a P4 1.8 w/512mb and a GeForce2 MX200 card, to see how the numbers/performance add up.  It just seems like the system is ok at first, then becomes increasingly sluggish in a short amount of time.

---

### Post by RayH on 2006-10-09
Building the P4 1.8 as I type, and on my AMD 2600, I switched the window manager back to Metacity... even though glxgears reports a slower draw, it's noticeably faster.  Do you guys think it's a matter of upgrading the video card?  Faster cpu?  Both?  If it's just the graphics card, is there a relatively inexpensive (say under $100) card that I can upgrade to?

---

### Post by tommcd on 2006-10-09
I don't have any experience with XGL/Beryl, so I can't help with that. I know many people have had problems with it though. Did you try glxgears before installing XGL/Beryl? Perhaps they are causing the slowdown.
As for a video card, I assume it is AGP. So you could get:
[http://www.newegg.com/Product/Product.asp?Item=N82E16814121542](http://www.newegg.com/Product/Product.asp?Item=N82E16814121542)
The nvidia 6600 cards are just over $100:
[http://www.newegg.com/Product/Product.asp?Item=N82E16814130232](http://www.newegg.com/Product/Product.asp?Item=N82E16814130232)
You will need a spare molex power connector for the 6600, but not the 6200. I have a 6200 in my system and I can play Doom3 and Quake4 at 1024x768 resolution with no problem. I had to turn down the effects for quake4 a bit. But the 6200 should handle XGL ok.
EDIT: If you don't have an AGP slot, and you need a PCI video card, then perhaps this:
[http://www.newegg.com/Product/Product.asp?Item=N82E16814130255](http://www.newegg.com/Product/Product.asp?Item=N82E16814130255)
Hope this helps.

---

### Post by RayH on 2006-10-10
tommcd - That was a lot of help actually, thanks.  My current card (the Geforce4 MX440 is an AGP 8x with 64mb of DDR, so I thought it would be plenty fast, but by reading on the forums, it appears that the more powerful systems are pushing 3600fps or so, and mine pushes anywhere between 250-450fps, depending on my setup.  I thought it would push more, but even with a basic build with the k7 kernel and updated nvidia drivers, I'm getting around 300fps.  I've been running this system with Beryl disabled and it's been running great, no more sluggish performance with Firefox no matter how long the system has been running, so I guess I'll wait until either the eyecandy is streamlined enough to run on a slower graphics card, or I'll upgrade eventually if it gets to me enough.

On a good note, I setup vmware server and a W2K VM on it tonight... runs sweet (plenty fast)!  So at least I achieved my real goal!

Thanks for the advice Tom (and all).

---

### Post by august_rzl on 2006-10-11
I have Ubuntu running on my Intel p4, 512 mb ram, and GeForce mx 440 (64 MB) agp. It seems that Ubuntu runs an i386 kernel by default. It does'nt have a performance. I want to update the kernel that match to p4. What should i do to update the kernel ?

---

### Post by tommcd on 2006-10-11
august_rzl,
A P4 CPU should use the 686 kernel. To get it:
'sudo apt-get install linux-686' in terminal. If your CPU has hyperthreading or is dual core, you want the 686-smp kernel.
'sudo apt-get install linux-686-smp'
Read this thread first:
[http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)
Everything you would ever want to know about kernels. Hope this helps.

---

### Post by podunk on 2006-10-11
340 FPS on a 64 MB video card seems slow? You might want to recheck your driver set up.

Compiz and all that is *very* cutting edge beta stuff. I decided after breaking the heck out of everything to stay away til it;s more stable and I know more - the me knowing more being most important part of the problem. :-)

As far a s new cards, check out Tigerdirect.com - they beat new egg every time I've checked. Look out for the rebate deals though - it's hell getting a rebate from these people. If it ain't a good deal at the listed price don't count on the rebate.

---

### Post by linkunderscore on 2006-10-11
i have the mx440 and its complete crap. I am suprised you even got xgl+compiz running at all with it. If you want to run xgl compiz or any graphics card intensive application you should probably invest in a better gfx card. 

You could get a 5700 or 6000+ for ~$100 or less. And those would run xgl+compiz great.

---

### Post by RayH on 2006-10-12
Thanks for all of your replies and thanks for the specific MX440 comparisons!  Yeah I've been running Metacity and it's running great, much more like I suspect it to, and I'm finding that the eyecandy isn't as needed as I thought.  I'm running VMWare with a W2K VM and that runs great on it too.  So you guys are absolutely right, it's a matter of me upgrading the video card when I'm ready.

All good stuff.  You guys are awesome on this forum, I hope as I proceed to learn more, that I can help out more people as you have helped me.  This forum is a great example of how all forums should be!

---

