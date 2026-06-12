---
title: "Samba dependency problems"
date: 2018-09-07
forum: General Help
---

### Post by gus_zernial on 2018-09-07
I have Kubuntu 18.04 on AMD64, including latest updates. Cannot install Samba, see below, dependency/version problems. Appreciate recommendations to diagnose/fix.   Thx, Gus

sudo aptitude install samba
The following NEW packages will be installed:
  attr{ab} libcephfs2{a} libldb1{a} python-crypto{a} python-dnspython{a} python-ldb{a} python-samba{a} python-tdb{a} samba samba-common-bin{a} 
  samba-dsdb-modules{ab} samba-libs{ab} samba-vfs-modules{a} tdb-tools{a} 
0 packages upgraded, 14 newly installed, 0 to remove and 0 not upgraded.
Need to get 10.0 MB of archives. After unpacking 57.0 MB will be used.
The following packages have unmet dependencies:
 samba-dsdb-modules : Depends: libwbclient0 (= 2:4.7.6+dfsg~ubuntu-0ubuntu2.2) but 2:4.8.5+dfsg-1 is installed
 attr : Depends: libattr1 (= 1:2.4.47-2build1) but 1:2.4.47-2+b2 is installed
 samba-libs : Depends: libwbclient0 (= 2:4.7.6+dfsg~ubuntu-0ubuntu2.2) but 2:4.8.5+dfsg-1 is installed
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     attr [Not Installed]                               
2)     python-samba [Not Installed]                       
3)     samba [Not Installed]                              
4)     samba-common-bin [Not Installed]                   
5)     samba-dsdb-modules [Not Installed]                 
6)     samba-libs [Not Installed]                         
7)     samba-vfs-modules [Not Installed]                  

     Leave the following dependencies unresolved:         
8)     samba recommends attr                              
9)     samba recommends samba-dsdb-modules                



Accept this solution? [Y/n/q/?] 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.

---

### Post by wildmanne39 on 2018-09-07
*Thread moved to **General Help for a more appropriate fit**.*

---

