---
title: "Slow Firefox! 30secs to Locate and enter Google with FasterFox"
date: 2006-11-02
forum: General Help
---

### Post by DreamHawk on 2006-11-02
Really, seriously, how do i fix this problem? I have read about Pango, and i have disabled it, or less i think i have... I have inserted the MOZ_DISABLE_PANGO=1 row in /etc/environment, without result... 

Another tip i got was to install FasterFox, so i did... No result...
Another tip, install latest firefox.. (2.0 in this case), No result...

Please help me, i know that it can't be this slow, not with 8mbit broadband!
My 0.25mbit was alot faster (at my mothers place, now i'm at my girlfriends place). 

Also, i try to connect to gaim, i've tried two times and neither does that work, is it a firefox bug? Or a "computer bug"? Or some problem with my modem? Please help... In general, the browser is the most used program (in my case) here, so please :)

---

### Post by kerry_s on 2006-11-02
I would say first check your modem/router firewall settings, try turning it off and see if there's a difference. If that don't work try installing another browser and see if that is slow to.

---

### Post by DreamHawk on 2006-11-02
When i access my router/modem on 192.168.1.1, i can't see any firewall settings.
And in windows firefox and everything works great, even with a firewall installed. Does ubuntu have a firewall installed? :S

Another thing, do you think that it would help if i put my internal ip in my modems DMZ ?

Thanks for answering so quickly :)

---

### Post by pattymnaish on 2006-11-02
Ubuntu does have a firewall built in - iptables. To configure it, firestarter is pretty good. You can use aptitude to get it.

---

### Post by DreamHawk on 2006-11-02
So basically i shall use apt-get to install firestarter, then after configuring it, i should have a fast computer again ? :P
(Sorry, i'm a newbie).

---

### Post by pattymnaish on 2006-11-02
Not necessarily. I just wanted to let you know of the built in firewall.

---

### Post by 51mmz0rz on 2006-11-02
I thought I knew the problem until you mentioned GAIM was also having trouble.  Anyway I think you should still try disabling IPv6.

1) Type *about:config* in the address bar of firefox.

2) As the *filter* type *ipv6*.

3) Look for the property **network.dns.disableIPv6**.

4) Set this to *TRUE*.

5) Restart Firefox.

I know this solved my slow Firefox issue, so try this because your GAIM issue might be independent of your slow Firefox.

---

### Post by bobbob94 on 2006-11-03
I had a similar problem with a painfully slow connection in Ubuntu, which worked fine in XP. After trying disabling ipv6 didn't work, I eventually found that the culprit was my cheapo Dynamode router, which I sorted out by setting a static IP, following the instructions in this thread: [http://www.ubuntuforums.org/showthread.php?t=65669](http://www.ubuntuforums.org/showthread.php?t=65669)
Might not be your problem, but it worked for me!

---

### Post by HereInOz on 2006-11-03
I agree with bobbob94.  Set a static IP address (192.168.1.15 or similar)and enter the DNS server addresses which you can get from your ISP.  Set your gateway to 192.168.1.1   You find the place to do this in System > Administration > Networking.  Many routers have difficulties with Ubuntu and DHCP, but I have no idea why.

---

### Post by Unbunk on 2006-11-03
I had the same problem, ubuntu was adding my routers IP aswell as my ISP DNSips to the DNS section.

Load up Networking and check the DNS tab, if your routers IP address is there try removing it. Then test it again.

---

### Post by davholla on 2007-07-03
> **HereInOz said:**
> I agree with bobbob94.  Set a static IP address (192.168.1.15 or similar)and enter the DNS server addresses which you can get from your ISP.  Set your gateway to 192.168.1.1   You find the place to do this in System > Administration > Networking.  Many routers have difficulties with Ubuntu and DHCP, but I have no idea why.
For some reason after I set a static IP address on the router things work fine but when I change my network configuration to static IP address it stops working.
Any ideas ?

---

