---
title: "Slow Bit torrent"
date: 2006-11-24
forum: General Help
---

### Post by chunt on 2006-11-24
I just setup this desktop to get my feet wet in Linux and am trying to use Bittorrent.  I can only seem to get about 20K down.  My windows machines usually run at about 200K - 500K down.  I put the machine as a DMZ on the router and also have all ports forwarded from 0 to 65,000 (whatever the top number is) both in and out set.

Is there anything I can do to fine tune this in Ubuntu?

thanks

Cassidy

---

### Post by Spano on 2006-11-25
Seems like you have everything covered.
What torrent client are you using?
Do you have a firewall installed?
I only forward ports 6881 thru 6889 from the router, No DMZ.
Use Bittornado set to the above ports.  Have Firestarter firewall
installed and set to allow bittorent service on ports 6881 - 6889.
Very speedy.

---

### Post by phatzmb on 2006-12-02
i just fixed a very irritating bittorrent problem i've been having for the last few days with azureus and ktorrent. my downloads and uploads were stalling - every 5 seconds. they went up to around 5-15kb/s, then back down to zero for a few seconds and so on. my ports were forwarded fine.

just now i tried turning of uPnP, which solved the problem immediately. i'm not sure exactly how uPnP works, but it would seem that while trying to open my ports it was ruining the port forwarding i already had.

---

### Post by fishe on 2007-03-01
> **phatzmb said:**
> i just fixed a very irritating bittorrent problem i've been having for the last few days with azureus and ktorrent. my downloads and uploads were stalling - every 5 seconds. they went up to around 5-15kb/s, then back down to zero for a few seconds and so on. my ports were forwarded fine.

just now i tried turning of uPnP, which solved the problem immediately. i'm not sure exactly how uPnP works, but it would seem that while trying to open my ports it was ruining the port forwarding i already had.

You turned off uPnP on your router correct? There is no uPnP setting in Ubuntu I take it. Although I know there is in some applications...Deluge doesn't have it though which I'm using.

I turned it off on router and it seemed to have a positive effect, but after more testing, I'm still getting crap speeds, generally <10k/s.

Maybe I should install firestarter and open ports...although there is nothing in iptables at the moment.

---

### Post by Hallvor on 2007-03-01
I had a problem with slow speeds too. It was caused by iptables (firewall). Just install firestarter and open the correct ports, and your downloads should fly. Make sure you do the same on your router. I always have much better download speeds in Ubuntu than under Windows. The record is something like 450kb/s. It completely saturated my download capacity. Upload speed is also much better under Ubuntu. (By the way, there is no need to make a dmz on your router. I have only three ports open. Two for aMule and one for Bittornado.) 

Secondly, slow speeds could be caused by your ISP (throttling). You should use a client with encryption/protocol obfuscation if you think that may be the case.

Good luck.

---

### Post by lukew on 2007-03-01
Might be worth checking the ip address of your portforwarding config on your router.

Luke

---

### Post by dkaddict on 2007-07-24
Port Forwarding, I have discovered, has never made any difference to my torrent speeds. My ISP 'Throttles' bandwidth between 4pm and Midnight every day. At 6am, for example, I get an average of 500kbps down on any torrent with plenty of seeders. I set uploads to unlimited and always seed two or three files while I am running a torrent client. UPNP, port forwarding, and such like just confused me until I found out that it was my ISP playing silly buggers with a service which was sold to me as 'unlimited'. At the end of the day, a download is a download.

Who knows how to beat the throttling? None of the 'encryption' options have ever helped in my case.

peace

dk

---

### Post by davidmorawski on 2007-07-24
Clearly the bottleneck can come from many places, so let me throw one more idea into the pot.

In my case, my Westell 6100 **modem**, which *doubles as a router*, was blocking traffic. So, even after opening up ports on my actual Linksys router and my firewall, my modem(/router) was still doing me unwanted favors behind the scenes. This, of course, was a fairly easy fix once I realized what I was dealing with.

The moral of the story is: Know your software, Know your hardware. Just know your system, in general, and the problem won't be too far away. And, as we all know, solving a problem becomes much easier once you find out what that problem is :) But I guess that's all pretty obvious.


Dave

---

