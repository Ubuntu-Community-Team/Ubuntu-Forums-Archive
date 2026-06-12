---
title: "Tar possibly corrupted: find out the exact reason ?"
date: 2020-11-10
forum: General Help
---

### Post by proturm6 on 2020-11-10
How could I find out the reason for a corrupted tar file?
```
 $ tar -tf mytar.tar
...
tar: Skipping to next header
tar: Archive contains ‘\347f\r&:n’ where numeric off_t value expected
...
```

The above occurred after ```
tar --delete
``` on that tar file.

---

### Post by HermanAB on 2020-11-10
Was that a compressed tar ball?

---

