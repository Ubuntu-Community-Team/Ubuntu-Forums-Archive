---
title: "Reduce size root partition, 2GB freed?"
date: 2007-03-17
forum: General Help
---

### Post by chewearn on 2007-03-17
Today, I decided to resize my Ubuntu root partition.  It was 144GB since I installed it, and I wanted to reduce to 20GB.  I boot up the GParted LiveCD, and everything proceed smoothly (no error).  I was able to boot up Ubuntu, and everything seems to work.

However, I later realized the used space has shrinked by about 2GB.  When the partition was 144GB, it used up 4.85GB.  But after resize to 20GB, it only used up 2.9GB.  Since GParted completed the resize without any error, I assumed this has something to do with ext3 filesystem.  I Googled, and did a search on the forum, but did not turn up any conclusive info.  The only thing that was mentioned is ext3 uses approx. 5% of the partition space for rootuser.

Just want to confirm with the experts here if this is correct, and should I be worried about the 2GB suddenly turned up.

---

