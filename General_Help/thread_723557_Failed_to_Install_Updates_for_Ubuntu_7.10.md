---
title: "Failed to Install Updates for Ubuntu 7.10"
date: 2008-03-13
forum: General Help
---

### Post by Darkhack on 2008-03-13
This is what I get when I try to do "apt-get upgrade"

```
(Reading database ... dpkg: error processing /var/cache/apt/archives/libphonon4_4%3a4.0.2-0ubuntu2~gutsy1~ppa1_i386.deb (--unpack):
 files list file for package `vlc' is missing final newline
Errors were encountered while processing:
 /var/cache/apt/archives/libphonon4_4%3a4.0.2-0ubuntu2~gutsy1~ppa1_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by {BzF}~JOKesTER on 2008-03-13
Try:

sudo apt-get update

---

