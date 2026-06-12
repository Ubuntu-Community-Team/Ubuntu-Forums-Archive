---
title: "Memcache"
date: 2019-02-10
forum: General Help
---

### Post by antmar904 on 2019-02-10
Hi all

I’m very new to Linux so if I’m not clear sorry. 

I had ownCloud running on server 16.04 with memcache/redid installed and everything was working fine. I then upgraded to Ubuntu 18.04 and now I keep getting a memcache error when I try to visit my site:

Memcache \OC\Memcache\Redis not available for local cache Is the matching PHP module installed and enabled?

I tried reinstalling redis but I’m still getting the error.

---

### Post by dragonfly41 on 2019-02-10
I would check if 18.04 has switched to higher order PHP.
You might have to choose PHP version. Just a guess from reading that report line .. "[COLOR=#000000]matching PHP"[/COLOR].

---

### Post by antmar904 on 2019-02-10
Are you suggesting I check what version of php is installed?  Then what’s next?  Thanks again.

---

