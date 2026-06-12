---
title: "Deleting Cache files??"
date: 2007-02-07
forum: General Help
---

### Post by NZ-Wanderer on 2007-02-07
Question:

Is it safe to delete the files out of:

var/cache/apt/archives

Reason for asking is that that directory is now over 8.1GB, and I would like to free up some space on my / partition..

---

### Post by codejunkie on 2007-02-07
> **NZ-Wanderer said:**
> Question:

Is it safe to delete the files out of:

var/cache/apt/archives

Reason for asking is that that directory is now over 8.1GB, and I would like to free up some space on my / partition..
yes, and you can do it easily by running the command ```
sudo apt-get clean
```to remove all files in there or ```
sudo apt-get autoclean
```to only remove the older versions of packages.

---

### Post by taurus on 2007-02-07
Yes.

```
sudo aptitude clean
```

---

### Post by NZ-Wanderer on 2007-02-07
Many thanks for the replies, much appreciated..

Be good to get some space back :)

---

### Post by taurus on 2007-02-07
If you are using synaptic, there is an option to remove the cache after it's installed.

---

