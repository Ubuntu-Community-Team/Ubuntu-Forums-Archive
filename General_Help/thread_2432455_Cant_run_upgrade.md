---
title: "Cant run upgrade"
date: 2019-12-02
forum: General Help
---

### Post by mwieting on 2019-12-02
When i try upgrading:
```
root@hassio:~# sudo apt-get upgrade -y
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
The following packages will be upgraded:
  cloud-init python3-distupgrade sosreport
3 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
97 not fully installed or removed.
Need to get 0 B/646 kB of archives.
After this operation, 2,048 B disk space will be freed.
Preconfiguring packages ...
(Reading database ... 178425 files and directories currently installed.)
Preparing to unpack .../python3-distupgrade_1%3a18.04.36_all.deb ...
/var/lib/dpkg/info/python3-distupgrade.prerm: 6: /var/lib/dpkg/info/python3-distupgrade.prerm: py3clean: not found
dpkg: warning: old python3-distupgrade package pre-removal script subprocess returned error exit status 127
dpkg: trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 6: /var/lib/dpkg/tmp.ci/prerm: py3clean: not found
dpkg: error processing archive /var/cache/apt/archives/python3-distupgrade_1%3a18.04.36_all.deb (--unpack):
 new python3-distupgrade package pre-removal script subprocess returned error exit status 127
/var/lib/dpkg/info/python3-distupgrade.postinst: 6: /var/lib/dpkg/info/python3-distupgrade.postinst: py3compile: not found
dpkg: error while cleaning up:
 installed python3-distupgrade package post-installation script subprocess returned error exit status 127
Preparing to unpack .../sosreport_3.6-1ubuntu0.18.04.4_amd64.deb ...
/var/lib/dpkg/info/sosreport.prerm: 6: /var/lib/dpkg/info/sosreport.prerm: py3clean: not found
dpkg: warning: old sosreport package pre-removal script subprocess returned error exit status 127
dpkg: trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 6: /var/lib/dpkg/tmp.ci/prerm: py3clean: not found
dpkg: error processing archive /var/cache/apt/archives/sosreport_3.6-1ubuntu0.18.04.4_amd64.deb (--unpack):
 new sosreport package pre-removal script subprocess returned error exit status 127
/var/lib/dpkg/info/sosreport.postinst: 6: /var/lib/dpkg/info/sosreport.postinst: py3compile: not found
dpkg: error while cleaning up:
 installed sosreport package post-installation script subprocess returned error exit status 127
Preparing to unpack .../cloud-init_19.2-36-g059d049c-0ubuntu2~18.04.1_all.deb ...
/var/lib/dpkg/info/cloud-init.prerm: 38: /var/lib/dpkg/info/cloud-init.prerm: py3clean: not found
dpkg: warning: old cloud-init package pre-removal script subprocess returned error exit status 127
dpkg: trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 38: /var/lib/dpkg/tmp.ci/prerm: py3clean: not found
dpkg: error processing archive /var/cache/apt/archives/cloud-init_19.2-36-g059d049c-0ubuntu2~18.04.1_all.deb (--unpack):
 new cloud-init package pre-removal script subprocess returned error exit status 127
/var/lib/dpkg/info/cloud-init.postinst: 320: /var/lib/dpkg/info/cloud-init.postinst: py3compile: not found
dpkg: error while cleaning up:
 installed cloud-init package post-installation script subprocess returned error exit status 127
Errors were encountered while processing:
 /var/cache/apt/archives/python3-distupgrade_1%3a18.04.36_all.deb
 /var/cache/apt/archives/sosreport_3.6-1ubuntu0.18.04.4_amd64.deb
 /var/cache/apt/archives/cloud-init_19.2-36-g059d049c-0ubuntu2~18.04.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@hassio:~#
```

---

### Post by wildmanne39 on 2019-12-02
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end, if you are editing a post to add code tags click the edit button then click the go advanced button, highlight the code then select the # symbol from the tool bar.

---

### Post by Impavidus on 2019-12-03
This is a direct result of your other thread ([https://ubuntuforums.org/showthread.php?t=2432391](https://ubuntuforums.org/showthread.php?t=2432391)). Your package management is messed up. You can't use apt to install upgrades until you fix it.

BTW, no need to use sudo to run something as root if you already have a root shell.

---

