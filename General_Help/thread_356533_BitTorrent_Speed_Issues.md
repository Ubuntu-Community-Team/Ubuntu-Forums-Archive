---
title: "BitTorrent Speed Issues"
date: 2007-02-08
forum: General Help
---

### Post by Slazer on 2007-02-08
Alright, I know this kind of question/problem has come up before on these forums but I haven't been able to find any way to fix my speed problem.

I am currently downloading a torrent, an .avi file that is 175mb, with **22763 seeds** and **9374 leechers**, and i cannot, EVER get above 50kb/s. I'm lucky to stay as high as 25-30kb/s.
Out of ALL of these people, I'm connected to 18 seeders and 4 leechers. 

In Windows, using uTorrent, I NEVER had this problem... I was ALWAYS able to download fast... (couple hundred kb/s) but on Linux, even since I started using it at my major OS two months ago... downloading via torrents was REALLY slow.

The bitTorrent program I'm using is KTorrent. I'm running Ubuntu Edgy Eft. I have a 6 megabit cable Internet connection, using a Cisco Linksys Wireless-G (I'm on a wired connection) WRT54GS router, which has port forwarding enabled manually on the router and through  KTorrent with the UPnP plugin.

I would seriously appreciate any and everyone that'll help me bring my download speeds back up with a torrent that has this many seeders and leechers. :(  My friend, who is across the hall from me, using a DSL connection, also running Ubuntu, downloading the same torrent, can get normal speeds of a couple hundred kb/s.

---

### Post by Slazer on 2007-02-08
Ok, I've decided to do a little test of my own and this just PROVES that there is something wrong with Ubuntu Linux and torrent. I don't know WHAT but there's something wrong.

I decided to boot into MS Windows and download the same torrent I mentioned above. This time, there are only 18000+ seeders (instead of 22000+) and 6000+ leechers (instead of 9000+).

I'm using uTorrent, and this time I don't even have my router manually configured... just doing it through uTorrent with UPnP. I'm on the EXACT same machine that my Ubuntu Linux is on (same monitor, keyboard, tower, mouse... freaking chair), and I'm getting 300+ kb/s downloading this torrent, sometimes getting above 500kb/s for a few seconds.

I started the torrent download just before I started typing this post.... now it's done.

As you can see, Ubuntu has SOMETHING not configured properly, or something not working properly if a torrent with this many seeders and leechers can't get above even 100kb/s.

What can I possibly do to make my torrent speeds increase? I don't like using Windows... but I don't like slow download speeds either! :(

---

### Post by bionnaki on 2007-02-08
I have the exact setup (wrt54g + ktorrent) and my speeds are just fine. Perhaps the problem is the upnp plugin. I do not use it. you should setup a static ip and forward the ports instead.

---

### Post by SeanTater on 2007-02-08
I ran into the same problem. For me it was that my upload was saturated which prevented me from sending TCP ACK packets quickly (english: I have to tell them I got the packet, but I was too busy giving others data). The fix: cap the upload rate at least 10-15KB/s less than the saturation point.

For me, that converted 50KB/s down, 45KB/s up, to 600KB/s down, 32 KB/s up.

But - YMMV.

---

