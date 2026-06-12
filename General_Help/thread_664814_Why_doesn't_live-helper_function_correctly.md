---
title: "Why doesn't live-helper function correctly?"
date: 2008-01-11
forum: General Help
---

### Post by rocketman768 on 2008-01-11
Using live-helper to make my own custom live boot image, I encountered some problems. First, it couldn't install grub or volumeid because it "could not stat /etc/fstab". In the chroot directory, fstab didn't even exist so I created it as a blank file and then got those installed. Second, the package list I chose was the "rescue" list. I noticed during the install that almost none of the cool packages got installed cuz apt couldn't find the package names. I chroot'd into the chroot directory and changed /etc/apt/sources.list to include the universe and multiverse repositories and then ran aptitude to install the rescue packages.

My question has two parts: 1) Has this happened to anyone else? 2) Shouldn't live-helper check to make sure the correct repositories are in sources.list by itself?

---

### Post by pointone on 2008-01-11
live-helper is primarily designed for Debian, and is still in the alpha stages of development. Ubuntu support is quite lacking. I'd suggest building a Debian-based image for better results.

---

