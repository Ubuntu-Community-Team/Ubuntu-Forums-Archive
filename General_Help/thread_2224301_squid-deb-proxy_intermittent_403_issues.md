---
title: "squid-deb-proxy intermittent 403 issues"
date: 2014-05-15
forum: General Help
---

### Post by rhpot1991 on 2014-05-15
I'm not sure how to diagnose this, I get intermittent 403 errors using squid-deb-proxy.  If I keep retrying eventually it will work, so this isn't a configuration issue.  I have looked into the squid logs and haven't found anything that stuck out as an issue.  I see these occurring on both Ubuntu URLs and 3rd party URLs like Google.

```
$ dpkg -l |grep squid-deb-proxy
ii  squid-deb-proxy                                             0.8.6                                               all          Squid proxy configuration to optimize package downloads
ii  squid-deb-proxy-client                                      0.8.6                                               all          automatic proxy discovery for APT based on Avahi
```

```
Fetched 3,732 B in 7s (482 B/s)                                                                                                       
W: Failed to fetch http://ppa.launchpad.net/mythbuntu/0.27/ubuntu/dists/trusty/main/binary-amd64/Packages  403  Forbidden

W: Failed to fetch http://ppa.launchpad.net/mythbuntu/0.27/ubuntu/dists/trusty/main/binary-i386/Packages  403  Forbidden

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/trusty/main/source/Sources  403  Forbidden

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-amd64/Packages  403  Forbidden

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages  403  Forbidden

```

Anyone have any ideas?

---

