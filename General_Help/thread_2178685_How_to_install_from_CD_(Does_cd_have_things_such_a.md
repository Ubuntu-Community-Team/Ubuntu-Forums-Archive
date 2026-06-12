---
title: "How to install from CD? (Does cd have things such as build-essential?)"
date: 2013-10-04
forum: General Help
---

### Post by CONCORAN on 2013-10-04
Hi, When I install Ubuntu server, I generally install only the necessary servers (no LAMP stack). Just the basic ones.
However, when I want to install other software, the necessary packages are missing, such as build-essential, perl, python etc. Are these available on install ISOs? If so, how to install those from ISOs as opposed to downloading? I prefer from ISOs as I am bandwidth challenged.
Thanks in advance for any help.

---

### Post by ian-weisser on 2013-10-05
The install .iso includes all the packages to create a system with contents of the ubuntu-desktop metapackage.

The ubuntu-desktop metapackage is selected by the Ubuntu Desktop team to represent a usable system for an average (non-programmer) user.
It does not include build-essential or other programming tools. You must add those yourself.
See [http://packages.ubuntu.com](http://packages.ubuntu.com) or **apt-cache depends ubuntu-desktop** for a list of the ubuntu-desktop metapackage contents.

The Ubuntu community has many resources for users, like you, who are software challenged.
See [https://help.ubuntu.com/community/AptGet/Offline](https://help.ubuntu.com/community/AptGet/Offline)

---

