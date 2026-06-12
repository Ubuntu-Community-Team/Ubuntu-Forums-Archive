---
title: "some repos down (archives.securtity....)"
date: 2007-07-11
forum: General Help
---

### Post by sefs on 2007-07-11
I am trying to install vmware-tools from the repos...but after clicking on the apply button, nothing happens it just sticks there.


and after a little while of waiting

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.20/vmware-tools-kernel-modules-2.6.20-16_2.6.20.5-16.29_i386.deb](http://security.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.20/vmware-tools-kernel-modules-2.6.20-16_2.6.20.5-16.29_i386.deb)
  Connection failed [IP: 91.189.88.31 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/multiverse/l/linux-meta/vmware-tools-kernel-modules_2.6.20.16.28.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/multiverse/l/linux-meta/vmware-tools-kernel-modules_2.6.20.16.28.1_i386.deb)

---

### Post by zvacet on 2007-07-11
Do you have all repos open?system>administration>software sources<chek all boxes and reload

---

### Post by dreadlord_chris on 2007-07-11
Try again a little later - that repo seems to be having some issues...

---

### Post by daniel of sarnia on 2007-07-11
People here [http://ubuntuforums.org/showthread.php?t=498386]("http://ubuntuforums.org/showthread.php?t=498386") including me are having similar problems with unresponsive repos.

---

### Post by thePsychologist on 2007-07-11
I've been having problems with it today (just a few minutes ago). Try waiting for a few seconds when it's stuck, kill apt-get/aptitude (Ctrl-C), and then do it again. For some reason that works for me.

---

