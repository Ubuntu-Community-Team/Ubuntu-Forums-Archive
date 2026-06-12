---
title: "How to upgrade a package?"
date: 2019-10-22
forum: General Help
---

### Post by notooth1 on 2019-10-22
Hello,

I currently have zfsutils-linux 0.7.12 on Ubuntu 19.10. Can anyone guide me to upgrade this package to the latest version (0.8.1)?

---

### Post by uRock on 2019-10-22
Hello and welcome to the forums.

You'd have to download and install it manually from [source]("https://zfsonlinux.org/") or [GIT]("https://github.com/zfsonlinux/zfs").

---

### Post by Holger_Gehrke on 2019-10-22
@uRock: Are you sure ? [Ubuntu package search]("https://packages.ubuntu.com/search?keywords=zfsutils-linux&searchon=names&suite=all&section=all") says 19.10 comes with 0.8.1, 0.7.12 is the package in 19.04 ...

@notooth1: Did you do a Release upgrade from 19.04 to 19.10 ? Unless the search results I mentioned above are wrong, that's the only situation I could imagine where you might for some reason end up with an older version of a package.

Holger

---

### Post by rsteinmetz70112 on 2019-10-22
Sometimes if a release upgrade goes wrong, possibly due to an interruption in the downloads or a corrupted download you end up this way.

But I would first check you system for consistency with 

```
sudo apt install -f
sudo dpkg --configure -a
```

Fix any errors
If those run without error:

```
sudo apt update
sudo apt upgrade
```

That should fix it.
If that doesn't fix it 

```
sudo apt install zfsutils-linux --reinstall
```

---

### Post by notooth1 on 2019-10-23
I got the new zfsutils-linux by installing the whole new Ubuntu 19.10. Thank you all.

---

### Post by slickymaster on 2019-10-23
*Thread moved to **General Help**.*

---

