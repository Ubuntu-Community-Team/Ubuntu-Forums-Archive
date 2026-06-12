---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2007-03-26
forum: General Help
---

### Post by matt91 on 2007-03-26
i cannot  install, remove, upgrade packages and i have tried forcing however it just doesnt work. i really need this fixing to do work on my server. i cannot reinstall the server as it is heavily configured.

here is an example error:
> root@server:~# apt-get remove postfix
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
postfix
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
postfix
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 2494kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 45200 files and directories currently installed.)
Removing postfix ...
/var/lib/dpkg/info/postfix.prerm: 41: /etc/init.d/postfix: not found
dpkg: error processing postfix (--remove):
subprocess pre-removal script returned error exit status 127
Errors were encountered while processing:
postfix
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@server:~#

please could somebody help, thank you.:) 
Matt

---

### Post by dannyboy79 on 2007-03-26
are there any lingering symlinks for postfix? also, try to use aptitude. did you try purge also?

---

### Post by matt91 on 2007-03-26
iv tried both of them but i get the same error message at the end

---

### Post by Ramses de Norre on 2007-03-26
Have you removed the postfix script in /etc/init.d/ manually?
Try to install postfix again first.
If that doesn't work, try running **sudo touch /etc/init.d/postfix** and then removing the package.

---

### Post by matt91 on 2007-03-27
i tried installing another package dovecot after postfix which failed with the same error message. when ever i tried to uninstall postfix again i got it wanting to remove dovecot at the same time. i fixed dovecot by deleting executable lines and then i managed to remove dovecot and then i could remove postfix.

thanks for your help.:)

---

