---
title: "can't update from local repo, two translation files missing"
date: 2018-12-29
forum: General Help
---

### Post by gobo7 on 2018-12-29
trying to update a brand new install of 18.04.1 using a local repo on a usb drive.
i have been unable to find a solution to the following two errors

```

Err:9 file:/media/reposB/ubuntu1804/mirror/archive.ubuntu.com/ubuntu bionic/main Translation-en
  File not found - /media/reposB/ubuntu1804/mirror/archive.ubuntu.com/ubuntu/dists/bionic/main/i18n/Translation-en (2: No such file or directory)

Err:21 file:/media/reposB/ubuntu1804/mirror/archive.ubuntu.com/ubuntu bionic-updates/main Translation-en
  File not found - /media/reposB/ubuntu1804/mirror/archive.ubuntu.com/ubuntu/dists/bionic-updates/main/i18n/Translation-en (2: No such file or directory)

```

i'm using apt-mirror v0.5.4-1 and have two different instances of the repo, these files are missing from both.  they are also missing from bionic at archive.ubuntu.com.

is there a recommended solution or work-around?

thanks.

---

### Post by howefield on 2018-12-29
Thread moved to the "*General Help*" forum.

---

### Post by gobo7 on 2018-12-29
> **howefield said:**
> Thread moved to the "*General Help*" forum.

is this question not related to installation and upgrade?

---

### Post by howefield on 2018-12-29
> **gobo7 said:**
> is this question not related to installation and upgrade?

No. It isn't related to the *Installation & Upgrades* forum.

---

### Post by gobo7 on 2018-12-29
i found a brute force way to correct for the issue.  and there were more than two.  it seems apt-get update stops after two errors.
  in each of the  following directories of the mirror, the -en file was created from the  Translation-en.gz file.

```

./bionic-updates/restricted/i18n/
./bionic-updates/multiverse/i18n/
./bionic-updates/universe/i18n/
./bionic-updates/main/i18n/
./bionic/restricted/i18n/
./bionic/multiverse/i18n/
./bionic/universe/i18n/
./bionic/main/i18n/

```

the sha1 sums were the same as in the Index file.  this allowed apt-get update to complete.  i have not found a reason why these eight directories, out of 20, are missing the -en file.

---

