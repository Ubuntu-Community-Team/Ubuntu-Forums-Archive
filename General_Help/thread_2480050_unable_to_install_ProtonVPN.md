---
title: "unable to install ProtonVPN"
date: 2022-10-17
forum: General Help
---

### Post by scoobflight on 2022-10-17
I'm receiving a series of errors when attempting to install ProtonVPN -

terminal: wget [https://protonvpn.com/download/protonvpn-stable-release_1.0.1-1_all.deb](https://protonvpn.com/download/protonvpn-stable-release_1.0.1-1_all.deb)

result:
--2022-10-17 11:43:44--  [https://protonvpn.com/download/protonvpn-stable-release_1.0.1-1_all.deb](https://protonvpn.com/download/protonvpn-stable-release_1.0.1-1_all.deb)
Resolving protonvpn.com (protonvpn.com)... 185.159.159.140
Connecting to protonvpn.com (protonvpn.com)|185.159.159.140|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3264 (3.2K) [application/octet-stream]
Saving to: &#8216;protonvpn-stable-release_1.0.1-1_all.deb&#8217;
protonvpn-stable-r 100%[==============>]   3.19K  --.-KB/s    in 0s      
2022-10-17 11:43:45 (62.9 MB/s) - &#8216;protonvpn-stable-release_1.0.1-1_all.deb&#8217; saved [3264/3264]


terminal: sudo dpkg -i protonvpn-stable-release_1.0.1-1_all.deb

result:
dpkg: warning: downgrading protonvpn-stable-release from 1.0.3 to 1.0.1-1
(Reading database ... 181775 files and directories currently installed.)
Preparing to unpack protonvpn-stable-release_1.0.1-1_all.deb ...
Unpacking protonvpn-stable-release (1.0.1-1) over (1.0.3) ...
Setting up protonvpn-stable-release (1.0.1-1) ...
Installing new version of config file /etc/apt/sources.list.d/protonvpn-stable.list ...


terminal: sudo apt-get update

result:
Ign:1 [https://repo.protonvpn.com/debian](https://repo.protonvpn.com/debian) stable InRelease
Hit:2 [https://brave-browser-apt-release.s3.brave.com](https://brave-browser-apt-release.s3.brave.com) stable InRelease    
Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal InRelease                
Err:4 [https://repo.protonvpn.com/debian](https://repo.protonvpn.com/debian) stable Release                   
  Certificate verification failed: The certificate is NOT trusted. The certificate chain uses expired certificate.  Could not handshake: Error in the certificate verification. [IP: 172.67.196.250 443]
Hit:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates InRelease        
Hit:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-backports InRelease
Hit:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease
Reading package lists... Done
E: The repository 'https://repo.protonvpn.com/debian stable Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.


terminal: sudo apt-get install protonvpn

result:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package protonvpn



all assistance would be appreciated.

:: Dave

---

### Post by scoobflight on 2022-10-17
after various searches and multiple challengers was able to get install.  two things done:  changed location and different wifi and forced another system update and worked.

---

