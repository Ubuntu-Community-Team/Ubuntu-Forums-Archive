---
title: "Trouble installing Pac Manager on 15.04"
date: 2015-09-23
forum: General Help
---

### Post by jwhitene on 2015-09-23
I'm trying to install pac manager 4.5.5.5 in a deb format that I downloaded from their sourceforge area.  

Most instructions for installing pac say the same thing:

dpkg -i pac*.deb
which fails due to dependencies.  
apt-get -f install 
then try it again
dpkg -i pac*.deb

which still leaves me without pac installed due to missing dependencies

I also tried using a repo like described here:  [http://sysads.co.uk/2014/08/install-pac-manager-4-5-4-ubuntu-14-04/](http://sysads.co.uk/2014/08/install-pac-manager-4-5-4-ubuntu-14-04/) but it didn't resolve missing deps.

Finally I found this article:  [http://www.unixmen.com/how-to-manage-multiple-ssh-sessions-using-cluster-ssh-and-pac-manager/](http://www.unixmen.com/how-to-manage-multiple-ssh-sessions-using-cluster-ssh-and-pac-manager/)

It advised using gdebi alone, instead of dpkg -i...followed by an apt-get -f install to fix dependencies.  

sudo apt-get install gdebi
sudo gdebi pac-4.5.5-all.deb

I'm just curious why dpkg/apt-get -f install failed to fix the dependencies?  Is it advisable to always use gdebi when install *.deb files?

Lastly, is pac manager the best ssh session manager for ubuntu, or are there better ones that I've not come across yet?  I really like mremote on windows.  It has a tree view of servers that you can put in nested folders, and it handles both ssh/ssh2/rdp/vnc etc.

---

### Post by ian-weisser on 2015-09-23
> **jwhitene said:**
> I'm just curious why dpkg/apt-get -f install failed to fix the dependencies?

Generally, failure to 'fix' dependencies occurs when a version conflict or file conflict is introduced by the proposed change.
We would need to see the exact error messages to answer your question with any useful detail.

---

### Post by jwhitene on 2015-09-23
OK, if I run across it again, I'll post the full details.  I was just mainly curious about apt-get -f install vs gdebi.  For now pac manager is installed and working.

---

