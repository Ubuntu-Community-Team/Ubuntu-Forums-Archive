---
title: "How to: 1. find 'Disks' App &amp; 2. delete files in USB drive without moving to trash"
date: 2019-01-06
forum: General Help
---

### Post by ubtnk on 2019-01-06
I am using LBT 18.10 Desktop 32 bit.

1. Can you please tell me how to find 'Disks' app? 'Discover' doesn't show and 'Muon' doesn't either. Or does it come along with LBT installation?
2. I have deleted some files in USB drive, but LBT created trash folder in it. Can you please tell me how to set up USB drive for deleting files without trash?

---

### Post by CatKiller on 2019-01-06
> **ubtnk said:**
> 2. I have deleted some files in USB drive, but LBT created trash folder in it. Can you please tell me how to set up USB drive for deleting files without trash?

Use Shift-Del rather than Del.

---

### Post by oldfred on 2019-01-06
Disks is standard in Ubuntu, but its full name is gnome-disk-utility, so I do not think it normally is in other flavors.

fred@Bionic-Z170N:~$ dpkg -s gnome-disk-utility | grep Version
Version: 3.28.3-0ubuntu1~18.04.1

---

### Post by Dennis N on 2019-01-06
In Lubuntu 18.10, **Disks** is in Discover. Look again. What to look for: see attached screen shot.

Note: I notice in checking Discover, it is not tailored to Lubuntu. Many applications it presents you would not want to install on Lubuntu.

---

