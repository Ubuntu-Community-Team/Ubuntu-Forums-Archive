---
title: "rTorrent can't add trackers anymore"
date: 2014-12-13
forum: General Help
---

### Post by Iznougoud on 2014-12-13
I didn't really know where to post this, so if some admin does have a better idea of where to put it - do feel free to move the post.

System: Headless Ubuntu server 14.04.

Software affected: rTorrent.

Issue: After a reboot yesterday (2014-12-12, required by a kernel update) rTorrent can list but not add trackers anymore, according to the error message given not being able to resolve host names; "could not resolve host name". Which is odd, since everything else depending on name resoultion seems to be in working order.

This far I haven't been able to find a log of any use, nor the possibility to configure a log file for rTorrent. Any advice on this would also be greatly appreciated.

---

### Post by gustavo-lapido on 2014-12-15
Since last week (not sure exactly the day), my rtorrent suddenly stopped doing what one should expect from it.

It shows its screen normally and all the torrents are there.

But no traffic at all.

It also returns this error

```
Tracker: [Could not resolve hostname.]
```

I rebuild it from scratch, but nothing has changed.

Iznougoud, does your client behave like that too (everything seems to work but no traffic)?

Like you, I'm running it on a headless Ubuntu 14.04 server.

---

### Post by Iznougoud on 2014-12-17
It does. Or more like it did. Since my last post I've been looking into configuration files for ruTorrent and the different users' (in total four accounts. mainly the scgi_socket-settings) respective rtorrent.rc-file looking for - if not a solution, at the very least an explanation. The present status being that rTorrent connects to Extratorrent and MiniNova only. This, and your experience, leads me to believe that this may be a widespread problem, not really affected by my local actions during the past few days.

I might also add that for 20 or 30 minutes the day before yesterday rTorrent seemed to connect fine again, and during an eveing or so the problem was intermittent before reverting to a non-functional status altogether. Which in my opinion confirms above mentioned suspicion. Although one would think that if this was a global problem Google would provide you with more hits..

---

### Post by gustavo-lapido on 2014-12-17
> **Iznougoud said:**
> It does. Or more like it did. Since my last post I've been looking into configuration files for ruTorrent and the different users' (in total four accounts. mainly the scgi_socket-settings) respective rtorrent.rc-file looking for - if not a solution, at the very least an explanation. The present status being that rTorrent connects to Extratorrent and MiniNova only. This, and your experience, leads me to believe that this may be a widespread problem, not really affected by my local actions during the past few days.

I was also beginning to wonder if it wasn't a widespread problem, specially when taking into account recent news on raids and takedowns on the p2p world, if you understand what I mean.

I found some recent testimonies that seem to reinforce that, [here]("https://github.com/rakshasa/rtorrent/issues/180"). (look at the latest comments).

From that same link, I tried Niluge-KiWi's workaround (the trackers blacklist one), but it didn't worked, at first (maybe this workaround should be improved to, instead of blacklisting bad trackers into /etc/hosts, try to disable the trackers inside rtorrent - what do you think?).


> **Iznougoud said:**
> I might also add that for 20 or 30 minutes the day before yesterday  rTorrent seemed to connect fine again, and during an eveing or so the  problem was intermittent before reverting to a non-functional status  altogether. Which in my opinion confirms above mentioned suspicion.  Although one would think that if this was a global problem Google would  provide you with more hits..

Yes, maybe.

So far I'm strongly suspecting that PB raid and a [well known public tracker outage]("https://torrentfreak.com/worlds-largest-bittorrent-tracker-goes-down-141205/") maybe has something to do with this.

But if those facts really explain this rtorrent issue, then I wonder why my Transmission client was able to download and upload.

Why Transmission was able to work normally under those adverse conditions but not rtorrent?

Wouldn't you give Transmission a try, just to see if it works also for you?

---

### Post by gustavo-lapido on 2014-12-17
UPDATE: At this moment, rtorrent is working normally.

Like I said before, I'm currently running the server where rtorrent runs with /etc/hosts file updated according to the "bad tracker" workaround I mentioned before.

I had also tweaked with resolv.conf, basically, by adding 8.8.8.8 and 8.8.4.4 nameservers to /etc/resolvconf/resolv.conf.d/base and issuing an resolvconf -u command).

Now, I'm not sure if any of this attempts explain why rtorrent is currently running or not

---

### Post by Iznougoud on 2014-12-18
Seems I took a different route since I've been updating the search engines and I've got four of them to work properly: Extratorrent, MiniNova, KickAssTorrents and TorrentDownloads. I suspect at least a few has been outdated for quite some time, so I suppose there's a silver lining to this after all.

["Github"]("https://github.com/Novik/ruTorrent/tree/master/plugins/extsearch/engines") is a repository for ruTorrent search engines that you may or may not find useful. Mind you, a good portion of those engines are outdated as well (the easisest way to determine this is to copy and paste the URL given in the php-code).

I will also have a look at your link, and hopefully further restore the functionality of ruToirrent :)

---

### Post by gustavo-lapido on 2014-12-19
I could have rtorrent back to activity by following [this]("http://forums.rutorrent.org/index.php?topic=4903.msg15467#msg15467").

---

### Post by Iznougoud on 2014-12-21
Ops. Silly me. I totally forgot I started that thread as well. How embarrassing ;)

---

