---
title: "connection problem - very low download/upload speed"
date: 2007-11-05
forum: General Help
---

### Post by tfreitas on 2007-11-05
i'm having very low download and upload speeds when trying to download a torrent
i've read all sort of stuff 'round here, tried them all and nothing works..
my download speed it's about 5-15 kb/s, when it should be about 150-250 kb/s.. strange thing is that when downloading files in the repository or in a web site, i get the average speed of 230 kb/s.. i know thats different, but at least i know i dont have any major problems with my connection

i'm using deluge as btclient, and have tried using azureus, ktorrent, transmission.. etc.. the ports are forwarded in my router.. i'm using a very high port (64444).. have disabled ipv6.. not using any firewall.. even uninstall iptables!! the torrent i'm testing is a ubuntu distro, so it has good healthy.. i don't know what else to do.. i've done everything that have worked with similar cases around here, but haven't got one improvement on my transfer rate.. i can't figure out a solution

---

### Post by mpierce on 2007-11-05
I use deluge as well.

There are several things that can be causing your problem if you are sure that your port forwarding is working correctly (I often hit speeds of 240). 

1) On the deluge edit/preference menu. Select network tab.  Make sure your port is shown here. Also enable mainline DHT, uTorrent-pex and prefer to encrypt entire stream. Then test it. 

On the bandwidth tab you show have these values given your speed:
Max connections 800
Max downloads -1
Max uploads -1
Max upload slots 15
Max half open 8
Max connections/torrent -1
Max upload slots/torrent -1

There should be nothing on proxies unless you use one. 

2) The other thing that may be causing your problem is that your router doesn't play well with P2P. You can do a Google search on that to find out the solution or look on the deluge or BitComet website as the info is on one of them with some solutions.

Hope this helps.

---

### Post by tfreitas on 2007-11-05
sorry.. i've forgot to tell about my deluge config.. it's was just the way you're suggesting to be, and with encryption and everything else.. i've forgot to mention it..
about the router issue, in windows xp (i've just entered permanently the ubuntu world!) i had those good download speeds about 150-250 kb/s.. and with others distro like fedora and mandriva too.. so i think i'll have to disagree with u.. i'm not trying to be rude! i appreciate very much your reply to my thread! 
thank you!

---

### Post by inchaos on 2007-11-08
I'm having the same problem you're talking about in uTorrent.

My download speeds remained around 5-10 kb/s until this morning when I checked the encryption box under the speed test tab.
Now I'm getting...50-80 kb/s, better, but still not what I'd like.

I've got everything set up as it should be, but according to the port test I did with this site:
[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)
all my ports are in stealth mode.  I have them set up for forwarding per my router and I don't have a software firewall that I know of.

I also tried this site:
[http://www.portforward.com/english/routers/port_forwarding/Netgear/WGR614v7/Utorrent.htm](http://www.portforward.com/english/routers/port_forwarding/Netgear/WGR614v7/Utorrent.htm)
It's got guides for all the routers you can think of.
I followed it exactly, to no avail.

You're right about the Windows thing, my boyfriend has uTorrent on Windows and he's kicking my torrent's butt.  

Does Ubuntu have a hidden firewall I don't know about?

---

### Post by timcredible on 2007-11-08
torrent download speeds are usually very low if the client isn't uploading also.  and a lot of times the upload is blocked due to no port forwarding or the port forwarding isn't correct.  so, i'd double-check the port forwarding.

---

### Post by inchaos on 2007-11-08
I thought that as well, with the whole 'downloads are proportional to your uploads' spiel.

But usually I can get my uploads going up to 100kb/s even if my downloads are super slow.

I wonder if it's a problem with my ISP or if I didn't get my static IP set up correctly.

---

