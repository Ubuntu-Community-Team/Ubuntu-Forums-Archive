---
title: "&quot;module: command not found&quot; on ubuntu 22.04"
date: 2022-05-17
forum: General Help
---

### Post by az-u on 2022-05-17
After sudo apt install environment-modules,  after typing the commonds " module list" and "module avail"
the screen tells me that "module: command not found"


$ sudo apt install environment-modules
[sudo] password for az: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following NEW packages will be installed:
  environment-modules
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 254 kB of archives.
After this operation, 836 kB of additional disk space will be used.
Get:1 [http://mirrors.huaweicloud.com/repository/ubuntu](http://mirrors.huaweicloud.com/repository/ubuntu) jammy/universe amd64 environment-modules amd64 5.0.1-1 [254 kB]
Fetched 254 kB in 0s (694 kB/s)             
Selecting previously unselected package environment-modules.
(Reading database ... 243756 files and directories currently installed.)
Preparing to unpack .../environment-modules_5.0.1-1_amd64.deb ...
Unpacking environment-modules (5.0.1-1) ...
Setting up environment-modules (5.0.1-1) ...
Processing triggers for man-db (2.10.2-1) ...

---

### Post by grahammechanical on 2022-05-17
> "module: command not found"

That response tells us the "module" is not a Linux command. Have you loaded any modules?

> $ module load foo/1.0 $ echo $LD_LIBRARY_PATH
/path/to/lib
$ screen
$ module list
Currently Loaded Modulefiles:
 1) foo/1.0
[https://modules.readthedocs.io/en/latest/FAQ.html](https://modules.readthedocs.io/en/latest/FAQ.html)

Regards

---

