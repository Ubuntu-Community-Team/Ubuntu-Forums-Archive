---
title: "Unable to install any software"
date: 2016-10-02
forum: General Help
---

### Post by Richard-S on 2016-10-02
I have Ubunto 10.10 on a Dell box with a Pentium 3 and 500 megs of RAM. I am at a remote office and my newer box died so I am using this older box. I can't afford to risk updating to a newer flavour. I have no time right now to handle a failed install.

I have attempted to install Libre office from a deb file and Gimp from the software center, as well as a few others. I get a revolving star and then it goes back to the install page asking me to press "Install."

Any ideas as to what am I doing wrong? My box is old but it exceeds the minimum requirements for Libre Office.

---

### Post by Bashing-om on 2016-10-02
Richard-S; Hello;

It is not that you are doing anything wrong - in that sense.
It is that release 10.10 is long long End_Of_Life, and the software repository no longer exist. It has no support !
End of story. 

The only viable thing you CAN DO is fresh install a supported release .

[INDENT]that is the way it is
[/INDENT]

---

### Post by Impavidus on 2016-10-02
That box is really old. [Lubuntu system requirements]("http://lubuntu.net/#System_Requirements") says 512 MB and Pentium 4 or Pentium M at least. I don't know whether that CPU supports PAE. If not, you can try some ultra-light Linux distro.

If this is really a temporary solution you could change the software sources and point it to the old releases:
[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
[http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-an-old-unsupported-release](http://askubuntu.com/questions/91815/how-to-install-software-or-upgrade-from-an-old-unsupported-release)

Your system will not be secure. Ubuntu 10.10 hasn't been supported for 4.5 years so there are quite a lot of unpatched known security holes.

---

### Post by mörgæs on 2016-10-03
A Pentium 3 supports PAE as do 2 and 4. 

Libreoffice is not that heavy to run, and I expect a Pentium 3 to work. Web browsing will be limited, though.

I suggest that you read the Old Hardware link in my signature. After that A) install the smallest possible desktop environment using the 16.04.1 minimal ISO and B) apply the changes mentioned for Libreoffice.

---

