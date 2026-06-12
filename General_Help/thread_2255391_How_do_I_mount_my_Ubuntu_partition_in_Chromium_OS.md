---
title: "How do I mount my Ubuntu partition in Chromium OS?"
date: 2014-12-04
forum: General Help
---

### Post by ArgentWarrior on 2014-12-04
First off, I apologize if I posted this in the wrong location. If a mod moves this, *please* pm me with the new link.

I managed to get Chromium OS working fine alongside my existing Ubuntu installation. Go me. It's been added to GRUB and I can swap between them at will. But, I need to be able to access my Ubuntu home directory, and the Chromium file manager doesn't really allow you to mount and browse other partitions. Is there a way to automount my Ubuntu partition at boot time? I'll worry about making symlinks and all that later.

Ubuntu 14.04 x86, if it's relevant. This is my partition scheme. I know I know, unallocated space.
[IMG]http://i.gyazo.com/0f55992b24afa616704c86733567eafb.png[/IMG]

---

### Post by ajgreeny on 2014-12-04
Does chromiumOS use an /etc/fstab file in the same way that Linux OSs do?

---

### Post by ArgentWarrior on 2014-12-04
> **ajgreeny said:**
> Does chromiumOS use an /etc/fstab file in the same way that Linux OSs do?. 

Chrome OS and Chromium are based on Gentoo, but pretty much any trace of Gentoo is stripped. The package manager (portage) is even crippled. It does have an /etc/fstab but it's empty. I don't know if it uses that file in the same way. It also uses two partitions, which is weird. One labeled STATE (user data) and one labeled ROOT-A (core OS files). I've scoured "STATE" but couldn't find my test files I created while in Chromium. Even /home/chronos" is empty when mounted in Ubuntu.

EDIT: I'm also using ArnoldTheBat's latest nightly, if that's relevant. I can obtain root in a shell easily, if I need that.

---

### Post by ajgreeny on 2014-12-06
I have downloaded and tried out the latest live USB from ArnoldTheBat, and running as a live system it immediately sees and lets me mount and use files on my installed Xubuntu 12.04 system, just like you can open most other partitions from a Linux OS, by clicking on the partition icons in the file-manager.

I have not really looked further into this, and as I was using it as a live system, not installed on disk, it may mean I was using a root account, therefore able to read any files on the hard disk.  I don't know enough about Chromium OS to say any more of real use.

---

