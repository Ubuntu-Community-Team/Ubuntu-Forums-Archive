---
title: "Back to Screem 0.12.1"
date: 2006-08-11
forum: General Help
---

### Post by MaaSTaaR on 2006-08-11
Hello ...

i have Screem 0.16.1 and it's work with me ugly , i was work with Screem 0.12 and it was work very nice , so how i can back to 0.12.1 and remove 0.16.1 forever ? :-k

---

### Post by mlind on 2006-08-11
[http://archive.ubuntu.com/ubuntu/pool/main/s/screem/](http://archive.ubuntu.com/ubuntu/pool/main/s/screem/)

Seems to contain older screem (for Breezy?). I think it *should* work if just install the .deb straight from that repository (with gdebi. just click the .deb link).
If it doesn't work, it needs to be rebuilt from source package.

I'll help you if package needs rebuilding.

---

### Post by MaaSTaaR on 2006-08-14
Hello ...

i downloaded the Screem 0.12.1 and i do "sudo dpkg -i screem_0.12.1-1ubuntu3_i386.deb" , but it's show for me these errors :

dpkg - warning: downgrading screem from 0.16.1-2ubuntu1 to 0.12.1-1ubuntu3.
(Reading database ... 113869 files and directories currently installed.)
Preparing to replace screem 0.16.1-2ubuntu1 (using screem_0.12.1-1ubuntu3_i386.deb) ...
Unpacking replacement screem ...
dpkg: dependency problems prevent configuration of screem:
 screem depends on libdbus-1-1 (>= 0.33); however:
  Package libdbus-1-1 is not installed.
 screem depends on libdbus-glib-1-1 (>= 0.33); however:
  Package libdbus-glib-1-1 is not installed.
dpkg: error processing screem (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 screem

---

### Post by mlind on 2006-08-14
> **MaaSTaaR said:**
> Hello ...

i downloaded the Screem 0.12.1 and i do "sudo dpkg -i screem_0.12.1-1ubuntu3_i386.deb" , but it's show for me these errors :

dpkg - warning: downgrading screem from 0.16.1-2ubuntu1 to 0.12.1-1ubuntu3.
(Reading database ... 113869 files and directories currently installed.)
Preparing to replace screem 0.16.1-2ubuntu1 (using screem_0.12.1-1ubuntu3_i386.deb) ...
Unpacking replacement screem ...
dpkg: dependency problems prevent configuration of screem:
 screem depends on libdbus-1-1 (>= 0.33); however:
  Package libdbus-1-1 is not installed.
 screem depends on libdbus-glib-1-1 (>= 0.33); however:
  Package libdbus-glib-1-1 is not installed.
dpkg: error processing screem (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 screem


Looks like the package needs a rebuild to work on dapper..
[Try if this works]("http://www.freefilehoster.com/uploads/1155594464screem_0.12.1-dapper.tar.gz")

---

