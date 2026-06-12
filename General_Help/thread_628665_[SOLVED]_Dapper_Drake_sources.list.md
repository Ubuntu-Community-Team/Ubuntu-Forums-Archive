---
title: "[SOLVED] Dapper Drake sources.list ?"
date: 2007-12-01
forum: General Help
---

### Post by TidusBlade on 2007-12-01
Somehow I screwed up the original dapper drake sources.list file xD And I edited the backup :( 
So if anybody knows where I can find a default sources.list I would appreciate it if you share it :D
Thanks in advance!

---

### Post by overdrank on 2007-12-01
> **TidusBlade said:**
> Somehow I screwed up the original dapper drake sources.list file xD And I edited the backup :( 
So if anybody knows where I can find a default sources.list I would appreciate it if you share it :D
Thanks in advance!

Hi and you can look here
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)
good luck! :KS

---

### Post by TidusBlade on 2007-12-01
Thanks! Page seems very helpful :D

---

### Post by -grubby on 2007-12-01
just add this to your sources.list:

```
## sources.list
## General comments about the sources.list file
 deb http://archive.ubuntu.com/ubuntu dapper main restricted
 deb-src http://archive.ubuntu.com/ubuntu dapper main restricted
 
## Comment about the 'Update' repositories
## Comments about the role of the updates
 deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
 deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted
 
## Comment on the 'Universe' repositories
## Comment about the support limitations of Universe & Multiverse
## repositories as well as licence restrictions and update policies.
## Please satisfy yourself as to your rights to use the software.
# deb http://archive.ubuntu.com/ubuntu dapper universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu dapper universe multiverse

## Comment on the 'Backports' repository
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Comment about update and security update limitations
# deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
# deb-src http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse 
# deb http://security.ubuntu.com/ubuntu breezy-security main restricted
# deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted
```

and then run

```
sudo apt-get update
```

---

### Post by TidusBlade on 2007-12-01
Thanks for that aswell nathan :) 
Found some source-o-matic on that page, gonna try it out, but I just wanna get something working now :P

---

