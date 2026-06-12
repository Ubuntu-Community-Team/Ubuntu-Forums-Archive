---
title: "BTRFS resize on a running / - n00b question"
date: 2013-09-17
forum: General Help
---

### Post by 64bitiso on 2013-09-17
Hello :)

I just did:

```

btrfs filesystem resize -30g /

```

On a test machine running 64 bit 13.04, and as a BTRFS n00b, I want to know why, when I do this, does it shrink the amount of free space *inside *the partition, and not the actual BTRFS formatted "/" partition itself? When I do a before and after view of the partition in "Gparted", I just see more space used when I shrank it... :/

Thank you.

---

