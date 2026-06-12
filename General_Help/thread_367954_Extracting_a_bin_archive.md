---
title: "Extracting a bin archive"
date: 2007-02-22
forum: General Help
---

### Post by z987k on 2007-02-22
Is there a way to extract the contents of a bin archive?  Not a bin as in the normal binary executable, but like the bin and cue files of cd images.

---

### Post by Xappe on 2007-02-22
use bchunk to convert the bin/cue to iso and mount the iso image on your system:

create a mountpoint (a directory of your choice), then
```
sudo mount -t iso9660 -o loop <isofile> <mountpoint>
```

---

### Post by z987k on 2007-02-22
bchunk, exactly what I needed, thanks!

---

