---
title: "dpkg error after installing freepascal  2.04 deb files"
date: 2006-11-30
forum: General Help
---

### Post by reynoldlariza on 2006-11-30
before.... everything is ok, i can install updates smoothly, however after attempting to install FreePascal 2.04, and one deb file just got failed to install.

This failure made me think that it's because of fpc, so I ignored it and left it as is.

Now since I have a notification update on the system tray, I activate it and let it install updates, but it didn't.

i tried 
sudo apt-get 
& 
aptitude dist-upgrade
even 

sudo apt-get -f install
sudo apt-get clean
sudo apt-get update

updating still fails...

here's the console...

```

reynold@rel:~$ sudo apt-get upgrade
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  gnupg lvm2 tar wine
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/11.1MB of archives.
After unpacking 324kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  wine
Install these packages without verification [y/N]? N
E: Some packages could not be authenticated
reynold@rel:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  gnupg lvm2 tar wine
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/11.1MB of archives.
After unpacking 324kB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.
reynold@rel:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  gnupg lvm2 tar wine
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/11.1MB of archives.
After unpacking 324kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
WARNING: The following packages cannot be authenticated!
  wine
Install these packages without verification [y/N]? y
dpkg: parse error, in file `/var/lib/dpkg/available' near line 24891 package `webmin-software':
 missing version
E: Sub-process /usr/bin/dpkg returned an error code (2)
reynold@rel:~$ 


```

---

### Post by reynoldlariza on 2006-11-30
after trying some familliar commands aptitude, dselect, and some switches... I removed the /var/dpkg/available

now i get this
```

dpkg: failed to open package info file `/var/lib/dpkg/available' for reading: No such file or directory
E: Sub-process /usr/bin/dpkg returned an error code (2)


```

anybody help?

---

