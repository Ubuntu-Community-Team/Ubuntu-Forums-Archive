---
title: "Problem With Specific Domain"
date: 2008-02-27
forum: General Help
---

### Post by godsfshrmn on 2008-02-27
I am unable to connect to a specific domain on my ubuntu server for some strange reason. I can ping any other site, such as yahoo or thepiratebay, but I cannot ping torrent-damage.net. I am able to go there just fine on this computer which is on the same network as the ubuntu server. What should I do to findout what is causing this?

---

### Post by astrotech226 on 2008-02-27
If it makes you feel any better, I can't ping it either.  But that's probably just because they are blocking/dropping icmp packets.

I am going to assume there is no gui on your Ubuntu server.  So try this and see what you get:

```
wget torrent-damage.net
```

It should save an index.html file with the web page from torrent-damage.net.  If it does, then everything is good!

If you don't get the file, there's probably something your direction blocking this like a firewall.  Or maybe a cached dns entry that needs flushed.  Type:
```

dig torrent-damage.net
```

And post what IP address you get back.

---

