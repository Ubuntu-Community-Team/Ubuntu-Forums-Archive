---
title: "How to stop this popup"
date: 2017-01-24
forum: General Help
---

### Post by strider310 on 2017-01-24
Each time I start Ubuntu I get this message. How to I stop this popup?
==============================

Failure to download extra data files


The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.


ttf-mscorefonts-installer


The download will be attempted again later, or you can try the download again now.  Running this command requires an active Internet connection.
==============================

---

### Post by bearlake on 2017-01-24
> **strider310 said:**
> Each time I start Ubuntu I get this message. How to I stop this popup?
==============================

Failure to download extra data files


The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.


ttf-mscorefonts-installer


The download will be attempted again later, or you can try the download again now.  Running this command requires an active Internet connection.
==============================

This should do the trick.

```
sudo apt purge ttf-mscorefonts-installer
```

```
wget http://ftp.de.debian.org/debian/pool/contrib/m/msttcorefonts/ttf-mscorefonts-installer_3.6_all.deb -P ~/Downloads
```

```
sudo apt install ~/Downloads/ttf-mscorefonts-installer_3.6_all.deb
```

1st command to get rid of the current package

2nd command to download the 3.6 version of the package to your Downloads folder.

3rd command to install the new package

---

### Post by strider310 on 2017-01-25
Thanks!

---

### Post by bearlake on 2017-01-25
> **strider310 said:**
> Thanks!

Glad I was able to help.

Should mark this thread as "[Solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")" as to help other folks with the same problem. :)

---

