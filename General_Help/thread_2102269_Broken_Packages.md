---
title: "Broken Packages?"
date: 2013-01-06
forum: General Help
---

### Post by JD32 on 2013-01-06
Anyone know what this means/how to correct it?. I cant install anything


```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package transmission is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 transmission-daemon : Depends: transmission-common (= 2.51-0ubuntu1) but 2.51-0ubuntu1.1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

---

### Post by JD32 on 2013-01-06
results of running "sudo apt-get -f install


```
d@server:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  transmission-daemon
The following packages will be upgraded:
  transmission-daemon
1 upgraded, 0 newly installed, 0 to remove and 70 not upgraded.
1 not fully installed or removed.
Need to get 0 B/232 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of transmission-daemon:
 transmission-daemon depends on transmission-common (= 2.51-0ubuntu1); however:
  Version of transmission-common on system is 2.51-0ubuntu1.1.
dpkg: error processing transmission-daemon (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 transmission-daemon
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

My transmission daemon is causing the problem but unsure how to correct it

---

### Post by Frogs Hair on 2013-01-06
Try the following . ```
sudo apt-get update
``` ```
sudo dpkg --configure -a
```

---

### Post by JD32 on 2013-01-06
after running an update i still get this...


```
jd@server:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of transmission-daemon:
 transmission-daemon depends on transmission-common (= 2.51-0ubuntu1); however:
  Version of transmission-common on system is 2.51-0ubuntu1.1.
dpkg: error processing transmission-daemon (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 transmission-daemon
jd@server:~$ 
```


is there anyway i can force a uninstall and re install? the daemon still works fine i just cant install anything new. Will deleting the files be the same as uninstalling?

---

