---
title: "A BitTorrent client with TRACKER LIST MERGING"
date: 2008-02-26
forum: General Help
---

### Post by dr.koljan on 2008-02-26
There are lots of BitTorrent clients for Linux out there, but it seems quite a few of them have a simple but useful feature - **merging of the tracker lists of identical torrents**.

It's especially useful when you are downloading from public trackers like mininova.org and some of them store the same torrent. For example, if I attempt to open a torrent which is already downloading in uTorrent, it offers me to extract the tracker list from the torrent file and add it to the existing torrent. This sometimes helps gain extra speed.

Unfortunately, the only Linux client capable of this I've found so far is KTorrent. However, it uses KDE which is sometimes uncomfortable under GNOME. Other popular BitTorrent clients, such as Deluge or Azureus, just give me an error or open another torrent.

If you believe you are using a very good BitTorrent client, then please try opening [this torrent]("http://www.mininova.org/tor/930611") and then [this one]("http://btjunkie.org/torrent/Shinsen-Subs-Rental-Magica-01-E6550D47-avi/32547a502d9dc69244f27cdb50dc919923d6c5c96344").

Thanks,

Nicholas

---

### Post by danwood76 on 2008-02-26
Both those torrents you linked too have the same trackers. (bt.edwardk.info)
So you will obviously get errors when trying to effectivly re add that torrent.

Using something like [www.isohunt.com](www.isohunt.com) groups all the trackers from the different sites together when you download them.
Though I think azureus does group trackers together when you add multiple torrents with the same hash.

---

