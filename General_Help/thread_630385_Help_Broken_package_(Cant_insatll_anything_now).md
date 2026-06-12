---
title: "Help Broken package (Cant insatll anything now)"
date: 2007-12-03
forum: General Help
---

### Post by BluntMAn420 on 2007-12-03
OK so I tried to uninstall tremulous-server and it had an error 

(E: tremulous-server: subprocess pre-removal script returned error exit status 5)
**I tried the fix broken packages in packet manager ** did not work
when i try to update
same thing
(E: tremulous-server: subprocess pre-removal script returned error exit status 5)

**I put in  sudo dpkg -r tremulous-server  in to the terminal**

richard@richard-desktop:~$ sudo dpkg -r tremulous-server
[sudo] password for richard:
(Reading database ... 111780 files and directories currently installed.)
Removing tremulous-server ...
invoke-rc.d: initscript tremulous-server, action "stop" failed.
dpkg: error processing tremulous-server (--remove):
 subprocess pre-removal script returned error exit status 5
invoke-rc.d: initscript tremulous-server, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 5
Errors were encountered while processing:
 tremulous-server
[B]

 I tried   sudo dpkg --remove --force-remove-reinstreq tremulous-server
[/B]
richard@richard-desktop:~$ sudo dpkg --remove --force-remove-reinstreq tremulous-server
(Reading database ... 111780 files and directories currently installed.)
Removing tremulous-server ...
invoke-rc.d: initscript tremulous-server, action "stop" failed.
dpkg: error processing tremulous-server (--remove):
 subprocess pre-removal script returned error exit status 5
invoke-rc.d: initscript tremulous-server, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 5
Errors were encountered while processing:
 tremulous-server

 Don't know what els to do please help

---

### Post by zvacet on 2007-12-03
```
sudo apt-get remove --purge tremulous-server
```

or

```
sudo apt-get -f install
```

---

### Post by BluntMAn420 on 2007-12-03
Thx for the help zvacet but they both did not work.

```
richard@richard-desktop:~$** sudo apt-get remove --purge tremulous-server**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  tremulous-server*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 848kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 129033 files and directories currently installed.)
Removing tremulous-server ...
invoke-rc.d: initscript tremulous-server, action "stop" failed.
dpkg: error processing tremulous-server (--purge):
 subprocess pre-removal script returned error exit status 5
invoke-rc.d: initscript tremulous-server, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 5
Errors were encountered while processing:
 tremulous-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

```
richard@richard-desktop:~$ **sudo apt-get -f install**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up tremulous-server (1.1.0-4) ...
invoke-rc.d: initscript tremulous-server, action "start" failed.
dpkg: error processing tremulous-server (--configure):
 subprocess post-installation script returned error exit status 5
Errors were encountered while processing:
 tremulous-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

anymore suggestions?:confused:

---

### Post by zvacet on 2007-12-04
```
sudo dpkg --remove --force-remove-reinstreq tremulous-server
```

---

### Post by BluntMAn420 on 2007-12-04
:( thx for trying but it did not work
```

richard@richard-desktop:~$ sudo dpkg --remove --force-remove-reinstreq tremulous-server
(Reading database ... 129497 files and directories currently installed.)
Removing tremulous-server ...
invoke-rc.d: initscript tremulous-server, action "stop" failed.
dpkg: error processing tremulous-server (--remove):
 subprocess pre-removal script returned error exit status 5
invoke-rc.d: initscript tremulous-server, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 5
Errors were encountered while processing:
 tremulous-server
richard@richard-desktop:~$ 


```

Well I'm sad but maybe it can still be fixed
Please Help if you can>

---

