---
title: "Problem while installing packages downloaded from internet"
date: 2013-06-24
forum: General Help
---

### Post by maxpayne61 on 2013-06-24
Hiii, I am new to ubuntu , but have a good understanding of command line interface and other stuffs. :) So after reading some posts fro internet i decided to install some of the packages of (.tar nd other compressed file format) from these 4 commands
  1)   ./configure 
2)  make 
3)  su 
4)  make install
 after changing my directory to the right destination folder. Although I was able to install some of the packages but 2 of the packages namely (bittorrent and skype) failed to install so i left them as it was. From that point my problem started, Now whenever i try to install anything from Ubuntu Software Centre it show some error messages stating "item cannot be install or repair untill package catalog is repaired".
 Then if i choose to repair , it ask me install a untrusted package libxss1 and nothing happens.  
And if try to install anything else i get a error message like this  

"The following packages have unmet dependencies:  bittorrent: Depends: python-wxgtk2.6 but it is not installed             Depends: python-twisted (>= 2.0) but it is not installed             Depends: python-crypto (>= 2.0) but it is not installed             Depends: python-psyco but it is not installed             Depends: python-zopeinterface but it is a virtual package skype: Depends: libgcc1 (>= 1:4.1.1) but 1:4.7.2-2ubuntu1 is installed        Depends: libqt4-dbus (>= 4:4.5.3) but 4:4.8.3+dfsg-0ubuntu3 is installed        Depends: libqt4-network (>= 4:4.8.0) but 4:4.8.3+dfsg-0ubuntu3 is installed        Depends: libqt4-xml (>= 4:4.5.3) but 4:4.8.3+dfsg-0ubuntu3 is installed        Depends: libqtcore4 (>= 4:4.7.0~beta1) but 4:4.8.3+dfsg-0ubuntu3 is installed        Depends: libqtgui4 (>= 4:4.8.0) but 4:4.8.3+dfsg-0ubuntu3 is installed        Depends: libstdc++6 (>= 4.6) but 4.7.2-2ubuntu1 is installed        Depends: libxss1 but it is not installed" 

Please provide me any help on this topic.....

---

### Post by dino99 on 2013-06-24
always use trusted packages sources: aka the ubuntu archives (to avoid broken dependencies, and other untrusted crap)
you can also install "unofficial" ubuntu packages from ppa(s) (launchpad)

[http://askubuntu.com/questions/122105/how-do-i-locate-and-remove-broken-packages-that-i-have-installed](http://askubuntu.com/questions/122105/how-do-i-locate-and-remove-broken-packages-that-i-have-installed)
[https://launchpad.net/ubuntu/+ppas](https://launchpad.net/ubuntu/+ppas)

---

