---
title: "Problem with apt-get update"
date: 2018-10-16
forum: General Help
---

### Post by fanezeu on 2018-10-16
Hello there. This is my first time posting on this forum so sorry if it's the wrong thread.

A long time ago i tried mining on a server that i own and did something , idk what , and now i can't do apt-get update . I'm receving the following errors:

```


root@ubuntu:~# apt-get update
Hit:1 http://ppa.launchpad.net/ethereum/ethereum-dev/ubuntu zesty InRelease
Get:2 http://security.ubuntu.com/ubuntu bionic-security InRelease [83.2 kB]
Hit:3 http://old-releases.ubuntu.com/ubuntu zesty InRelease
Hit:4 http://old-releases.ubuntu.com/ubuntu zesty-updates InRelease
Ign:5 http://ppa.launchpad.net/ethereum/ethereum-qt/ubuntu zesty InRelease
Hit:6 http://old-releases.ubuntu.com/ubuntu zesty-security InRelease
Hit:7 http://ppa.launchpad.net/ethereum/ethereum/ubuntu zesty InRelease
Hit:8 http://in.archive.ubuntu.com/ubuntu bionic InRelease
Ign:9 http://ppa.launchpad.net/nemh/systemback/ubuntu zesty InRelease
Hit:10 http://ppa.launchpad.net/teejee2008/ppa/ubuntu zesty InRelease
Get:11 http://in.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]
Hit:12 http://ppa.launchpad.net/webupd8team/java/ubuntu zesty InRelease
Get:13 http://security.ubuntu.com/ubuntu bionic-security/main Sources [53.0 kB]
Hit:14 http://ppa.launchpad.net/webupd8team/unstable/ubuntu zesty InRelease
Err:15 http://ppa.launchpad.net/ethereum/ethereum-qt/ubuntu zesty Release
  404  Not Found [IP: 91.189.95.83 80]
Get:16 http://security.ubuntu.com/ubuntu bionic-security/main amd64 Packages [18                                                                                                                                                             3 kB]
Err:17 http://ppa.launchpad.net/nemh/systemback/ubuntu zesty Release
  404  Not Found [IP: 91.189.95.83 80]
Get:18 http://security.ubuntu.com/ubuntu bionic-security/main i386 Packages [146                                                                                                                                                              kB]
Get:19 http://security.ubuntu.com/ubuntu bionic-security/main Translation-en [71                                                                                                                                                             .3 kB]
Get:20 http://in.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]
Get:21 http://in.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [36                                                                                                                                                             4 kB]
Get:22 http://in.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages [4                                                                                                                                                             03 kB]
Get:23 http://in.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Package                                                                                                                                                             s [564 kB]
Get:24 http://in.archive.ubuntu.com/ubuntu bionic-updates/universe i386 Packages                                                                                                                                                              [559 kB]
Reading package lists... Done
E: The repository 'http://ppa.launchpad.net/ethereum/ethereum-qt/ubuntu zesty Re                                                                                                                                                             lease' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disa                                                                                                                                                             bled by default.
N: See apt-secure(8) manpage for repository creation and user configuration deta                                                                                                                                                             ils.
E: The repository 'http://ppa.launchpad.net/nemh/systemback/ubuntu zesty Release                                                                                                                                                             ' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disa                                                                                                                                                             bled by default.
N: See apt-secure(8) manpage for repository creation and user configuration deta                                                                                                                                                             ils.



```

---

### Post by deadflowr on 2018-10-16
*Thread moved to **General Help***
Right thread, wrong sub forum. So moved.

You need to disable or remove the ppa for the zesty releases you have.
I see two, one for ethereum and another for systemback.
As this is a server you'll need to manually remove the folders for them in the specialized 3rd party repository folder at
/etc/apt/sources.list.d
look for the folders with those names. Then remove them.

---

