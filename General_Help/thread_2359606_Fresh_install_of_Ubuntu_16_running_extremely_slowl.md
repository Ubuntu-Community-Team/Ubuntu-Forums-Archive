---
title: "Fresh install of Ubuntu 16 running extremely slowly"
date: 2017-04-25
forum: General Help
---

### Post by charles-laferriere on 2017-04-25
Hello folks,
I'm fairly new to ubuntu. 
I've wiped the disk and installed a fresh ubuntu install. 
Funny thing. 
As soon as I have, for instance, music on, and facebook, or an application installing, it is incredibly slow. Music is hectic. 
It is running on a quad core i5, 4gb ram, 240gb hard drive.
So. Yeah. It doesn't make sense :\ 
My intention was to create a home server with it. Any inputs welcome.
Charles

---

### Post by TheFu on 2017-04-25
Welcome to the forums.  You've explained the issue, but haven't provided any details about the system itself or the configuration.

We need more facts.

So - when it comes to troubleshooting Linux issues, there are a few common techniques.
* check the log files. google "ubuntu log files" to find how.
* verify the different components are using the best drivers available.  Use **sudo lshw** to see all the hardware and the drivers.  Then search for the exact chip and ubuntu for any known issues. Look for specific sound drivers, GPU drivers as the main issues.
* Not all Core i5 CPUs are created equal.  A 1st generation compared to a 6th generation are like night and day.
* Poor system performance can be traced back to all sorts of things. 
** Make certain you are completely patched - **sudo apt update && sudo apt upgrade** Run those commands weekly.
** Check for partition sector alignment issues first. Google for how to do that.
** Check for DNS issues - yes - DNS.  It can make a fast machine slow if DNS isn't working well.
** Never let any partition on a disk have less than 2GB of free storage. It used to be more than 95% utilized, but with larger disks, this wasted a bunch of storage for no good reason. 
* If you don't have a GUI, things will run much faster, but you cannot run GUI applications.
* Did you enable disk encryption?
* Which process is using all the CPU?  Use **top** to see that.
* Which process is using all the RAM?
* How is the virtual memory being handled?  **vmstat** or **free** can show that.
* Different music players are heavier than others.
* If you've asked for 50 things, CPU is fully used and RAM is overused, then audio playback could stutter.

An "ubuntu server" wouldn't have a GUI, so I'm unsure what you mean about facebook or music.  Please explain.

All of the commands above are run from a shell.  It is important to learn those since you said "server" - forget GUI tools.

---

### Post by charles-laferriere on 2017-04-26
Well that first reply made me lose a few baby teeth..
Ok, so far:

[B]
[COLOR=#000000]So - when it comes to troubleshooting Linux issues, there are a few common techniques.[/COLOR]
[COLOR=#000000]* check the log files. google "ubuntu log files" to find how.
[/COLOR]more than 350 pages.  not sure if it's normal? I think I would starve before going through that :\ 

[COLOR=#000000]* verify the different components are using the best drivers available. Use [/COLOR][/B][B]sudo lshw to see all the hardware and the drivers. Then search for the exact chip and ubuntu for any known issues. Look for specific sound drivers, GPU drivers as the main issues.
Yep, seems ok,

* Not all Core i5 CPUs are created equal. A 1st generation compared to a 6th generation are like night and day.
1rst gen. :)

* Poor system performance can be traced back to all sorts of things. 
*shrug*

** Make certain you are completely patched - sudo apt update && sudo apt upgrade Run those commands weekly.
Thanks, will do.

** Check for partition sector alignment issues first. Google for how to do that.
----havn't gone through completely on this one yet-------

** Check for DNS issues - yes - DNS. It can make a fast machine slow if DNS isn't working well.
!!! When I unplug the Ethernet cable, the computer has a normal, good and steady speed. 
This seems to be "IT"!

** Never let any partition on a disk have less than 2GB of free storage. It used to be more than 95% utilized, but with larger disks, this wasted a bunch of storage for no good reason. 
Roger.

* If you don't have a GUI, things will run much faster, but you cannot run GUI applications.
My intention was to create a home server ubuntu based. Thought i would run it through a vmbox?

* Did you enable disk encryption?
Yes.

* Which process is using all the CPU? Use top to see that.
Firefox, using 30ish percent.
Nothing else... sometimes software updater with 10-12%. 
It still doesn't run properly... incredibly slow. UNTIL I unplug the cable. 

* Which process is using all the RAM?
Frefo and xorg? It's incredible fine NOW as i'm typing this from another computer.

* How is the virtual memory being handled? vmstat or free can show that.
free 1081984 
buff 94144
cache 1771648


* Different music players are heavier than others.
Noted. It was youtube.

* If you've asked for 50 things, CPU is fully used and RAM is overused, then audio playback could stutter.
I asked for youtube, and two webpages. It could take as long as 1 minute to switch tab, it would freeze for, sometimes, 2 to 3 minutes at a stretch. Unusable really..

An "ubuntu server" wouldn't have a GUI, so I'm unsure what you mean about facebook or music. Please explain.

Hm. Well, I thought I would get my "teeth" into the world of servers through a VMbox ubuntu server? while still using the gui? I'm likely an idiot here.

All of the commands above are run from a shell. It is important to learn those since you said "server" - forget GUI tools.
Got it. Will do.[/B]

---

### Post by charles-laferriere on 2017-05-07
Poop.

---

