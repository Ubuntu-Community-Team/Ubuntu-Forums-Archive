---
title: "/usb/bin/MergeXML crashes"
date: 2016-04-29
forum: General Help
---

### Post by mch-heidinger on 2016-04-29
Hi,

MergeXML is used in a package (usbdm for Kinetis Design Studio) and crashes. (CoreDump). How do I find out, which package it belongs to, and how to report the problem?
/usr/bin/MergeXML --help did not give any information.

Is there a chance to downgrade the package?

Thanks for your help,
Michael

---

### Post by oldos2er on 2016-04-29
What version of Ubuntu are you using? I can't find any package in the default repositories named "usbdm"; where did you get it from?

---

### Post by mch-heidinger on 2016-05-01
I'm using the latest Ubuntu (16.04).
[https://sourceforge.net/projects/usbdm/](https://sourceforge.net/projects/usbdm/)
but to install, you first have to install kinetis design studio, which is available by nxp.
[http://www.nxp.com/products/software-and-tools/run-time-software/kinetis-software-and-tools/ides-for-kinetis-mcus/kinetis-design-studio-integrated-development-environment-ide:KDS_IDE](http://www.nxp.com/products/software-and-tools/run-time-software/kinetis-software-and-tools/ides-for-kinetis-mcus/kinetis-design-studio-integrated-development-environment-ide:KDS_IDE)

How Do I blame a package for beeing corrupt?

---

### Post by oldos2er on 2016-05-01
If Nxp created the deb, you will need to contact them. It looks like they have a community forum here: [http://community.freescale.com/welcome](http://community.freescale.com/welcome)

---

### Post by mch-heidinger on 2016-05-02
Yes, but for me, it looks like the problem is NOT this package, it's the /usr/bin/MergeXML
as this tool fails with a core dump, i think that is not normal.

---

