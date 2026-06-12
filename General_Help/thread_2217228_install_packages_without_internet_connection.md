---
title: "install packages without internet connection"
date: 2014-04-16
forum: General Help
---

### Post by Marchello_Lippi on 2014-04-16
Hi all, 


my need is to install these packages on PC without internet connection: 


sudo apt-get install usb-modeswitch
sudo apt-get install usb-modeswitch-data


How do I download all necessary packages (with dependencies) using another computer before installing them on "disconnected" pc ?

Where should I place downloaded packages on "disconnected" PC to install them?

---

### Post by stalkingwolf on 2014-04-16
if you have them installed on one computer I think you can use apt on cd to create a cd/dvd of all the apt packages installed and then use it to install them.

---

### Post by ibjsb4 on 2014-04-16
I know that Keryx and Synaptic can be used for this.

[https://help.ubuntu.com/community/InstallingSoftware#Installing_packages_without_an_Internet_connection](https://help.ubuntu.com/community/InstallingSoftware#Installing_packages_without_an_Internet_connection)

---

### Post by buzzingrobot on 2014-04-16
```
sudo dpkg -i <package_name.deb>
``` will install the package once you get it on the right machine.

dpkg does not resolve dependencies, but it should complain and tell you what's mising. You can also check dependencies by searching for the package's page at packages.ubuntu.com.

If both packages seem to be dependencies of each other, install both simultaneously with "dpkg -i *.deb". (Assuming they are the only deb's in that folder.)

Gdebi, a handy little GUI installer, will chase down dependencies if they're in repos in your sources list. (Same as Software Center, Synaptic, apt-get... .) If it's installed, Gdebi should appear as an option when you right click on a deb in Files, and choose "Open With...".  (It may then be necesary to look under "Other Application...".)  Gdebi can also be set as the default installer by right clicking on a deb in Files, then Properties->Open With and choosing it, then setting the default.

---

### Post by ian-weisser on 2014-04-17
Another way to chase down the complete dependency list is apt-get
```
sudo apt-get install --simulate usb-modeswitch
```
Then you download those packages from [http://packages.ubuntu.com](http://packages.ubuntu.com)
Copy the packages into /var/cache/apt/archives/
Then apt-get install should work normally:
```
sudo apt-get install usb-modeswitch
```

---

