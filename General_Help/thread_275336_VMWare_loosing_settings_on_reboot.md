---
title: "VMWare loosing settings on reboot?"
date: 2006-10-11
forum: General Help
---

### Post by rupy on 2006-10-11
Everytime I restart my pc vmware seems to loose all settings and I have to completely reconfigure it:

> 
ru@rubuntu:~$ vmware
vmware is installed, but it has not been (correctly) configured
for this system. To (re-)configure it, invoke the following command:
/usr/bin/vmware-config.pl.


Once I run the above script I can run vmware 100%... until I reboot.

---

### Post by rupy on 2006-10-14
Bump... any ideas?

---

### Post by fisting_mayfield on 2007-09-17
Hi, I found a workaround, 

copy vmware-player-distrib/installer/services.sh from the vmware tar file
rename services.sh to vmware and cp it to /etc/init.d/
Make sure it's executable (sudo chmod 755 /etc/init.d/vmware)

i was stuck with the same problem for ages, but this has just solved it for me

(credit goes to OsuCowboy for the fix)


-Fist

---

