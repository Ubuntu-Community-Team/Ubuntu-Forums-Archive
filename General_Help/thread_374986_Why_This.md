---
title: "Why This?"
date: 2007-03-03
forum: General Help
---

### Post by Loner_Tech on 2007-03-03
Ubuntu is a good distro the whole world knows it but why this stupid limitation in the installer it wont install on an hdd having more than 4 partitions it says u cant have more than 4 primary partitions altho two of the total 5 partitions are logical and three are primary is the ubuntu installer so dumb dat it cant even identify the right type of partition an hdd is actually having i mean acronis disk director suite shows me dat two are logical and three are primary and i have been using acronis products for a long time now and they never went wrong its the installer only i guess or wateva it is now am on zenwalk and not only zenwalk even vector linux installs like a breeze am really disappointed due to this issue i really wanted to try fluxbuntu but now i wont until and unless this issue is fixed.

---

### Post by Kateikyoushi on 2007-03-03
First it is not an ubuntu limitation, it dates back to the time when the partition table wsa stored in the boot sector of intel machines, so every MS OS and linux has to live with it. Logical partitions are in an extended partition which counts as primary.

---

### Post by Loner_Tech on 2007-03-03
> **Kateikyoushi said:**
> First it is not an ubuntu limitation, it dates back to the time when the partition table wsa stored in the boot sector of intel machines, so every MS OS and linux has to live with it. Logical partitions are in an extended partition which counts as primary.

So its proves slack is much more intelligent than debian?

---

### Post by mcduck on 2007-03-03
> **Loner_Tech said:**
> So its proves slack is much more intelligent than debian?

No, you can't have more than 4 primary partitions (or 3 primary and one extended), no matter what OS you use. If you need more partitions, they have to be logical partitions inside the extended partition.

---

