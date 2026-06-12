---
title: "Uninstall problem"
date: 2013-12-14
forum: General Help
---

### Post by Bryce_Hutchison on 2013-12-14
I'm just wondering how to un-install downloaded packages installed outside the repository.:)
Any help would be very much appresiated.:D

---

### Post by codemaniac on 2013-12-14
depends upon how you installed the package. If you have installed them from source tarball, the tar should contain a README or INSTALL file that sometimes mentions the steps for uninstall.

---

### Post by grahammechanical on 2013-12-14
Are you sure that the application is not listed in Software Centre with an option to remove? You can install Synaptic Package Manager (not installed by default from 12.10 onwards). Then you can search for the package. Select it and right click and select Mark for Complete Removal. Allow time for Synaptic to build its index.

Regards.

---

### Post by Bryce_Hutchison on 2013-12-14
:p Thank you all for your help.:KS

---

### Post by mikelavekkia on 2013-12-14
"var\log\apt\history.log" or "var\log\dpkg.log" and locate file name or date of install and tou can see all file install with package now copy interestesìd file and in terminal:
sudo dpkg -P file1 file2 file3... if you compile and install from source with make go in build directory and hit " sudo make uninstall" in terminall

---

