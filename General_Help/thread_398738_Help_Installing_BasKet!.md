---
title: "Help Installing BasKet!"
date: 2007-04-01
forum: General Help
---

### Post by Kunstar on 2007-04-01
I really want to install [BasKet]("http://basket.kde.org/index.php") (KDE application) in Ubuntu Edgy but it doesn't come as a package and as a newbie to ubuntu i don't quite know what i'm doing. I've read that it has lots of dependencies.....can someone please write a how to guide on how to go about installing it without messing anything up!

---

### Post by Maestro23 on 2007-04-01
> **Kunstar said:**
> I really want to install [BasKet]("http://basket.kde.org/index.php") (KDE application) in Ubuntu Edgy but it doesn't come as a package and as a newbie to ubuntu i don't quite know what i'm doing. I've read that it has lots of dependencies.....can someone please write a how to guide on how to go about installing it without messing anything up!

Version 1.0.1 is in the Repositories.  

Synaptic(GUI):  Open up synaptic, and search for "basket"  Mark for installation.  It will install any dependencies it needs.

Command Line:  

> sudo aptitude install basket

Will also install any dependencies it needs.

If you don't see it on your search, you need to add extra repositories: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

If you install from their website or anything from source, you will need to find the dependencies yourself and install them. (Potential headache for someone new to linux).

*Always check the repositories for a program first. Good luck.

---

### Post by team on 2007-04-04
Try this one:
[http://www.getdeb.net/download.php?release=506&fpos=0](http://www.getdeb.net/download.php?release=506&fpos=0)

---

### Post by der_joachim on 2007-04-05
> **team said:**
> Try this one:
[http://www.getdeb.net/download.php?release=506&fpos=0](http://www.getdeb.net/download.php?release=506&fpos=0)

Thank you. :)

---

### Post by Kunstar on 2007-04-05
Its not the 1.0 version that is available in the repositories. How do I get that one?? Help please!

---

### Post by Maestro23 on 2007-04-05
> **Kunstar said:**
> Its not the 1.0 version that is available in the repositories. How do I get that one?? Help please!

What version of Ubuntu are you running?  I'm running Feisty and its in my repositories.  Did you enable all your repositories?

You can download the latest version from their site and follow the Installation instructions (Will be an INSTALL/README doc in the extracted directory).  Believe it's a tarball at their site.  You will need to read up Section 4: Installing from source: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

[http://basket.kde.org/](http://basket.kde.org/)

---

