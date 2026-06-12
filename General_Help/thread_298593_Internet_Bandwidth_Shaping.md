---
title: "Internet Bandwidth Shaping"
date: 2006-11-12
forum: General Help
---

### Post by PacShady on 2006-11-12
Hey all

Previously posted this in "Other Support Categories" but now I can't write to it, plus it seems no one saw it anyways. I need a Linux alternative to the program "NetLimiter".

NetLimiter is an all-purpose bandwidth shaping utility. Not only can it shape a computer's entire network connection, but it's ALSO good for limiting specific programs traffic, blocking traffic altogther, and one can also set up time conditions on limits imposed on programs, for instance, one program can be shaped between the hours of 8am-8pm at 8KB/s, and outside of these times shaping is removed. This kind of setup is really awesome for instance setting up a download program to download at full speed during night, but during the day traffic for that specific program is slowed to allow other programs such as web browsers etc. to use the free bandwidth.

Unfortunately, my searching so far has only brought up QoS shapers, which work on a priority system which I've found to be quite ineffective for what I need, rather than a fixed limiting system like NetLimiter. Also, I've not found one program at all so far that has a graphical frontend (so call me a n00b, I don't care, I HATE using the command line for advanced functions like this), and I've not found one program either that has time conditions that are able to be set, so one must make changes manually whenever shaping is required (which defeats the purpose of what I need it for). Finally, many of the shapers I've found are for large networks, and shape entire connections to workstations rather than specific programs.

So, is there any solution to this on Linux? I think a great number of home users would benefit from such a program as this, but so far I've had no luck in finding one.

'Shady

---

### Post by evilghost on 2006-11-13
[http://packages.ubuntu.com/dapper/net/trickle](http://packages.ubuntu.com/dapper/net/trickle)

Consider using Trickle.

---

### Post by PacShady on 2006-11-14
I think I've looked into Trickle, it's a CLI program, and I think was about the only program that allowed the shaping of singular programs on a workstation, however I don't think it had automatic shaping rule changing which is what I need.

I do a LOT of downloading, mostly on BitTorrent, which ties up my very slow 256k connection and prevents myself and anyone else on my home LAN from browsing on the internet normally (it gets even worse when my connection is shaped to 64k!). At night, I like BitTorrent to download at maximum speed, but during the day (starting from about 6am) I need it to slow down to allow for others at home to use my connection. Since I have a sleeping disorder that means I usually don't wake up until LONG after this time, I can't regulate the bandwidth myself, thus the need for automatic shaping set to specific rules dependent on the time of day. And I'd really not like to have to deal with getting another box to set up as a proxy server, my *nix expertise isn't exactly advanced enough I'd feel comfortable trying to do that kind of thing with, not including the fact I ran out of power points a LONG time ago, and the best "available" box I have is a Pentium 100 from 1995 with maybe 200MB HDD and 32MB RAM, plus any solution like that for it to work to ANY degree it would need to be able to shape ports instead of entire LAN IP's.

At the moment, if I plan on downloading anything on BitTorrent, I need to boot into Windows (*shudder*) and allow NetLimiter to do the job for me. I'd really love a Linux alternative, I'm sick of Windows, and the sooner I can ditch it the better, this is one of the last things I need an alternative for.

'Shady

---

### Post by fragos on 2006-11-14
If a priority based scheme isn't working for you its not, or for some reason can't be, configured correctly.  Prioroty based shaping makes better use of your total bandwidth by allowing low priority traffic to burst during lulls in high priority traffic.  Many QoS implemetations are limited in effectiveness because of the amount of CPU power required.

---

### Post by esaym on 2006-11-14
> **PacShady said:**
> I think I've looked into Trickle, it's a CLI program, and I think was about the only program that allowed the shaping of singular programs on a workstation, however I don't think it had automatic shaping rule changing which is what I need.

I do a LOT of downloading, mostly on BitTorrent, which ties up my very slow 256k connection and prevents myself and anyone else on my home LAN from browsing on the internet normally (it gets even worse when my connection is shaped to 64k!). At night, I like BitTorrent to download at maximum speed, but during the day (starting from about 6am) I need it to slow down to allow for others at home to use my connection. Since I have a sleeping disorder that means I usually don't wake up until LONG after this time, I can't regulate the bandwidth myself, thus the need for automatic shaping set to specific rules dependent on the time of day. And I'd really not like to have to deal with getting another box to set up as a proxy server, my *nix expertise isn't exactly advanced enough I'd feel comfortable trying to do that kind of thing with, not including the fact I ran out of power points a LONG time ago, and the best "available" box I have is a Pentium 100 from 1995 with maybe 200MB HDD and 32MB RAM, plus any solution like that for it to work to ANY degree it would need to be able to shape ports instead of entire LAN IP's.

At the moment, if I plan on downloading anything on BitTorrent, I need to boot into Windows (*shudder*) and allow NetLimiter to do the job for me. I'd really love a Linux alternative, I'm sick of Windows, and the sooner I can ditch it the better, this is one of the last things I need an alternative for.

'Shady
Taken a step farther it would not be hard to run QOS that would allow bit torrent to use all the available bandwidth without causing problems.

I would recommend getting smoothwall set up as the gateway and firewall to your network and install the QOS mod for it.

I have mine set so that all unclassified traffic, which includes p2p traffic, gets all the available bandwidth.  Pings stay low, web browsing is crisp, and no matter what happens on the network I never get any lag in online games. 

Oh and yes you will need another (older) computer to run it :)

[http://community.smoothwall.org/forum/viewtopic.php?t=7922&sid=b93477e83eb656902fe2192b819aca56](http://community.smoothwall.org/forum/viewtopic.php?t=7922&sid=b93477e83eb656902fe2192b819aca56)

---

### Post by PacShady on 2006-11-14
The thing with priority-based solutions, is that I'd need to set up a proxy server between my LAN and my ADSL router to set it up. I doubt setting up a workstation-based priority system would work, since my computer is not likely to know if and when another computer on the network is using bandwidth. The only available system built into my router (I think) is QoS, which doesn't seem to work correctly, or else I just don't understand it enough to set it up correctly. So if I am to use priority-based systems, then my only option would be to set up my Pentium 100 with some relatively easy-to-set-up proxy program that does priority-based port shaping and set it up between the LAN and ADSL router. I'd also have to know that, in the event of a power failure or what not, that when I press the power button on the proxy box, that it will boot up and return to working order with all options intact without the need for interaction since I obviously won't be having any peripherals attached to it. Preferably, it would also need a web-based interface that I could change settings on.

If I was to use a solution as this, is there any possibility of setting up the same box to run as an internet content filtering system, that can be set up to use different options on different LAN IP addresses? This isn't a required service, it's just something else I've been looking out for lately. Thanks

'Shady

---

### Post by nix4me on 2006-11-14
Use m0n0wall on an old computer with 2 ethernet ports as a router/firewall.

Traffic shaping is built into m0n0wall and works very nicely.

nix4me

---

### Post by PacShady on 2006-11-14
With any of these proxy solutions, do you know how easy it might be to get some kind of web content filtering software, such as dansguardian, to be installed with them? Or if a priority-based shaping service can be set up on a CensorNet box and used as a proxy? Just wondering.

'Shady

---

### Post by esaym on 2006-11-15
I would not call these "proxy solutions".  They are gateways with built in firewalls.  Smoothwall has more mods then you will ever be able to find a use for.  Just spend about 2 weeks on the forums and read read read read. The mods are very easy to install. [http://community.smoothwall.org/forum/viewforum.php?f=16](http://community.smoothwall.org/forum/viewforum.php?f=16)

Like I said, the only draw back to smoothwall is needing another computer.  100mhz might work but ask on the forums for more info:mrgreen:

---

### Post by PacShady on 2006-11-15
Sweet, unless someone can suggest a better option, looks like this Smoothwall might be my best bet, already I've found mods for Dansguardian AND QoS. When I finish my exams, I'm definitely looking through their forums and looking at what they've got. Thanks!

'Shady

---

### Post by esaym on 2006-11-17
Glad you like it.  The QOS setup can be kinda scary.  The qos with gui that Netwhiz made started from a wondershaper script that I and a few others were using about 3 years ago so I know my way around it pretty good.  I have pictures of example set ups if you want to see them, just pm me.  I'm sure some pics are in the thread though.  You should read the whole qos thread.  Even though its long it has lots of good info in it, sadly some of the  same questions are asked on on every page so don't fall victim too :wink:

If there is a qos term or feature that you don't understand then type it on google.  There is lots of information on google about qos.

---

### Post by PacShady on 2006-11-17
OK, started playing round with SmoothWall, got one set up and working fine with fixes 1-9 installed. Then when I installed the SuperKernel (needed for QoS), it stopped working with my ethernet cards (it still detected them, still knew what they were, just couldn't connect to anything outside of them). Same goes for when I install using the SuperKernel ISO (slightly out of date now), same results. I'm now trying to ask about what could be causing it in the forum, see if they have any ideas as to why it's not working for me.

'Shady

---

### Post by airtonix on 2007-04-14
what about this: (im not sure about the argument for loading an iso image with vmware)

> trickle -d 40 -u 10 `vmware uber-lightweight-linux-firewall-distro.iso`this iso would have something like damn small linux or someother variant....

since ive called up vmware to load a pre-setup virtual machine via trickle, it limits the speed that could possibly come out of the virtual network cards in the virtual-machine.

and forgive me if i am wrong but i think you can actually create as many network devices on a virtual machine as you need...so this means you can setup different vitual-server-proxy-shaper-servers for any ip or subnet....

what you would do also is to make the gateway of all your flatmates machines the ip of the virtual machine running the ISO. then on the virtual machine you would make its gateway the IP of the real-machine its running on....in effect he virtual mchine becomes just another puter in your subnet.


[I]but does this work he says? im not sure would be cool to do. think of all the other things you could do with virtual machines?

12:56 PM : i just found the "[/I]uber-lightweight-linux-firewall-distro[I]" it has traffic shaping as part of its feature list, and its only 5megs : [http://m0n0.ch/wall/](http://m0n0.ch/wall/)__
[/I]

---

