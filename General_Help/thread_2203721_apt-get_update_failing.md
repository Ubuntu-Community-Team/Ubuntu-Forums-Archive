---
title: "apt-get update failing"
date: 2014-02-04
forum: General Help
---

### Post by hillerj on 2014-02-04
I am doing an "apt-get update" and receiving the following errors.  I have searched the forums and followed instructions on some similar posts but still can't get past it.  Any suggestions?

```
W: Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_quantal_universe_binary-amd64_Packages  Hash Sum mismatch


W: Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_quantal_universe_binary-i386_Packages  Hash Sum mismatch


E: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by ubudog on 2014-02-04
Try removing the contents of /var/lib/apt/lists.

```
sudo rm -rf /var/lib/apt/lists/*
```

Then re-run the apt-get update, and it should redownload the lists for you.

---

### Post by hillerj on 2014-02-04
Thanks for the very very very quick reply.  And as a bonus it worked!  Thank you so much.  I could have sworn I had found that solution elsewhere but I guess not.

---

### Post by ubudog on 2014-02-04
> **hillerj said:**
> Thanks for the very very very quick reply.  And as a bonus it worked!  Thank you so much.  I could have sworn I had found that solution elsewhere but I guess not.

Great to hear, glad it worked!

---

