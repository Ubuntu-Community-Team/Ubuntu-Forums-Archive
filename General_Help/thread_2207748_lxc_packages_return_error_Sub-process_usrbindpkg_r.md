---
title: "lxc packages return error: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2014-02-25
forum: General Help
---

### Post by ej-loudersoft on 2014-02-25
Hi All --

I'm stumped.  Every time I try to update or install any packages, the following is happening.  I found an old thread about this but it's not helping me at all to figure out what to do.  Any time I try to upgrade or install anything, these lxc packages keep failing and, thus, anything else I try to install or upgrade fails.  Please help!! I don't know what the heck I'm supposed to do.  Thank you.

```
xxxxxxx@xxxxxxx:/var/lib/dpkg/info$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 240 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up lxc (0.7.5-3ubuntu69) ...
start: Job failed to start
invoke-rc.d: initscript lxc-net, action "start" failed.
dpkg: error processing lxc (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of lxc-docker-0.7.6:
 lxc-docker-0.7.6 depends on lxc; however:
  Package lxc is not configured yet.
dpkg: error processing lxc-docker-0.7.6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lxc-docker:
 lxc-docker depends on lxc-docker-0.7.6; however:
  Package lxc-docker-0.7.6 is not configured yet.
dpkg: error processing lxc-docker (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 lxc
 lxc-docker-0.7.6
 lxc-docker
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by jeanjd63 on 2014-02-25
Hello

What is your version ubuntu and is it à 32 or 64 bits architecture?

---

### Post by ej-loudersoft on 2014-02-25
> **jeanjd63 said:**
> Hello

What is your version ubuntu and is it à 32 or 64 bits architecture?

Ubuntu 12.04.2 LTS (GNU/Linux 2.6.32-042stab083.2 x86_64)

---

### Post by ibjsb4 on 2014-02-25
Try 

```
sudo dpkg --configure -a
```

How did you install lxc-docker?

---

### Post by jeanjd63 on 2014-02-25
You can try this :
```
wget http://launchpadlibrarian.net/155348558/lxc_0.7.5-3ubuntu69_amd64.deb 
```
[B]sudo  dpkg  -i  --force-all lxc_0.7.5-3ubuntu69_amd64.deb

[/B]Then :[B]
sudo  apt-get  install -f

[/B]And if it's ok you do :
[B]sudo  apt-get  autoremove
sudo  apt-get  update
sudo  apt-get  dist-upgrade[/B]

---

### Post by ej-loudersoft on 2014-02-25
> **ibjsb4 said:**
> Try 

```
sudo dpkg --configure -a
```

How did you install lxc-docker?

this happened a while ago, I can't recall. that command didn't work.

---

### Post by ej-loudersoft on 2014-02-25
> **jeanjd63 said:**
> You can try this :
```
wget http://launchpadlibrarian.net/155348558/lxc_0.7.5-3ubuntu69_amd64.deb 
```
[B]sudo  dpkg  -i  --force-all lxc_0.7.5-3ubuntu69_amd64.deb

[/B]Then :[B]
sudo  apt-get  install -f

[/B]And if it's ok you do :
[B]sudo  apt-get  autoremove
sudo  apt-get  update
sudo  apt-get  dist-upgrade[/B]

No go.  Output:

```
xxxx@xxxx:~$ sudo dpkg -i --force-all lxc_0.7.5-3ubuntu69_amd64.deb(Reading database ...
dpkg: warning: files list file for package `lxc-docker-0.7.6' missing, assuming package has no files currently installed.


dpkg: warning: files list file for package `lxc-docker' missing, assuming package has no files currently installed.
(Reading database ... 66357 files and directories currently installed.)
Preparing to replace lxc 0.7.5-3ubuntu69 (using lxc_0.7.5-3ubuntu69_amd64.deb) ...
Unpacking replacement lxc ...
Setting up lxc (0.7.5-3ubuntu69) ...
start: Job failed to start
invoke-rc.d: initscript lxc-net, action "start" failed.
dpkg: error processing lxc (--install):
 subprocess installed post-installation script returned error exit status 1
Processing triggers for man-db ...
Errors were encountered while processing:
 lxc
xxxx@xxxx:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 240 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up lxc (0.7.5-3ubuntu69) ...
start: Job failed to start
invoke-rc.d: initscript lxc-net, action "start" failed.
dpkg: error processing lxc (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of lxc-docker-0.7.6:
 lxc-docker-0.7.6 depends on lxc; however:
  Package lxc is not configured yet.
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                    dpkg: error processing lxc-docker-0.7.6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lxc-docker:
 lxc-docker depends on lxc-docker-0.7.6; however:
  Package lxc-docker-0.7.6 is not configured yet.
dpkg: error processing lxc-docker (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 lxc
 lxc-docker-0.7.6
 lxc-docker
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by jeanjd63 on 2014-02-26
You can try :
```
wget http://mirror.yandex.ru/mirrors/docker/pool/main/l/lxc-docker-0.7.6/lxc-docker-0.7.6_0.7.6_amd64.deb
```
and then 
**sudo  dpkg  -i  --force-all  lxc-docker-0.7.6_0.7.6_amd64.deb**

---

### Post by ej-loudersoft on 2014-02-27
> **jeanjd63 said:**
> You can try :
```
wget http://mirror.yandex.ru/mirrors/docker/pool/main/l/lxc-docker-0.7.6/lxc-docker-0.7.6_0.7.6_amd64.deb
```
and then 
**sudo  dpkg  -i  --force-all  lxc-docker-0.7.6_0.7.6_amd64.deb**

Tried this then went back to the previous command set, still stuck. See below & thank you for all your help.

```
xxxxx@xxxxx:~$ sudo dpkg -i --force-all lxc-docker-0.7.6_0.7.6_amd64.deb(Reading database ...
dpkg: warning: files list file for package `lxc-docker-0.7.6' missing, assuming package has no files currently installed.


dpkg: warning: files list file for package `lxc-docker' missing, assuming package has no files currently installed.
(Reading database ... 66392 files and directories currently installed.)
Preparing to replace lxc-docker-0.7.6 0.7.6 (using lxc-docker-0.7.6_0.7.6_amd64.deb) ...
Unpacking replacement lxc-docker-0.7.6 ...
dpkg: lxc-docker-0.7.6: dependency problems, but configuring anyway as you requested:
 lxc-docker-0.7.6 depends on lxc; however:
  Package lxc is not configured yet.
Setting up lxc-docker-0.7.6 (0.7.6) ...


Configuration file `/etc/default/docker', does not exist on system.
Installing new config file as you requested.


Configuration file `/etc/init.d/docker', does not exist on system.
Installing new config file as you requested.


Configuration file `/etc/init/docker.conf', does not exist on system.
Installing new config file as you requested.
docker start/running, process 17826
xxxx@xxxxxx:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up lxc (0.7.5-3ubuntu69) ...
start: Job failed to start
invoke-rc.d: initscript lxc-net, action "start" failed.
dpkg: error processing lxc (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up lxc-docker (0.7.6) ...
Errors were encountered while processing:
 lxc
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

---

### Post by jeanjd63 on 2014-02-27
[Here]("https://bugs.launchpad.net/ubuntu/+source/lxc/+bug/939795") see the post #4
and then do a :
[B]sudo  apt-get  install  -f
[/B]
If it's not good you can try to suppress this :
[B]sudo  apt-get  purge  "lxc *"
[/B]Then :[B]
sudo  apt-get  install -f
[/B]

---

