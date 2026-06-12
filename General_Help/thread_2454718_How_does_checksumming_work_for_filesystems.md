---
title: "How does checksumming work for filesystems?"
date: 2020-12-04
forum: General Help
---

### Post by jcdenton1995 on 2020-12-04
Hello all,

Just reading about metadata checksumming for ext4 but I can't find an explanation of how it basically works. Does the filesystem driver basically hash metadata before it is written to the disk while still stored in memory, and then hash the metadata on the disk once it's written to check it's not been corrupted during the write?

---

### Post by HermanAB on 2020-12-05
Here is something:
[https://ext4.wiki.kernel.org/index.php/Ext4_Metadata_Checksums](https://ext4.wiki.kernel.org/index.php/Ext4_Metadata_Checksums)

---

### Post by jcdenton1995 on 2020-12-07
Thanks!

---

