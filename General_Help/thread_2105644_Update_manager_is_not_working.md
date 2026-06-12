---
title: "Update manager is not working"
date: 2013-01-16
forum: General Help
---

### Post by Exp3rt on 2013-01-16
Hello all dear,
My update manager has a few problem. my Internet speed is 128 kbps, after few minutes this problem will be appear.
```
W:Failed to fetch gzip:/var/lib/apt/lists/partial/us.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages  Hash Sum mismatch
, E:Some index files failed to download. They have been ignored, or old ones used instead.

```
My Ubuntu version is 12.4 LTS 32 bit OS.
what should I do?

---

### Post by fantab on 2013-01-16
Run the following commands from the Terminal one by one:

```
$ sudo -i
# apt-get clean
# cd /var/lib/apt
# mv lists lists.old
# mkdir -p lists/partial
# apt-get clean
# apt-get update
#exit
```

Close the Terminal and run the Update Manager

---

### Post by Exp3rt on 2013-03-27
> **fantab said:**
> Run the following commands from the Terminal one by one:

```
$ sudo -i
# apt-get clean
# cd /var/lib/apt
# mv lists lists.old
# mkdir -p lists/partial
# apt-get clean
# apt-get update
#exit
```

Close the Terminal and run the Update Manager
Tanks a lot,
It worked.

---

