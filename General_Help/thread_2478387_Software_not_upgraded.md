---
title: "Software not upgraded"
date: 2022-08-25
forum: General Help
---

### Post by satimis on 2022-08-25
Hi all,

Ubuntu22.04 upgraded from Ubuntu20.04 (last week)

Running Software Updater, it indicates "the software is up-to-day"

On Terminal
$ sudo apt update```

Hit:1 http://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://security.ubuntu.com/ubuntu jammy-security InRelease               
Hit:3 http://hk.archive.ubuntu.com/ubuntu jammy InRelease                      
Hit:4 http://hk.archive.ubuntu.com/ubuntu jammy-updates InRelease
Hit:5 http://hk.archive.ubuntu.com/ubuntu jammy-backports InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
2 packages can be upgraded. Run 'apt list --upgradable' to see them.

```

$ sudo apt upgrade```

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libnftables1 nftables
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.

```
What shall I do?

Run "sudo apt install them" ?

Please advise.  Thanks

Regards

---

### Post by Impavidus on 2022-08-25
That must be the phased updates. If you wish, you can run```
sudo apt upgrade nftables
```That will upgrade those packages. If you don't and no problems are reported with these upgrades, **apt upgrade** will upgrade them later.

---

### Post by satimis on 2022-08-25
> **Impavidus said:**
> That must be the phased updates. If you wish, you can run```
sudo apt upgrade nftables
```That will upgrade those packages. If you don't and no problems are reported with these upgrades, **apt upgrade** will upgrade them later.
Thanks for your advice.

It seems to me that there is no problem in running Ubuntu 22.04 without them.  I'll leave them a while until next upgrade

Regards

---

