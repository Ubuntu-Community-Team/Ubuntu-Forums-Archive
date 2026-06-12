---
title: "squid &amp; tor proxy servers"
date: 2007-10-01
forum: General Help
---

### Post by iconicmoronic on 2007-10-01
i want to know if the squid proxy server performs the same sort of tasks as the TOR proxy server?

i'm trying to configure squid, and its been confusing. i hate to be a quitter, but it took me three seconds to configure TOR, so do these two applications work the same?

---

### Post by Seisen on 2007-10-01
Tor works in layers like in an onion hence why it is called onion routing while squid proxy is  more of a cache.

---

### Post by iconicmoronic on 2007-10-02
so what? anonymous wise TOR is more efficient and tracker wise Squid is more apt? i guess what i'm looking for in a proxy is the best optimizationl how so?:

I enjoy privacy, and I enjoy information.

Tor then is good for anonymous --ness? and Squid good to know where I've been? Cached information to me is as good as any other, so what I mean is I want a proxy that does both. Whose been where?  Where have I been?

---

### Post by SeanTater on 2007-10-02
squid has several functions, but connecting through a squid cache will only make your information anonymous if you are connecting through someone else's squid server (read on "open proxy"). About the same goes for tor, but it has a network for it, so you theoretically (I've never used it) don't have to go looking for an open proxy.

But in honesty, they have entirely different goals in mind as I see it; Squid can do web server acceleration and cache too, transparent proxy, and other cool stuff tor was not intended for.

In English:

If you want relative anonymity, use Tor.
If you're just looking for web pages to load faster, use squid.

---

