---
title: "how to really remove software with synaptic"
date: 2008-02-01
forum: General Help
---

### Post by nlz on 2008-02-01
when i remove software packages with synaptic and later on i reinstall them, my PC doesn't need to download those packages again. That means that there are a lot of unused packages on my harddisk. How can i remove these, or how can i let synaptic delete the packages that i selected for complete removal?

---

### Post by danillo on 2008-02-01
Those packages are stored in /var/cache/apt/archives, I think. But I think there's an option in synaptic on the "Files" tab to remove stored packages.

---

### Post by narf y akim on 2008-02-01
> **nlz said:**
> when i remove software packages with synaptic and later on i reinstall them, my PC doesn't need to download those packages again. That means that there are a lot of unused packages on my harddisk. How can i remove these, or how can i let synaptic delete the packages that i selected for complete removal?
 Hello,
When you remove a package in Synaptic there are two options: "remove" and "completely remove". Which of these do you use?

---

### Post by bodhi.zazen on 2008-02-01
use "purge"

```
sudo apt-get remove --purge <package>
```

From the man page :

> --purge
    Use purge instead of remove for anything that would be removed. An asterisk ("*") will be displayed next to packages which are scheduled to be purged. Configuration Item: APT::Get::Purge.

use "clean"

```
sudo apt-get clean
```

From the man page :

> clean
    clean clears out the local repository of retrieved package files. It removes everything but the lock file from /var/cache/apt/archives/ and /var/cache/apt/archives/partial/. When APT is used as a dselect(8) method, clean is run automatically. Those who do not use dselect will likely want to run apt-get clean from time to time to free up disk space. 

autoclean
    Like clean, autoclean clears out the local repository of retrieved package files. The difference is that it only removes package files that can no longer be downloaded, and are largely useless. This allows a cache to be maintained over a long period without it growing out of control. The configuration option APT::Clean-Installed will prevent installed packages from being erased if it is set to off.

See also : [http://ubuntuforums.org/showthread.php?&t=140920](http://ubuntuforums.org/showthread.php?&t=140920)

[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html](http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html)

---

### Post by GreenMeanie on 2008-02-01
The easy way is in gnome when using synaptic GUI just got the files tab and select not to save to HD.

---

### Post by nlz on 2008-02-04
Thanks for all the help, as danillio said, the packages are stored, in synaptic there is also a funtion of deleted all cached files. This will delete all the archives downloaded with synaptic.

---

### Post by jan quark on 2008-02-04
for packages  got from synaptic, use

```
sudo apt-get remove --purge package
```

for downloaded packages, use 

```
sudo dpkg -r package
```

---

