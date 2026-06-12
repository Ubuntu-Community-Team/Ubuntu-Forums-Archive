---
title: "Obtaining packages w/o apt-get from Windows"
date: 2005-06-22
forum: General Help
---

### Post by 2sdnub on 2005-06-22
I use Kubuntu 5.04,  installed on a machine without access to the internet. I am posting from a Windows machine. I want to obtain packages, specifically x-dev and x-window-system-dev, obviously I cannot use apt-get, so how would I go about getting these packages? Thank you for your help!

---

### Post by xalphas on 2005-06-22
By getting debs and dependency debs from here. [http://packages.ubuntu.com/hoary/x11/x-window-system-dev](http://packages.ubuntu.com/hoary/x11/x-window-system-dev)
Then go back to kubuntu and dpkg -i *.deb into the folder of downloaded debs.

---

