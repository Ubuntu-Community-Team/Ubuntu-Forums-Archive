---
title: "Firefox won't start in Ubuntu 12.04"
date: 2013-11-07
forum: General Help
---

### Post by rtrampert on 2013-11-07
Hello, I just upgraded from 10.04 to 12.04 and now Firefox won't start. I'm using the Gnome3 desktop and I see that Firefox is starting but never starts. I've tries unistalling and reinstalling the package and restoring a backup of .mozilla in my home folder to no avail. Please help. BTW, I tried to load Firefox from the terminal and got this message:
 XPCOMGlueLoad error for file /opt/firefox/libxul.so:libXrender.so.1: cannot open shared object file: No such file or directory
Couldn't load XPCOM.

I'm not sure where to obtain this file.

Thanks in advance.

---

### Post by sammiev on 2013-11-07
I ran into this once and a simple reboot fixed the issue. Just 1 easy thing to try and if that fails try to create a new account. Have disabled all your add-ons and try it?

---

### Post by Impavidus on 2013-11-07
I've never seen a /opt/firefox directory. Did you by any chance manually install the latest firefox there when using 10.04, as you didn't get automatic updates any more? And still have a launcher pointing there somehow? By default firefox should be installed somewhere in /usr and have nothing to do with /opt.

---

### Post by rtrampert on 2013-11-07
I did try to install Firefox 25 manually in 10.04. How do I correct this?

---

### Post by Impavidus on 2013-11-07
Difficult to say without knowing how you tried to manually install firefox. I think you can best delete all files refering to the manually installed firefox. Read the files to see whether they contain references to other files related to firefox. As the installation of firefox during the upgrade should have overwritten any firefox in /usr/bin and in the PATH /usr/local/bin takes precedence over /usr/bin, I think you installed firefox (or at least, a launch script) in /usr/local/bin or possibly in ~/bin. When you have cleaned up the manually installed firefox, you may want to reinstall the automatically installed one, just to be sure.

If you installed firefox in /usr/local and /opt, you were probably smart enough not to put anything in /usr/bin or /usr/lib.

---

### Post by rtrampert on 2013-11-24
I solve my problem with Firefox rather dramaically by reinstalling 12.04 directly frim the install CD after backing up my files and then reinstalling all the software I has installed. I know there was probably an easier way to do this, but I had to get my system back up asap and couldn't wait for a response. Thanks anyways, guys.

---

