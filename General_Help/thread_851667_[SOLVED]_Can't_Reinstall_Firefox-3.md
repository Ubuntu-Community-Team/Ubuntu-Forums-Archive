---
title: "[SOLVED] Can't Reinstall Firefox-3"
date: 2008-07-06
forum: General Help
---

### Post by Greasyfingers on 2008-07-06
After some trouble configuring Firefox-3 in Hardy, I decided to reinstall it. I uninstalled all the Firefox packages, but now I can't reinstall Firefox-3. Firefox-2 seemed to install with no problem.

I uninstalled using Synaptic, and have tried reinstalling using both Synaptic and apt-get.

This is the output from apt-get:

```
~$ sudo apt-get install firefox-3.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  firefox-3.0: Depends: xulrunner-1.9 (< 1.9~b6~) but 1.9+nobinonly-0ubuntu0.8.04.1 is to be installed
E: Broken packages

```

This seems to imply that the available options for the xulrunner package is incompatible with FF3.

Help! How can I get FF3 back?

---

### Post by tamoneya on 2008-07-06
first of all make sure you run the update.  Then check for broken packages.  Then try installing xulrunner manually.  Then try firefox again:```
sudo apt-get update
sudo apt-get check 
sudo apt-get install xulrunner
sudo apt-get install firefox-3.0
```  Post back any errors you get.

---

### Post by Greasyfingers on 2008-07-06
Thanks for the speedy reply, but I get the same result.

This is the complete output from your suggestion:
```
*@ubuntu:~$ sudo apt-get update 
Hit http://archive.canonical.com hardy Release.gpg
Ign http://archive.canonical.com hardy/partner Translation-en_GB    
Hit http://security.ubuntu.com hardy-security Release.gpg           
Ign http://security.ubuntu.com hardy-security/main Translation-en_GB
Hit http://gb.archive.ubuntu.com hardy Release.gpg                   
Hit http://gb.archive.ubuntu.com hardy/main Translation-en_GB        
Hit http://archive.canonical.com hardy Release                       
Hit http://gb.archive.ubuntu.com hardy/restricted Translation-en_GB  
Hit http://gb.archive.ubuntu.com hardy/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com hardy/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com hardy Release 
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_GB
Ign http://security.ubuntu.com hardy-security/universe Translation-en_GB
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_GB
Hit http://security.ubuntu.com hardy-security Release
Hit http://archive.canonical.com hardy/partner Packages
Hit http://gb.archive.ubuntu.com hardy/main Packages
Hit http://gb.archive.ubuntu.com hardy/restricted Packages
Hit http://gb.archive.ubuntu.com hardy/main Sources
Hit http://gb.archive.ubuntu.com hardy/restricted Sources
Hit http://gb.archive.ubuntu.com hardy/universe Packages
Hit http://gb.archive.ubuntu.com hardy/universe Sources
Hit http://gb.archive.ubuntu.com hardy/multiverse Packages
Hit http://gb.archive.ubuntu.com hardy/multiverse Sources
Hit http://security.ubuntu.com hardy-security/main Packages
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Reading package lists... Done
*@ubuntu:~$ sudo apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done
*@ubuntu:~$ sudo apt-get install xulrunner
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xulrunner is already the newest version.
The following packages were automatically installed and are no longer required:
  libxfcegui4-4 mesa-utils libxfce4mcs-client3 libcompizconfig0 xfce4-panel
  libx11-xcb1 libxfce4util4 libexo-0.3-0 lesstif2 apturl liblua5.1-0 libanthy0
  xulrunner-1.9-gnome-support libxfce4mcs-manager3 libgtkglext1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
*@ubuntu:~$ sudo apt-get install firefox-3.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  firefox-3.0: Depends: xulrunner-1.9 (< 1.9~b6~) but 1.9+nobinonly-0ubuntu0.8.04.1 is to be installed
E: Broken packages


``` 

Any further suggestion gratefully accepted.

---

### Post by tamoneya on 2008-07-06
ahh i see.  Try this:```
sudo apt-get autoremove
sudo apt-get install xulrunner-1.9
sudo apt-get install firefox-3.0
```

---

### Post by aysiu on 2008-07-07
I'd do a slight modification of that: ```
sudo apt-get remove xulrunner xulrunner-1.9 firefox-2 firefox-3.0
sudo apt-get autoremove
sudo apt-get install firefox-3.0
```

---

### Post by Greasyfingers on 2008-07-07
Thanks, folks. That's fixed it.

---

