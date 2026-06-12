---
title: "evince not working"
date: 2022-12-26
forum: General Help
---

### Post by ksso on 2022-12-26
Hi,

Just have tried installing evince, reinstalling, deleting, etc
It appears to have been installed,
but the gui does not appear to work with it, so it is difficult because even if appears to be installed
can not use it

similare issue with chromium, but after deinstallation-installation, it appears to use it

thank you very much

---

### Post by slickymaster on 2022-12-26
*Thread moved to **General Help**.*

---

### Post by Impavidus on 2022-12-27
Have you installed the deb version or the snap version or some other version?```
snap list | grep evince
dpkg --list evince
```
What happens when you attempt to start evince from the command line?```
evince somefile
```Use the proper path+filename, so it can be found from the present working directory, or change directory first. Just take any file understood by evince. If you use the snap version, make sure this file is in your home directory.

---

