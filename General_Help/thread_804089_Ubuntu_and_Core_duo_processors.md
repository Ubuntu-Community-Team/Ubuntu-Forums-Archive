---
title: "Ubuntu and Core duo processors?"
date: 2008-05-22
forum: General Help
---

### Post by esteckis on 2008-05-22
Does Ubuntu take advantage of Core Duo? Hello everyone and thanks for your help. Here are some questions and I am a little confused.

My two systems are:

Laptop Dell 6400 with Intel Core duo 1.6 dedicated ati 124mb video, 1 gig of ram.
Desktop AMD 3600 = 1.6 duo processor. ATI 1250 on board video 256 mb, 2 gigs of ram.

When I use windows with speedswitch (scales processor down on lappy)per demand and SafeXP (which lets me disable a lot of windows xp stuff that I don't need) My processors are running at 1% with no  other programs running by me on the lappy and desktop.

When I use UBUNTU on either system, with me having no programs running by me, the system resources monitor shows 30% use and on each system I see the processor graph showing the 30% processor use switching back and forth between each processor.  Is UBUNTU really set up yet for duo processors?  I thought the ideal way for processor use was to spread the resources evenly between each processor? Is the Ubuntu system monitor giving me a really accurate graphic reading?  If I go to the system monitor and check all the processes running, I only ever see something using 1 or 2 % of system resources (of course I have checked off to view all processes). 

I have all the indexing disabled on Ubuntu already because I never need to do such intense searches. Anyhow, I find it more beneficial for me to learn the file structure by manually browsing the folders.

The other reason I ask this is because on my Dell 6400 Lappy with the 9 cell battery, I get 5 hours runtime time using XP.  Using Ubuntu, I only get 3-1/2 hours runtime.  There are two things that I can think of that cause the difference in battery time.

1 ATI driver: under XP use, the ATI driver has a battery option to  extend battery time but not on UBUNTU.
2 Broadcom driver for wireless.  Could it be that these restricted drivers are not really written for efficiency under Ubuntu?

---

### Post by ryanhaigh on 2008-05-22
If you open the terminal (apps>accesories>terminal) and enter the command ```
top
``` you will get a list of running processes sorted by cpu usage which is a little easier to read. This should give you a better indication of whats using all your cpu.

The other thing you can do is check whether your cpu is being scaled. There are other ways to do this by the easiest is (in the terminal again) use the command ```
cat /proc/cpuinfo 
```.

Ubuntu is quite capable of using the dual cores of your systems cpus but as with any os only threaded processes may be balanced accross the cpu, if a single threaded process is using all your cpu you will see only one core active at a time, the load is often transfered between the cpus as you have seen.

One point I would mention is that while ubuntu can use your 2 cores the generic kernel is not taking advantage of ALL the features of your cpu, perhaps the SSE extensions and certainly the 64bit. Whether you want to change the the 64bit version depends on how badly you want to use your cpus full capacity. Personally, because of some issues people experience when using 64bit, I have chosen to stick with the i386/generic system however I have read that there are fewer issues with the latest 64bit versions.

---

### Post by esteckis on 2008-05-22
Thanks for the ideas, I will definitely try your suggestions to see why the system monitor graph is always showing 20 to 30% CPU usage when I am not running any programs.

---

### Post by mockingbird on 2008-05-22
I'm not really familiar with the Debian install process,

But you might have to recompile your kernel to take advantage of your CPU.

For a great guide (Don't worry Ubuntu 8.04 and Etch are virtually identical), go here:

[http://www.howtoforge.com/kernel_compilation_debian_etch](http://www.howtoforge.com/kernel_compilation_debian_etch)

---

### Post by lavinog on 2008-05-30
> There are two things that I can think of that cause the difference in battery time.

1 ATI driver: under XP use, the ATI driver has a battery option to extend battery time but not on UBUNTU.
2 Broadcom driver for wireless. Could it be that these restricted drivers are not really written for efficiency under Ubuntu? 
Yes and Yes

1: Which ati driver are you using? The ati restricted driver causes some issues with suspend. but there are a couple of things you can do with aticonfig: (type aticonfig --help    and look for info on powerplay settings)
In windows my laptop (ATI radeon express 200m) with powersave on reduced the graphics capibilities...many things looked like they use 16 bit color instead of 24bit like gradients are blocky.

2: The restricted broadcom driver i think is the ndiswrapper driver...which was written for windows...not linux. If it isn't the ndiswrapper driver and it is the broadcom bc3 driver then it is a product of reverse engineering and still has many bugs because broadcom doesn't support linux.

3: another thing that maybe eating up your battery is hard drive usage. can you hear your hard drive spin up and down frequently...you may need to tweek it. Unfortunately there is no easy way to do this yet.

> I will definitely try your suggestions to see why the system monitor graph is always showing 20 to 30% CPU usage when I am not running any programs.
Currently it seems that the system monitor graph uses alot of processing power...try raising the the update interval and see if the cpu usage drops.

---

### Post by bla on 2008-05-30
Well in ubuntu 8.04 system monitor shows how much each cpu is doing...

---

### Post by esteckis on 2008-05-31
On my desktop with the AMD dual core 3600 = 1600 mhz, I did the CPU info and also installed the 64 bit version Heron which made a big improvment. I also see on the cpu info that speed steeping is being utilized which I like because why run at full speed all the time and heat everything up when it is not needed. The laptop I will figure out later on.

---

