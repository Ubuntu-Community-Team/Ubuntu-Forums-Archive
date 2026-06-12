---
title: "server request hangs"
date: 2015-08-09
forum: General Help
---

### Post by bandito40 on 2015-08-09
I am running Ubuntu 14.04 on Chromebook c720.  About every 5 mins the requests made from another computer seam to hang for about a minute every 5 minutes.  I noticed it using telnet and also kodi remote control which runs http requests on port 8080. Anything one know why?

---

### Post by TheFu on 2015-08-10
I don't think this is c720 specific.  I would guess it is either interference on the wifi channel in use or DNS issues - try a better DNS server.
For LAN connections, it is best to have all systems on the LAN know about each other by using static IPs and managing the /etc/hosts files on all the LAN devices.  That will remove any dependency on DNS for local requests.

BTW - I found the default swap file sized during an ubuntu install on the c720 to be 50% too small at 2G. Modern web browsers are RAM hogs and make having more swap necessary.  Before I increased the swap size to 4G, my C720 would lock up with out-of-memory failures about once a month.  Since then - never locks up for that reason.

---

### Post by bandito40 on 2015-08-16
> **TheFu said:**
> I don't think this is c720 specific.  I would guess it is either interference on the wifi channel in use or DNS issues - try a better DNS server.
For LAN connections, it is best to have all systems on the LAN know about each other by using static IPs and managing the /etc/hosts files on all the LAN devices.  That will remove any dependency on DNS for local requests.

BTW - I found the default swap file sized during an ubuntu install on the c720 to be 50% too small at 2G. Modern web browsers are RAM hogs and make having more swap necessary.  Before I increased the swap size to 4G, my C720 would lock up with out-of-memory failures about once a month.  Since then - never locks up for that reason.

It tried a few different methods of what you had said.  The first one which seamed to work the best was just reformatting the swap partition with DD.  It worked great then I tried to resize the partition with the Live stick and it crashed.  I reinstalled Ubuntu this time with a 6gb swap partition but doesn't seem to have solved the problem.  Since I reinstalled Ubuntu I no longer have command line history and I can't remember exact DD command I used or where I had found it.  By chance would you know what the syntax for the DD command should be?

---

### Post by TheFu on 2015-08-16
I always use **mkswap** to create swap partitions. Haven't ever used dd , but dd has a manpage, if you need that.  **man dd**
It has been so long, I don't remember the original issue.

---

### Post by bandito40 on 2015-08-19
I tried mkswap and dd again.  Seams to work until I reboot. It's weird because directly at the computer the lagging never happens.  Only over the network. I have tried three different routers also.  Very strange.

---

### Post by TheFu on 2015-08-19
Did you fix the /etc/hosts already?

---

### Post by bandito40 on 2015-08-20
I fixed the host file on both machines. I added **192.168.0.1 one.machineone one** to the host file on computer 2 and **192.168.0.2 two.machinetwo two** to the host file on machine one. Still have the same problem.

---

### Post by TheFu on 2015-08-21
> **bandito40 said:**
> I fixed the host file on both machines. I added **192.168.0.1 one.machineone one** to the host file on computer 2 and **192.168.0.2 two.machinetwo two** to the host file on machine one. Still have the same problem.

While I suppose it doesn't hurt to use those FQDNs, I've never seen anyone do that on a LAN.  There is a network heirarchy implied with FQDN. Machines on the same LAN, usually have the same domain-name or no domain-name set. Try this in the /etc/hosts

```
127.0.0.1 localhost
192.168.0.1 one
192.168.0.2 two

```
Alas - I doubt that is the issue and it is probably the wifi and interference. I don't use wifi with my C720 much - never at home.  Wifi is prone to interference and is impossible to resolved for most people.  If the location is half a mile away from all neighbors, the you should be able to get this working better. If the location is an apartment, dorm, or even quarter acre single-family-home lots, the neighbors could easily be the cause with their 2.4Ghz stuff.  Many wifi routers have a "site survey" mode to find available channels.  On 802.11g (and any 2.4Ghz only routers), there are only 3 channels that do not overlap and interfere with the other channels - 1, 6, 11.  [http://ubuntuforums.org/showthread.php?t=2271116&highlight=wifi+interference](http://ubuntuforums.org/showthread.php?t=2271116&highlight=wifi+interference) explains.

---

### Post by bandito40 on 2015-09-06
Modifying the host file as you have shown seems to have solved the problem.  It was acting up one day but I think that may have been related to heat.  The room I have the router in gets pretty heated up on some of the hotter days.

---

### Post by bandito40 on 2015-10-09
I know I marked this thread as solved.  It has been a month now since the last post on this thread.  Just wanted to give the latest update. My router is dual band.  Runs on 2.4 mhz and 5 mhz.  Appears the problem I was having is related to band frequency. When both computers are on 5 mhz the system runs smoothly.  When one or both are on the 2.4 mhz then it lags. Having said that I am sure that the problem will return once my neighbourhood starts to use 5 mhz routers so the real solution is to hard-wired.

---

