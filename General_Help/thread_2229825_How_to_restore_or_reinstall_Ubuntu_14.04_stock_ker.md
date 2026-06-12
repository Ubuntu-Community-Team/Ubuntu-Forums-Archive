---
title: "How to restore or reinstall Ubuntu 14.04 stock kernels"
date: 2014-06-15
forum: General Help
---

### Post by mvburgos on 2014-06-15
Hello, I uninstalled all stock kernels to save space but I had installed mainline 3.15 kernel before that. Since then I'm getting 30+ boot delay and I want to restore if possible the /boot section like if i had just installed Ubuntu, if not I would like to know all the kernel packages that comes with ubuntu 14.04 and how can i install them alall via command line.

The idea is to troubleshoot which package is the one that causes the long boot delay after uninstalled so I keep it.

This is happening in my Asus Chromebox with Ubuntu 14.04 x64. Thanks!

I'll post the boot logs to see if someone figure it out the long boot delay.

[COLOR=#333333][FONT=UbuntuRegular][boot.log]("https://db.tt/igcNhItG")[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular][dmesg]("https://db.tt/Re1VhqTZ")[/FONT][/COLOR]

---

### Post by philinux on 2014-06-15
You can install linux-generic which will pull in the latest kernel and dependencies.

There is also the package bootchart to debug the startup delay.

---

### Post by mvburgos on 2014-06-15
Thanks. Installed Linux generic but still same thing. I rather restore /boot partition to start fresh and troubleshoot by myself. I don't want to be in the waiting game again until a dev check this, I already have several days with this boot delay issue.

---

### Post by philinux on 2014-06-15
Devs don't normally visit the forums.

I'd use bootchart.

---

