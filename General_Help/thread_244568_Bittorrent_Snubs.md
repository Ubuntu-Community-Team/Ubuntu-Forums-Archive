---
title: "Bittorrent Snubs"
date: 2006-08-26
forum: General Help
---

### Post by jmflyer on 2006-08-26
More of a question for a torrent newb...  (Using Ktorrent)

I'm trying to prevent snubs.  I've got my max-upload set to 5kb/s.  I'm getting snubbed because often times my upload speed = 0 kb/s (mostly because I'm the new guy on this torrent).

So the question...  When ktorrent reports my max upload speed is it reporting  per/torrent or a total of all torrents?  

I'm wondering if I get a popular torrent and leave it seeding so that I have a good upload speed, if that will help out with the other torrents I'm trying to dload.

Thanks,
jmflyer

---

### Post by stoeptegel on 2006-08-29
> **jmflyer said:**
> 
I'm trying to prevent snubs.  I've got my max-upload set to 5kb/s.  I'm getting snubbed because often times my upload speed = 0 kb/s (mostly because I'm the new guy on this torrent).

You can't really prevent snubbing, it will always happen in some degree because you simply can not upload to all connected peers at the same time. (not to speak about snub-horny bitcomet and it's derivatives-> bad bad)

> 
So the question...  When ktorrent reports my max upload speed is it reporting  per/torrent or a total of all torrents?

Depends on where you read it, in the row of a torrent it's the speed per torent only. In gui below to the right and in systray hover it's the total bandwidth of all torrents.
 
> 
I'm wondering if I get a popular torrent and leave it seeding so that I have a good upload speed, if that will help out with the other torrents I'm trying to dload.

Nope, your behaving on a torrent should be treated by the other side on the same torrent only, it shouldn't get affected by another torrent which a same peer could be connected with you. It's designed to deal with some degree of a performence measurement per swarm.

---

