---
title: "Ubuntu swapfile"
date: 2019-07-28
forum: General Help
---

### Post by hsaptus on 2019-07-28
So I lost my swapfile and now I can't create it . everything I try I get the read-only reply. Using the sudo command but no go.
Using Ubuntu 18.04 tls
Any idea?

---

### Post by HermanAB on 2019-07-28
Everything you never wanted to know about swap files is explained very nicely in the swapon man page:
$ man swapon

---

### Post by hsaptus on 2019-07-28
Not exactly the same. I know how to create it. The read-only thing is in between

---

### Post by TheFu on 2019-07-28
**mkswap** is the command to create/format it.
**swapon** is the command to make it available.
Both of those tools have manpages.

It might be necessary to use **dd** to create a file of a specific length before using mkswap.

Yep, some tool is needed to make a file that can be formatted into swap with mkswap. You can make that initial file any way you like. You can copy, concatenate, dd, or conjure a file of the size you want for swap (4.1G is probably a reasonable answer for any Linux desktop).  It doesn't matter how the file is made, since mkswap is going to overwrite everything inside anyways.  Just don't use a hardlink file or a device (like a specific partition), unless you intend to destroy the contents while converting it into swap.

---

