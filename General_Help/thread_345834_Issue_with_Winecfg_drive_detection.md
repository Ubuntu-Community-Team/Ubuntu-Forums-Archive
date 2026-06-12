---
title: "Issue with Winecfg drive detection"
date: 2007-01-24
forum: General Help
---

### Post by Patrick K on 2007-01-24
I just installed wine in Edgy using the Add/Remove app. I have an old Win 3.1 program that I want to run. It is installed on the E: drive. I was able to start it with wine but, not surprisingly, the paths to the data files didn't work. I do not have the installation program anymore and it is no longer available. Plus, I want to be able to work with the data in both Linux and Windows 98.

I fired up winecfg and on the drive page clicked on "autodetect". Wine assigned drive letters to the partitions but the letters were not correct for the drives. In the list of drives I cannot select any of the drives to remove them. Nothing at all happens when I try to select one of the drives. I have a list of the Linux drive names correlated with the proper drive letters but cannot select any to make the corrections. I uninstalled then reinstalled wine but the incorrect assigned letters and names remain. 

Any thoughts on fixing this?

Patrick

---

### Post by YokoZar on 2007-01-25
First off, try installing a later Wine: [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

As a rule, Wine works best when you install apps into its virtual windows drive rather than trying to run them off of an existing Windows installation.  This is so Wine doesn't get confused looking for configuration data (eg registry information) in it's own structure when it's actually on the windows drive somewhere.

---

### Post by Patrick K on 2007-01-25
Thanks for the reply. I resolved the Drive problem. I will install the newer package you suggested. 

It turns out the app I want to use is a W95 version not 3.1, I guess I must have upgraded it. I wonder if I export the registry keys can I import them into wine's registry file? There is just no way to install it in wine.

---

