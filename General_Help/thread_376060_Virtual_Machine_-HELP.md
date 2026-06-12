---
title: "Virtual Machine -HELP"
date: 2007-03-04
forum: General Help
---

### Post by helliewm on 2007-03-04
I have tried to install Virtual Machine but it got stuck during the installation. I now cannot use Add/Remove programs, Synaptic or Updates. I could not click OK on the license. I get an error message saying Virtual machine needs to be reinstalled but I cannot find archive.

Help, how can I correct this??

Helen

---

### Post by zvacet on 2007-03-04
Does it have uninstall file?Look in usr/bin.If it´s there than 
```
sudo -i
```
```
cd /usr/bin
```
```
root@localhost#./name_of_uninstall_file
```
You can chek other directories(home,home hidden files,etc,etc/init.d,tmp...If it is left something delete it.Tryto install again.
Good luck!

---

### Post by ramjet_1953 on 2007-03-05
Broken packages can really be a pain!

You could try this:

code:
[COLOR="Red"]dpkg-reconfigure <package name, ex &#8220;xserver-xorg&#8221; or &#8220;gdm&#8221;>
[/COLOR]
As an absolute last resort, try this:

backup your var/log/dpkg/status file  

code:
[COLOR="Red"]sudo kate /var/log/dpkg/status[/COLOR]

search for <app name>

manually delete the entry for Virtual Machine

Save the file

code:
[COLOR="Red"]sudo apt-get update[/COLOR]

Regards,
Roger :cool:

---

