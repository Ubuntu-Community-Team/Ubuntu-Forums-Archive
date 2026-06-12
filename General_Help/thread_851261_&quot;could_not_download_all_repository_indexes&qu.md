---
title: "&quot;could not download all repository indexes&quot;"
date: 2008-07-06
forum: General Help
---

### Post by zero777zero on 2008-07-06
my update manager has been working fine with one exception, i'll often get this message:

could not download all repository indexes

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.

Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Failed to fetch cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/dists/hardy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Some index files failed to download, they have been ignored, or old ones used instead.


----

when i googled for this problem it was all on installation, but my Hardy Heron has been running fine for me since installation.

hardware: sony vaio vgn-fz190

---

### Post by drs305 on 2008-07-06
This message is generated when you don't have the ubuntu install CD inserted when you run updates. To eliminate the message, open Synaptic, Settings, Repositories and uncheck the CD-rom in the lower left section.

If you get further messages you can post your sources.list for inspection:
```

cat /etc/apt/sources.list

```

---

