---
title: "Unable to download xosd"
date: 2005-09-03
forum: General Help
---

### Post by PhilOSparta on 2005-09-03
libxosd2 was part of my Ubuntu load.  I assume that I need xosd-bin to actually run xosd commands.    When Synaptic attempts to download xosd-bin I get the following:

W: Failed to fetch [ftp://mirror.mcs.anl.gov/pub/ubuntu/pool/universe/x/xosd/xosd-bin_2.2.14-1ubuntu1_i386.deb](ftp://mirror.mcs.anl.gov/pub/ubuntu/pool/universe/x/xosd/xosd-bin_2.2.14-1ubuntu1_i386.deb)
  Unable to fetch file, server said 'Failed to open file.  ' [IP: 140.221.37.132 21]

Does the file exist?  Is there another mirror site where the file can be located?

Thanks for your help.

Phil

---

### Post by [pl]ice on 2005-09-04
Pob: 1 [ftp://mirror.mcs.anl.gov](ftp://mirror.mcs.anl.gov) hoary/universe xosd-bin 2.2.14-1ubuntu1 [19,9kB]
Pobrano 19,9kB w 19s (1008B/s)

that worked for me.

from sources.list:
i think it's this one:
deb [ftp://mirror.mcs.anl.gov/pub/ubuntu](ftp://mirror.mcs.anl.gov/pub/ubuntu) hoary main restricted universe multiverse


deb [ftp://mirror.mcs.anl.gov/pub/ubuntu](ftp://mirror.mcs.anl.gov/pub/ubuntu) hoary-updates main restricted

---

### Post by PhilOSparta on 2005-09-10
[QUOTE='[pl]ice']Pob: 1 [ftp://mirror.mcs.anl.gov](ftp://mirror.mcs.anl.gov) hoary/universe xosd-bin 2.2.14-1ubuntu1 [19,9kB]
Pobrano 19,9kB w 19s (1008B/s)

that worked for me.

from sources.list:
i think it's this one:
deb [ftp://mirror.mcs.anl.gov/pub/ubuntu](ftp://mirror.mcs.anl.gov/pub/ubuntu) hoary main restricted universe multiverse


deb [ftp://mirror.mcs.anl.gov/pub/ubuntu](ftp://mirror.mcs.anl.gov/pub/ubuntu) hoary-updates main restricted[/QUOTE]
 Thanks!  It worked fine.

Phil

---

