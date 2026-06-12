---
title: "Where do kTorrent keep the .torrent file?"
date: 2007-05-29
forum: General Help
---

### Post by iggyboy on 2007-05-29
Hiya everyone :)

Recently I notice my private torrrent site banned kTorrent, Now I left no other choice than look for alternative torrent client. Now my question is, where is kTorrent keep the .torrent file?

By default I let the kTorrent to handle .torrent file whenever I download .torrent file through Firefox. This automatically open-up kTorrent and start the downloading. Now I need those .torrent file to use in my (not decided yet) new torrent client for seeding up.

I did search my whole Harddisk for *.torrent file, but none is found. I do realise there are some torrent file located in; **/home/myname/.kde/share/apps/ktorrent/torXX** folders, but none of them are as in original name (.torrent) as downloaded before?

Another things, I'm not certain but I guess there is no way for me to directly use another client to complete a partially download kTorrent torrent file. However I am wondering is there another method or solution available for me to complete my partially downloaded file, meaning to use another client like uTorrent under wine with some sort off conversion from one client to another?

Thank you in advance :)

---

### Post by kuja on 2007-05-29
Original name or not, that's where it stores the torrents by default. 

Looking at the depends it doesn't look like ktorrent uses libtorrent for torrenting, and that probably shoots any hopes for compatibility in the foot. As for conversions, I've never heard of such a script. Give google a run and hope you get lucky, otherwise I guess you'll probably have to restart it with the other client.

---

### Post by kelvin spratt on 2007-05-29
ditch the private site don't let people dictate and play god what you use is up to you thats the idea of using Linux freedom of choice,their is not much you can't get from the pirate bay leave DHT on a lot of the latest torrents are trackerless and don't show as having any seeds

---

