---
title: "APT &quot;error could not resolve....&quot;"
date: 2018-10-02
forum: General Help
---

### Post by androidzip on 2018-10-02
[HTML]ali@ubuntu:~$ sudo apt-get install git-core gnupg flex bison gperf libsdl-dev[sudo] password for ali: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'git' instead of 'git-core'
Note, selecting 'libsdl1.2-dev' instead of 'libsdl-dev'
gnupg is already the newest version (2.2.4-1ubuntu1.1).
The following additional packages will be installed:
  git-man libasound2-dev libbison-dev libcaca-dev liberror-perl libfl-dev
  libfl2 libglib2.0-dev libglib2.0-dev-bin libpcre16-3 libpcre3-dev
  libpcre32-3 libpcrecpp0v5 libpng-dev libpng-tools libpulse-dev
  libsdl1.2debian libsigsegv2 libslang2-dev m4 pkg-config python3-distutils
  python3-lib2to3
Suggested packages:
  bison-doc flex-doc git-daemon-run | git-daemon-sysvinit git-doc git-el
  git-email git-gui gitk gitweb git-cvs git-mediawiki git-svn libasound2-doc
  libglib2.0-doc m4-doc
The following NEW packages will be installed:
  bison flex git git-man gperf libasound2-dev libbison-dev libcaca-dev
  liberror-perl libfl-dev libfl2 libglib2.0-dev libglib2.0-dev-bin libpcre16-3
  libpcre3-dev libpcre32-3 libpcrecpp0v5 libpng-dev libpng-tools libpulse-dev
  libsdl1.2-dev libsdl1.2debian libsigsegv2 libslang2-dev m4 pkg-config
  python3-distutils python3-lib2to3
0 upgraded, 28 newly installed, 0 to remove and 129 not upgraded.
Need to get 11.0 MB of archives.
After this operation, 63.5 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Err:1 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libsigsegv2 amd64 2.12-1
  Could not resolve 'us.archive.ubuntu.com'
Err:2 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 m4 amd64 1.4.18-1
  Could not resolve 'us.archive.ubuntu.com'
Err:3 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 flex amd64 2.6.4-6
  Could not resolve 'us.archive.ubuntu.com'
Err:4 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libbison-dev amd64 2:3.0.4.dfsg-1build1
  Could not resolve 'us.archive.ubuntu.com'
Err:5 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 bison amd64 2:3.0.4.dfsg-1build1
  Could not resolve 'us.archive.ubuntu.com'
Ign:6 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 liberror-perl all 0.17025-1
Ign:7 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 git-man all 1:2.17.1-1ubuntu0.1
Ign:8 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 git amd64 1:2.17.1-1ubuntu0.1
Err:9 http://us.archive.ubuntu.com/ubuntu bionic/universe amd64 gperf amd64 3.1-1
  Could not resolve 'us.archive.ubuntu.com'
Err:10 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libasound2-dev amd64 1.1.3-5ubuntu0.1
  Could not resolve 'us.archive.ubuntu.com'
Ign:11 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libpng-dev amd64 1.6.34-1ubuntu0.18.04.1
Err:12 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libslang2-dev amd64 2.3.1a-3ubuntu1
  Could not resolve 'us.archive.ubuntu.com'
Err:13 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libcaca-dev amd64 0.99.beta19-2build2~gcc5.3
  Could not resolve 'us.archive.ubuntu.com'
Err:14 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libfl2 amd64 2.6.4-6
  Could not resolve 'us.archive.ubuntu.com'
Err:15 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libfl-dev amd64 2.6.4-6
  Could not resolve 'us.archive.ubuntu.com'
Ign:16 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 python3-lib2to3 all 3.6.5-3
Ign:17 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 python3-distutils all 3.6.5-3
Ign:18 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libglib2.0-dev-bin amd64 2.56.2-0ubuntu0.18.04.2
Err:19 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libpcre16-3 amd64 2:8.39-9
  Could not resolve 'us.archive.ubuntu.com'
Err:20 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libpcre32-3 amd64 2:8.39-9
  Could not resolve 'us.archive.ubuntu.com'
Err:21 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libpcrecpp0v5 amd64 2:8.39-9
  Could not resolve 'us.archive.ubuntu.com'
