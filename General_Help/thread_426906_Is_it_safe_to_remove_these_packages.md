---
title: "Is it safe to remove these packages?"
date: 2007-04-28
forum: General Help
---

### Post by DougieFresh4U on 2007-04-28
J**ust doing a check here on my feisty machine, it wanted to do the following:**
Calculating upgrade... Done
The following packages will be REMOVED:
  e17 ecore1-bin edje0-bin emodule0-alarm emodule0-cpu emodule0-deskshow
  emodule0-flame emodule0-forecasts emodule0-language emodule0-mail
  emodule0-mem emodule0-mixer emodule0-moon emodule0-net emodule0-photo
  emodule0-rain emodule0-screenshot emodule0-slideshow emodule0-snow
  emodule0-taskbar emodule0-tclock emodule0-uptime emodule0-weather
  emodule0-winselector emodule0-wlan emodules0-all enlightenment
The following NEW packages will be installed:
  libecore1-bin libefreet1
The following packages will be upgraded:
  enlightenment-data enlightenment-theme enlightenment-theme-cthulhain
  enlightenment-theme-darkness enlightenment-theme-kor
  enlightenment-theme-milky enlightenment-theme-simply-white libecore1
  libecore1-con libecore1-config libecore1-dbus libecore1-desktop
  libecore1-evas libecore1-fb libecore1-file libecore1-ipc libecore1-job
  libecore1-txt libecore1-x libedje0 libeet0 libembryo0 libevas1
  libevas1-engine-buffer libevas1-engine-software-generic
  libevas1-engine-software-x11 libevas1-loader-eet libevas1-loader-gif
  libevas1-loader-jpeg libevas1-loader-png libevas1-loader-svg
  libevas1-loader-tiff libevas1-loader-xpm libevas1-loaders-all
  libevas1-saver-eet libevas1-saver-jpeg libevas1-saver-png libexml1
38 upgraded, 2 newly installed, 27 to remove and 0 not upgraded.
Need to get 20.2MB of archives.
After unpacking 9216kB disk space will be freed.
Do you want to continue [Y/n]?

---

### Post by mojoman on 2007-04-29
If you're just doing the ordinary run of the mill upgrade I doubt that there would be any danger, at least of totally rendering your system unusable. However, I'd probably have a look at what these packages do just in case before proceeding, and maybe keep their name somewhere, just in case. Use ```
apt-cache show <PACKAGENAME>
``` to get info on the packages it wants to remove and see what they do.

/mojoman

---

### Post by DougieFresh4U on 2007-04-29
> **mojoman said:**
> If you're just doing the ordinary run of the mill upgrade I doubt that there would be any danger, at least of totally rendering your system unusable. However, I'd probably have a look at what these packages do just in case before proceeding, and maybe keep their name somewhere, just in case. Use ```
apt-cache show <PACKAGENAME>
``` to get info on the packages it wants to remove and see what they do.

/mojoman

Thanks, will check into that,  
**EDIT: ** I think I was missing some E17 repos as I only saw that 1/2 of them were in repos and I put the rest in and now all is good & nothing removed :)

---

