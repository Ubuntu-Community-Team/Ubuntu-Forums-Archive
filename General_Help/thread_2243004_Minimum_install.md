---
title: "Minimum install"
date: 2014-09-05
forum: General Help
---

### Post by mayagrafix on 2014-09-05
Just updated to 14.04 on very old laptop. Everything works great on just 117 megs of ram (LXDE distro). This pc only use is for reading PDF documents. Previously had uninstalled all other software using Software Center but now upgrade reinstalled again. Is there an easier way? Do not need Libre Office, Games, music player or Browser, etc. Just plain ol PDF Doument Viewer.

---

### Post by deadflowr on 2014-09-05
If the machine has a functional network connection, you can try a mini install.
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
when you get to the part of installing packages, you can avoid the 'buntu-desktop meta-packages and go down to manually select packages, or whatever it is called, and then sort of ala carte whatever you want.

---

### Post by christopher9 on 2014-09-05
And there's always Lubuntu 14.04...

---

### Post by mörgæs on 2014-09-05
+1 to a minimal install. After that you just need **sudo apt-get install lxde** for a minimal desktop environment, even lighter than a standard Lubuntu. 

LXDE is possibly (I don't remember) so light that you have to do package management and updates by command line.

---

### Post by Toz on 2014-09-05
Elfy is coordinating the testing of a [Xubuntu minimal iso]("https://lists.ubuntu.com/archives/xubuntu-devel/2014-September/010405.html") install for 14.10. Test iso images located at:

32 bit - 
[http://archive.ubuntu.com/ubuntu/dists/utopic/main/installer-i386/current/images/netboot/mini.iso]("http://archive.ubuntu.com/ubuntu/dists/utopic/main/installer-i386/current/images/netboot/mini.iso")
64 bit - 
[http://archive.ubuntu.com/ubuntu/dists/utopic/main/installer-amd64/current/images/netboot/mini.iso]("http://archive.ubuntu.com/ubuntu/dists/utopic/main/installer-amd64/current/images/netboot/mini.iso")

I plan on testing it this weekend to see what it includes. If you test it as well, please enter your test info in the [QA tracker]("http://iso.qa.ubuntu.com/qatracker/milestones/315/builds/76947/testcases/1655/results") - it would be a great help.

---

