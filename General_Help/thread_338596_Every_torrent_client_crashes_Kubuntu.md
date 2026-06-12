---
title: "Every torrent client crashes Kubuntu"
date: 2007-01-14
forum: General Help
---

### Post by kombucha on 2007-01-14
I began using KTorrent again the other day, but it started crashing incredibly frequently. It would crash while I was navigating its menus, when it was running in the background and I was doing something else, and even when it alone was running and I was away from my computer. It would utterly lock up my computer and require a hard restart to fix. So I switched to Azureus, assuming it was a problem with KTorrent, and the exact same thing happened. Odd, I thought, as I switched to BitTornado, but of course I had the same problem. Trying to think outside the box, I installed uTorrent onto Cedega, but faced the same crashes.
Obviously the common factor here is that all bittorrent clients are somehow crashing my computer. This isn't for one specific torrent either; I've tried many, and they all crash very quicky (tends to be a few minutes in). Any ideas? I've even tried disabling Beryl, but that didn't help.

---

### Post by cuplex on 2007-02-18
hey i got the same problems. but its not alaways the whole system crashing sometimes its just closing the client itself! i tried nearly every linux client and everyone crashed after a few hours or less! its not possible to download anything well it is but it takes forever!

i couldn't find anything i already installed dapper again and tried on a fresh install! same here! didnt try via vmwareserver or cedega!

---

### Post by soapytheclown on 2007-05-04
yeah im having the same problem at uni ktorrent is the only client thqat works in linux but randomly it crashes someitmes after hour but now its crashing randomly every 5 mins or so its a real pain is ther a way to find out whats going on or how to fix it.

---

### Post by unnes on 2007-05-04
> **soapytheclown said:**
> yeah im having the same problem at uni ktorrent is the only client thqat works in linux but randomly it crashes someitmes after hour but now its crashing randomly every 5 mins or so its a real pain is ther a way to find out whats going on or how to fix it.

There is a known bug in KTorrent 2.03 that causes the program to crash when trying to acquire peers via DHT. Try either disabling DHT or upgrading to KTorrent 2.1.4.

---

### Post by Ikonoclasm on 2007-05-04
Ooh, glad I found this post. I was planning on using KTorrent when I installed Feisty. Glad to know the most recent version's okay.

---

### Post by strixy on 2007-05-18
I don't suppose anyone has gotten or tried to get KTorrent 2.1.4 into the repository yet?

---

### Post by cmost on 2007-05-18
Any objection to using Azureus?  It's the best Bittorrent client around in my opinion (and apparently the opinion of the latest Linux Format.)

---

### Post by hvbakel on 2007-05-18
Ktorrent  2.1.4 is in the backports repository, you'll need to add the following line to /etc/apt/sources.list

```
deb http://ca.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
```

---

### Post by Rhadamanthos on 2007-06-18
Thanks for the tip on backports, I've just gotten the new version of Ktorrent. 

Unfortunately, still seem to be having the same problem (saying "remove torrent" freezes). Maybe DHT will work now at least.

---

### Post by 0x001A4 on 2007-09-13
I am having this same problem and I am using KTorrent 2.2.2 in 64bit Gentoo.
Every time I start KTorrent, probably 2 or 3 minutes later everything locks up. I cant move my mouse and the keyboard becomes unresponsive.

Did you ever get this resolved? If so, what did you do?

---

### Post by Rhadamanthos on 2007-09-16
Actually, I got some help from the Ktorrent forums on my issue. My torrents had become corrupted, so even when I had the new version it wasn't able to remove the torrent. The Ktorrent people told me how to delete the data files (~/.kde/share/apps/ktorrent/tor#, where # is the number of the torrent) and from there on I was fine.

This doesn't sound like your problem, but Ktorrent 2.2.1 is the latest version in the Ubuntu repos, so I'm not sure if we're going to have the same issue as you.

---

