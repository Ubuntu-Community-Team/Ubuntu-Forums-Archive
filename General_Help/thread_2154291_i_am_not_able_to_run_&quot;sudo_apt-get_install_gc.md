---
title: "i am not able to run &quot;sudo apt-get install gcc make binutils ncurses*-dev perl uboot&quot;"
date: 2013-06-14
forum: General Help
---

### Post by py2901 on 2013-06-14
i am not able to run "sudo apt-get install gcc make binutils ncurses*-dev perl uboot-mkimage"
terminal throwing 

[sudo] password for assisi: 
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/in.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.



this type of error
plz help me as soon as possible because of it my entire work is stopped

---

### Post by slickymaster on 2013-06-14
Please try the following in a terminal window:```
sudo rm /var/lib/apt/lists/* -vf && sudo apt-get update
```

---

