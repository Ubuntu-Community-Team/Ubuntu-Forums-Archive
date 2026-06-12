---
title: "uninstalling conexant drivers"
date: 2008-03-15
forum: General Help
---

### Post by shaan_aragorn on 2008-03-15
I am having a bit of a problem uninstalling my conexant HSF modem drivers in ubuntu 7.10
I downloaded the open source .deb file from [http://www.surak.eti.br/linux/ubuntu/deb/conexant/](http://www.surak.eti.br/linux/ubuntu/deb/conexant/)

this is the output i got when i tried uninstalling the driver from the package manager as well as from the terminal.

shantanu@shantanu-desktop:~$ sudo dpkg -r conexant
[sudo] password for shantanu:
(Reading database ... 90709 files and directories currently installed.)
Removing conexant ...
ERROR: Module hsfserial does not exist in /proc/modules
ERROR: Module hsfengine does not exist in /proc/modules
ERROR: Module hsfbasic2 does not exist in /proc/modules
ERROR: Module hsfosspec does not exist in /proc/modules
dpkg: error processing conexant (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 conexant

---

