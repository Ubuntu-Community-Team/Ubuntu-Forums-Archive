---
title: "Synaptic and apt-get not working after failed attempt at downgrading CUPS"
date: 2012-12-16
forum: General Help
---

### Post by themartin78 on 2012-12-16
Dear all,

I attempted to downgrade CUPS yesterday by pinning it to the 11.10 version, but the process failed.

However, now apt-get and synaptic refuse to work (and so does dpkg) due to dependency problems. In various threads I found "apt-get -f install" as a possible solution, but it only produces the following output:

```
dpkg: dependency problems prevent configuration of cups:
 cups-filters (1.0.18-0ubuntu0.1) breaks cups (<< 1.5.0-16) and is installed.
  Version of cups to be configured is 1.5.0-8.
dpkg: error processing cups (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 cups
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any idea of how I can get rid of that problem? Help will be greatly appreciated!

My version of Ubuntu is 12.04

Oh, and by the way... it would be ok to have my old (12.04 that is) version of CUPS again.

---

### Post by thnewguy on 2012-12-16
I think you may have to unpin the older version of CUPS and then run apt-get -f install.

---

### Post by themartin78 on 2012-12-16
I actually already did that... to no avail though :( The problem remains.

I also tried to remove the cups package... which didn't work either and resulted in a very similar error message (it referred to the same conflict).

---

