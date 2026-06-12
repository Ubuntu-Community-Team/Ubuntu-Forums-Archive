---
title: "Authenticating Error"
date: 2008-06-27
forum: General Help
---

### Post by elbow rub on 2008-06-27
I'm Being prompted to install 2 updates, partial update it says. When I choose it, I end up with an authenticating error, saying to try again later. Having done that since 11 hours ago, I still get the error. 

I'm attaching two files, the updates and the error.

Thanks in advance

elbow rub

---

### Post by prshah on 2008-06-27
> **elbow rub said:**
> I'm Being prompted to install 2 updates, partial update it says. When I choose it, I end up with an authenticating error, 
Open a terminal (Applications-Accessories-Terminal), then give the following commands and post the output here. ```

sudo apt-get update && sudo apt-get upgrade

```

If all goes well, the first command will update your repository information (links to where software is available from) and then, if successful, will upgrade all packages on your system that need upgrading. If the first command is not successful, the second will not execute (hence the "&&"), and the error messages that the first command gives will help in diagnosis.

---

### Post by elbow rub on 2008-06-27
>  sudo apt-get update && sudo apt-get upgrade
[sudo] password for gianluca: 
Get:1 [http://ftp.debian.org](http://ftp.debian.org) etch Release.gpg [378B]
Ign [http://ftp.debian.org](http://ftp.debian.org) etch/main Translation-en_US                          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg                      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US          
Get:2 [http://ftp.debian.org](http://ftp.debian.org) etch Release [58.2kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release.gpg                           
Ign [http://ftp.debian.org](http://ftp.debian.org) etch Release                                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Translation-en_US         
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://ftp.debian.org](http://ftp.debian.org) etch/main Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release              
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates/multiverse Sources
Fetched 379B in 1s (372B/s)
Reading package lists... Done
W: GPG error: [http://ftp.debian.org](http://ftp.debian.org) etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A70DAF536070D3A1 NO_PUBKEY B5D0C804ADB11277
W: You may want to run apt-get update to correct these problems
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  initramfs-tools initscripts
The following packages will be upgraded:
  libavc1394-0 sysv-rc
2 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 76.9kB of archives.
After this operation, 36.9kB disk space will be freed.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  sysv-rc libavc1394-0
Install these packages without verification [y/N]? y
Get:1 [http://ftp.debian.org](http://ftp.debian.org) etch/main sysv-rc 2.86.ds1-38 [56.1kB]
Get:2 [http://ftp.debian.org](http://ftp.debian.org) etch/main libavc1394-0 0.5.3-1+b1 [20.7kB]
Fetched 76.9kB in 0s (211kB/s)    
(Reading database ... 113748 files and directories currently installed.)
Preparing to replace sysv-rc 2.86.ds1-14.1ubuntu45 (using .../sysv-rc_2.86.ds1-38_all.deb) ...
Unpacking replacement sysv-rc ...
Setting up sysv-rc (2.86.ds1-38) ...
(Reading database ... 113748 files and directories currently installed.)
Preparing to replace libavc1394-0 0.5.3-1build1 (using .../libavc1394-0_0.5.3-1+b1_i386.deb) ...
Unpacking replacement libavc1394-0 ...
Setting up libavc1394-0 (0.5.3-1+b1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
gianluca@gianluca-desktop:~$ 

It seemed to have worked, I just posted to be sure. I ran the sudo apt-get update, I just assumed it took care of the sudo apt-get upgrade.

Thank you very much

elbow rub

---

