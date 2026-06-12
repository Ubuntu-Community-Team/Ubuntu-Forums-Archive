---
title: "apt-update very slow on 18.04"
date: 2019-01-06
forum: General Help
---

### Post by kroyee on 2019-01-06
I recently updated from 16.04 to 18.04, and my speed when running apt-update and apt-install etc usually varies between complete stand-still and up to 1,5kB/sec.

I've tried using many different mirrors without any difference, or small differences. Never seen any speeds faster then 3kB or so.

I also tried disabling ipv6 by adding ```
GRUB_CMDLINE_LINUX_DEFAULT="IPV6.DISABLE=1"
``` to /etc/default/grub and then ```
sudo update-grub
```.

No difference.

I'm currently trying to run a apt-get update, it's been running for around 15-20 min now and it looks like it tried to get the same file over and over again until it succeeds.

```
super@super-Peppy:~/programming/DRL-Tetris$ sudo apt updateHit:1 http://packages.microsoft.com/repos/vscode stable InRelease
Get:2 http://uk-mirrors.evowise.com/ubuntu bionic InRelease [242 kB]       
Hit:3 https://download.docker.com/linux/ubuntu bionic InRelease                
Get:2 http://uk-mirrors.evowise.com/ubuntu bionic InRelease [242 kB]           
Get:2 http://uk-mirrors.evowise.com/ubuntu bionic InRelease [242 kB]           
Get:2 http://uk-mirrors.evowise.com/ubuntu bionic InRelease [242 kB]           
Get:2 http://uk-mirrors.evowise.com/ubuntu bionic InRelease [242 kB]           
Get:2 http://uk-mirrors.evowise.com/ubuntu bionic InRelease [242 kB]           
Get:4 http://uk-mirrors.evowise.com/ubuntu bionic-updates InRelease [88,7 kB]
Get:4 http://uk-mirrors.evowise.com/ubuntu bionic-updates InRelease [88,7 kB]  
Get:5 http://uk-mirrors.evowise.com/ubuntu bionic-backports InRelease [74,6 kB]
Get:6 http://uk-mirrors.evowise.com/ubuntu bionic-security InRelease [83,2 kB] 
Get:7 http://uk-mirrors.evowise.com/ubuntu bionic/main i386 Packages [1&#8239;007 kB]
Get:7 http://uk-mirrors.evowise.com/ubuntu bionic/main i386 Packages [1&#8239;007 kB]
Get:7 http://uk-mirrors.evowise.com/ubuntu bionic/main i386 Packages [1&#8239;007 kB]
Get:7 http://uk-mirrors.evowise.com/ubuntu bionic/main i386 Packages [1&#8239;007 kB]
Get:7 http://uk-mirrors.evowise.com/ubuntu bionic/main i386 Packages [1&#8239;007 kB]
Get:7 http://uk-mirrors.evowise.com/ubuntu bionic/main i386 Packages [1&#8239;007 kB]
Get:7 http://uk-mirrors.evowise.com/ubuntu bionic/main i386 Packages [1&#8239;007 kB]
Get:8 http://uk-mirrors.evowise.com/ubuntu bionic/main amd64 Packages [1&#8239;019 kB]
Get:8 http://uk-mirrors.evowise.com/ubuntu bionic/main amd64 Packages [1&#8239;019 kB]
Get:8 http://uk-mirrors.evowise.com/ubuntu bionic/main amd64 Packages [1&#8239;019 kB]
Get:8 http://uk-mirrors.evowise.com/ubuntu bionic/main amd64 Packages [1&#8239;019 kB]
Get:8 http://uk-mirrors.evowise.com/ubuntu bionic/main amd64 Packages [1&#8239;019 kB]
Get:8 http://uk-mirrors.evowise.com/ubuntu bionic/main amd64 Packages [1&#8239;019 kB]
Get:8 http://uk-mirrors.evowise.com/ubuntu bionic/main amd64 Packages [1&#8239;019 kB]
Get:8 http://uk-mirrors.evowise.com/ubuntu bionic/main amd64 Packages [1&#8239;019 kB]
Get:8 http://uk-mirrors.evowise.com/ubuntu bionic/main amd64 Packages [1&#8239;019 kB]
Get:8 http://uk-mirrors.evowise.com/ubuntu bionic/main amd64 Packages [1&#8239;019 kB]
Get:8 http://uk-mirrors.evowise.com/ubuntu bionic/main amd64 Packages [1&#8239;019 kB]
Get:9 http://uk-mirrors.evowise.com/ubuntu bionic/main Translation-en [516 kB] 
Get:9 http://uk-mirrors.evowise.com/ubuntu bionic/main Translation-en [516 kB] 
Get:9 http://uk-mirrors.evowise.com/ubuntu bionic/main Translation-en [516 kB] 
Get:9 http://uk-mirrors.evowise.com/ubuntu bionic/main Translation-en [516 kB] 
Get:10 http://uk-mirrors.evowise.com/ubuntu bionic/main amd64 DEP-11 Metadata [477 kB]
Get:10 http://uk-mirrors.evowise.com/ubuntu bionic/main amd64 DEP-11 Metadata [477 kB]

```

I have two machines here with 18.04 and they both behave the same. On my friends laptop running 17.04 it however runs fine. Completes within 10sec.

I'm stumped, have no real idea how to go about finding the problem.
Please tell me what additional info you might need.
Cheers

---

### Post by kroyee on 2019-01-06
Turns out all I needed was to run ```
sudo apt-get clean
``` and now everything works again. Never had this issue before, but hey. Live and learn.
Cheers!

---

### Post by Impavidus on 2019-01-07
I wonder how your friend can check for updates on his 17.04 system in 10 seconds, as 17.04 has been dead for quite a while. Unless that means that it stops producing error messages within 10 seconds.

---

