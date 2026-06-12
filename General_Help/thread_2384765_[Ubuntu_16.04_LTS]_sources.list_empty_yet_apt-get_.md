---
title: "[Ubuntu 16.04 LTS] sources.list empty yet apt-get update provides a lot of responses."
date: 2018-02-11
forum: General Help
---

### Post by george.m2 on 2018-02-11
Dear users and staff/mods of ubuntu forums,

   I was wondering if anyone here could help me out with the sources.list problem being empty yet it still shows alot of ign and 404 errors.

Places I've checked are:-
1) /etc/apt/sources.list (empty)
2) /etc/apt/sources.list.d (alexlarsson-ubuntu-flatpak-xenial.list.save, cpug-devs-ubuntu-ppa-xenial.list.save, diesch-ubuntu-testing-xenial.list.save)
3) /usr/share/doc/apt/examples/sources.list (empty)

Below is what I get when I run apt-get update despite _sources.list_ being empty:-
```
Ign:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy InReleaseGet:2 [http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu](http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu) xenial InRelease [18.0 kB]
Ign:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates InRelease
Ign:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy Release                                             
Ign:2 [http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu](http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu) xenial InRelease                          
Ign:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates Release               
Ign:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/universe i386 Packages   
Ign:7 [http://ppa.launchpad.net/cpug-devs/ppa/ubuntu](http://ppa.launchpad.net/cpug-devs/ppa/ubuntu) xenial InRelease
Ign:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/universe all Packages    
Ign:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/universe Translation-en_US
Get:10 [http://ppa.launchpad.net/diesch/testing/ubuntu](http://ppa.launchpad.net/diesch/testing/ubuntu) xenial InRelease [17.5 kB]
Ign:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/universe Translation-en
Ign:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/universe i386 DEP-11 Metadata
Ign:10 [http://ppa.launchpad.net/diesch/testing/ubuntu](http://ppa.launchpad.net/diesch/testing/ubuntu) xenial InRelease         
Ign:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/universe DEP-11 64x64 Icons   
Ign:14 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/multiverse i386 Packages
Ign:15 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/multiverse all Packages
Ign:16 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/multiverse Translation-en_US
Ign:17 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/multiverse Translation-en
Ign:18 [http://ppa.launchpad.net/cpug-devs/ppa/ubuntu](http://ppa.launchpad.net/cpug-devs/ppa/ubuntu) xenial Release
Ign:19 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/multiverse i386 DEP-11 Metadata
Ign:20 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/multiverse DEP-11 64x64 Icons
Ign:21 [http://ppa.launchpad.net/cpug-devs/ppa/ubuntu](http://ppa.launchpad.net/cpug-devs/ppa/ubuntu) xenial/main i386 Packages
Ign:22 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/universe i386 Packages
Ign:23 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/universe all Packages
Ign:24 [http://ppa.launchpad.net/cpug-devs/ppa/ubuntu](http://ppa.launchpad.net/cpug-devs/ppa/ubuntu) xenial/main all Packages
Ign:25 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/universe Translation-en_US
Ign:26 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/universe Translation-en
Ign:27 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/universe i386 DEP-11 Metadata
Ign:28 [http://ppa.launchpad.net/cpug-devs/ppa/ubuntu](http://ppa.launchpad.net/cpug-devs/ppa/ubuntu) xenial/main Translation-en_US
Ign:29 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/universe DEP-11 64x64 Icons
Ign:30 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/multiverse i386 Packages
Ign:31 [http://ppa.launchpad.net/cpug-devs/ppa/ubuntu](http://ppa.launchpad.net/cpug-devs/ppa/ubuntu) xenial/main Translation-en
Ign:32 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/multiverse all Packages
Ign:33 [http://ppa.launchpad.net/cpug-devs/ppa/ubuntu](http://ppa.launchpad.net/cpug-devs/ppa/ubuntu) xenial/main i386 DEP-11 Metadata
Ign:34 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/multiverse Translation-en_US
Ign:35 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/multiverse Translation-en
Ign:36 [http://ppa.launchpad.net/cpug-devs/ppa/ubuntu](http://ppa.launchpad.net/cpug-devs/ppa/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:37 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/multiverse i386 DEP-11 Metadata
Ign:38 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/multiverse DEP-11 64x64 Icons
Ign:21 [http://ppa.launchpad.net/cpug-devs/ppa/ubuntu](http://ppa.launchpad.net/cpug-devs/ppa/ubuntu) xenial/main i386 Packages
Ign:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/universe i386 Packages
Ign:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/universe all Packages    
Ign:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/universe Translation-en_US
Ign:24 [http://ppa.launchpad.net/cpug-devs/ppa/ubuntu](http://ppa.launchpad.net/cpug-devs/ppa/ubuntu) xenial/main all Packages
Ign:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/universe Translation-en
Ign:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/universe i386 DEP-11 Metadata
Ign:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/universe DEP-11 64x64 Icons
Ign:14 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/multiverse i386 Packages
Ign:15 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/multiverse all Packages
Ign:16 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/multiverse Translation-en_US
Ign:17 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/multiverse Translation-en
Ign:19 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/multiverse i386 DEP-11 Metadata
Ign:20 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/multiverse DEP-11 64x64 Icons
Ign:28 [http://ppa.launchpad.net/cpug-devs/ppa/ubuntu](http://ppa.launchpad.net/cpug-devs/ppa/ubuntu) xenial/main Translation-en_US
Ign:22 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/universe i386 Packages
Ign:23 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/universe all Packages
Ign:25 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/universe Translation-en_US
Ign:31 [http://ppa.launchpad.net/cpug-devs/ppa/ubuntu](http://ppa.launchpad.net/cpug-devs/ppa/ubuntu) xenial/main Translation-en
Ign:26 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/universe Translation-en
Ign:27 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/universe i386 DEP-11 Metadata
Ign:29 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/universe DEP-11 64x64 Icons
Ign:30 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/multiverse i386 Packages
Ign:33 [http://ppa.launchpad.net/cpug-devs/ppa/ubuntu](http://ppa.launchpad.net/cpug-devs/ppa/ubuntu) xenial/main i386 DEP-11 Metadata
Ign:32 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/multiverse all Packages
Ign:36 [http://ppa.launchpad.net/cpug-devs/ppa/ubuntu](http://ppa.launchpad.net/cpug-devs/ppa/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:34 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/multiverse Translation-en_US
Ign:35 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/multiverse Translation-en
Ign:21 [http://ppa.launchpad.net/cpug-devs/ppa/ubuntu](http://ppa.launchpad.net/cpug-devs/ppa/ubuntu) xenial/main i386 Packages
Ign:37 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/multiverse i386 DEP-11 Metadata
Ign:38 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/multiverse DEP-11 64x64 Icons
Ign:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/universe i386 Packages
Ign:24 [http://ppa.launchpad.net/cpug-devs/ppa/ubuntu](http://ppa.launchpad.net/cpug-devs/ppa/ubuntu) xenial/main all Packages
Ign:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/universe all Packages
Ign:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/universe Translation-en_US
Ign:28 [http://ppa.launchpad.net/cpug-devs/ppa/ubuntu](http://ppa.launchpad.net/cpug-devs/ppa/ubuntu) xenial/main Translation-en_US
Ign:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/universe Translation-en
Ign:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/universe i386 DEP-11 Metadata
Ign:31 [http://ppa.launchpad.net/cpug-devs/ppa/ubuntu](http://ppa.launchpad.net/cpug-devs/ppa/ubuntu) xenial/main Translation-en
Ign:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/universe DEP-11 64x64 Icons
Ign:14 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/multiverse i386 Packages
Ign:15 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/multiverse all Packages
Ign:33 [http://ppa.launchpad.net/cpug-devs/ppa/ubuntu](http://ppa.launchpad.net/cpug-devs/ppa/ubuntu) xenial/main i386 DEP-11 Metadata
Ign:16 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/multiverse Translation-en_US
Ign:17 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/multiverse Translation-en
Ign:36 [http://ppa.launchpad.net/cpug-devs/ppa/ubuntu](http://ppa.launchpad.net/cpug-devs/ppa/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:19 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/multiverse i386 DEP-11 Metadata
Ign:20 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/multiverse DEP-11 64x64 Icons
Ign:22 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/universe i386 Packages
Ign:21 [http://ppa.launchpad.net/cpug-devs/ppa/ubuntu](http://ppa.launchpad.net/cpug-devs/ppa/ubuntu) xenial/main i386 Packages
Ign:23 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/universe all Packages
Ign:25 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/universe Translation-en_US
Ign:24 [http://ppa.launchpad.net/cpug-devs/ppa/ubuntu](http://ppa.launchpad.net/cpug-devs/ppa/ubuntu) xenial/main all Packages
Ign:26 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/universe Translation-en
Ign:27 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/universe i386 DEP-11 Metadata
Ign:28 [http://ppa.launchpad.net/cpug-devs/ppa/ubuntu](http://ppa.launchpad.net/cpug-devs/ppa/ubuntu) xenial/main Translation-en_US
Ign:29 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/universe DEP-11 64x64 Icons
Ign:30 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/multiverse i386 Packages
Ign:31 [http://ppa.launchpad.net/cpug-devs/ppa/ubuntu](http://ppa.launchpad.net/cpug-devs/ppa/ubuntu) xenial/main Translation-en
Ign:32 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/multiverse all Packages
Ign:34 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/multiverse Translation-en_US
Ign:33 [http://ppa.launchpad.net/cpug-devs/ppa/ubuntu](http://ppa.launchpad.net/cpug-devs/ppa/ubuntu) xenial/main i386 DEP-11 Metadata
Ign:35 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/multiverse Translation-en
Ign:37 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/multiverse i386 DEP-11 Metadata
Ign:36 [http://ppa.launchpad.net/cpug-devs/ppa/ubuntu](http://ppa.launchpad.net/cpug-devs/ppa/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:38 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/multiverse DEP-11 64x64 Icons
Ign:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/universe i386 Packages
Ign:21 [http://ppa.launchpad.net/cpug-devs/ppa/ubuntu](http://ppa.launchpad.net/cpug-devs/ppa/ubuntu) xenial/main i386 Packages
Ign:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/universe all Packages
Ign:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/universe Translation-en_US
Ign:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/universe Translation-en
Ign:24 [http://ppa.launchpad.net/cpug-devs/ppa/ubuntu](http://ppa.launchpad.net/cpug-devs/ppa/ubuntu) xenial/main all Packages
Ign:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/universe i386 DEP-11 Metadata
Ign:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/universe DEP-11 64x64 Icons
Ign:28 [http://ppa.launchpad.net/cpug-devs/ppa/ubuntu](http://ppa.launchpad.net/cpug-devs/ppa/ubuntu) xenial/main Translation-en_US
Ign:14 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/multiverse i386 Packages
Ign:15 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/multiverse all Packages
Ign:16 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/multiverse Translation-en_US
Ign:31 [http://ppa.launchpad.net/cpug-devs/ppa/ubuntu](http://ppa.launchpad.net/cpug-devs/ppa/ubuntu) xenial/main Translation-en
Ign:17 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/multiverse Translation-en
Ign:19 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/multiverse i386 DEP-11 Metadata
Ign:33 [http://ppa.launchpad.net/cpug-devs/ppa/ubuntu](http://ppa.launchpad.net/cpug-devs/ppa/ubuntu) xenial/main i386 DEP-11 Metadata
Ign:20 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/multiverse DEP-11 64x64 Icons
Ign:22 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/universe i386 Packages
Ign:36 [http://ppa.launchpad.net/cpug-devs/ppa/ubuntu](http://ppa.launchpad.net/cpug-devs/ppa/ubuntu) xenial/main DEP-11 64x64 Icons
Ign:23 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/universe all Packages
Ign:25 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/universe Translation-en_US
Ign:26 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/universe Translation-en
Err:21 [http://ppa.launchpad.net/cpug-devs/ppa/ubuntu](http://ppa.launchpad.net/cpug-devs/ppa/ubuntu) xenial/main i386 Packages
  404  Not Found
Ign:27 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/universe i386 DEP-11 Metadata
Ign:29 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/universe DEP-11 64x64 Icons
Ign:24 [http://ppa.launchpad.net/cpug-devs/ppa/ubuntu](http://ppa.launchpad.net/cpug-devs/ppa/ubuntu) xenial/main all Packages
Ign:30 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/multiverse i386 Packages
Ign:32 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/multiverse all Packages
Ign:28 [http://ppa.launchpad.net/cpug-devs/ppa/ubuntu](http://ppa.launchpad.net/cpug-devs/ppa/ubuntu) xenial/main Translation-en_US
Ign:34 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/multiverse Translation-en_US
Ign:35 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/multiverse Translation-en
Ign:31 [http://ppa.launchpad.net/cpug-devs/ppa/ubuntu](http://ppa.launchpad.net/cpug-devs/ppa/ubuntu) xenial/main Translation-en
Ign:37 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/multiverse i386 DEP-11 Metadata
Ign:38 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/multiverse DEP-11 64x64 Icons
Ign:33 [http://ppa.launchpad.net/cpug-devs/ppa/ubuntu](http://ppa.launchpad.net/cpug-devs/ppa/ubuntu) xenial/main i386 DEP-11 Metadata
Ign:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/universe i386 Packages
Ign:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/universe all Packages                                    
Ign:36 [http://ppa.launchpad.net/cpug-devs/ppa/ubuntu](http://ppa.launchpad.net/cpug-devs/ppa/ubuntu) xenial/main DEP-11 64x64 Icons                      
Ign:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/universe Translation-en_US
Ign:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/universe Translation-en
Ign:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/universe i386 DEP-11 Metadata
Ign:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/universe DEP-11 64x64 Icons
Ign:14 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/multiverse i386 Packages
Ign:15 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/multiverse all Packages
Ign:16 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/multiverse Translation-en_US
Ign:17 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/multiverse Translation-en
Ign:19 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/multiverse i386 DEP-11 Metadata
Ign:20 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/multiverse DEP-11 64x64 Icons
Ign:22 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/universe i386 Packages
Ign:23 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/universe all Packages
Ign:25 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/universe Translation-en_US
Ign:26 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/universe Translation-en
Ign:27 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/universe i386 DEP-11 Metadata
Ign:29 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/universe DEP-11 64x64 Icons
Ign:30 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/multiverse i386 Packages
Ign:32 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/multiverse all Packages
Ign:34 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/multiverse Translation-en_US
Ign:35 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/multiverse Translation-en
Ign:37 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/multiverse i386 DEP-11 Metadata
Ign:38 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/multiverse DEP-11 64x64 Icons
Err:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/universe i386 Packages
  404  Not Found [IP: 91.189.91.23 80]
Ign:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/universe all Packages
Ign:9 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/universe Translation-en_US
Ign:11 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/universe Translation-en
Ign:12 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/universe i386 DEP-11 Metadata
Ign:13 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/universe DEP-11 64x64 Icons
Ign:14 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/multiverse i386 Packages
Ign:15 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/multiverse all Packages
Ign:16 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/multiverse Translation-en_US
Ign:17 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/multiverse Translation-en
Ign:19 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy/multiverse i386 DEP-11 Metadata
Err:22 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/universe i386 Packages
  404  Not Found [IP: 91.189.91.23 80]
Ign:23 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/universe all Packages
Ign:25 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/universe Translation-en_US
Ign:26 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/universe Translation-en
Ign:27 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/universe i386 DEP-11 Metadata
Ign:29 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/universe DEP-11 64x64 Icons
Ign:30 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/multiverse i386 Packages
Ign:32 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/multiverse all Packages
Ign:34 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/multiverse Translation-en_US
Ign:35 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/multiverse Translation-en
Ign:37 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) saucy-updates/multiverse i386 DEP-11 Metadata
Fetched 35.5 kB in 39s (901 B/s)
Reading package lists... Done
W: The repository 'http://us.archive.ubuntu.com/ubuntu saucy Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: [http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu](http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu) xenial InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY C793BFA2FA577F07
W: The repository 'http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu xenial InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://us.archive.ubuntu.com/ubuntu saucy-updates Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: GPG error: [http://ppa.launchpad.net/diesch/testing/ubuntu](http://ppa.launchpad.net/diesch/testing/ubuntu) xenial InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 5AF549300FEB6DD9
W: The repository 'http://ppa.launchpad.net/diesch/testing/ubuntu xenial InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: The repository 'http://ppa.launchpad.net/cpug-devs/ppa/ubuntu xenial Release' does not have a Release file.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/saucy/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/saucy/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.23 80]
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/saucy-updates/universe/binary-i386/Packages](http://us.archive.ubuntu.com/ubuntu/dists/saucy-updates/universe/binary-i386/Packages)  404  Not Found [IP: 91.189.91.23 80]
E: Failed to fetch [http://ppa.launchpad.net/cpug-devs/ppa/ubuntu/dists/xenial/main/binary-i386/Packages](http://ppa.launchpad.net/cpug-devs/ppa/ubuntu/dists/xenial/main/binary-i386/Packages)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.

```

Any help is appreciated. Thanks

---

### Post by wildmanne39 on 2018-02-11
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by deadflowr on 2018-02-12
What does all of /etc/apt show
```
ls /etc/apt
```
might be you have a save file , something like sources.list-dist-upgrade or there abouts.

---

### Post by ajgreeny on 2018-02-12
You also are seeing many references to saucy repos in your output which are never going to show anything as they disappeared a long time ago.
I assume this must be an OS updated from a previous version, maybe saucy, but tell us everything you can.

---

