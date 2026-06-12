---
title: "Can't install any programs"
date: 2015-02-19
forum: General Help
---

### Post by o-andrew on 2015-02-19
Hi, I'm trying to install a torrent client on my Ubuntu server Trusty tarh. but I keep getting the same error what ever I try to install.

any help would be appreciated as I have very little knowledge. (noob) Thanks in advance. 

Here is everything from putty.

```
  ubuntu@192.168.0.11's password:
Welcome to Ubuntu 14.04.1 LTS (GNU/Linux 3.13.0-39-generic x86_64)


 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)


  System information as of Thu Feb 19 22:34:58 GMT 2015


  System load:  0.04               Processes:           128
  Usage of /:   29.5% of 14.98GB   Users logged in:     0
  Memory usage: 9%                 IP address for eth0: 192.168.0.11
  Swap usage:   0%


  Graph this data and manage this system at:
    [https://landscape.canonical.com/](https://landscape.canonical.com/)
Last login: Thu Feb 19 22:34:58 2015 from 192.168.0.13


ubuntu@ubuntuserver:~$ sudo apt-get update
[sudo] password for ubuntu:
Hit [http://plex.r.worldssl.net](http://plex.r.worldssl.net) lucid InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease
Hit [http://plex.r.worldssl.net](http://plex.r.worldssl.net) lucid/main amd64 Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates InRelease
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg [933 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg
Hit [http://plex.r.worldssl.net](http://plex.r.worldssl.net) lucid/main i386 Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports InRelease
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release [62.0 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-updates Release
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources [70.3 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty-backports Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main amd64 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main Sources
Ign [http://plex.r.worldssl.net](http://plex.r.worldssl.net) lucid/main Translation-en_GB
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted Sources
Ign [http://plex.r.worldssl.net](http://plex.r.worldssl.net) lucid/main Translation-en
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources [2,061 B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources [17.9 kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/multiverse Sources
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources [1,896 B]
Get:7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/main amd64 Packages [1,350 kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages [214 kB]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages [8,87                                                                                        5 B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages [87.3                                                                                         kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages [3,4                                                                                        58 B]
Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages [205 kB]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages [8,84                                                                                        6 B]
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages [87.3 k                                                                                        B]
Get:15 [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages [3,62                                                                                        4 B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en
Get:16 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/restricted amd64 Packages [13.0 kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en
Get:17 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) trusty/universe amd64 Packages [5,859 kB]
Get:18 [http://www.plexapp.com](http://www.plexapp.com) lucid InRelease
67% [7 Packages bzip2 0 B] [18 InRelease gpgv 25.9 kB] [17 Packages 838 kB/5,85S                                                                                        plitting up /var/lib/apt/lists/partial/www.plexapp.com_repo_dists_lucid_InReleas                                                                                        Ign [http://www.plexapp.com](http://www.plexapp.com) lucid InRelease
E: GPG error: [http://www.plexapp.com](http://www.plexapp.com) lucid InRelease: Clearsigned file isn't val                                                                                        id, got 'NODATA' (does the network require authentication?)
ubuntu@ubuntuserver:~$ sudo apt-get install deluged
Reading package lists... Done
Building dependency tree
Reading state information... Done
W: Duplicate sources.list entry [http://ppa.launchpad.net/jcfp/ppa/ubuntu/](http://ppa.launchpad.net/jcfp/ppa/ubuntu/) trusty                                                                                        /main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_jcfp_ppa_ubuntu_dists                                                                                        _trusty_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://ppa.launchpad.net/jcfp/ppa/ubuntu/](http://ppa.launchpad.net/jcfp/ppa/ubuntu/) trusty                                                                                        /main amd64 Packages (/var/lib/apt/lists/ppa.launchpad.net_jcfp_ppa_ubuntu_dists                                                                                        _trusty_main_binary-amd64_Packages)
W: Duplicate sources.list entry [http://ppa.launchpad.net/jcfp/ppa/ubuntu/](http://ppa.launchpad.net/jcfp/ppa/ubuntu/) trusty                                                                                        /main i386 Packages (/var/lib/apt/lists/ppa.launchpad.net_jcfp_ppa_ubuntu_dists_                                                                                        trusty_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://ppa.launchpad.net/jcfp/ppa/ubuntu/](http://ppa.launchpad.net/jcfp/ppa/ubuntu/) trusty                                                                                        /main i386 Packages (/var/lib/apt/lists/ppa.launchpad.net_jcfp_ppa_ubuntu_dists_                                                                                        trusty_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Unable to locate package deluged
ubuntu@ubuntuserver:~$


```

---

### Post by QIII on 2015-02-19
Hello!

You have Lucid repos in your sources list and so many PPAs I'm not surprised you are having issues.

I would remove the Lucid repos and all of the PPAs, including the duplicate entries, to see if you can get a clean update and dist-upgrade.  Then check to see if the PPAs contain packages for your current release.  If they do, add them back one by one and attempt to update.

And I think the package you are looking for is deluge, not deluged.

---

### Post by o-andrew on 2015-02-20
> **QIII said:**
> Hello!

You have Lucid repos in your sources list and so many PPAs I'm not surprised you are having issues.

I would remove the Lucid repos and all of the PPAs, including the duplicate entries, to see if you can get a clean update and dist-upgrade.  Then check to see if the PPAs contain packages for your current release.  If they do, add them back one by one and attempt to update.

And I think the package you are looking for is deluge, not deluged.

Hi thanks for that  i have got it going now.

Cheers.

---

