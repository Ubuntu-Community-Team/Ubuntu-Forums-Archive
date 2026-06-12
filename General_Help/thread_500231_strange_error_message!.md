---
title: "strange error message!"
date: 2007-07-13
forum: General Help
---

### Post by ssn1978 on 2007-07-13
whenever I try to install any program I get this error message 
E: clvm: subprocess post-installation script returned error exit status 3
Also, while shutdown it says many error messages related to CLVM.. can anybody please help me to understand what these messages are and how to fix them?
thank you!

---

### Post by Rui Pais on 2007-07-13
Hi.
That means that you have clvm package (half) installed but installer couldn't finish installation due to some error during final configuration. 
Evey time you run something related with package management it tries finish that configuration. 

Do you use clvm? if not just remove the package. 
If you use it, you need to reinstall it, probably purge it first to avoid the problem:
```
sudo aptitude purge clvm
sudo aptitude install clvm
```

good luck

---

### Post by ssn1978 on 2007-07-13
thanks for prompt reply. I dont know if this package is required...
so tried to remove it and I got the following error message.
root@SSNlinux:/home/ssn# sudo aptitude purge clvm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages will be automatically REMOVED:
  clvm{p} 
The following packages will be REMOVED:
  clvm{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 492kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 146334 files and directories currently installed.)
Removing clvm ...
Stopping Cluster LVM Daemon invoke-rc.d: initscript clvm, action "stop" failed.
dpkg: error processing clvm (--purge):
 subprocess pre-removal script returned error exit status 1
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 3
Errors were encountered while processing:
 clvm
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
root@SSNlinux:/home/ssn# 


I am new user of Ubuntu.. dont really understand all this. Please suggest me what to do.
thanks

---

### Post by Rui Pais on 2007-07-13
Ok. if you don't know if clvm is required that probably means that you don't need it. 

clvm is a clustering interface for lvm2 (the Linux Logical Volume Manager). 
If you don't know what this are then you don't need it. 
Are using Ubuntu Dapper? (it used to install lvm2 by default, but not clvm...i think)

Anyway since purge don't want to remove anything else it's safe to remove.

clvm run (or tries) as a service. So it must be stopped before remove. 
That part failed aborting the remove. 

Try first remove and then purge:
```
sudo apt-get remove clvm
sudo aptitude purge clvm
```

---

### Post by ssn1978 on 2007-07-13
Thanks Rui,
I am using Ubuntu 7.04. I have installed many packages but dont know how clvm gets installed, I am sure I have not selected this for installation. I run both the commands you mentioned and following was the outcome. I dont think that I was able to remove it. 
```
root@SSNlinux:/home/ssn# sudo apt-get remove clvm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  clvm
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 492kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 146519 files and directories currently installed.)
Removing clvm ...
Stopping Cluster LVM Daemon invoke-rc.d: initscript clvm, action "stop" failed.
dpkg: error processing clvm (--remove):
 subprocess pre-removal script returned error exit status 1
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 3
Errors were encountered while processing:
 clvm
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@SSNlinux:/home/ssn# sudo aptitude purge clvm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
The following packages will be REMOVED:
  clvm{p} 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 492kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 146519 files and directories currently installed.)
Removing clvm ...
Stopping Cluster LVM Daemon invoke-rc.d: initscript clvm, action "stop" failed.
dpkg: error processing clvm (--purge):
 subprocess pre-removal script returned error exit status 1
Starting Cluster LVM Daemon clvmd could not connect to cluster manager
Consult syslog for more information
invoke-rc.d: initscript clvm, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 3
Errors were encountered while processing:
 clvm
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
root@SSNlinux:/home/ssn# 

```
Please suggest me what to do next..

---

### Post by Rui Pais on 2007-07-13
ok lets try force it:
 ```
sudo apt-get remove --force-yes clvm
```

and you can try to remove first the service from the list:
```
update-rc.d clvm remove
```

btw you don't need to run as root. It's dangerous.
Thats why sudo is used. It will assign to that command administrative powers and only to that one.
good luck

---

### Post by emil01 on 2007-08-28
eyyy

i read all the instructions and tried it but still doesnt work

---

### Post by VinT on 2007-08-29
The same problem I threat by the next way

 sudo update-rc.d -f clvm remove
sudo rm /etc/init.d/clvm
sudo apt-get remove clvm

Thats all...:)

---

### Post by emil01 on 2007-09-06
i reinstalled ubuntu and it error stopped .

---

### Post by hiebert on 2007-09-06
> **VinT said:**
> The same problem I threat by the next way

 sudo update-rc.d -f clvm remove
sudo rm /etc/init.d/clvm
sudo apt-get remove clvm

Thats all...:)

Finally no more clvm problems.. Thanks a lot VinT!

---

