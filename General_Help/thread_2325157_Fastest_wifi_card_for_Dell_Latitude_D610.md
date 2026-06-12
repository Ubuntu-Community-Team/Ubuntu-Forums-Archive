---
title: "Fastest wifi card for Dell Latitude D610"
date: 2016-05-19
forum: General Help
---

### Post by Ralph L on 2016-05-19
I have two Dell Latitude D610 laptops on which I would like to speed up the wifi.  If I plug directly into my cable modem (ethernet) I get 30Mbps download, but thru my Linksys wrt110 B/G/N router I get only 12Mbps download. The D610 broadcom and intel wireless cards support only "B/G", which are supposed to run at 54Mbps, but don't.  If I could find an "N" card for the D610, I think it would fix the problem, but I haven't been able to find one.  So now I am looking for recommendations on the fastest "G" card for the D610.  My current cards for the two computers are 1. Dell wireless 1370 with Broadcom BCM4318 chip, and 2.  Intel 2200BG card.  Does anybody know of faster "BG" cards?????????

I noticed a Dell wireless 1450A/B/G dual band card with the Broadcom 4309 (also called BCM4309MP) chip.  Would this card be faster?  I don't know if "dual band" means it runs faster.  Does anybody know???  The 4309 part number makes the card appear older than the BCM4318, so I don't know what to think.

Also, drivers could be slowing my wifi down.  Does anybody know if there are faster drivers for either my Broadcom card, or my Intel card????  In addition, does anybody know if the linux driver would drive the 1450 card, if I bought one????  I guess one possibility would be to run Windows drivers under ndiswrapper.  I have done this before, but it is a pain.

Any help, opinions, etc would be much appreciated.

---

### Post by TheFu on 2016-05-21
[http://www.laptop-junction.com/toast/content/dell-wifi-gets-very-slow](http://www.laptop-junction.com/toast/content/dell-wifi-gets-very-slow) - says that some of the 1370 miniCards had HW issues, so your idea to replace it seems smart. About the other card, all I found was Intel saying that miniPCI cards need to be upgraded by the vendor who provided the laptop due to FCC regs.  Looks like they really just want folks to disable the internal wifi adapter and use USB adapters. [https://wikidevi.com/wiki/List_of_Wi-Fi_Device_IDs_in_Linux](https://wikidevi.com/wiki/List_of_Wi-Fi_Device_IDs_in_Linux) is where I'd start to find wifi chips that support the 4.x kernel. I'd probably look for 3.2+ kernel support, since 14.04 is still out there and save-my-butt distros will probably have older kernels.  Also, I'd avoid the "nub" wifi USB adapters. IME, they get really hot and start to fail. Have 3 dead "nubs" here.  Oddly, the 2inch USB sticks get warm, not hot, and seem to last much longer.  

There are many different areas where wifi fails. You'll need to systematically address each point to get the best possible performance.  The router would be the 1st place I fixed. Older routers had performance issues that just don't apply to newer routers. Cheap, fast, embedded chips are made for GigE connections these days, unlike older routers.  Or if you want great wifi performance, you can add a dedicated AP to the router, disable the wifi inside the router and have some amazing connectivity for about $60. I'm talking about leaving the "consumer" level, and moving to a cheap, enterprise, WAP from Ubiquiti. These things are amazing and can have very long range in areas that don't have interference.  I've seen some of the $90 Ubiquitis provide 500ft of uni-directional coverage at a farmhouse. Simply amazing.  Of course, the bandwidth available dropped with the distance, but inside the building it was 100+Mbps wifi.  Don't be afraid of "enterprise" ... I use a free Android app to configure it at each client-site.

What is the router being used? The issue might not be with the old D610 at all. Looked up the wrt110 - seems it was pre-N draft and a 10/100 router.  Time for a new router and WAP?  Your budget would determine which router + WAP to use, but I'd stay away from the cheapo consumer brands which don't get vendor updates after 3 yrs.

[http://ubuntuforums.org/showthread.php?t=2090742](http://ubuntuforums.org/showthread.php?t=2090742) provides some steps and advice. Generally, with B/G wifi, each device halves the bandwidth. 1 device = 26Mbps; 2 devices = 13Mbps.  You get the idea. It is the connection, not the actual push of data by each device. Plus not all "N" are the same.  Turns out "N" can be 75Mbps - 300Mbps ... and those are just the theoretical connections, not real-world.  Half for every device added to the wifi-network.  It is only recent wifi solutions - "AC" - which don't have that issue to the same extent.

Drivers for Linux almost never come with any hardware. Actually, if it does, it is usually for a terribly, 5+ yrs out-of-date, kernel.  Useless.  I've found that staying with HW that has direct, good, built-in kernel support for anything I want to accomplish is the best solution. If the kernel doesn't support it out of the box, I don't want it. Use that link above.

A D610 is pretty old.  For the price of fixing these things, you could get a new-to-you laptop that is 2-5x faster. Heck, a $150 chromebook would be 3x faster and have great wifi.  Just sayin'.  You'd want to be specific about which CPU the chromebook has (some of them suck!), but still ...  Of course, the client-side doesn't do anything to fix router-side issues.

---

### Post by Ralph L on 2016-05-21
theFu
Thanks for the reply.  I will look into some of your recommendations.

---

