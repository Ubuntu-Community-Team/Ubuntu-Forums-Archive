---
title: "hp officejet j4580 wont print"
date: 2012-11-11
forum: General Help
---

### Post by Necromon on 2012-11-11
Hello,

os: lubuntu 12.04 
printer: hp officejet j4580 all in one printer
installed hplip latest 
using 4500 series ppd

Issue: everything installs and seems fine but cannot print test page or any other page. 

Only clues Ive found so far:

when i ran the hp-check -t , i see this warning in the output:
---------------------------------
| INSTALLED CUPS PRINTER QUEUES |
---------------------------------

 
WARNING
-------
Type: Unknown
Device URI: gnome-keyring:: couldn't connect to: /run/user/david/keyring-reOnDx/pkcs11: No such file or directory

------------------------------
| DISCOVERED SCANNER DEVICES |
------------------------------

WARNING: gnome-keyring:: couldn't connect to: /run/user/david/keyring-reOnDx/pkcs11: No such file or directory


Aside from that, Im pulling my hair out. I tried removing printer and adding again. powering down pc and printer and turning back on. my printer is listed as supported on hplipopensource and ubuntu 12.04 listed supported also. Im lost at this point and I hate printers before I have issues with them. Any help is greatly appreciated, thanks!

---

