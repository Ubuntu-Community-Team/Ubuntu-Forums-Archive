---
title: "Site unaccessible from Kubuntu, yet accessible from MS"
date: 2006-12-08
forum: General Help
---

### Post by mibadt on 2006-12-08
Hi,
I'm on a fully updated Kubuntu Edgy, connected to a 10.0.0.x LAN which includes a router and ADSL modem. I use this PC regularly without any problem accessing the Internet (browsing, email, usegroups, etc.). This Kubuntu also runs the Guarddog FW.

Until about 2 weeks ago, I could browse the site [www.keh.com](www.keh.com) both using firefox and Konqueror (both configured to accept cookies). I the last to 2 weeks, I cant access that site from either browser (it just hangs a long time), while, at the same time, I access it from a MS based pc/Firefox located on the same 10.0.0.X lan. I even tried to temporarily disable the Firewall on my Kubuntu, without any improvement.

THe KUbuntu gets the NS resolved as can be seen from the following 2 lines (nada afterwards):

ping [www.keh.com](www.keh.com)
PING [www.keh.com](www.keh.com) (64.156.7.29) 56(84) bytes of data.


Does anybody has a clue what's going on?

---

### Post by lloyd_b on 2006-12-08
That's an interesting one.  I just tried it from Ubuntu/Firefox - same thing.  What's interesting is that Xorg jumped from 2% cpu usage to over 30% cpu usage, and Firefox cpu usage jumped way up as well.  At the same time, network activity dropped to 0.

So the problem is NOT with your machine.  I suspect that the site has added *something* that's that's MS specific.  What that might be I have no idea.

May I suggest posting this to the Firefox support people?  If MS has come up with a new trick for making Firefox break, then they need to know about it.

Lloyd B.

---

### Post by eXisor on 2006-12-08
Site loads fine for me in ubuntu/ff2/opera, so it's not a ff2/opera/ubuntu problem. It could be you guys have a suboptimal mtu setting for the site.

---

### Post by lloyd_b on 2006-12-08
"Suboptimal MTU setting"?  First time I've ever heard that one.  My MTU is 1514, which I believe is pretty much standard for ethernet.

Or are you referring to the path MTU?

Note:  It's not a matter of "slow" loading - the site just flat out doesn't load (and with network monitor showing 0 bytes being received).

Lloyd B.

---

### Post by mibadt on 2006-12-08
Originally, my MTU has been the standard 1500.
I've tried several lower values all the way to 576 without any improvement.

---

### Post by Johan! on 2006-12-08
The site works OK here. (Ubuntu 6.10, Firefox 2)

