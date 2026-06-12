---
title: "Silicon Empire instillation"
date: 2018-01-27
forum: General Help
---

### Post by Joe_Linux on 2018-01-27
I tried to install Silicon Empire (for bluray burning) [https://blog.hostonnet.com/how-to-install-silicon-empire-in-ubuntu](https://blog.hostonnet.com/how-to-install-silicon-empire-in-ubuntu)
```
joe@joe-X555LAB:~$ sudo add-apt-repository ppa:noobslab/apps
[sudo] password for joe: 
Sorry, try again.
[sudo] password for joe: 
 This PPA Contains Applications for Ubuntu/Linux Mint from different sources but debianized by [http://www.NoobsLab.com](http://www.NoobsLab.com)
 More info: [https://launchpad.net/~noobslab/+archive/ubuntu/apps](https://launchpad.net/~noobslab/+archive/ubuntu/apps)
Press [ENTER] to continue or ctrl-c to cancel adding it

gpg: keyring `/tmp/tmp9m8ngg6i/secring.gpg' created
gpg: keyring `/tmp/tmp9m8ngg6i/pubring.gpg' created
gpg: requesting key F59EAE4D from hkp server keyserver.ubuntu.com
gpg: /tmp/tmp9m8ngg6i/trustdb.gpg: trustdb created
gpg: key F59EAE4D: public key "Launchpad PPA for NoobsLab" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
joe@joe-X555LAB:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease                    
Hit:3 [http://ppa.launchpad.net/brandonsnider/cdrtools/ubuntu](http://ppa.launchpad.net/brandonsnider/cdrtools/ubuntu) xenial InRelease  
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]    
Hit:5 [http://ppa.launchpad.net/dhor/myway/ubuntu](http://ppa.launchpad.net/dhor/myway/ubuntu) xenial InRelease              
Get:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 DEP-11 Metadata [62.7 kB]
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]  
Get:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main DEP-11 64x64 Icons [66.2 kB]
Hit:9 [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) xenial InRelease          
Get:10 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe amd64 DEP-11 Metadata [51.4 kB]
Get:11 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe DEP-11 64x64 Icons [80.2 kB]
Get:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 DEP-11 Metadata [307 kB]
Hit:13 [http://ppa.launchpad.net/mkusb/ppa/ubuntu](http://ppa.launchpad.net/mkusb/ppa/ubuntu) xenial InRelease
Hit:14 [http://ppa.launchpad.net/noobslab/apps/ubuntu](http://ppa.launchpad.net/noobslab/apps/ubuntu) xenial InRelease          
Get:15 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main DEP-11 64x64 Icons [216 kB]
Get:16 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 DEP-11 Metadata [191 kB]
Get:17 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe DEP-11 64x64 Icons [257 kB]
Get:18 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/multiverse amd64 DEP-11 Metadata [5,892 B]
Get:19 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/main amd64 DEP-11 Metadata [3,328 B]
Get:20 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports/universe amd64 DEP-11 Metadata [4,712 B]
Fetched 1,552 kB in 3s (462 kB/s)                                             
Reading package lists... Done
joe@joe-X555LAB:~$ sudo apt-get install silicon-empire
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package silicon-empire
joe@joe-X555LAB:~$ 
```

Does anyone know where I might find this application ? Thank you

---

### Post by cruzer001 on 2018-01-27
You didn't take a very close look at what you were downloading.  Silicon-empire has been dropped from the PPA.

[https://launchpad.net/%7Enoobslab/+archive/ubuntu/apps/+index?field.series_filter=xenial](https://launchpad.net/%7Enoobslab/+archive/ubuntu/apps/+index?field.series_filter=xenial)

---

