---
title: "looking for a virtual filesystem to join other filesystems"
date: 2020-03-03
forum: General Help
---

### Post by Skaperen on 2020-03-03
i've been looking around and found overlayFS, unionFS, and mergerFS, but still not what i really want, which is to make one new mount point that contains one read-only directory with one or more (usually more than one) directories mapped to a read-only name in that one mount point read-only directory.  it would be like a group of one or more bind-mounts that together appear as one combined filesystem.  mount options would be given, the list of directories and the name to make each appear as, under that one mount point.

any suggestions?  any place that lists and describes *all* Linux filesystem types?

---

### Post by HermanAB on 2020-03-04
There is a distributed file system that is in wide use by large outfits. [https://en.m.wikipedia.org/wiki/Comparison_of_distributed_file_systems](https://en.m.wikipedia.org/wiki/Comparison_of_distributed_file_systems)

---

### Post by Skaperen on 2020-03-04
everything i want to join together (various directories across one or more mounted filesystems) is on one host as is all the uses (mount point).  but the distributed nature certainly inspires.

i'm thinking i could create bind mounts of each directory and then unionFS those bind mounts together,, hoping it accepts them as a whole filesystem.

---