BTW, the URL of the site after it's fully loaded is:
[http://www.keh.com/onlinestore/home.aspx](http://www.keh.com/onlinestore/home.aspx)
Maybe this URL works?

---

### Post by lloyd_b on 2006-12-08
This is getting weirder and weirder.  I went into the other room and fired up the desktop (XP/Ubunutu Dual boot).  I can access that site from both Windows and Ubuntu.  I can even access it from Konqueror (the machine has KDE installed, though I normally run Gnome).

Both machines access the internet via the same DSL connection.

The Firefox version on the desktop is IDENTICAL to the version on my laptop.  Both machines are updated to all most-recent (6.10) from the repositories.

The only difference is that the desktop (with it's tons of disk space) has pretty much everything loaded on it, while the laptop has a smaller subset of the available packages.

There's obviously a secondary factor involved, but I'll be damned if I can figure out what it is...

FYI: While trying to load the site, I do get redirected to "www.keh.com/onlinestore/home.aspx".  It just never loads anything after that.

Lloyd B.

---

### Post by eXisor on 2006-12-08
lloyd_b: MTU = Maximum Transmission Unit. AFAIK 1500 is the max possible.

An incorrect mtu may lead to slowdowns AND sites not loading at all.

Your optimal mtu is basically decided by your isp. Mine (iBurst), for instance, operates best at 1352. Anything above that may work, but some sites (gmail, hotmail etc) won't load at all.

I don't know if there is a linux equivalent, but in windows you can use drtcp or tcpoptimizer to check and set the mtu. The latter tool lets you test for packet fragmentation at a specific site, so it may help in diagnosing the problem.

---

### Post by Arisna on 2006-12-08
The site just loaded for me in a rather heavy Kubuntu Dapper environment using Konqueror, with and without Privoxy running.  I also have the Flash 9 beta installed, but I don't think there is any flash there.

---

### Post by lloyd_b on 2006-12-08
> lloyd_b: MTU = Maximum Transmission Unit. AFAIK 1500 is the max possible.

Tell that to Linux:

```
lloyd@laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 08:00:46:02:7A:34  
          inet addr:192.168.0.25  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::a00:46ff:fe02:7a34/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1514  Metric:1
          RX packets:157582 errors:0 dropped:0 overruns:0 frame:0
          TX packets:127120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:140218641 (133.7 MiB)  TX bytes:13037957 (12.4 MiB)
```

Note that MTU is set to 1514.  This is the default that the machine starts up with.

> Your optimal mtu is basically decided by your isp. Mine (iBurst), for instance, operates best at 1352. Anything above that may work, but some sites (gmail, hotmail etc) won't load at all.


What you're talking about is what I called "path MTU" - the MTU between you and an internet site (as opposed to the MTU between you and other machines on the local network).

You know, in 15+ years working in network environments, I have NEVER heard of MTU being a factor in ANYTHING.  In theory, the need to fragment/reassemble packets that exceed a segment MTU should cause a performance hit, but the nature of TCP/IP is such that it's designed to handle such fragmentation.  And reducing your MTU when such isn't actually required will hurt your performance on the local network, as it may take more packets to move a given amount of data.

And of course it turns out that in this instance, you know more about it than I do - I just tested the site with my MTU set to 1200, and it's working.:o 

You are correct that "ifconfig" will not permit you to set an MTU greater than 1500 (that 1514 figure is what the stupid thing *defaults* to, for some reason).  

FYI - My main email account is msn.com (hotmail).  I've never had any problem accessing it (I guess Qwest is more forgiving about it than iBurst).  This is the first site I've encountered with this particular issue. 

I think I'll set the MTU in "/etc/network/interfaces" on this machine - while I've never had a problem before, if it happens once, it'll happen again.  I wonder why that device (it's a KLSI USB Ethernet) defaults to that value?  I just checked the driver source - they're explicitly setting the MTU to 1514.

I still question whether an ISP *should* be dropping packets that exceed a specified MTU, but the fact is they own the wires, so they can set the rules.

Now if someone can come up with a solution for mibadt - he's already tried changing his MTU...

Lloyd B.

---

### Post by mibadt on 2006-12-08
Hi,
For hat it's worth, I ran KNoppix 5.0.1 (English, CD version) on the same PC, connected to same LAN and from within Knoppix I couldn't access KEH's site neither by Konqueror nor by Firefox (at the same time I had no problem browsing several other sites using any of these 2 browsers).
Modifying my eth0 MTU from the default 1500 to 576 didn't help either.

Regards,
Michael Badt
:mad:

---

### Post by mibadt on 2006-12-09
One guess,
My Kubuntu has IPV6 disabled (as my router doesn't support it). Could this be related?

---

### Post by eXisor on 2006-12-12
[quote="lloyd_b"]I still question whether an ISP *should* be dropping packets that exceed a specified MTU, but the fact is they own the wires, so they can set the rules.[/quote]

I don't think they actively drop the packets, rather their systems and configs add latency which results in a particular mtu being optimal. The fragmented packets get retried and after x number of goes the protocol handler just gives up.

From the sound of it you've proved that particular card is a factor (since the site works with a higher mtu from the other - identical software - system). A network card specific mtu is a first for me too. Perhaps there is another variable were not seeing? Have you tried swapping out the cable? Changing the router port?

mibadt: Switching ipv6 off will not cause the symptom you are seeing. It must be something else.

---

