---
title: "How do I encrypt a flash drive?"
date: 2014-06-30
forum: General Help
---

### Post by PopsTheSailor on 2014-06-30
Using 13.10
Looking for directions on how to encrypt my flash drive. I found some directions but they are old and don't seem to work. My research says that ecryptfs is the latest thing but I can't find any directions on how to encrypt a new flash drive (no data on it yet).

---

### Post by HermanAB on 2014-06-30
# cryptsetup -y -v luksFormat /dev/whatever

Read the man page.  It is all in there, but it sure helps having an example like the above to begin with.

---

