---
title: "Ubuntu 18.04 increase / partition size to include iscsi volume size"
date: 2020-10-13
forum: General Help
---

### Post by edisonch on 2020-10-13
Dear All,
I have 1 Ubuntu Server 18.04 that connects to another server SAN - using ISCSI. I have able to write to SAN from Ubuntu. I mount the iscsi drive in /etc/fstab and I can restart the Ubuntu and the iscsi drive is online.
Iscsi drive has 15 TB storage. Ubuntu server has only 931 GB Usable storage and it is filled up to 96% already. Ubuntu refuses to let me do any action that requires any usage of hard drive space.

How do I let Ubuntu 18.04 know that the space for space partition root ( / ) that I have more space than 931 GB ?

Thank you for your help

---

