---
title: "Customization of the installation"
date: 2013-09-03
forum: General Help
---

### Post by leonixyz on 2013-09-03
Hello, I'm developing a project for the school, I have to write a bash script that allows the user to customize an Ubuntu 12.04 ISO file, by installing, uninstalling, upgrading packages, and so on.  Basically the script mounts the ISO to a folder, mounts and copy the content of the squashfs to another folder, and chroot into it.  Thus, a single script should manage all possible operations, that are: uninstall packages, install packages, upgrade the system, perform a dist-upgrade.  Thanks to the developers of apt-get it is very simple to do these operations, my question is: is there a particular order to do (hypotetically) all these operations?  I thought that this sequence could be a good one: ```
1) apt-get update 2) apt-get remove $something 3) apt-get install $something 4) apt-get upgrade 5) apt-get install -f      # to fix, if any, broken dependencies, right? 6) apt-get autoremove 7) apt-get clean 8) apt-get dist-upgrade
```  What do You think? Thanks, Giulio```
PS: Why, if I submit this post, all newline characters are substituted by blank spaces?
```

---

