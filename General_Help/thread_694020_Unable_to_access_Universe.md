---
title: "Unable to access Universe"
date: 2008-02-11
forum: General Help
---

### Post by Poleh on 2008-02-11
Hi

forgive the n00b question. I re-installed a fresh Gutsy/7.10 recently, with Local NZ repo site and since then can't access the Universe repository at all. The connection seems to time out.

I have this exact same behaviour on different networks, so don't think it's a firewall/DNS issue.

The error I am gettins is:
```
http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz: Connection failed [IP: 91.189.88.31 80]
```

I have started with a fresh sources.list and still see now joy... any help would be appreciated...

---

### Post by apetresc on 2008-02-12
Can you ping 91.189.88.31? If not, the server is down. I was having the same problem with the Canadian servers yesterday. There's nothing to do about it except switch to another mirror. Try switching "archive" to "us.archive". It may be a bit slower since it's all the way in the USA, but it'll at least work. In a few days, try switching to the old one again, it should repair itself by then.

---

