---
title: "fwupdate error after upgrade to 17.04"
date: 2017-03-27
forum: General Help
---

### Post by Yahoé on 2017-03-27
The upgrade reported an error on fwupdate and fwupdate-signed. dpkg --configure -a returns:

mkdir: unable to create "/boot/efi/EFI/ubuntu" Input/output error
rm: unable to delete '/boot/efi/EFI/ubuntu/fwupx64.efi' Input/output error
cp: unable to access '/boot/efi/EFI/ubuntu/fwupx64.efi' Input/output error
dpkg: error processing package fwupdate (--configure)
dpkg: dependencies issues prevent fwupdate-signed configuration

Any idea what is happening here?

---

### Post by leodaft on 2018-01-15
I have the same problem too.:-(

---

### Post by zika on 2018-01-15
Check permissions first```
:~$ ls /boot/efi -alt
total 12
drwxr-xr-x 4 root root 4096 jan 15 08:06 ..
drwxr-xr-x 3 root root 4096 mar 20  2016 .
drwxr-xr-x 3 root root 4096 mar 20  2016 EFI
:~$ ls /boot/efi/EFI -alt
total 12
drwxr-xr-x 3 root root 4096 okt 21  2016 ubuntu
drwxr-xr-x 3 root root 4096 mar 20  2016 .
drwxr-xr-x 3 root root 4096 mar 20  2016 ..
:~$ ls /boot/efi/EFI -alt
total 12
drwxr-xr-x 3 root root 4096 okt 21  2016 ubuntu
drwxr-xr-x 3 root root 4096 mar 20  2016 .
drwxr-xr-x 3 root root 4096 mar 20  2016 ..
:~$ ls /boot/efi/EFI/ubuntu -alt
total 12
drwxr-xr-x 3 root root 4096 okt 21  2016 .
drwxr-xr-x 3 root root 4096 mar 20  2016 ..
drwxr-xr-x 2 root root 4096 mar 20  2016 fw
:~$ ls /boot/efi/EFI/ubuntu/fw -alt
total 8
drwxr-xr-x 3 root root 4096 okt 21  2016 ..
drwxr-xr-x 2 root root 4096 mar 20  2016 .
:~$ sudo apt install fwupdate-signed  -s
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  fwupdate-signed
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Inst fwupdate-signed (1.15+9-3 Ubuntu:18.04/bionic [amd64])
Conf fwupdate-signed (1.15+9-3 Ubuntu:18.04/bionic [amd64])
```Alternatively re{nam,mov}e folders...
Update&#8321;: Mea culpa. Since thread was posted in UDV I (wrongly) supposed it was addressing 18.04-to-be not reading name of thread properly... ;)

---

### Post by dino99 on 2018-01-15
That version is now dead
[http://news.softpedia.com/news/ubuntu-17-04-zesty-zapus-has-reached-end-of-life-upgrade-to-ubuntu-17-10-now-519360.shtml](http://news.softpedia.com/news/ubuntu-17-04-zesty-zapus-has-reached-end-of-life-upgrade-to-ubuntu-17-10-now-519360.shtml)

---

