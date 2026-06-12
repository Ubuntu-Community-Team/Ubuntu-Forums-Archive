---
title: "Should I remove older version b4 I install new one?"
date: 2014-10-05
forum: General Help
---

### Post by javierdl on 2014-10-05
Just downloaded a tar.gz file to install a program. Am I to uninstall the previous version first, or will the installer of the new version will do that automatically?
In case it makes a difference, the program is LibreOffice.

Thanks guys,

JDL

---

### Post by Vaphell on 2014-10-06
Is there any reason why you are going the manual installation route?

I'd go with LO PPA
[https://launchpad.net/~libreoffice/+archive/ubuntu/libreoffice-4-3](https://launchpad.net/~libreoffice/+archive/ubuntu/libreoffice-4-3)
and if for whatever reason it was not suitable, i'd look for .deb file on the LO website.

---

### Post by javierdl on 2014-10-07
Yes, because I didn't see the PPA option at the LibreOffice website ;)
Thank you so much for providing the PPA :)
**Should I uninstall the old one first?**

JDL

---

### Post by mastablasta on 2014-10-08
yes, remove it to prevent any possible conflicts. then use PPA.

---

### Post by javierdl on 2014-10-08
Thanks for the info guys! So I did remove LO, and used the PPA from the link. But it installed what seemed to be a launcher / host for the actual applications (Writer, Impress, Draw, etc), without those apps. Is this normal?

JDL

---

### Post by deadflowr on 2014-10-09
> **javierdl said:**
> Thanks for the info guys! So I did remove LO, and used the PPA from the link. But it installed what seemed to be a launcher / host for the actual applications (Writer, Impress, Draw, etc), without those apps. **Is this normal**?

JDL

Depends.
It is somewhat unclear as to everything that happened.

When you removed LO before the ppa install, were they from the original Ubuntu packages or from the tar file?

If from the tar file, then yes removal was right.

But if from the original Ubuntu packages, then there was no need to remove them, as the ppa would have simply updated the existing packages.
(It might have ask you that it needed to remove some packages and install brand new ones, but overall you only needed to run an update like any other update)

Ubuntu does not come with full libreoffice installed.
It comes with libreoffice-writer, -calc, impress, and -draw.
I would think, though that if you installed the main meta-package "libreoffice", that those would have been installed, additionally, as well.
See if,
You can launch writer from the libreoffice main page, does a launcher show up for writer?
If so, can you add to the launcher dock.(right click >> lock to launcher
(I will always assume this is default ubuntu, until stated otherwise)

My 5, or 6 cents

---

