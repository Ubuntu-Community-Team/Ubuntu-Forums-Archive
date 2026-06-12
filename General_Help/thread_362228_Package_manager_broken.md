---
title: "Package manager broken"
date: 2007-02-15
forum: General Help
---

### Post by mevets on 2007-02-15
I installed VirtualBox using their edgy deb file ([http://www.virtualbox.org/download/1.3.4/VirtualBox_1.3.4_Ubuntu_edgy_i386.deb)](http://www.virtualbox.org/download/1.3.4/VirtualBox_1.3.4_Ubuntu_edgy_i386.deb)). During the install the package manager stalled tremendously and I had to force quit it. Now I can not interact with Software Updates, Snyaptic, etc. At one point software updates informed me I had to run dkpg in the terminal so I did so. Now I get an error saying package VirtualBox needs to be reinstalled but it cannot find the package and the error that it cannot open something in cache.

Is there a way to fix this? For example could I tell it where the deb file is to reinstall VirtualBox, which will not install when I run it. I recieve the error that it is either corrupted or I do not have the right permissions.

---

### Post by Kateikyoushi on 2007-02-15
Try to delete the corrupted packages from your machine then install again.

---

### Post by mevets on 2007-02-15
I did that. I then I redownloaded the deb file from their site and I recieve the same message.

I maybe that I do not have the right permissions. If so, how would I run the package with root priveleges? I tried to sudo gdebi but I really dont know if I should be running the pkg with root or gdebi, etc.

---

