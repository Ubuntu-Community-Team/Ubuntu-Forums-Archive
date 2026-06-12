---
title: "anybody help me how to solve this"
date: 2013-01-09
forum: General Help
---

### Post by Mohan1289 on 2013-01-09
i tried 
```
sudo apt-get upgrade
```but all i got is this

```

Err http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ precise/main wine1.5 i386 1.5.20-0ubuntu2
  403  Forbidden: category denied
Err http://www.duinsoft.nl/pkg/ debs/all update-sun-jre all 1.2.8   
  403  Forbidden: category denied
Get:1 http://archive.ubuntu.com/ubuntu/ precise-updates/main man-db i386 2.6.1-2ubuntu1 [742 kB]
Err http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ precise/main wine1.5-i386 i386 1.5.20-0ubuntu2
  403  Forbidden: category denied
Err http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ precise/main wine i386 1.5.20-0ubuntu2
  403  Forbidden: category denied
Fetched 742 kB in 4s (181 kB/s) 
Failed to fetch http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.5/wine1.5_1.5.20-0ubuntu2_i386.deb  403  Forbidden: category denied
Failed to fetch http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.5/wine1.5-i386_1.5.20-0ubuntu2_i386.deb  403  Forbidden: category denied
Failed to fetch http://www.duinsoft.nl/pkg/pool/all/update-sun-jre_1.2.8_all.deb  403  Forbidden: category denied
Failed to fetch http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/pool/main/w/wine1.5/wine_1.5.20-0ubuntu2_i386.deb  403  Forbidden: category denied
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```can anyone tell me how to solve this?

---

### Post by sanderj on 2013-01-09
Did you first do a "sudo apt-get update"?

---

### Post by Mohan1289 on 2013-01-09
> **sanderj said:**
> Did you first do a "sudo apt-get update"?

YES i did but there too are some errors.. like this


```

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/main/source/Sources  403  Forbidden: category denied

W: Failed to fetch http://extras.ubuntu.com/ubuntu/dists/precise/main/binary-i386/Packages  403  Forbidden: category denied

W: Failed to fetch http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/precise/main/source/Sources  403  Forbidden: category denied

W: Failed to fetch http://www.duinsoft.nl/pkg/dists/debs/all/binary-i386/Packages  403  Forbidden: category denied

W: Failed to fetch http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/precise/main/binary-i386/Packages  403  Forbidden: category denied

E: Some index files failed to download. They have been ignored, or old ones used instead.


```

---

### Post by sanderj on 2013-01-09
Did you Google '403  Forbidden: category denied' ?

---

### Post by Mohan1289 on 2013-01-09
> **sanderj said:**
> Did you Google '403  Forbidden: category denied' ?

No i didn't i think it may be because of company's firewall. they block some sites i dono why but  i can't even open manpages.ubuntu

---

### Post by ibjsb4 on 2013-01-09
Are you running 32 or 64 bit?  In terminal:

```
uname -m
```

---

### Post by ibjsb4 on 2013-01-09
First, go here and uncheck "Source code".  

[https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Ubuntu_Software_Tab)

That will take care of
//extras.ubuntu.com/ubuntu/dists/precise/main/source/Sources and //ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/precise/main/source/Sources.

Why are you using the "wine ppa"?  The stable version is in the software center.  Consider removing it.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

Duinsoft Webdesign is not in english, don't know what to do with it other than uncheck it until you find a fix.

//www.duinsoft.nl/pkg/dists/debs/all/binary-i386/Packages

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

Run another update after you get that done.

---

### Post by Mohan1289 on 2013-01-10
> **ibjsb4 said:**
> Are you running 32 or 64 bit?  In terminal:

```
uname -m
```

```
uname -m
```
i686

but when i type 
```
uname -a
```
it gave me
```
Linux ubuntu 3.2.0-34-generic-pae #53-Ubuntu SMP Thu Nov 15 11:11:12 UTC 2012 i686 i686 i386 GNU/Linux
```

---

### Post by ibjsb4 on 2013-01-10
i686 i386 = 32 bit

---

### Post by Mohan1289 on 2013-01-11
> **ibjsb4 said:**
> i686 i386 = 32 bit

Thanks all.. i accidentally cracked my system

i typed
```

sudo apt-get remove wine*

```and then all the packages one by one had been deleted... i reinstalled the OS :guitar:](*,)](*,):-({|=):P:cool::twisted::twisted:

---

