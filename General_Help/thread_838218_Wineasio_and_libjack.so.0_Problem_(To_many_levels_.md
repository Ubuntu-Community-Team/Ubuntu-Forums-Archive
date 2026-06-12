---
title: "Wineasio and libjack.so.0 Problem (To many levels of symbloic links)"
date: 2008-06-23
forum: General Help
---

### Post by kempy1000 on 2008-06-23
Hello

Im trying to install wineasio driver so that my virtualdj (running in wine) will work with my external usb audio interface.

However i have tried installing via a script and it worked first time but i did not compile wineasio.so.dll with enough inputs and outputs. so i recompiled it and to install it again caused an error with libjack.so.0 so i removed that file (probably the wrong thing to do!!). It then complianed of no libjack.so.0 so i reinstalled jack and now when installing i get the error below.

Output from ./wineasio_script

```


This script will download and install wineasio
This might take awhile, please be patient
First it will install the latest wine, jack and some other usefull stuff
Reading package lists... Done
Building dependency tree       
Reading state information... Done
wine is already the newest version.
wine-dev is already the newest version.
libjack0.100.0-dev is already the newest version.
qjackctl is already the newest version.
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.
Configuring wine
Note: wineprefixcreate is deprecated and shouldn't be needed anymore.
      WINEPREFIX creation and updates now happen automatically when needed.

Could not load Mozilla. HTML rendering will be disabled.
wine: configuration in '/home/ben/.wine' has been updated.
Then it will download the wineasio driver and place it in your wine-folder
Warning: could not find DOS drive for current working directory '', starting in the Windows directory.
err:module:load_builtin_dll failed to load .so lib for builtin L"wineasio.dll": libjack.so.0: cannot open shared object file: Too many levels of symbolic links
Failed to load DLL wineasio.dll
sudo: cannot get working directory
ln: accessing `/usr/lib/libjack.so.0': Too many levels of symbolic links
All done :-) ... Now you can use the win-version of EnergyXT2 (or Reaper) with wineasio
Press [ENTER] to close the shell


```

Thanks Chris

---

