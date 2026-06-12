---
title: "apt-get problem"
date: 2007-10-29
forum: General Help
---

### Post by devilears on 2007-10-29
Trying to uninstall  gnome-games-data   , but getting this:

root@L000021597:/etc/apt# apt-get remove gnome-games-data
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gnome-cards-data
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  gnome-games-data
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
28 not fully installed or removed.
Need to get 0B of archives.
After unpacking 28.1MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 201156 files and directories currently installed.)
Removing gnome-games-data ...
[B]Segmentation fault
dpkg: error processing gnome-games-data (--remove):
 subprocess post-removal script returned error exit status 139
Errors were encountered while processing:
 gnome-games-data
E: Sub-process /usr/bin/dpkg returned an error code (1)

what gives?
[/B]

---

### Post by MrFSL on 2007-10-30
Probably a segfault in scollkeeper-update.

Try doing:
```
sudo apt-get update; sudo apt-get -f installl; sudo apt-get upgrade; sudo dpkg --configure -a
``` 

If none of this works I suggest running the postrm script from the package one line at a time.

---

### Post by devilears on 2007-10-30
Thanks, but none of that worked:-(   
How do I "run the postrm script from the package one line at a time" ?

---

### Post by MrFSL on 2007-10-30
You can download the package from:
[http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-games/gnome-games-data_2.18.1-0ubuntu1_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/g/gnome-games/gnome-games-data_2.18.1-0ubuntu1_all.deb)

Then you can right click and extract the deb to a folder.

Inside you should find a file named: control.tar.gz.

Right click and extract that file as well.

Inside that compressed file you will find the script named - "postrm" - which is in fact the post removal script.

You can open it in gedit and view the contents or run it from the terminal. I suggest seeing what kind of output you get from running the script or seeing exactly where it fails etc.

For future reference - the files in the script prerm is run followed by the removal of the installed files which can be found in data.tar.gz followed by the script postrm. It seems as though your removal is failing in the postrm stage.

---

