---
title: "Broken package - unable to fix"
date: 2018-07-13
forum: General Help
---

### Post by makem2 on 2018-07-13
```

makem@ssdTOSH:~$ sudo apt update
[sudo] password for makem: 
Hit:1 http://ppa.launchpad.net/rolfbensch/sane-git/ubuntu xenial InRelease
Get:2 http://security.ubuntu.com/ubuntu xenial-security InRelease [107 kB]               
Hit:3 http://gb.archive.ubuntu.com/ubuntu xenial InRelease                               
Get:4 http://gb.archive.ubuntu.com/ubuntu xenial-updates InRelease [109 kB]              
Hit:5 http://ppa.launchpad.net/rolfbensch/sane-release/ubuntu xenial InRelease           
Get:6 http://gb.archive.ubuntu.com/ubuntu xenial-backports InRelease [107 kB]            
Get:7 https://deb.opera.com/opera-stable stable InRelease [2,592 B]
Get:8 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [67.7 kB]
Get:9 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [68.0 kB]
Get:10 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [107 kB]
Get:11 http://security.ubuntu.com/ubuntu xenial-security/universe DEP-11 64x64 Icons [142 kB]
Get:12 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [318 kB]
Get:13 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [238 kB]
Get:14 http://gb.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 Packages [642 kB]
Get:15 http://gb.archive.ubuntu.com/ubuntu xenial-updates/universe i386 Packages [586 kB]
Get:16 https://deb.opera.com/opera-stable stable/non-free amd64 Packages [1,822 B]
Get:17 http://gb.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [246 kB]
Get:18 http://gb.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [340 kB]
Get:19 http://gb.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [5,964 B]
Get:20 http://gb.archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata [3,328 B]
Get:21 http://gb.archive.ubuntu.com/ubuntu xenial-backports/universe amd64 DEP-11 Metadata [5,100 B]
Fetched 3,095 kB in 0s (3,195 kB/s)                               
AppStream cache update completed, but some metadata was ignored due to errors.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.
makem@ssdTOSH:~$ apt list --upgradable
Listing... Done
libsane/xenial 1.0.27+git20180630-xenial0 amd64 [upgradable from: 1.0.25+git20150528-1ubuntu2.16.04.1]
N: There are 3 additional versions. Please use the '-a' switch to see them.
makem@ssdTOSH:~$ apt list -a --upgradable
Listing... Done
libsane/xenial 1.0.27+git20180630-xenial0 amd64 [upgradable from: 1.0.25+git20150528-1ubuntu2.16.04.1]
libsane/xenial 1.0.27-xenial1 amd64
libsane/xenial-updates,now 1.0.25+git20150528-1ubuntu2.16.04.1 amd64 [installed,upgradable to: 1.0.27+git20180630-xenial0]
libsane/xenial 1.0.25+git20150528-1ubuntu2 amd64


makem@ssdTOSH:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 libsane : Depends: libsane-common (= 1.0.25+git20150528-1ubuntu2.16.04.1)
E: Unmet dependencies. Try using -f.
makem@ssdTOSH:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  libsane
Suggested packages:
  hpoj libsane-extras
The following packages will be upgraded:
  libsane
1 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
Need to get 0 B/2,104 kB of archives.
After this operation, 652 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 272805 files and directories currently installed.)
Preparing to unpack .../libsane_1.0.27+git20180630-xenial0_amd64.deb ...
Unpacking libsane:amd64 (1.0.27+git20180630-xenial0) over (1.0.25+git20150528-1ubuntu2.16.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/libsane_1.0.27+git20180630-xenial0_amd64.deb (--unpack):
 trying to overwrite '/etc/sane.d/gphoto2.conf', which is also in package libsane-common 1.0.27+git20180630-xenial0
Processing triggers for libc-bin (2.23-0ubuntu10) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libsane_1.0.27+git20180630-xenial0_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
makem@ssdTOSH:~$ 

```

Error when trying to overwrite  '/etc/sane.d/gphoto2.conf', so I remove it:

