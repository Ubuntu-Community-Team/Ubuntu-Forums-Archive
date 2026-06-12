---
title: "Can't build libtorrent/rtorrent from trunk"
date: 2007-08-07
forum: General Help
---

### Post by SleepJunkie on 2007-08-07
[http://libtorrent.rakshasa.no/wiki/Install](http://libtorrent.rakshasa.no/wiki/Install)

I'm following that guide using the latest version of Ubuntu. When I get to the first step that says "./configure" I get presented with this.

```
checking for OPENSSL... configure: error: Package requirements (openssl) were not met:

No package 'openssl' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables OPENSSL_CFLAGS
and OPENSSL_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```

I'm not sure exactly what I should be doing. I followed the instructions from the link I provided. I'm not sure if I should be getting help here or from that website, but I think this is more of a general problem, and not application specific. Thanks.

---

### Post by tbroderick on 2007-08-08
Do you have libssl-dev installed?

---

### Post by SleepJunkie on 2007-08-08
Yep, I have it installed.

I put Azureus on for now.. so I guess I'll just use that until I can get this fixed.

---

### Post by tbroderick on 2007-08-08
> **SleepJunkie said:**
> Yep, I have it installed.


pkg-config and libcurl3-openssl-dev too?

---

### Post by RandB on 2007-11-20
Am up against the same problem, "No package 'openssl ' found.
same messages.
I do not have libss-dev installed. Am not sure where to find it.
Where is the simplest explanation for dummies on how to handle these problems?

---

### Post by zvacet on 2007-11-21
Are you looking for[this](http://www.howtoforge.com/compiling_rtorrent_from_svn_on_ubuntu_gutsy_gibbon)

---

### Post by zvacet on 2007-11-21
Are you looking for[this](http://www.howtoforge.com/compiling_rtorrent_from_svn_on_ubuntu_gutsy_gibbon)


Sorry for double post.Delete it!

---

### Post by RandB on 2007-11-21
Thankyou zvacet. I followed the directions from the link you posted and it works perfectly on Drake. Have uninstalled Azureus.

---

