---
title: "Torrents disable my internet?"
date: 2007-10-14
forum: General Help
---

### Post by Onay on 2007-10-14
I've installed the torrent client Deluge, but whenever I try to download anything through it it causes my USB wireless d-link adapter to virtually disconnect. In other words, my network manager claims that I'm connected, and it shows signal strength and who I'm connected to, but if I were to try and load a web page, then it won't load at all.

What could be causing this? Is usb wireless just too unstable?

On a side note, whenever I have a usb flash drive or external HDD, and I unmount it, the exact same thing happens. Any help is very much appreciated.

---

### Post by ThrobbingBrain66 on 2007-10-14
What is your upload rate set at?  Anything above 20 kb/s bogs my connection down so much it's unusable.

---

### Post by Onay on 2007-10-15
It disables my internet completely, not just bogging it down. No webpages load at all, and after about 5 minutes my upload and download rates drop to 0, showing me that there are no peers or seeders when in fact there may be hundreds of them.

---

### Post by ubuntu27 on 2007-10-15
Onai. Your problem may be the ISP (Internet Service Provider). Some ISP are known to ban bitorrent connection.

[Check out this page]("http://www.azureuswiki.com/index.php/Bad_ISPs") and see if you ISP is one of them:


[http://www.azureuswiki.com/index.php/Bad_ISPs](http://www.azureuswiki.com/index.php/Bad_ISPs)


**EDIT**

> **Onay said:**
>  On a side note, whenever I have a usb flash drive or external HDD, and I unmount it, the exact same thing happens. Any help is very much appreciated.


Re-reading your post, my theories about ISP seems to be wrong.  
It may be a bug. What OS are you using? Ubuntu Feisty? 

I don't know what could be causing your problem. I am not an expert sorry.  Let's wait for someone more knowledgeable.

---

### Post by Onay on 2007-10-15
I don't think it's an ISP thing, since when I used to have Windows they always worked fine.

I am a Fiesty user, but perhaps once the final Gutsy is released I can upgrade and see how that works out for me.

As far as I know, wireless usb cards are very much unstable and therefore unsupported. After much tweaking, building ndiswrapper from the source, etc. I finally got it to work, but it's so unstable that when I unmount other usb devices, download torrents, or hibernate/suspend it always disconnects in one way or another. I really hope that this can be improved, since I completely switched over from windows, and it is becoming an issue with everyday usability.

---

### Post by stinger30au on 2007-10-15
perhaps the router is locking up with p2p programs.
my" netcomm nb1300 +4 " would do it all the time.i binned it and got a billion 7402LM, never looked back

---

### Post by NHaGa on 2007-10-28
I have the exact same problem as Onay. It happened in Feisty and it's happening in Gutsy. The problem isn't limited to torrents, it happens with amule as well. I guess it may have to do with high bandwidth usage.

I have a linksys WRT54GC router and a linksys Wireless-G usb wireless adapter.
If anyone could help... I am new to linux, just moved from winxp and I don't really know where to look for the cause or any logs.

---

### Post by thebucksstop on 2007-11-11
I'll chip in here too - I've got the same problem. I've got a brand new DIR-655 router, which works fine with my flatmate's Vista PC and uTorrent, so I don't think the problem lies there. My card's not USB, it's an Edimax PCI card (RT61 chipset).

When I start to hit high bandwidth usage, my internet connection drops away to 0b/s, and network-manager falls out of the connection, asking for the WPA key in order to reconnect. Unfortunately, even then it won't reconnect to the router - I have to do a full reboot in order to regain access. 

So, in summary - wireless works until I start using high bandwidth, then it gets disconnected and I have to reboot to get it back.

Anyone able to help us all out?

---

### Post by NHaGa on 2007-11-13
It seems this has been solved...
A big thanks to gb5uqx for posting a fix in this thread:

[http://ubuntuforums.org/showpost.php?p=3755385&postcount=3](http://ubuntuforums.org/showpost.php?p=3755385&postcount=3)

---

### Post by thebucksstop on 2007-11-14
Great, thanks. I'd read something about changing from wlan0 to l0 elsewhere on the forum...can't find the link now. But crucially, hadn't been able to figure out how to do it! I'll check this one out when I get home.

Thanks!

---

