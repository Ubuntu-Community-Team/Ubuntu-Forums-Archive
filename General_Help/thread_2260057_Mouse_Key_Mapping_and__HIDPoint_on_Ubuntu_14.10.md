---
title: "Mouse Key Mapping and  HIDPoint on Ubuntu 14.10"
date: 2015-01-08
forum: General Help
---

### Post by johnathanamber on 2015-01-08
Hello everyone,

I am attempting to setup my extra mouse buttons to perform various actions. Checking things out, I find HIDPoint. They have the G7 Laser Mouse listed that has the same buttons that my M705 seemingly does. Has anyone been able to map their mouse buttons using HIDPoint or another method?

Here is what I get when attempting to install HIDPoint:
```

name@richas:/media/name/Files/Programs$ sudo bash ./hidpoint1-0.bin 
Verifying archive integrity... All good.
Uncompressing HIDPoint2.0 Build 130326 Setup..........................................................................................................................................................................................................................................
[3;J


Welcome to the HIDPoint Installation.
Please wait while the installer extracts the files to a temporary folder.

HIDPoint Installer has successfully extracted the installation
files to : /tmp/selfgz1797315602
The installer needs to have admin priviliges to copy files
to /usr/bin and load the driver.
Please run the hidpoint1-0.bin file using the sudo command.
  (ignore if you ran hidpoint1-0.bin file using the sudo command)


sudo ./hidpoint1-0.bin


Running the hidpoint-1.0 using the sudo command will not require you to enter
the admin password.
If your have any questions about the install please visit
our website http://www.hidpoint.com


Do you wish to continue with the Installation? [Y/n] and hit enter y
*****************************************************************************
*                                                                           *
* To run HIDPoint on a 64 bit OS, you first need to install 32 bit libraries*
*                                                                           *
*****************************************************************************
libpng does not exist
libtiff does not exist
Gathering System information and generating a log
Launching HIDPoint Installer
./hidpointsetup: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory

```

Any ideas?

Thanks guys/gals,
Johnathan

---

