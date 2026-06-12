---
title: "All Internet Traffic Slow with Amule running"
date: 2007-05-27
forum: General Help
---

### Post by m.musashi on 2007-05-27
I thought I'd give amule a try and installed it a couple days ago. I noticed that when it's running my whole internet experience is very slow. These forum pages, for example, take 10-20 seconds to load. Normally they load in just a couple seconds. I killed amule and within a few minutes everything is back to normal speeds. As soon as I start it again everything is slow.

Amule is slow too. It's only downloading about 15kbps so there is no way it's eating up all the bandwidth.

I'm on comcast so I started wondering if they throttle speed for bit torrent users. I've never had a problem before but perhaps amule triggers something that bittornado doesn't.

Anyone have a similar experience or know a fix? If it's a throttling issue, can I send all emule traffic over port 80? Would that hide it or mess up all my other surfing?

Thanks in advance.

---

### Post by bung33 on 2007-05-28
Even though your download speed is low, you could be uploading at much higher rates. Typically, these programs will remove all upload speed limits by default, so this could be the reason everything is slowing down. Another solution would be to encrypt the torrented data, if the program you're using has that capability. I would not direct the traffic to port 80, as that is used for other purposes and, if used, could actually decrease your speed even more. I have had Comcast create problems for me too when torrenting, only to find they dissappear when the torrent activity stops. You should try using a different client with encryption options if you can't get better results...

---

### Post by m.musashi on 2007-05-28
The upload speeds are also very low. Only 10 -15 kbps. Do any encryption options exist that are not built into the client? Azureus doesn't work well for me (that's why I'm giving amule a try).

---

### Post by Hallvor on 2007-05-28
What you are describing is typical if your router can`t handle the number of connections. It will slow down both your upload and download speed. This happens if you have many popular files on your download list, so that the number of sources is too much for your router to handle. It will also make internet browsing painfully slow. If this is the case for you, you could try setting a lower max connections value in the aMule options menu.

aMule will rarely be as fast as bittorrent, unless you have many popular files on your download list and a good router. This is because the regular user shares hundreds of files, and the upload is spread among them. In bittorrent, the upload capacity is usually concentrated on a single file. Because of this, you will find an incredible number of rare files in aMule, but they may be a bit slower to get. But if you can wait, you will be rewarded.

Edit: Many isps throttle the standard ports, so it may be a good idea to change them.

---

### Post by m.musashi on 2007-05-28
I was only downloading one file. Would tha cause what you suggest?

As for throttling, I thought they did that based on traffic shaping (not sure what that means but it's what I read) so it wouldn't matter which port you used - or is that part of the shaping? Encryption seems to be an option but some ISPs (quest) throttle encrypted traffic (according to the azureus wiki I think).

---

### Post by Hallvor on 2007-05-29
Yes, it could be the case if it was a popular file. I don`t know what type of router you have, but some of them can`t handle many connections at all. I can say for sure that it is not Ubuntu or aMule itself causing the slowdowns. It is a hardware issue.

Throttling: It depends in the ISP. Some ISPs just throttle the default ports, since most users use them anyway. More advanced throttling will throttle based on behavior and even if the P2P app uses protocol obfuscation.

Edit: Almost forgot: Your router will handle the large number of connections better if you set the TCP and UDP timeout settings to a smaller value when you log on to your router. I have mine to 120 ms, and this will make the router able to handle a larger number of connections.

---

### Post by m.musashi on 2007-05-29
Thanks for the help. I will change the ports and play with the router a bit. It's a linksys 54g or something like that. It's connected to a linksys cable modem.

Is there a way to tell if I'm actually being throttled or is it more a matter of observation and educated guessing?

---

### Post by Hallvor on 2007-05-29
If you have a Linksys WRT54G, it would probably be a good idea to flash your router with better firmware. The original Linksys firmware is mediocre, but with better firmware it will handle P2P traffic very well, and you`ll have a better router in your hands.

I use this linux-based firmware myself:
[http://www.dd-wrt.com/wiki/index.php/Installation](http://www.dd-wrt.com/wiki/index.php/Installation)

As for throttling, check out if your ISP is on the list:
[http://www.azureuswiki.com/index.php/Bad_ISPs](http://www.azureuswiki.com/index.php/Bad_ISPs)

But I do know that the list is not complete. This thread is well worth reading!
[http://forum.emule-project.net/index.php?showtopic=121265&hl=throttling](http://forum.emule-project.net/index.php?showtopic=121265&hl=throttling)

---

### Post by m.musashi on 2007-05-29
I've been leery of changing the firmware. I know it works right now and I have no idea how it will work if I change. If I'm unhappy, do you know if I can "go back" to the Linksys firmware? I did get things running a bit better and I don't do P2P very often so I'm not sure if the payoff outweighs the risk. Oh well, I've been wanting to try this so maybe I'll just go for it. Did you have to flash the firmware from Windows? In a couple places it said that the upgrade would fail if you used firefox.

Thanks for the links.

---

### Post by Hallvor on 2007-05-30
I think it is possible to revert back to the original firmware for most models, but read to make sure. But if you are happy with what you have, there is no need to change. I changed because the original firmware needed a hard reset (not just a power cycle) every month or so, and powercycling at least once a week. It just couldn`t handle heavy P2P traffic.

I did use a cabled laptop and a TFTP-tool in Windows to flash my router, and I also used IE6. Problems with Firefox, yes.

---

### Post by m.musashi on 2007-05-30
Thanks again for the info. I think I will go ahead and flash the firmware on my router but first I'll see if I can download a stock firmware to replace if I need to.

> This thread is well worth reading!
[http://forum.emule-project.net/index...&hl=throttling](http://forum.emule-project.net/index...&hl=throttling)
I've been reading through this thread you gave me and there is a lot of conflicting information. However, a couple things caught my attention. First is the idea of Protocol Obfuscation. What exactly is that and how do you enable it? Of course, if the thread starter is right, it doesn't work so maybe it's not worth investigating.

Later, someone claming to work for an ISP gave [some tips](http://forum.emule-project.net/index.php?s=&showtopic=121265&view=findpost&p=871197) on staying less obvious. He says to limit connections to around 30. I found some options like that in amule but I'm not sure which to change. Is there a good guide anywhere that perscribes an optimal (i.e. leading to good overall performance) configuration?

---

### Post by Hallvor on 2007-05-30
About protocol obfuscation: [http://en.wikipedia.org/wiki/Protocol_obfuscation](http://en.wikipedia.org/wiki/Protocol_obfuscation)

Protocol obfuscation is not featured in aMule, but is in eMule from 0.47a (I think). It does run in Wine with a few glitches. PO did work well for some time, but not always anymore. If you are able to download/upload at good speed using bittorrent without being throttled, aMule is probably not throttled either.

If you limit the connections to about 30, as suggested, aMule becomes next to useless because it will probably take many days to download a single movie. 

Optimal performance is as many connections as your router and modem possibly can handle without choking. It is a matter of testing. Many connections = more sources = faster download.

---

