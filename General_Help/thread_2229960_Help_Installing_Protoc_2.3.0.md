---
title: "Help Installing Protoc 2.3.0"
date: 2014-06-16
forum: General Help
---

### Post by spyder0101 on 2014-06-16
Hello everyone. 

I'm looking for help installing protoc 2.3.0 in Ubuntu 14.04.  I was following this guide [this guide]("http://sumitshresthatech.blogspot.com/2012/03/installing-protocol-buffer-230-in-newer.html"), which in short said remove the installed libprotobuf8, then download and install 2.3.0.  Running ```
sudo apt-get remove libprotobuf8
``` gave me the following:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libserf-1-1
Use 'apt-get autoremove' to remove it.
The following packages will be REMOVED:
  compiz compiz-gnome libcompizconfig0 libprotobuf8 ubuntu-desktop unity
0 upgraded, 0 newly installed, 6 to remove and 5 not upgraded.
After this operation, 9,495 kB disk space will be freed.
```

I don't want to remove unity, but I need protoc 2.3.0.  What are my options?

Thanks in advance for the help.

---