```

sudo mv  /etc/sane.d/gphoto2.conf  /etc/sane.d/gphoto2.conf.old
mv: cannot stat '/etc/sane.d/gphoto2.conf': No such file or directory
makem@ssdTOSH:~$ ls -la /etc/sane.d
total 340
drwxr-xr-x   3 root root  4096 Jul 13 10:52 .
drwxr-xr-x 139 root root 12288 Jul 13 16:31 ..
-rw-r--r--   1 root root    25 Mar 31  2017 abaton.conf
-rw-r--r--   1 root root    14 Mar 31  2017 agfafocus.conf
-rw-r--r--   1 root root    24 Mar 31  2017 apple.conf
-rw-r--r--   1 root root    26 Mar 31  2017 artec.conf
-rw-r--r--   1 root root  4140 Mar 31  2017 artec_eplus48u.conf
-rw-r--r--   1 root root   548 Mar 31  2017 avision.conf
-rw-r--r--   1 root root    29 Mar 31  2017 bh.conf
-rw-r--r--   1 root root   193 Mar 31  2017 canon630u.conf
-rw-r--r--   1 root root    26 Mar 31  2017 canon.conf
-rw-r--r--   1 root root  3885 Mar 31  2017 canon_dr.conf
-rw-r--r--   1 root root  1160 Mar 31  2017 canon_pp.conf
-rw-r--r--   1 root root   509 Mar 31  2017 cardscan.conf
-rw-r--r--   1 root root   754 Mar 31  2017 coolscan2.conf
-rw-r--r--   1 root root   754 Mar 31  2017 coolscan3.conf
-rw-r--r--   1 root root    34 Mar 31  2017 coolscan.conf
-rw-r--r--   1 root root   984 Mar 31  2017 dc210.conf
-rw-r--r--   1 root root   984 Mar 31  2017 dc240.conf
-rw-r--r--   1 root root   704 Mar 31  2017 dc25.conf
-rw-r--r--   1 root root   492 Mar 31  2017 dell1600n_net.conf
-rw-r--r--   1 root root  1098 Mar 31  2017 dll.conf
drwxr-xr-x   2 root root  4096 Aug  1  2017 dll.d
-rw-r--r--   1 root root    12 Mar 31  2017 dmc.conf
-rw-r--r--   1 root root  2569 Mar 31  2017 epjitsu.conf
-rw-r--r--   1 root root   376 Mar 31  2017 epson2.conf
-rw-r--r--   1 root root   793 Mar 31  2017 epson.conf
-rw-r--r--   1 root root   221 Mar 31  2017 epsonds.conf
-rw-r--r--   1 root root  2248 Mar 31  2017 fujitsu.conf
-rw-r--r--   1 root root  2008 Mar 31  2017 genesys.conf
-rw-r--r--   1 root root  1149 Mar 31  2017 gphoto2.bk
-rw-r--r--   1 root root  7795 Mar 31  2017 gt68xx.conf
-rw-r--r--   1 root root   396 Mar 31  2017 hp3900.conf
-rw-r--r--   1 root root    76 Mar 31  2017 hp4200.conf
-rw-r--r--   1 root root   238 Mar 31  2017 hp5400.conf
-rw-r--r--   1 root root   497 Mar 31  2017 hp.conf
-rw-r--r--   1 root root    22 Mar 31  2017 hpsj5s.conf
-rw-r--r--   1 root root    24 Mar 31  2017 hs2p.conf
-rw-r--r--   1 root root    38 Mar 31  2017 ibm.conf
-rw-r--r--   1 root root  2599 Mar 31  2017 kodakaio.conf
-rw-r--r--   1 root root   367 Mar 31  2017 kodak.conf
-rw-r--r--   1 root root   113 Mar 31  2017 leo.conf
-rw-r--r--   1 root root   119 Mar 31  2017 lexmark.conf
-rw-r--r--   1 root root   187 Mar 31  2017 ma1509.conf
-rw-r--r--   1 root root  1254 Mar 31  2017 magicolor.conf
-rw-r--r--   1 root root   666 Mar 31  2017 matsushita.conf
-rw-r--r--   1 root root   279 Mar 31  2017 microtek2.conf
-rw-r--r--   1 root root   268 Mar 31  2017 microtek.conf
-rw-r--r--   1 root root  2125 Mar 31  2017 mustek.conf
-rw-r--r--   1 root root  3824 Mar 31  2017 mustek_pp.conf
-rw-r--r--   1 root root   809 Mar 31  2017 mustek_usb.conf
-rw-r--r--   1 root root    13 Mar 31  2017 nec.conf
-rw-r--r--   1 root root   573 Mar 31  2017 net.conf
-rw-r--r--   1 root root   365 Mar 31  2017 p5.conf
-rw-r--r--   1 root root    75 Mar 31  2017 pie.conf
-rw-r--r--   1 root root   492 Mar 31  2017 pixma.conf
-rw-r--r--   1 root root  4142 Mar 31  2017 plustek.conf
-rw-r--r--   1 root root   943 Mar 31  2017 plustek_pp.conf
-rw-r--r--   1 root root   391 Mar 31  2017 qcam.conf
-rw-r--r--   1 root root    29 Mar 31  2017 ricoh.conf
-rw-r--r--   1 root root   183 Mar 31  2017 rts8891.conf
-rw-r--r--   1 root root    13 Mar 31  2017 s9036.conf
-rw-r--r--   1 root root  1076 Jul 12 21:23 saned.conf
-rw-r--r--   1 root root    48 Mar 31  2017 sceptre.conf
-rw-r--r--   1 root root  1464 Mar 31  2017 sharp.conf
-rw-r--r--   1 root root   115 Mar 31  2017 sm3840.conf
-rw-r--r--   1 root root  2239 Mar 31  2017 snapscan.conf
-rw-r--r--   1 root root    10 Mar 31  2017 sp15c.conf
-rw-r--r--   1 root root  2224 Mar 31  2017 st400.conf
-rw-r--r--   1 root root   178 Mar 31  2017 stv680.conf
-rw-r--r--   1 root root    28 Mar 31  2017 tamarack.conf
-rw-r--r--   1 root root   355 Mar 31  2017 teco1.conf
-rw-r--r--   1 root root   636 Mar 31  2017 teco2.conf
-rw-r--r--   1 root root   217 Mar 31  2017 teco3.conf
-rw-r--r--   1 root root  1807 Mar 31  2017 test.conf
-rw-r--r--   1 root root  1495 Mar 31  2017 u12.conf
-rw-r--r--   1 root root   386 Mar 31  2017 umax1220u.conf
-rw-r--r--   1 root root  3094 Mar 31  2017 umax.conf
-rw-r--r--   1 root root  1684 Mar 31  2017 umax_pp.conf
-rw-r--r--   1 root root  3424 Mar 31  2017 xerox_mfp.conf
makem@ssdTOSH:~$ 

```

