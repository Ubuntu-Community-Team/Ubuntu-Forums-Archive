---
title: "bittorrent question"
date: 2005-10-08
forum: General Help
---

### Post by xmastree on 2005-10-08
I'm currently downloading a DVD with bittorrent. Total is 4.3GB, and the only place with enough room for it is my shared drive. I've just realised that as it's FAT32, there's a 4GB limit, and I suspect that there might be one large file which is too big. Can't say for sure yet, as I'm only 9% into it, but most of that is one file.

So, I have a cunning plan, just in case, but I thought I'd ask first.

What I'm thinking is I'll use a spare disk with enough space, make it one big linux partition and temporarily replace my CDrom with it. Then I'll copy the partial download to it, unmount the FAT32 drive and mount this new one in the same place.

Then I'll fire up bittorrent again, and hopefully it'll see the files in the same place and not realise that they're on a different phyisical drive so it'll just continue as normal.

You think it'll work?

---

### Post by stoeptegel on 2005-10-08
It will work if your client has an option to save the download to a custom location.

---

### Post by pinoyskull on 2005-10-08
it will work, i tried it with azureus :)

---

### Post by xmastree on 2005-10-08
[QUOTE=stoeptegel]It will work if your client has an option to save the download to a custom location.[/QUOTE]It does, which is how I told it to save it there in the first place. I might not need to, depending on how big the other files are, but they're all zero just now. I need to wait a few more days... :rolleyes: 

I'm getting between 2-3KB/s at the moment, although I'm uploading at typically 15.

---

### Post by stoeptegel on 2005-10-08
[QUOTE=xmastree]

I'm getting between 2-3KB/s at the moment, although I'm uploading at typically 15.[/QUOTE]

Kubuntu 5.04 dvd? Ow that's bad.:(

---

### Post by xmastree on 2005-10-08
[QUOTE=stoeptegel]Kubuntu 5.04 dvd? Ow that's bad.:([/QUOTE]No, it's not Kubuntu, it's something, erm, commercial... 

I don't feel guilty though. I tried to buy it online, but they don't seem to acknowledge the existence of the Philippines, and they ignored my three emails asking how I could buy it from here.

It's got 12 days remaining at the moment... :-(

---

### Post by stoeptegel on 2005-10-08
Low speed... is your client connectable on the specified port? Have you set the allowed number of connections higher? Sometimes higher meens lower performence, test this. Also, you might have set you upload too high, which could causes you download connection bandwidth to squeeze down like this. 80-85% uploadsetting of your real upload is a good rule.

---

### Post by xmastree on 2005-10-09
Actually, it was my isp's problem. It got slower, and slower, then everything stopped... I tried resetting the network connection but it couldn't connect to DHCP.
It's fixed itself now and things are much better. Thanks for the advice about limiting uploading, I've set a limit there now.

---

