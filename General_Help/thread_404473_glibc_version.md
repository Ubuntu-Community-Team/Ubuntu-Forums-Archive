---
title: "glibc version ?"
date: 2007-04-08
forum: General Help
---

### Post by Talon2 on 2007-04-08
I'm trying to install the current version of the BOINC client.  It won't run.

The installations instructions say:

BOINC 5.8.17 requires GLIBC 2.3 or better to run

How can I figure out what version of glibc is in Ubuntu?

Thanks.

Note:  I'm aware of the old version of BOINC in the repositories.  I'm not interested in that version and yes, I have requested the repository be updated.

---

### Post by zvacet on 2007-04-08
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=glibc&searchon=names&subword=1&version=edgy&release=all]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=glibc&searchon=names&subword=1&version=edgy&release=all")

---

### Post by saaz on 2007-04-16
I'm having the GLIBC problem also. I'm on Breezy and since there doesn't appear to be a boinc-client or boinc-manager package for this version of Ubuntu, I'm trying to run the copy of BOINC I got directly from the boinc.berkeley.edu site. The error I get is:

```
./boinc: /lib/tls/i686/cmov/libc.so.6: version `GLIBC_2.4' not found (required by ./boinc)

```

zvacet's reply didn't help either. Not sure where to find the version of glibc it's looking for at this point.

---

