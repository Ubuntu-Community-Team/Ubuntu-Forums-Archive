---
title: "List of Installed Programs"
date: 2013-10-09
forum: General Help
---

### Post by Vesnog on 2013-10-09
In Ubuntu 12.04 LTS is there a way to extract the list of all installed programs? The reason behind is that I plan reinstalling Ubuntu due to experiencing internal errors; I have my personal files on a separate logical partition.

---

### Post by RH3dDbz on 2013-10-09
Hello Vesnog, there's a program called "Synaptic Package Manager", this program show you all programs are installed in the computer, and give you option to uninstall, maybe this program can help you.

---

### Post by oldfred on 2013-10-09
Above is one good way. 
 [http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)
File > Save Markings As, tick the "Save full state, not only changes". If you don't tick the 'full state', you will probably get an empty file.
To restore, you would use File, 'Read Markings'



You can also use command line.
       from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages
From New install
sudo dpkg --set-selections < my-packages
sudo apt-get -y update
sudo apt-get dselect-upgrade

---

### Post by Easy Limits on 2013-10-09
The software center shows installed programs.  Button at top.

---

