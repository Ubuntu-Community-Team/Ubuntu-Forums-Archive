---
title: "apt errors while updating repositories"
date: 2019-08-04
forum: General Help
---

### Post by icegood on 2019-08-04
Today i obtained strange errors from repositories from ubuntu:

apt-get update:
```

Ign:1 http://ddebs.ubuntu.com xenial InRelease
Ign:2 http://ddebs.ubuntu.com xenial-updates InRelease 
Ign:3 http://ddebs.ubuntu.com xenial-security InRelease
Ign:4 http://ddebs.ubuntu.com xenial-proposed InRelease
Hit:5 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Hit:6 http://ddebs.ubuntu.com xenial Release                            
Hit:7 http://ddebs.ubuntu.com xenial-updates Release                    
Hit:8 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease      
Ign:9 http://ddebs.ubuntu.com xenial-security Release
Hit:10 http://ddebs.ubuntu.com xenial-proposed Release                  
Get:11 http://ddebs.ubuntu.com xenial Release.gpg [819 B]               
Hit:12 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease   
Get:13 http://ddebs.ubuntu.com xenial-updates Release.gpg [819 B]
Ign:14 http://ddebs.ubuntu.com xenial-security/main amd64 Packages          
Ign:15 http://ddebs.ubuntu.com xenial-security/main i386 Packages           
Hit:16 http://us.archive.ubuntu.com/ubuntu xenial-security InRelease        
Ign:11 http://ddebs.ubuntu.com xenial Release.gpg                           
Ign:17 http://ddebs.ubuntu.com xenial-security/main all Packages
Ign:18 http://ddebs.ubuntu.com xenial-security/main Translation-en_US
Ign:19 http://ddebs.ubuntu.com xenial-security/main Translation-en
Ign:20 http://ddebs.ubuntu.com xenial-security/main amd64 DEP-11 Metadata
Ign:13 http://ddebs.ubuntu.com xenial-updates Release.gpg
Ign:21 http://ddebs.ubuntu.com xenial-security/main DEP-11 64x64 Icons
Ign:22 http://ddebs.ubuntu.com xenial-security/restricted amd64 Packages
Ign:23 http://ddebs.ubuntu.com xenial-security/restricted i386 Packages
Ign:24 http://ddebs.ubuntu.com xenial-security/restricted all Packages
Ign:25 http://ddebs.ubuntu.com xenial-security/restricted Translation-en_US
Ign:26 http://ddebs.ubuntu.com xenial-security/restricted Translation-en
Ign:27 http://ddebs.ubuntu.com xenial-security/restricted amd64 DEP-11 Metadata
Ign:28 http://ddebs.ubuntu.com xenial-security/restricted DEP-11 64x64 Icons
Ign:29 http://ddebs.ubuntu.com xenial-security/universe amd64 Packages
Ign:30 http://ddebs.ubuntu.com xenial-security/universe i386 Packages
Ign:31 http://ddebs.ubuntu.com xenial-security/universe all Packages
Ign:32 http://ddebs.ubuntu.com xenial-security/universe Translation-en_US
Ign:33 http://ddebs.ubuntu.com xenial-security/universe Translation-en
Ign:34 http://ddebs.ubuntu.com xenial-security/universe amd64 DEP-11 Metadata
Ign:35 http://ddebs.ubuntu.com xenial-security/universe DEP-11 64x64 Icons
Ign:36 http://ddebs.ubuntu.com xenial-security/multiverse amd64 Packages
Ign:37 http://ddebs.ubuntu.com xenial-security/multiverse i386 Packages
Ign:38 http://ddebs.ubuntu.com xenial-security/multiverse all Packages
Ign:39 http://ddebs.ubuntu.com xenial-security/multiverse Translation-en_US
Ign:40 http://ddebs.ubuntu.com xenial-security/multiverse Translation-en
Ign:41 http://ddebs.ubuntu.com xenial-security/multiverse amd64 DEP-11 Metadata
Ign:42 http://ddebs.ubuntu.com xenial-security/multiverse DEP-11 64x64 Icons
Get:43 http://ddebs.ubuntu.com xenial-proposed Release.gpg [819 B]
Ign:14 http://ddebs.ubuntu.com xenial-security/main amd64 Packages
Ign:15 http://ddebs.ubuntu.com xenial-security/main i386 Packages
Ign:43 http://ddebs.ubuntu.com xenial-proposed Release.gpg
Ign:17 http://ddebs.ubuntu.com xenial-security/main all Packages
Ign:18 http://ddebs.ubuntu.com xenial-security/main Translation-en_US
Ign:19 http://ddebs.ubuntu.com xenial-security/main Translation-en
Ign:20 http://ddebs.ubuntu.com xenial-security/main amd64 DEP-11 Metadata
Ign:21 http://ddebs.ubuntu.com xenial-security/main DEP-11 64x64 Icons
Ign:22 http://ddebs.ubuntu.com xenial-security/restricted amd64 Packages
Ign:23 http://ddebs.ubuntu.com xenial-security/restricted i386 Packages
Ign:24 http://ddebs.ubuntu.com xenial-security/restricted all Packages
Ign:25 http://ddebs.ubuntu.com xenial-security/restricted Translation-en_US
Ign:26 http://ddebs.ubuntu.com xenial-security/restricted Translation-en
Ign:27 http://ddebs.ubuntu.com xenial-security/restricted amd64 DEP-11 Metadata
Ign:28 http://ddebs.ubuntu.com xenial-security/restricted DEP-11 64x64 Icons
Ign:29 http://ddebs.ubuntu.com xenial-security/universe amd64 Packages
Ign:30 http://ddebs.ubuntu.com xenial-security/universe i386 Packages
Ign:31 http://ddebs.ubuntu.com xenial-security/universe all Packages
Ign:32 http://ddebs.ubuntu.com xenial-security/universe Translation-en_US
Ign:33 http://ddebs.ubuntu.com xenial-security/universe Translation-en
Ign:34 http://ddebs.ubuntu.com xenial-security/universe amd64 DEP-11 Metadata
Ign:35 http://ddebs.ubuntu.com xenial-security/universe DEP-11 64x64 Icons
Ign:36 http://ddebs.ubuntu.com xenial-security/multiverse amd64 Packages
Ign:37 http://ddebs.ubuntu.com xenial-security/multiverse i386 Packages
Ign:38 http://ddebs.ubuntu.com xenial-security/multiverse all Packages
Ign:39 http://ddebs.ubuntu.com xenial-security/multiverse Translation-en_US
Ign:40 http://ddebs.ubuntu.com xenial-security/multiverse Translation-en
Ign:41 http://ddebs.ubuntu.com xenial-security/multiverse amd64 DEP-11 Metadata
Ign:42 http://ddebs.ubuntu.com xenial-security/multiverse DEP-11 64x64 Icons
Ign:14 http://ddebs.ubuntu.com xenial-security/main amd64 Packages
Ign:15 http://ddebs.ubuntu.com xenial-security/main i386 Packages
Ign:17 http://ddebs.ubuntu.com xenial-security/main all Packages
Ign:18 http://ddebs.ubuntu.com xenial-security/main Translation-en_US
Ign:19 http://ddebs.ubuntu.com xenial-security/main Translation-en
Ign:20 http://ddebs.ubuntu.com xenial-security/main amd64 DEP-11 Metadata
Ign:21 http://ddebs.ubuntu.com xenial-security/main DEP-11 64x64 Icons
Ign:22 http://ddebs.ubuntu.com xenial-security/restricted amd64 Packages
Ign:23 http://ddebs.ubuntu.com xenial-security/restricted i386 Packages
Ign:24 http://ddebs.ubuntu.com xenial-security/restricted all Packages
Ign:25 http://ddebs.ubuntu.com xenial-security/restricted Translation-en_US
Ign:26 http://ddebs.ubuntu.com xenial-security/restricted Translation-en
Ign:27 http://ddebs.ubuntu.com xenial-security/restricted amd64 DEP-11 Metadata
Ign:28 http://ddebs.ubuntu.com xenial-security/restricted DEP-11 64x64 Icons
Ign:29 http://ddebs.ubuntu.com xenial-security/universe amd64 Packages
Ign:30 http://ddebs.ubuntu.com xenial-security/universe i386 Packages
Ign:31 http://ddebs.ubuntu.com xenial-security/universe all Packages
Ign:32 http://ddebs.ubuntu.com xenial-security/universe Translation-en_US
Ign:33 http://ddebs.ubuntu.com xenial-security/universe Translation-en
Ign:34 http://ddebs.ubuntu.com xenial-security/universe amd64 DEP-11 Metadata
Ign:35 http://ddebs.ubuntu.com xenial-security/universe DEP-11 64x64 Icons
Ign:36 http://ddebs.ubuntu.com xenial-security/multiverse amd64 Packages
Ign:37 http://ddebs.ubuntu.com xenial-security/multiverse i386 Packages
Ign:38 http://ddebs.ubuntu.com xenial-security/multiverse all Packages
Ign:39 http://ddebs.ubuntu.com xenial-security/multiverse Translation-en_US
Ign:40 http://ddebs.ubuntu.com xenial-security/multiverse Translation-en
Ign:41 http://ddebs.ubuntu.com xenial-security/multiverse amd64 DEP-11 Metadata
Ign:42 http://ddebs.ubuntu.com xenial-security/multiverse DEP-11 64x64 Icons
Ign:14 http://ddebs.ubuntu.com xenial-security/main amd64 Packages
Ign:15 http://ddebs.ubuntu.com xenial-security/main i386 Packages
Ign:17 http://ddebs.ubuntu.com xenial-security/main all Packages
Ign:18 http://ddebs.ubuntu.com xenial-security/main Translation-en_US
Ign:19 http://ddebs.ubuntu.com xenial-security/main Translation-en
Ign:20 http://ddebs.ubuntu.com xenial-security/main amd64 DEP-11 Metadata
Ign:21 http://ddebs.ubuntu.com xenial-security/main DEP-11 64x64 Icons
Ign:22 http://ddebs.ubuntu.com xenial-security/restricted amd64 Packages
Ign:23 http://ddebs.ubuntu.com xenial-security/restricted i386 Packages
Ign:24 http://ddebs.ubuntu.com xenial-security/restricted all Packages
Ign:25 http://ddebs.ubuntu.com xenial-security/restricted Translation-en_US
Ign:26 http://ddebs.ubuntu.com xenial-security/restricted Translation-en
Ign:27 http://ddebs.ubuntu.com xenial-security/restricted amd64 DEP-11 Metadata
Ign:28 http://ddebs.ubuntu.com xenial-security/restricted DEP-11 64x64 Icons
Ign:29 http://ddebs.ubuntu.com xenial-security/universe amd64 Packages
Ign:30 http://ddebs.ubuntu.com xenial-security/universe i386 Packages
Ign:31 http://ddebs.ubuntu.com xenial-security/universe all Packages
Ign:32 http://ddebs.ubuntu.com xenial-security/universe Translation-en_US
Ign:33 http://ddebs.ubuntu.com xenial-security/universe Translation-en
Ign:34 http://ddebs.ubuntu.com xenial-security/universe amd64 DEP-11 Metadata
Ign:35 http://ddebs.ubuntu.com xenial-security/universe DEP-11 64x64 Icons
Ign:36 http://ddebs.ubuntu.com xenial-security/multiverse amd64 Packages
Ign:37 http://ddebs.ubuntu.com xenial-security/multiverse i386 Packages
Ign:38 http://ddebs.ubuntu.com xenial-security/multiverse all Packages
Ign:39 http://ddebs.ubuntu.com xenial-security/multiverse Translation-en_US
Ign:40 http://ddebs.ubuntu.com xenial-security/multiverse Translation-en
Ign:41 http://ddebs.ubuntu.com xenial-security/multiverse amd64 DEP-11 Metadata
Ign:42 http://ddebs.ubuntu.com xenial-security/multiverse DEP-11 64x64 Icons
Ign:14 http://ddebs.ubuntu.com xenial-security/main amd64 Packages
Ign:15 http://ddebs.ubuntu.com xenial-security/main i386 Packages
Ign:17 http://ddebs.ubuntu.com xenial-security/main all Packages
Ign:18 http://ddebs.ubuntu.com xenial-security/main Translation-en_US
Ign:19 http://ddebs.ubuntu.com xenial-security/main Translation-en
Ign:20 http://ddebs.ubuntu.com xenial-security/main amd64 DEP-11 Metadata
Ign:21 http://ddebs.ubuntu.com xenial-security/main DEP-11 64x64 Icons
Ign:22 http://ddebs.ubuntu.com xenial-security/restricted amd64 Packages
Ign:23 http://ddebs.ubuntu.com xenial-security/restricted i386 Packages
Ign:24 http://ddebs.ubuntu.com xenial-security/restricted all Packages
Ign:25 http://ddebs.ubuntu.com xenial-security/restricted Translation-en_US
Ign:26 http://ddebs.ubuntu.com xenial-security/restricted Translation-en
Ign:27 http://ddebs.ubuntu.com xenial-security/restricted amd64 DEP-11 Metadata
Ign:28 http://ddebs.ubuntu.com xenial-security/restricted DEP-11 64x64 Icons
Ign:29 http://ddebs.ubuntu.com xenial-security/universe amd64 Packages
Ign:30 http://ddebs.ubuntu.com xenial-security/universe i386 Packages
Ign:31 http://ddebs.ubuntu.com xenial-security/universe all Packages
Ign:32 http://ddebs.ubuntu.com xenial-security/universe Translation-en_US
Ign:33 http://ddebs.ubuntu.com xenial-security/universe Translation-en
Ign:34 http://ddebs.ubuntu.com xenial-security/universe amd64 DEP-11 Metadata
Ign:35 http://ddebs.ubuntu.com xenial-security/universe DEP-11 64x64 Icons
Ign:36 http://ddebs.ubuntu.com xenial-security/multiverse amd64 Packages
Ign:37 http://ddebs.ubuntu.com xenial-security/multiverse i386 Packages
Ign:38 http://ddebs.ubuntu.com xenial-security/multiverse all Packages
Ign:39 http://ddebs.ubuntu.com xenial-security/multiverse Translation-en_US
Ign:40 http://ddebs.ubuntu.com xenial-security/multiverse Translation-en
Ign:41 http://ddebs.ubuntu.com xenial-security/multiverse amd64 DEP-11 Metadata
Ign:42 http://ddebs.ubuntu.com xenial-security/multiverse DEP-11 64x64 Icons
Err:14 http://ddebs.ubuntu.com xenial-security/main amd64 Packages
  404  Not Found
Ign:15 http://ddebs.ubuntu.com xenial-security/main i386 Packages
Ign:17 http://ddebs.ubuntu.com xenial-security/main all Packages
Ign:18 http://ddebs.ubuntu.com xenial-security/main Translation-en_US
Ign:19 http://ddebs.ubuntu.com xenial-security/main Translation-en
Ign:20 http://ddebs.ubuntu.com xenial-security/main amd64 DEP-11 Metadata
Ign:21 http://ddebs.ubuntu.com xenial-security/main DEP-11 64x64 Icons
Ign:22 http://ddebs.ubuntu.com xenial-security/restricted amd64 Packages
Ign:23 http://ddebs.ubuntu.com xenial-security/restricted i386 Packages
Ign:24 http://ddebs.ubuntu.com xenial-security/restricted all Packages
Ign:25 http://ddebs.ubuntu.com xenial-security/restricted Translation-en_US
Fetched 2 457 B in 7s (341 B/s)
Reading package lists... Done
W: The repository 'http://ddebs.ubuntu.com xenial-security Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: http://ddebs.ubuntu.com xenial Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C8CAB6595FDFF622
W: The repository 'http://ddebs.ubuntu.com xenial Release' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: http://ddebs.ubuntu.com xenial-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C8CAB6595FDFF622
W: The repository 'http://ddebs.ubuntu.com xenial-updates Release' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: http://ddebs.ubuntu.com xenial-proposed Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C8CAB6595FDFF622
W: The repository 'http://ddebs.ubuntu.com xenial-proposed Release' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch http://ddebs.ubuntu.com/dists/xenial-security/main/binary-amd64/Packages  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.

```