So why error when overwriting if it does not exist?

---

### Post by Xian on 2018-07-14
Let's try a couple of commands to get back on track:

```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/libsane_1.0.27+git20180630-xenial0_amd64.deb
```If "--force-overwrite" doesn't work, you can try "--force-all" instead


If this completes without error then finally:
```
sudo apt-get install -f
```

---

### Post by makem2 on 2018-07-15
```

makem@ssdTOSH:~$ sudo dpkg -i --force-overwrite /var/cache/apt/archives/libsane_1.0.27+git20180630-xenial0_amd64.deb
[sudo] password for makem: 
Selecting previously unselected package libsane:amd64.
(Reading database ... 271720 files and directories currently installed.)
Preparing to unpack .../libsane_1.0.27+git20180630-xenial0_amd64.deb ...
Unpacking libsane:amd64 (1.0.27+git20180630-xenial0) ...
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/etc/sane.d/gphoto2.conf', which is also in package libsane-common 1.0.27+git20180630-xenial0
Setting up libsane:amd64 (1.0.27+git20180630-xenial0) ...
Installing new version of config file /etc/sane.d/agfafocus.conf ...
Installing new version of config file /etc/sane.d/artec.conf ...
Installing new version of config file /etc/sane.d/artec_eplus48u.conf ...
Installing new version of config file /etc/sane.d/avision.conf ...
Installing new version of config file /etc/sane.d/canon_dr.conf ...
Installing new version of config file /etc/sane.d/canon_pp.conf ...
Installing new version of config file /etc/sane.d/cardscan.conf ...
Installing new version of config file /etc/sane.d/dc210.conf ...
Installing new version of config file /etc/sane.d/dc240.conf ...
Installing new version of config file /etc/sane.d/dc25.conf ...
Installing new version of config file /etc/sane.d/dell1600n_net.conf ...
Installing new version of config file /etc/sane.d/dll.conf ...
Installing new version of config file /etc/sane.d/epjitsu.conf ...
Installing new version of config file /etc/sane.d/epson.conf ...
Installing new version of config file /etc/sane.d/epson2.conf ...
Installing new version of config file /etc/sane.d/epsonds.conf ...
Installing new version of config file /etc/sane.d/fujitsu.conf ...


Configuration file '/etc/sane.d/gphoto2.conf'
 ==> Deleted (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : start a shell to examine the situation
 The default action is to keep your current version.
*** gphoto2.conf (Y/I/N/O/D/Z) [default=N] ? y
Installing new version of config file /etc/sane.d/gphoto2.conf ...
Installing new version of config file /etc/sane.d/gt68xx.conf ...
Installing new version of config file /etc/sane.d/hp3900.conf ...
Installing new version of config file /etc/sane.d/hpsj5s.conf ...
Installing new version of config file /etc/sane.d/kodakaio.conf ...
Installing new version of config file /etc/sane.d/leo.conf ...
Installing new version of config file /etc/sane.d/magicolor.conf ...
Installing new version of config file /etc/sane.d/matsushita.conf ...
Installing new version of config file /etc/sane.d/mustek.conf ...
Installing new version of config file /etc/sane.d/mustek_pp.conf ...
Installing new version of config file /etc/sane.d/mustek_usb.conf ...
Installing new version of config file /etc/sane.d/pixma.conf ...
Installing new version of config file /etc/sane.d/plustek.conf ...
Installing new version of config file /etc/sane.d/plustek_pp.conf ...
Installing new version of config file /etc/sane.d/sharp.conf ...
Installing new version of config file /etc/sane.d/tamarack.conf ...
Installing new version of config file /etc/sane.d/teco2.conf ...
Installing new version of config file /etc/sane.d/u12.conf ...
Installing new version of config file /etc/sane.d/umax.conf ...
Installing new version of config file /etc/sane.d/umax_pp.conf ...
Installing new version of config file /etc/sane.d/xerox_mfp.conf ...
Processing triggers for libc-bin (2.23-0ubuntu10) ...
makem@ssdTOSH:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
makem@ssdTOSH:~$ 

```

Thank you.

---