Err:22 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libpcre3-dev amd64 2:8.39-9
  Could not resolve 'us.archive.ubuntu.com'
Err:23 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 pkg-config amd64 0.29.1-0ubuntu2
  Could not resolve 'us.archive.ubuntu.com'
Ign:24 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libglib2.0-dev amd64 2.56.2-0ubuntu0.18.04.2
Ign:25 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libpng-tools amd64 1.6.34-1ubuntu0.18.04.1
Err:26 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libpulse-dev amd64 1:11.1-1ubuntu7.1
  Could not resolve 'us.archive.ubuntu.com'
Err:27 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libsdl1.2debian amd64 1.2.15+dfsg2-0.1
  Could not resolve 'us.archive.ubuntu.com'
Err:28 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 libsdl1.2-dev amd64 1.2.15+dfsg2-0.1
  Could not resolve 'us.archive.ubuntu.com'
Err:6 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 liberror-perl all 0.17025-1
  Could not resolve 'us.archive.ubuntu.com'
Ign:7 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 git-man all 1:2.17.1-1ubuntu0.1
Err:16 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 python3-lib2to3 all 3.6.5-3
  Could not resolve 'us.archive.ubuntu.com'
Err:17 http://us.archive.ubuntu.com/ubuntu bionic/main amd64 python3-distutils all 3.6.5-3
  Could not resolve 'us.archive.ubuntu.com'
Err:8 http://security.ubuntu.com/ubuntu bionic-updates/main amd64 git amd64 1:2.17.1-1ubuntu0.1
  Could not resolve 'us.archive.ubuntu.com'
Err:11 http://security.ubuntu.com/ubuntu bionic-updates/main amd64 libpng-dev amd64 1.6.34-1ubuntu0.18.04.1
  Could not resolve 'us.archive.ubuntu.com'
Err:18 http://security.ubuntu.com/ubuntu bionic-updates/main amd64 libglib2.0-dev-bin amd64 2.56.2-0ubuntu0.18.04.2
  Could not resolve 'us.archive.ubuntu.com'
Err:24 http://security.ubuntu.com/ubuntu bionic-updates/main amd64 libglib2.0-dev amd64 2.56.2-0ubuntu0.18.04.2
  Could not resolve 'us.archive.ubuntu.com'
Err:25 http://security.ubuntu.com/ubuntu bionic-updates/main amd64 libpng-tools amd64 1.6.34-1ubuntu0.18.04.1
  Could not resolve 'us.archive.ubuntu.com'
Ign:7 http://security.ubuntu.com/ubuntu bionic-updates/main amd64 git-man all 1:2.17.1-1ubuntu0.1
Err:7 http://security.ubuntu.com/ubuntu bionic-updates/main amd64 git-man all 1:2.17.1-1ubuntu0.1
  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/...12-1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/...18-1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/....4-6_amd64.deb  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/...ild1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/...ild1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/...7025-1_all.deb  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/po...ntu0.1_all.deb  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/po...u0.1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/....1-1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/...u0.1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/po...04.1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/...ntu1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/...c5.3_amd64.deb  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/....4-6_amd64.deb  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/....4-6_amd64.deb  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/....6.5-3_all.deb  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/....6.5-3_all.deb  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/po...04.2_amd64.deb  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/...39-9_amd64.deb  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/...39-9_amd64.deb  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/...39-9_amd64.deb  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/...39-9_amd64.deb  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/...ntu2_amd64.deb  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/po...04.2_amd64.deb  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/po...04.1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/...u7.1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/...-0.1_amd64.deb  Could not resolve 'us.archive.ubuntu.com'
E: Failed to fetch http://us.archive.ubuntu.com/ubuntu/...-0.1_amd64.deb  Could not resolve 'us.archive.ubuntu.com' E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?[/HTML]

---

### Post by ajgreeny on 2018-10-02
Duplicate of [https://ubuntuforums.org/showthread.php?t=2402625&p=13805362#post13805362](https://ubuntuforums.org/showthread.php?t=2402625&p=13805362#post13805362)

**Please do not create duplicate posts;** it is confusing for all including you and dilutes the forum's ability to help. 

Closed.

---