my repositories are:
grep -nrE "^deb"
```
apt/sources.list:5:deb http://us.archive.ubuntu.com/ubuntu/ xenial main restricted
apt/sources.list:10:deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
apt/sources.list:16:deb http://us.archive.ubuntu.com/ubuntu/ xenial universe
apt/sources.list:18:deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
apt/sources.list:26:deb http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
apt/sources.list:28:deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
apt/sources.list:36:deb http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
apt/sources.list:46:deb http://us.archive.ubuntu.com/ubuntu/ xenial-security main restricted
apt/sources.list:48:deb http://us.archive.ubuntu.com/ubuntu/ xenial-security universe
apt/sources.list:50:deb http://us.archive.ubuntu.com/ubuntu/ xenial-security multiverse
apt/sources.list.d/ddebs.list:1:deb http://ddebs.ubuntu.com xenial main restricted universe multiverse
apt/sources.list.d/ddebs.list:2:deb http://ddebs.ubuntu.com xenial-updates main restricted universe multiverse
apt/sources.list.d/ddebs.list:3:deb http://ddebs.ubuntu.com xenial-security main restricted universe multiverse
apt/sources.list.d/ddebs.list:4:deb http://ddebs.ubuntu.com xenial-proposed main restricted universe multiverse
```

Who knows what's going on?

---

### Post by icegood on 2019-08-04
All i did is changed hostname (/etc/hostname and /etc/hosts) but i didn't found any information that it relates to smth bad...

---

### Post by oldos2er on 2019-08-04
The 404 errors are because there's no xenial-security folder at [http://ddebs.ubuntu.com/dists/](http://ddebs.ubuntu.com/dists/)

You can install the missing keys with ```
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys [KEY_ID]
``` where KEY_ID is the alphanumeric string shown after the 
NO_PUBKEY warning.

---

### Post by icegood on 2019-08-04
tnx. Very nice 100% answer.

---

