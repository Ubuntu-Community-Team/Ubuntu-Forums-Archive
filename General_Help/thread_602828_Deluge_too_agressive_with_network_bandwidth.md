---
title: "Deluge too agressive with network bandwidth"
date: 2007-11-04
forum: General Help
---

### Post by thelost on 2007-11-04
I am using the excellent Deluge as my primary Bittorrent client. It's great because it is extremely similar to uTorrent in simplicity and execution, but obviously gnome native so looks good too.

However....

It's an absolute network hog. I've tried being as conservative with the  bandwidth settings but to no avail. I'm not inexperienced with bittorrent as a protocol so I realize what can happen if you are not careful with the upload speed/amount of connections being made.

Funnily enough, if I run utorrent through wine then I don't have the same problem with network bandwidth, even with similar network settings as Deluge.

I'm not keen to run utorrent through wine, I would prefer to be able to run deluge. At this rate though, I would rather run Azureus because for all its bloat I can be sure at least that I can control the network settings and not have all other network tasks slow down every time I am using bittorrent.

Any thoughts on turning deluge into a more manageable trickle?

---

### Post by moopoo on 2007-11-05
Sorry, no solution. But I experience the same problems. Sometimes my internet connection drops drastically after using Deluge for some minutes. Surfing becomes impossible.

Then there are three options:
a) I quit Deluge. bandwith magically reappears. When I start deluge again, the problems start all over.
b) I wait and hope that bandwith comes back. If that is the case, bandwith will drop again some minutes later.
c) I quit Deluge. Restart the router and thus reconnect to the internet (new IP). With conservative settings, Deluge is likely to work properly.

My new settings make use of single ports and not port ranges. The ports (TCP and UDP) are somewhere in the 50.000s. I have the feeling, that some peers or trackers cause the problems. As long as I don't reconnect to the internet, the problems return regularly: after Deluge has caused the problems, ktorrent and µtorrent will eat up my bandwith, too.

Surprisingly, the router does not choke. I don't have to reboot it, just to surf the web. Quitting Deluge temporarily helps.

----
Ubuntu Gutsy Gibbon
Deluge 0.5.6.2
Fritz!Box 7050 router (wired)
DSL 2000

---

### Post by ellgor on 2007-11-05
Hi

Give Transmission a go, its in the Gnome site. I have tried it and have changed to it (and a few others) and imho works great, ie you can do other things without getting any drag effect, hope this is of help.

Regards,Ellgor.

---

### Post by por100pre1 on 2007-11-05
Try adjusting **Global Bandwidth Usage** in Deluge preferences. Deluge will use all bandwidth available (-1) by default.

---

### Post by thelost on 2007-11-05
> **ellgor said:**
> Hi

Give Transmission a go, its in the Gnome site. I have tried it and have changed to it (and a few others) and imho works great, ie you can do other things without getting any drag effect, hope this is of help.

Regards,Ellgor.

I've had a lot of experience with Transmission, it's a great client and I'd recommend it to anyone who has not got set in their ways. Unfortunately I really like to have everything laid out in the classic azureus/utorrent/deluge way.

I'll give the Global Bandwidth Settings a go.

---

### Post by moopoo on 2007-11-06
Thanks for the info.

- Transmission is nice, but i need a classic client, like thelost already said.

- Global Bandwith is limited. The problems even occur if the download is at 10% of my capacity.

- Maybe it has something to with moblock (http whitelisted). I turned it off after I couldn't google or even reach my router's web interface. Then everything worked again. But maybe it's just because i had turned off deluge a few mins ago.

---

### Post by moopoo on 2007-11-06
i'll give transmission a chance. at the moment it works perfectly. thanks.

---

### Post by ThrobbingBrain66 on 2007-11-06
Have you throttled the upload rate as well?  My connection acted the same as yours, but after I set my upload rate to 15 KiB/s, everything works great.

---

### Post by moopoo on 2007-11-07
Yes.. I throttled everything.

**Maximum: **
~ 250k down / ~ 24k up
[B]
Experimental, conservative Settings: [/B]
100 down / 6 up
Max Connections: 75 (99 recommended)
Max Half-Open: 5 (8 recommended)

But... **Transmission** works fine!

---

### Post by thelost on 2007-11-07
transmission works much better for me, but i can't put up with the GUI.

Azureus, which was my last ditch attempt crashes every single time I try to open the torrent detail stream. Oh well, i think someone needs to log Deluge's speed problems on their trac. It should be much better behaved than it is.

---

### Post by Ram Crammer on 2007-11-08
I've been running Deluge 0.5.6.2 for several days now, nonstop.  No bandwidth problems encountered at all, even with 6 torrent downloads running at once.  I have configured unlimited download speed, 80 connections, 50Kbs max upload with 4 max upload slots and 8 half-open connections.  Per torrent settings are both unlimited.  I'm on a DSL connection thru a 2-Wire 700HG gateway router.  Yes, with all this, I do have some drag, but can still view movies on UTube, etc.  So, drag has not been that noticeable, really.  Normal surfing seems just a wee bit sluggish at times, but I'd rather have Deluge take a little bit from network, than to have it always crawling.  In any case, Deluge quickly throttles back when I need more bandwidth for surfing, so I don't see any real problem with it.  Deluge aims to be as unobtrusive as possible, and I think it does this quite well, while still achieving excellent performance.  

I had been using Deluge v. 0.5.0 till recently, and found it pretty lame, but this new version seems to have solved all of my issues and added some very slick new features. Kudos to the Deluge team.  Great effort, gang!!  Love the classic interface.  Very simple and logical.  I also love the ease of installation and setup.  Brain-dead simple and foolproof.  Not like Azureus which requires a masters degree in torrent technology to install, set up, and run.  Azureus suffers massive bloat and complexity.  I never was able to resolve my NAT problems with Azureus.  Deluge has none of that nonsense.  It just works, at least for me :)

Anyway, just thought I'd share my perspective on this issue.

---

### Post by inversekinetix on 2007-11-08
I've been using Ktorrent for a while now,  I really like it, It gets a little more out of my upload bandwidth than uTorrent on windows,  I managed to get a 17MB/s upload and 60MB/s download with it.  Does anyone know how many half open connections ubuntu supports? or how to change that value?

---

### Post by thelost on 2007-11-08
> **Ram Crammer said:**
> .......
I had been using Deluge v. 0.5.0 till recently, and found it pretty lame, but this new version seems to have solved all of my issues and added some very slick new features. Kudos to the Deluge team..........

I gotta agree on this front - just upgraded to the latest & greatest and all in all it seems to be a bit kinder to my bandwidth. I think after all this discussion I may even decide to stay with Deluge, heh.

---

### Post by trash on 2007-11-13
I just got satellite internet and they are very picky about bandwidth usage, so much so that they 'don't allow filesharing using apps like kazza, limewire..'. They didn't mention bittorrents so I am not paying any attention to the 'rule' haha.... That said, I want to stay off their radar!

The only thing that worked for me with Deluge is limiting the number of Global connections to 50(99 wan't good enough). My network speed is back to highspeed normal and downloading(40)/upload(20) isn't sufffering.

---

