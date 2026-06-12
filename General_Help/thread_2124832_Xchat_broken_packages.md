---
title: "Xchat broken packages"
date: 2013-03-12
forum: General Help
---

### Post by nicomigs on 2013-03-12
I am new to ubuntu(or linux) and I don't have any idea about programming, but I am trying to learn about ubuntu, linux and programming and I thought that it will be really helpful if I have Xchat by my side. But after updating a while ago, my Xchat was uninstalled(i don't know why and how) and when I was trying to reinstall it, software manager said that I have a broken package. I also tried installing it from terminal but it said 





```
Some packages could not be installed. This may mean that you haverequested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 xchat : Depends: libperl5.12 (>= 5.12.4) but it is not installable
E: Unable to correct problems, you have held broken packages.



```

---

### Post by ibjsb4 on 2013-03-12
Try

```
sudo dpkg --configure -a

sudo apt-get -f install
```

---

### Post by nicomigs on 2013-03-13
tried it.here's what is said.

```
Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  xchat-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
explorer@linuxnoob:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  xchat-common
0 upgraded, 0 newly installed, 1 to remove and 4 not upgraded.
After this operation, 3,408 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 173653 files and directories currently installed.)
Removing xchat-common ...
Processing triggers for gconf2 ...



```


after that, i tried installing xchat again but here's what it said again

```
explorer@linuxnoob:~$ sudo apt-get install xchatReading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 xchat : Depends: libperl5.12 (>= 5.12.4) but it is not installable
E: Unable to correct problems, you have held broken packages.



```

---

### Post by ibjsb4 on 2013-03-13
What version are you running?  In terminal:

```
cat /etc/issue
```

---

