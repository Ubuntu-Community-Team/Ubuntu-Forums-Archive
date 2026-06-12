---
title: "fuse(smb) and updatedb"
date: 2007-07-14
forum: General Help
---

### Post by yang on 2007-07-14
I just installed fusesmb on Feisty, and it seems to be working fine. However, I want to index the files on my network for fast searching, so I tried running updatedb. However:

```

$ fusesmb fusesmb/
$ ls fusesmb/
WORKGROUP
[.. works fine ..]
$ updatedb -v -U ~/fusesmb/
updatedb: fatal error: Could not access index path '/home/yang/fusesmb/': Permission denied
$ ll 'which fusesmb'
-rwxr-sr-x 1 root slocate 31260 2007-02-21 16:37 /usr/bin/slocate
$ sudo ls fusesmb/
ls: fusesmb/:Permission denied

```

Any help? Is this related to the permissions on updatedb? Thanks in advance.

ADDENDUM: I just tried using doodle, and that fails to crawl as well. It just exits immediately.

---

### Post by akarun on 2007-10-27
Hi,

I could solve the problem you had, but the problem doesn't end there..

The problem with that is, you need to allow other users to browse through the folder

```
sudo gedit /etc/fuse.conf
```

add line 

```
user_allow_other
```

Mount the fusesmb in the following manner:

 ```
fusesmb -o allow_root -o nonempty /home/akarun/network/

 sudo updatedb  -v -U ~/network/
```

Now, a database is built..

The actual problem starts here..
Updatedb doesn't actually go any further than the WORKGROUP NAMES
The following was the output of updatedb

```
/home/akarun/network
/home/akarun/network/AMITTUHOME
/home/akarun/network/AMITTUHOME/PC219851897729
/home/akarun/network/AMITTUHOME/PC219851897729/C$
/home/akarun/network/AMITTUHOME/PC219851897729/C$
/home/akarun/network/AMITTUHOME/PC219851897729/D$
/home/akarun/network/BLGROUP
/home/akarun/network/CHOOTH
/home/akarun/network/DHARM
/home/akarun/network/DOPALAB
/home/akarun/network/DSLG
/home/akarun/network/FREE
/home/akarun/network/GANGA
/home/akarun/network/HOME
/home/akarun/network/IIT MADRAS
/home/akarun/network/IIT
/home/akarun/network/IITM LAN
/home/akarun/network/IITM
/home/akarun/network/IITM_LAN
/home/akarun/network/IITMADRAS
/home/akarun/network/IRIMPANAM.INS
/home/akarun/network/JAM
/home/akarun/network/JAMUNA
/home/akarun/network/KURMESH
/home/akarun/network/LAN
/home/akarun/network/LAPPY
/home/akarun/network/MANDAK
/home/akarun/network/MARKETRX
/home/akarun/network/MEGHA
/home/akarun/network/MGMT
/home/akarun/network/MS
/home/akarun/network/MSHOME
/home/akarun/network/NUSSTU
/home/akarun/network/PCCELL
/home/akarun/network/RESOURCE
/home/akarun/network/ROOM
/home/akarun/network/SABAYONDOMAIN
/home/akarun/network/SADHU
/home/akarun/network/SI
/home/akarun/network/STUDENT
/home/akarun/network/SUHAS
/home/akarun/network/TAPTI
/home/akarun/network/TARAMANI
/home/akarun/network/TEST
/home/akarun/network/WIN
/home/akarun/network/WING4
/home/akarun/network/WING6
/home/akarun/network/WORKGROUP


```


Clearly the shares inside each WORKGROUP was not scanned..
Is there any workaround for this. 
With this I can't search for the files in the shares.

Thanks in advance!

Arun

---

