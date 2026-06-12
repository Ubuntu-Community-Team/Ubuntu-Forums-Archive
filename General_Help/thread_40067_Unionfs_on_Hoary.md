---
title: "Unionfs on Hoary"
date: 2005-06-07
forum: General Help
---

### Post by chrono325 on 2005-06-07
Hi all,
I just installed Hoary yesterday, but have been a Gentoo user for over a year now. I am using Ubuntu on a dual boot WinXP box and wish to mount some of the directories like My Music etc. under Ubuntu using Unionfs. Problem is, I cannot find the package for Unionfs. I have Universe in my repositories but not Multiverse (which I assume I would not need). Through a bit of googling, I found a deb called "unionfs-utils_1.0.11-1_i386.deb", but issuing an "rpm -i unionfs-utils_1.0.11-1_i386.deb" failed to read the manifest. There is an excellent chance that I am just using RPM wrong, this is my first distro other than Gentoo. If anyone has any pointers, please let me know.

Fantastic distro overall, I was most impressed by how simple, complete, and FAST  :smile: the installation was.

---

### Post by [pl]ice on 2005-06-07
try alien -i xxxx

---

### Post by adwait on 2005-06-07
If the file ends in *.deb, it is not an rpm. In Ubuntu, you use the dpkg command. Try dpkg -i (filename) command.

---

