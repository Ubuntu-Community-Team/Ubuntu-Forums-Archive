---
title: "networking removed after update"
date: 2016-05-13
forum: General Help
---

### Post by sam_baker2 on 2016-05-13
hi,
Just updated my desktop xubuntu 14.04 LTS, amd64 machine , and noticed the network was not working.
Luckily I had another machine and went online and used this solution, in case anyone else has same thing happen.
I went to [http://askubuntu.com/questions/727127/last-upgrade-crashes-network-manager-no-internet-connection-no-applet/727462#727462](http://askubuntu.com/questions/727127/last-upgrade-crashes-network-manager-no-internet-connection-no-applet/727462#727462)
and followed the instructions to download and install the old network-manager.
I needed these three files for my amd64 machine:
```

libnl-3-200_3.2.21-1_amd64.deb
[http://archive.ubuntu.com/ubuntu/pool/main/libn/libnl3/libnl-3-200_3.2.21-1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/libn/libnl3/libnl-3-200_3.2.21-1_amd64.deb) 
libnl-genl-3-200_3.2.21-1_amd64.deb
[http://archive.ubuntu.com/ubuntu/pool/main/libn/libnl3/libnl-genl-3-200_3.2.21-1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/libn/libnl3/libnl-genl-3-200_3.2.21-1_amd64.deb)
libnl-route-3-200_3.2.21-1_amd64.deb
[http://archive.ubuntu.com/ubuntu/pool/main/libn/libnl3/libnl-route-3-200_3.2.21-1_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/libn/libnl3/libnl-route-3-200_3.2.21-1_amd64.deb)


```
 if you have i386 machine, these files:
[http://archive.ubuntu.com/ubuntu/pool/main/libn/libnl3/libnl-3-200_3.2.21-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libn/libnl3/libnl-3-200_3.2.21-1_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/libn/libnl3/libnl-genl-3-200_3.2.21-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libn/libnl3/libnl-genl-3-200_3.2.21-1_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/libn/libnl3/libnl-route-3-200_3.2.21-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libn/libnl3/libnl-route-3-200_3.2.21-1_i386.deb)


then, using terminal, I went into the folder were they were saved and did this:
```

sudo dpkg -i libnl-*.deb

```
then
```

sudo service network-manager restart

```
This installs the earlier network-manager.

---

