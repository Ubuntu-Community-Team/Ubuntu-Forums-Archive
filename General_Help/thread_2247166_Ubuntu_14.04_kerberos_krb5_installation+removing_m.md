---
title: "Ubuntu 14.04 kerberos krb5 installation+removing messed up login"
date: 2014-10-06
forum: General Help
---

### Post by akimb0 on 2014-10-06
Dear community,

i needed to install temporary the krb5 packages for some testing on my station.
The installation was done by 

```
sudo apt-get install krb5-*
```

I accepted the installation of all additional dependencies and requiered packages which pops up.
After testing i dont needed the packages anymore and removed them from the system to keep it clean and simple. The remove process was done by

```
sudo apt-get purge krb5-admin-server krb5-auth-dialog krb5-clients krb5-config krb5-doc krb5-gss-samples krb5-kdc krb5-kdc-ldap krb5-locales krb5-multidev krb5-otp krb5-pkinit krb5-strength krb5-sync-plugin 
krb5-sync-tools krb5-telnetd krb5-user
```

Removing the additional installed packages was done by a quick

```
sudo apt-get autoremove
```

I rebooted the system and back on the login screen am not able to login because of the following error message:

```
unable to get default kerberos realm
```

Login dont work in gui and console mode. 
So it seems there is still some kerberos crap installed. 
As i only have one account and the standard guest account i cant log into the system, however i have a dualboot system with opensuse installed on a different partition so at least im able to access the files from suse if needed.
Any kind of a lightning or help would be much appreciated.

---

### Post by akimb0 on 2014-10-07
Booting in recovery mode and setup kerberos with a fake realm let me login again. Im afraid on how to uninstall krb5 packages now without messing up the system again?
Is there a save way to remove all kerberos related files and services from the system?

---

### Post by akimb0 on 2014-10-10
Resolved it:

- Booting into recovery mode and installing all related krb5 packages
- Setup kerberos during the installation process
- Reboot
- Login
- Remove all packages related to the kerberos installation **except** krb5-locales krb5-multidev libgssapi-krb5-2 libkrb5-26-heimdal libkrb5-3 libkrb5-dbg:amd64 libkrb5-dev libkrb5support0
- Reboot
- Done

---

