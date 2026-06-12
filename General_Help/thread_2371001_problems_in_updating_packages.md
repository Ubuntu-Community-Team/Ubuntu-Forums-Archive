---
title: "problems in updating packages"
date: 2017-09-09
forum: General Help
---

### Post by su:bhatta on 2017-09-09
Hi,

trying to update Ubuntu Studio and getting the below :

```

Get:1 http://dl.google.com/linux/chrome/deb stable/main amd64 google-chrome-stable amd64 61.0.3163.79-1 [65.5 MB]
Get:2 http://in.archive.ubuntu.com/ubuntu zesty-updates/main amd64 samba-libs amd64 2:4.5.8+dfsg-0ubuntu0.17.04.6 [5,079 kB]
Get:3 http://in.archive.ubuntu.com/ubuntu zesty-updates/main amd64 libwbclient0 amd64 2:4.5.8+dfsg-0ubuntu0.17.04.6 [32.4 kB]                                                                                                   
Get:4 http://in.archive.ubuntu.com/ubuntu zesty-updates/main amd64 libsmbclient amd64 2:4.5.8+dfsg-0ubuntu0.17.04.6 [53.4 kB]                                                                                                   
Get:5 http://in.archive.ubuntu.com/ubuntu zesty-updates/main amd64 libgnutls-openssl27 amd64 3.5.6-4ubuntu4.2 [20.5 kB]                                                                                                         
Get:6 http://in.archive.ubuntu.com/ubuntu zesty-updates/main amd64 libgnutls30 amd64 3.5.6-4ubuntu4.2 [627 kB]                                                                                                                  
Get:6 http://in.archive.ubuntu.com/ubuntu zesty-updates/main amd64 libgnutls30 amd64 3.5.6-4ubuntu4.2 [627 kB]                                                                                                                  
Err:6 http://in.archive.ubuntu.com/ubuntu zesty-updates/main amd64 libgnutls30 amd64 3.5.6-4ubuntu4.2
  Hash Sum mismatch
  Hashes of expected file:
   - SHA256:fceab1e048594263284c98b3279204b534115bcd7b25622df9d2543e00f9f105
   - SHA1:1e7cfbb3d428f4c075bfe6c35bdfd06776a310db [weak]
   - MD5Sum:a44332c6ae1d30f09a66206213a51e0c [weak]
   - Filesize:627362 [weak]
  Hashes of received file:
   - SHA256:ff024dbd9091b949bdfcea6432528284302f657084cc609726a6c7bd2ea23244
   - SHA1:5e4c27473e7b9de5f6db95fe98e349255ec5586c [weak]
   - MD5Sum:1f1b6763a00c27650def3a06cc6e4335 [weak]
   - Filesize:627362 [weak]
  Last modification reported: Thu, 17 Aug 2017 23:20:30 +0000
Get:7 http://in.archive.ubuntu.com/ubuntu zesty-updates/main amd64 file amd64 1:5.29-3ubuntu0.1 [21.8 kB]
Get:8 http://in.archive.ubuntu.com/ubuntu zesty-updates/main amd64 libmagic1 amd64 1:5.29-3ubuntu0.1 [68.3 kB]
Get:9 http://in.archive.ubuntu.com/ubuntu zesty-updates/main amd64 libmagic-mgc amd64 1:5.29-3ubuntu0.1 [181 kB]
Get:10 http://in.archive.ubuntu.com/ubuntu zesty-updates/universe amd64 catdoc amd64 1:0.94.3~git20160113.dbc9ec6+dfsg-1+deb9u1build0.17.04.1 [85.4 kB]                                                                         
Get:11 http://in.archive.ubuntu.com/ubuntu zesty-updates/main amd64 gnome-software-plugin-snap amd64 3.22.7-0ubuntu3.17.04.7 [26.3 kB]                                                                                          
Get:12 http://in.archive.ubuntu.com/ubuntu zesty-updates/main amd64 gnome-software amd64 3.22.7-0ubuntu3.17.04.7 [305 kB]                                                                                                       
Get:13 http://in.archive.ubuntu.com/ubuntu zesty-updates/main amd64 gnome-software-common all 3.22.7-0ubuntu3.17.04.7 [2,481 kB]                                                                                                
Get:14 http://in.archive.ubuntu.com/ubuntu zesty-updates/universe amd64 kwayland-integration amd64 4:5.9.5-0ubuntu0.1 [21.6 kB]                                                                                                 
Get:15 http://in.archive.ubuntu.com/ubuntu zesty-updates/main amd64 libgd3 amd64 2.2.4-2ubuntu0.3 [117 kB]                                                                                                                      
Get:16 http://in.archive.ubuntu.com/ubuntu zesty-updates/main amd64 python-defusedxml all 0.4.1-2ubuntu0.17.04.1 [35.0 kB]                                                                                                      
Get:17 http://in.archive.ubuntu.com/ubuntu zesty-updates/main amd64 snapd amd64 2.27.5+17.04 [7,635 kB]                                                                                                                         
Get:18 http://in.archive.ubuntu.com/ubuntu zesty-updates/main amd64 liblouis-data all 3.0.0-3ubuntu0.2 [1,120 kB]                                                                                                               
Get:19 http://in.archive.ubuntu.com/ubuntu zesty-updates/main amd64 liblouis12 amd64 3.0.0-3ubuntu0.2 [70.5 kB]                                                                                                                 
Get:20 http://in.archive.ubuntu.com/ubuntu zesty-updates/universe amd64 python-magic all 1:5.29-3ubuntu0.1 [5,950 B]                                                                                                            
Fetched 83.3 MB in 2min 28s (561 kB/s)                                                                                                                                                                                          
E: Failed to fetch http://in.archive.ubuntu.com/ubuntu/pool/main/g/gnutls28/libgnutls30_3.5.6-4ubuntu4.2_amd64.deb  Hash Sum mismatch
   Hashes of expected file:
    - SHA256:fceab1e048594263284c98b3279204b534115bcd7b25622df9d2543e00f9f105
    - SHA1:1e7cfbb3d428f4c075bfe6c35bdfd06776a310db [weak]
    - MD5Sum:a44332c6ae1d30f09a66206213a51e0c [weak]
    - Filesize:627362 [weak]
   Hashes of received file:
    - SHA256:ff024dbd9091b949bdfcea6432528284302f657084cc609726a6c7bd2ea23244
    - SHA1:5e4c27473e7b9de5f6db95fe98e349255ec5586c [weak]
    - MD5Sum:1f1b6763a00c27650def3a06cc6e4335 [weak]
    - Filesize:627362 [weak]
   Last modification reported: Thu, 17 Aug 2017 23:20:30 +0000
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

---

### Post by su:bhatta on 2017-09-10
This is solved after todays update.

Marking it so.

---

