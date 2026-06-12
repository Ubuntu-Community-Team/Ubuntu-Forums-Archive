---
title: "Installing a Plugin Using rpm"
date: 2017-02-07
forum: General Help
---

### Post by shane_faulkinbury2 on 2017-02-07
I have a plugin downloaded and I'm trying to install it using rpm.  Here is what the plugin tells me what to do.  ```
As root, enter in terminal:		+ # rpm -Uvh <rpm_package_file>
		+ Click Enter key and follow prompts
```

However in the folder I do not see any rpm file.  Can someone please tell me what to do?

---

### Post by deadflowr on 2017-02-07
Either try to convert it using alien or get the proper deb package.
A quick how-to on alien:
[http://www.howtogeek.com/howto/ubuntu/install-an-rpm-package-on-ubuntu-linux/]("http://www.howtogeek.com/howto/ubuntu/install-an-rpm-package-on-ubuntu-linux/")

---

### Post by wildmanne39 on 2017-02-07
Ubuntu does not use rpm files it uses .debs. There is a way to install an rpm in ubuntu but it has to be converted to a .deb file first, have you looked for the app you want to install in a .deb version?

The link tells you how to convert a rpm to a .deb but it does not always work.
[http://www.howtogeek.com/howto/ubuntu/install-an-rpm-package-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/install-an-rpm-package-on-ubuntu-linux/)

---

### Post by Perfect Storm on 2017-02-07
/ninja'd by wildmanne39 and deadflowr

You could convert the .rpm to .deb
```
sudo apt-get install alien dpkg-dev debhelper build-essential
sudo alien packagename.rpm
sudo dpkg -i packagename.deb
```

---

### Post by ajgreeny on 2017-02-07
Are you trying to install adobe-flashplugin which is what seems to be your intention?

If so simply enable the canonical-partner repos in software-sources, refresh the repos with ```
sudo apt update
``` and install it that way with ```
sudo apt install adobe-flashplugin
```
Foolproof, quick and simple!

---

### Post by &amp;KyT$0P# on 2017-02-07
> **ajgreeny said:**
> Are you trying to install adobe-flashplugin which is what seems to be your intention?

If so ...
... [https://ubuntuforums.org/showthread.php?t=2349018](https://ubuntuforums.org/showthread.php?t=2349018)

---

### Post by shane_faulkinbury2 on 2017-02-07
Sorry I didn't get back to you all earlier, but I solved my own problem.  I downloaded Software from the Ubuntu Spftware Center and installed Adobe Flash Player from there.  You had some great ideas, but this one is working perfectly for me on Chrome, Opera and Firefox.

---

### Post by oldos2er on 2017-02-07
Is this the same issue as your two previous threads on trying to install flashplugin on Ubuntu?

---

### Post by vasa1 on 2017-02-07
> **wildmanne39 said:**
> Ubuntu does not use rpm files it uses .debs. There is a way to install an rpm in ubuntu but it has to be converted to a .deb file first, have you looked for the app you want to install in a .deb version?

The link tells you how to convert a rpm to a .deb but it does not always work.
[http://www.howtogeek.com/howto/ubuntu/install-an-rpm-package-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/install-an-rpm-package-on-ubuntu-linux/)
+1

IIRC, this is the second question in the last few days involving rpms. The other is here: [I'm trying to upgrade Libreoffice to 5.3.0 so I went to their website and downloaded the rpm. Can someone please tel me how to install it?]("https://ubuntuforums.org/showthread.php?t=2351343&p=13602242#post13602242").

From [Wikipedia]("https://en.wikipedia.org/wiki/RPM_Package_Manager"):> RPM Package Manager (RPM) (originally Red Hat Package Manager; now a recursive acronym) is a package management system.
There are several distros that use rpm packages. Debian-based distros do not. They use .debs. I see no reason to try installing rpm packages on Ubuntu when the deb equivalent is available unless one is interested in acquiring the skill to install rpm packages on Debian-based systems.

---

### Post by shane_faulkinbury2 on 2017-02-08
Sorry guys, I was trying the rpm route, but decided to dump that idea almost immediately.  Like I said, the route I took worked for me!

---

