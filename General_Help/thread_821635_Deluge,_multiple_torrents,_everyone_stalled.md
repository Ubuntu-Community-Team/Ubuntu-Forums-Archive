---
title: "Deluge, multiple torrents, everyone stalled"
date: 2008-06-07
forum: General Help
---

### Post by unicorn_2003_1 on 2008-06-07
Hi all,

I'm using Deluge to seed one file and download another one. 

If I just enable one of them, everything is fine, downloading/uploading is normal. However, if I let both of the them run, they all stall, none of them can get the normal speed. I mean, if one torrent can get 60K/s download, 15K/s upload, when running two of them, it would be like 10K/s download, 3K/s upload in total.

I remembered having this problem too when I was running utorrent on Windows. What could be causing this problem?

Is it my wireless router? the number of uploading slots? Can I tweak some setting to get over this problem?

Thanks

---

### Post by little_penguin on 2008-06-07
I don't use Deluge so I'm not really sure, but have you configured port forwarding on your router as well as in Deluge?
By the way, utorrent also runs fine in linux with wine.

Regards,
LP

---

### Post by unicorn_2003_1 on 2008-06-07
I didn't setup port forwarding for bittorrent (for eMule yeah), cause I use random ports and let UPnP set up the port. I also tried utorrent with wine, fine exactly.

Probably my router has problems handling multiple torrents? This kind of thing also happens when I run bt and emule simutaneously (within the upload limit of course).

Then again, when I run emule alone, 50+ files at the same time, works like a charm. 

Gotta get OpenWRT and read the router log, Lol.

Many thanks anyway.

---

### Post by little_penguin on 2008-06-07
I doubt that your router is unable to handle multiple torrents. But I read in a few places that upnp doesn't always work correctly, so maybe you might instead want to disable that and forward separate ports for emule and your bittorrent client and see if it works any better? Just a random idea.

Regards,
LP

---

