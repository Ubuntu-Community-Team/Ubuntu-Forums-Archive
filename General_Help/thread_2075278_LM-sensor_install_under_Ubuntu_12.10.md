---
title: "LM-sensor install under Ubuntu 12.10"
date: 2012-10-23
forum: General Help
---

### Post by Mark Phelps on 2012-10-23
As part of doing my "standard" set of customization tweaks with a new Ubuntu version, I went to install lm-sensors today ... and got a message that 18 packages would be held back if I did this!

I really don't want to hold back ANY packages.

So, has anyone actually installed lm-sensors in 12.10?

If so, what has been your experience with this?

---

### Post by QIII on 2012-10-23
Had it running fine in my Ubuntu, Xubuntu and Kubuntu installs.  Maybe just a case of dependencies waiting to get moved to your mirror?

---

### Post by Mark Phelps on 2012-10-23
> **QIII said:**
> Had it running fine in my Ubuntu, Xubuntu and Kubuntu installs.  Maybe just a case of dependencies waiting to get moved to your mirror?

So, it didn't hold back packages when you installed it?

I know I can make it from source, but I'd rather just use the .deb -- but I don't want to get into a "broken packages" situation where I have a bunch held back and can't do regular updates anymore.

---

### Post by pqwoerituytrueiwoq on 2012-10-23
i have lm sensors installed only held package i have is file-roller and that is cause i downgraded to the one in precise over some of its bugs

My extra apt-get sources:
```
sudo sed -i 's/\# deb h/deb h/;s/\# deb-src h/deb-src h/' /etc/apt/sources.list
sudo apt-add-repository -y ppa:xorg-edgers/ppa
sudo -E wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list
sudo add-apt-repository -y "deb http://packages.mate-desktop.org/repo/ubuntu quantal main"
sudo add-apt-repository -y "deb http://archive.getdeb.net/ubuntu quantal-getdeb apps"
sudo add-apt-repository -y "deb http://archive.getdeb.net/ubuntu quantal-getdeb games"
sudo apt-add-repository -y ppa:unity-team/staging
wget -q -O- http://archive.getdeb.net/getdeb-archive.key | sudo apt-key add -
```
using xubuntu, the mate repo is just for caja

---

### Post by Cheesemill on 2012-10-23
Just installed here on Ubuntu 12.10, no problems at all.
```
root@quantal:~# apt-get install lm-sensors
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  fancontrol sensord read-edid i2c-tools
The following NEW packages will be installed
  lm-sensors
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 100.0 kB of archives.
After this operation, 411 kB of additional disk space will be used.
Get:1 http://gb.archive.ubuntu.com/ubuntu/ quantal/universe lm-sensors amd64 1:3.3.1-2ubuntu2 [100.0 kB]
Fetched 100.0 kB in 0s (276 kB/s)    
Selecting previously unselected package lm-sensors.
(Reading database ... 161921 files and directories currently installed.)
Unpacking lm-sensors (from .../lm-sensors_1%3a3.3.1-2ubuntu2_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up lm-sensors (1:3.3.1-2ubuntu2) ...
Processing triggers for ureadahead ...
root@quantal:~# 
```

---

### Post by Mark Phelps on 2012-10-23
Cheesemill:  OK, went ahead and did the install ... but mine said 8 packages not upgraded, not one.  However, seems to be working OK.

---

### Post by pqwoerituytrueiwoq on 2012-10-23
probably means there were updates available there were not installed
you were not notified by the update manager because they are not security updates and non-security are once a week be default

---

