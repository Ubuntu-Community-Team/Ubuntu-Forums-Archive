---
title: "problem with deb file installation"
date: 2007-08-11
forum: General Help
---

### Post by richardy on 2007-08-11
Hi,
I recently installed Xubuntu (feisty fawn) and have so far been very happy with it. However while trying to install limewire (basic) which came as a .deb file, i got half way thru the installation (using gdebi installation tool)  then it hung while trying to install a required dependancy (sun-java). When i tried to restart the install i got the following message:

"only one management tool is allowed to run at the same time - please close the other application"

However no other applications were open. Now when ever i try to install the package i get teh same error even after shutting down and restarting etc.

Any help yu can give to resolve this issue would be much appreciated.

Cheers.

---

### Post by aysiu on 2007-08-11
Paste these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal) ```
sudo killall dpkg
sudo apt-get update
sudo apt-get install sun-java6-plugin
``` Then try double-clicking the Limewire .deb

By the way, I don't use Limewire myself, but the general consensus among forum members is that Frostwire is "better" (whatever that means). You may want to check it out:
[http://www.frostwire.com/](http://www.frostwire.com/)

---

