---
title: "Where apt downloads the .deb packages?"
date: 2008-06-14
forum: General Help
---

### Post by rivalslayer on 2008-06-14
When apt downloads all the packages from the net, where does it store them, can I use it for the future? Or it deletes the packages?

Please help!:confused:

---

### Post by xravexheavenx on 2008-06-14
It should clean them up unless you specify otherwise.

---

### Post by ad_267 on 2008-06-14
They're in /var/cache/apt/archives


It doesn't delete them, but you can remove them with "sudo apt-get clean"

From "man apt-get"
> clean
           clean clears out the local repository of retrieved package files.
           It removes everything but the lock file from
           /var/cache/apt/archives/ and /var/cache/apt/archives/partial/. When
           APT is used as a dselect(8) method, clean is run automatically.
           Those who do not use dselect will likely want to run apt-get clean
           from time to time to free up disk space.

       autoclean
           Like clean, autoclean clears out the local repository of retrieved
           package files. The difference is that it only removes package files
           that can no longer be downloaded, and are largely useless. This
           allows a cache to be maintained over a long period without it
           growing out of control. The configuration option
           APT::Clean-Installed will prevent installed packages from being
           erased if it is set to off.

       autoremove
           autoremove is used to remove packages that were automatically
           installed to satisfy dependencies for some package and that are no
           more needed.


---

### Post by ad_267 on 2008-06-14
Also have a look at aptoncd if you want something for backing up packages easily like for use on another computer.

---

### Post by NullHead on 2008-06-14
There is also [http://packages.ubuntu.com](http://packages.ubuntu.com)

---

