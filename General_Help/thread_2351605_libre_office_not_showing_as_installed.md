---
title: "libre office not showing as installed"
date: 2017-02-05
forum: General Help
---

### Post by Nailhac on 2017-02-05
Ubuntu 16.04 
I use Libre Office 5.2.2.2 but it is not shown in the list of installed apps in Ubuntu. I was about to update it to the newer version 5.2.5 but could not find my installed version listed in installed apps. I was hoping the new version would clear up the import and position image problems. Should I uninstall my 5.2.2.2 and reinstall latest version?? Thanks in advance.

---

### Post by wildmanne39 on 2017-02-05
Unless you have the version installed that came with Ubuntu or it was installed using a .deb file it will not show up in the installed apps.

Looks like there is a .deb file of libreoffice 5.3 so you should be able to install it with software center or whatever installer you are using, if you uninstall the old one first but leave the configuration files then you can install the new version and have your old settings, but if the settings might be a problem then remove the configuration files too.
[https://www.libreoffice.org/download/download/](https://www.libreoffice.org/download/download/)

---

### Post by vasa1 on 2017-02-05
Please show the output of```
apt list --installed | grep libreoffice
``` and ```
apt-cache policy libreoffice
```

---

### Post by ajgreeny on 2017-02-05
If you enable the ppa at [https://launchpad.net/~libreoffice/+archive/ubuntu/ppa](https://launchpad.net/~libreoffice/+archive/ubuntu/ppa) your system will automatically install the newest versions from that ppa along with normal updates.

I have used it for a few years now with no problems and am currently using LO 5.3

---

