---
title: "ubuntu crashes with 3rd party lib"
date: 2013-03-22
forum: General Help
---

### Post by vijai2013 on 2013-03-22
Hello,
       Today I have a lots of crash report dialog box saying libz.so.1.2.7 crashes and the dialog box pops up every 5 minutes.This makes my os hang for a wile...Is there any way to remove this lib and re-install it?
I have ubuntu 12.04 LTS 64 bit.My system is up to date and also run apt-get update.But it doesnt fix the issue.Any kind of help is appreciated.Thanks.
Regards,
vijai

---

### Post by Impavidus on 2013-03-22
libz is contained in the package zlib1g. You can try reinstalling that package. You won't be able to uninstall it without uninstalling a lot of other packages, as pretty much everything that can use compression depends on zlib.

---

