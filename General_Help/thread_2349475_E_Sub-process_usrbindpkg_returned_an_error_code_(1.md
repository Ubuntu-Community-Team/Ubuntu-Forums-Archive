---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2017-01-15
forum: General Help
---

### Post by demonlord98 on 2017-01-15
I have this when I try 
```
~$ sudo apt-get -f install
```

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  libgnuradio-iqbalance
The following NEW packages will be installed:
  libgnuradio-iqbalance
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/93.4 kB of archives.
After this operation, 532 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 247340 files and directories currently installed.)
Preparing to unpack .../libgnuradio-iqbalance_0.37.2-myriadrf5~xenial_amd64.deb ...
Unpacking libgnuradio-iqbalance (0.37.2-myriadrf5~xenial) ...
dpkg: error processing archive /var/cache/apt/archives/libgnuradio-iqbalance_0.37.2-myriadrf5~xenial_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libgnuradio-iqbalance.so', which is also in package gr-iqbal 0.37.2-5
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Processing triggers for libc-bin (2.23-0ubuntu5) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libgnuradio-iqbalance_0.37.2-myriadrf5~xenial_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


Can you help me please I can not update with apt-get

---

### Post by demonlord98 on 2017-01-15
I used ```
sudo apt-get  remove gr-osmosdr libgnuradio-osmosdr0.1.4 gqrx-sdr -f
``` to solve the problem, and it have been solved but I want gqrx so what to do now.

---

### Post by demonlord98 on 2017-01-15
Solved it, thanks to this topic on google groups:
[https://groups.google.com/forum/#!topic/gqrx/EtCHsr7B_mo](https://groups.google.com/forum/#!topic/gqrx/EtCHsr7B_mo)
I just have to remove [B]gr-iqbal.

```
sudo apt-get remove gr-iqbal
```
[/B]

---

