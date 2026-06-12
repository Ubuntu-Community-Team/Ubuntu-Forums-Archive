---
title: "Source code download (apt-get)"
date: 2008-03-10
forum: General Help
---

### Post by myle on 2008-03-10
```
myle@myle-desktop:~$ sudo apt-get source coreutils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Could not open file /var/lib/apt/lists/gauvain.tuxfamily.org_repos_dists_gutsy_contrib_source_Sources - open (2 No such file or directory)

```

What's wrong? How can I download the source code through apt-get?

---

### Post by justleen on 2008-03-10
looks like there is an extra repository which can not be openen.
The command is correct, as far as I can tell (just check man apt-get, this shoudl download and extract the source in the current work dir)

if i check that path that is failing, I see all my reopositories listed.
check /etc/apt/sources.list  for any "weird" sources. comment them out, run apt-get update afterwards and try again?

---

### Post by myle on 2008-03-31
Thanks, it worked. I removed some weird sources.

---

