---
title: "Kernel Headers"
date: 2007-06-23
forum: General Help
---

### Post by shadows85 on 2007-06-23
I'm close to losing my mind with this! I try to use qemu, virtual box, vm server and all have the same error.. something about kernel headers I try:
```

sudo apt-get install linux-headers-`uname -r`

```
which apparently works for everyone except me.. instead I get this:
```

david@davids-computer-4441:~$ sudo apt-get install linux-headers-`uname -r`
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-2.6.17-11-386
david@davids-computer-4441:~$ 

```
I'm tired of wasting my time on this, yet this is one of the only things that will keep me with ubuntu.. Dual Booting is a pain and some about all of the programs I want to use are not on linux.. (wine cant run them either..)

---

### Post by taurus on 2007-06-23
Can you post your /etc/apt/sources.list?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```
Otherwise, run synaptic, System -> Administrator -> Synaptic Package Manager, and look for the version of your kernel.

p.s.  Did you upgrade to Feisty or did you do a fresh install?  I thought Feisty comes with kernel 2.6.20-15-generic.

```
uname -a
```

---

### Post by shadows85 on 2007-06-23
> **taurus said:**
> Can you post your /etc/apt/sources.list?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```
Otherwise, run synaptic, System -> Administrator -> Synaptic Package Manager, and look for the version of your kernel.

p.s.  Did you upgrade to Feisty or did you do a fresh install?  I thought Feisty comes with kernel 2.6.20-15-generic.

```
uname -a
```

upgraded, and one second I'll attach it.

---

### Post by shadows85 on 2007-06-23
```

deb http://us.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.


deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universedeb http://www.getautomatix.com/apt feisty main
#AUTOMATIX REPOS START

deb http://www.getautomatix.com/apt feisty main

deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://archive.ubuntu.com/ubuntu feisty-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-updates universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu feisty universe multiverse
#AUTOMATIX REPOS END

deb http://www.virtualbox.org/debian feisty non-free

```

---

### Post by taurus on 2007-06-23
If you are using Feisty, how come you still have two repos for Dapper in your /etc/apt/sources.list?

```
deb http://security.ubuntu.com/ubuntu [COLOR="Blue"]dapper[/COLOR]-security universe
deb-src http://security.ubuntu.com/ubuntu [COLOR="Blue"]dapper[/COLOR]-security universe
```
You need to remove those two repos

```
gksudo gedit /etc/apt/sources.list
```
and then run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by shadows85 on 2007-06-23
> **taurus said:**
> If you are using Feisty, how come you still have two repos for Dapper in your /etc/apt/sources.list?

```
deb http://security.ubuntu.com/ubuntu [COLOR="Blue"]dapper[/COLOR]-security universe
deb-src http://security.ubuntu.com/ubuntu [COLOR="Blue"]dapper[/COLOR]-security universe
```
You need to remove those two repos

```
gksudo gedit /etc/apt/sources.list
```
and then run

```
sudo aptitude update
sudo aptitude upgrade
```

ok, I did that, was that all there was to it?

---

### Post by taurus on 2007-06-23
Now see if you can install the kernel header for your machine.

---

### Post by shadows85 on 2007-06-23
> **taurus said:**
> Now see if you can install the kernel header for your machine.

nope... 

```
david@davids-computer-4441:~$ sudo apt-get install linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-2.6.17-11-386
david@davids-computer-4441:~$ 

```

---

### Post by az on 2007-06-23
> **shadows85 said:**
> nope... 

```
david@davids-computer-4441:~$ sudo apt-get install linux-headers-`uname -r`
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux-headers-2.6.17-11-386
david@davids-computer-4441:~$ 

```

sudo apt-get install linux-headers-generic

---

### Post by shadows85 on 2007-06-23
> **az said:**
> sudo apt-get install linux-headers-generic


```
david@davids-computer-4441:~$ sudo apt-get install linux-headers-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up vmware-server (1.0.3-1) ...
/etc/init.d/vmware-server: 176: vmware_product_name: not found
Warning: Unable to find 's main database /etc/vmware/locations.

invoke-rc.d: initscript vmware-server, action "start" failed.
dpkg: error processing vmware-server (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
david@davids-computer-4441:~$ 

```

Yet the problem persists on the vm programs.

---

### Post by shadows85 on 2007-06-23
This is hell.... I can't find anything on google, yahoo, or ask to help me..

---

### Post by jocko on 2007-06-23
Looks like you are running an old kernel (2.6.17).
Try to reboot. When grub loads hit escape to get the boot menu.
If your upgrade to feisty worked fine you should have a 2.6.20 kernel installed.

---

### Post by shadows85 on 2007-06-23
> **jocko said:**
> Looks like you are running an old kernel (2.6.17).
Try to reboot. When grub loads hit escape to get the boot menu.
If your upgrade to feisty worked fine you should have a 2.6.20 kernel installed.

... THANK YOU! Turned out my start up manager was booting me up with a older version of kernel.. worked like a charm! Thanks fixed!

---

