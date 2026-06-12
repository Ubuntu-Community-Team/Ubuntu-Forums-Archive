---
title: "creating an updated install dis.c with my current config"
date: 2007-12-01
forum: General Help
---

### Post by pikaia on 2007-12-01
I checked out a few threads on this that included APTonCD and a tar backup, but I still had questions whether these programs and HOWTO's provide a full install point for my system.  I've been trying Ubuntu out for about a month now and have it installed on an old 10GB slave hard drive on my system.  But since I've slimmed down the boot time (used to be upwards of 3-5 minutes) I've been using it more than Windows.  I've customized the desktop and installed a ton of packages and don't want to go back and do it all over when I pick up a new SATA drive to install on... Is SystemImager, APTonCD or the tar backup the way to go?  If so, which one?

I guess what I had in mind was a CD or DVD that I boot from and install and when its done I have my current config.  

I'm currently running Feisty.  

Also I've tried installing the xDVDshrink through Automatix and it keeps erroring out.  I always get errors when installing packages caused by OpenOffice somehow... but they seem to be inconsequential to the install... despite the error messages, but not for dvdshrink... any ideas?  Also can't seem to update to Openoffice 2.3.

Thanks.

---

### Post by brymux on 2007-12-01
AptonCD requires you to install the packages manualy.It can be added as a source for synaptic after you burn the image so you don't have to re-download all of your packages.But it only backs up your apt-packages 
any others you should back up yourself.
I think your trying to create your own custom distro....
You should check out the Gparted-Clonezilla live cd.when you get your new hard drive just clone your old one onto the new one then reformat the old one to Fat32 and use it as a go between your 2 OS's.
Hope this helps.

---

