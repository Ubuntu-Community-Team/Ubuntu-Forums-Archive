---
title: "installing Feisty as a command line system need help please.. [Resolved]"
date: 2007-05-05
forum: General Help
---

### Post by billdotson on 2007-05-05
I have the Feisty alternate installer CD and have (or did have) a command line system installed.  I want to install as little as I can because this is going to be a part-time ftp server.  I want to just install X, fluxbox, proftpd, gproftpd and firefox.  Although when I do sudo aptitude install xserver-xorg installs a bunch of packages but a lot of dependencies fail.

How do I go about setting up X and fluxbox on just a command line system since sudo aptitude install xserver-xorg doesn't work (or at least get all the dependencies right)

---

### Post by aysiu on 2007-05-05
Read this:
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

---

### Post by billdotson on 2007-05-05
thanks aysui I will try that!  Hopefully this will work.. my other machine is OLD.. AMD K-6 333MHz processor, 4GB HDD and 64MB PC100 RAM.. even the alternate installer has to go into low memory mode.

---

### Post by yabbadabbadont on 2007-05-05
> **billdotson said:**
> I have the Feisty alternate installer CD and have (or did have) a command line system installed.  I want to install as little as I can because this is going to be a part-time ftp server.  I want to just install X, fluxbox, proftpd, gproftpd and firefox.  Although when I do sudo aptitude install xserver-xorg installs a bunch of packages but a lot of dependencies fail.

How do I go about setting up X and fluxbox on just a command line system since sudo aptitude install xserver-xorg doesn't work (or at least get all the dependencies right)

By default, aptitude considers "recommended" packages as dependencies and will install them too.  Then it installs the recommended packages for the recommended packages.  Then it installs......  you can see how it will snowball out of control.  If you use plain old apt-get, you won't run into that problem.  (that's how I installed my Feisty system the last time)  If you insist on using aptitude, run aptitude, hit ctrl-t for the menu, then go to the Options->Dependency Handling menu and deselect "Install Recommended Packages Automatically".  Then aptitude will treat dependencies the same way that apt-get does.

---

### Post by billdotson on 2007-05-05
thanks aysiu.. that got it workin for me.  No dependency errors.  FTP server fixed up.  Thanks!

---

