---
title: "apt install build-essential  Boms out on 22.04"
date: 2023-10-03
forum: General Help
---

### Post by rmstock2 on 2023-10-03
This is happening since this October 2023.
Last time it worked fine was in June 2023
here's the log :

```



root@ubuntu:/mnt/Downloads/ubu2204/debian# apt install build-essential
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  binutils binutils-common binutils-x86-64-linux-gnu cpp-11 dpkg-dev fakeroot
  g++ g++-11 gcc gcc-11 gcc-11-base gcc-12-base libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libasan6 libatomic1
  libbinutils libc-dev-bin libc-devtools libc6 libc6-dbg libc6-dev libcc1-0
  libcrypt-dev libctf-nobfd0 libctf0 libdpkg-perl libfakeroot libgcc-11-dev
  libgcc-s1 libgomp1 libitm1 liblsan0 libnsl-dev libquadmath0 libstdc++-11-dev
  libstdc++6 libtirpc-dev libtsan0 libubsan1 linux-libc-dev lto-disabled-list
  make manpages-dev rpcsvc-proto
Suggested packages:
  binutils-doc gcc-11-locales debian-keyring g++-multilib g++-11-multilib
  gcc-11-doc gcc-multilib autoconf automake libtool flex bison gcc-doc
  gcc-11-multilib glibc-doc git bzr libstdc++-11-doc make-doc
Recommended packages:
  libnss-nis libnss-nisplus
The following NEW packages will be installed:
  binutils binutils-common binutils-x86-64-linux-gnu build-essential dpkg-dev
  fakeroot g++ g++-11 gcc gcc-11 libalgorithm-diff-perl
  libalgorithm-diff-xs-perl libalgorithm-merge-perl libasan6 libatomic1
  libbinutils libc-dev-bin libc-devtools libc6-dev libcc1-0 libcrypt-dev
  libctf-nobfd0 libctf0 libfakeroot libgcc-11-dev libitm1 liblsan0 libnsl-dev
  libquadmath0 libstdc++-11-dev libtirpc-dev libtsan0 libubsan1 linux-libc-dev
  lto-disabled-list make manpages-dev rpcsvc-proto
The following packages will be upgraded:
  cpp-11 gcc-11-base gcc-12-base libc6 libc6-dbg libdpkg-perl libgcc-s1
  libgomp1 libstdc++6
9 upgraded, 38 newly installed, 0 to remove and 545 not upgraded.
Need to get 79.2 MB/82.3 MB of archives.
After this operation, 184 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://security.ubuntu.com/ubuntu jammy-security/main amd64 gcc-12-base amd64 12.3.0-1ubuntu1~22.04 [20.1 kB]
Get:2 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 libc6-dbg amd64 2.35-0ubuntu3.3 [13.9 MB]
Get:3 http://security.ubuntu.com/ubuntu jammy-security/main amd64 libstdc++6 amd64 12.3.0-1ubuntu1~22.04 [699 kB]
Get:4 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 libcrypt-dev amd64 1:4.4.27-1 [112 kB]
Get:5 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 rpcsvc-proto amd64 1.4.2-0ubuntu6 [68.5 kB]
Get:6 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 libtirpc-dev amd64 1.3.2-2ubuntu0.1 [192 kB]
Get:7 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 libnsl-dev amd64 1.3.0-2build2 [71.3 kB]
Get:8 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 gcc amd64 4:11.2.0-1ubuntu1 [5112 B]
Get:9 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 g++ amd64 4:11.2.0-1ubuntu1 [1412 B]
Get:10 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 make amd64 4.3-4.1build1 [180 kB]
Get:11 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 lto-disabled-list all 24 [12.5 kB]
Get:12 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 build-essential amd64 12.9ubuntu3 [4744 B]
Get:13 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 libfakeroot amd64 1.28-1ubuntu1 [31.5 kB]
Get:14 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 fakeroot amd64 1.28-1ubuntu1 [60.4 kB]
Get:15 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 libalgorithm-diff-perl all 1.201-1 [41.8 kB]
Get:16 http://security.ubuntu.com/ubuntu jammy-security/main amd64 libgomp1 amd64 12.3.0-1ubuntu1~22.04 [126 kB]
Get:17 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 libalgorithm-diff-xs-perl amd64 0.04-6build3 [11.9 kB]
Get:18 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 libalgorithm-merge-perl all 0.08-3 [12.0 kB]
Get:19 cdrom://Ubuntu 22.04.1 LTS _Jammy Jellyfish_ - Release amd64 (20220809.1) jammy/main amd64 manpages-dev all 5.10-1ubuntu1 [2309 kB]
Get:20 http://security.ubuntu.com/ubuntu jammy-security/main amd64 libgcc-s1 amd64 12.3.0-1ubuntu1~22.04 [53.9 kB]
Get:21 http://security.ubuntu.com/ubuntu jammy-security/main amd64 binutils-common amd64 2.38-4ubuntu2.3 [222 kB]
Get:22 http://security.ubuntu.com/ubuntu jammy-security/main amd64 libbinutils amd64 2.38-4ubuntu2.3 [662 kB]
Get:23 http://security.ubuntu.com/ubuntu jammy-security/main amd64 libctf-nobfd0 amd64 2.38-4ubuntu2.3 [107 kB]
Get:24 http://security.ubuntu.com/ubuntu jammy-security/main amd64 libctf0 amd64 2.38-4ubuntu2.3 [103 kB]
Get:25 http://security.ubuntu.com/ubuntu jammy-security/main amd64 binutils-x86-64-linux-gnu amd64 2.38-4ubuntu2.3 [2327 kB]
Get:26 http://security.ubuntu.com/ubuntu jammy-security/main amd64 binutils amd64 2.38-4ubuntu2.3 [3190 B]
Get:27 http://security.ubuntu.com/ubuntu jammy-security/main amd64 linux-libc-dev amd64 5.15.0-84.93 [1330 kB]
Get:28 http://security.ubuntu.com/ubuntu jammy-security/main amd64 cpp-11 amd64 11.4.0-1ubuntu1~22.04 [10.0 MB]
Get:29 http://security.ubuntu.com/ubuntu jammy-security/main amd64 gcc-11-base amd64 11.4.0-1ubuntu1~22.04 [20.2 kB]
Get:30 http://security.ubuntu.com/ubuntu jammy-security/main amd64 libcc1-0 amd64 12.3.0-1ubuntu1~22.04 [48.3 kB]
Get:31 http://security.ubuntu.com/ubuntu jammy-security/main amd64 libitm1 amd64 12.3.0-1ubuntu1~22.04 [30.2 kB]
Get:32 http://security.ubuntu.com/ubuntu jammy-security/main amd64 libatomic1 amd64 12.3.0-1ubuntu1~22.04 [10.4 kB]
Get:33 http://security.ubuntu.com/ubuntu jammy-security/main amd64 libasan6 amd64 11.4.0-1ubuntu1~22.04 [2282 kB]
Get:34 http://security.ubuntu.com/ubuntu jammy-security/main amd64 liblsan0 amd64 12.3.0-1ubuntu1~22.04 [1069 kB]
Get:35 http://security.ubuntu.com/ubuntu jammy-security/main amd64 libtsan0 amd64 11.4.0-1ubuntu1~22.04 [2260 kB]
Get:36 http://security.ubuntu.com/ubuntu jammy-security/main amd64 libubsan1 amd64 12.3.0-1ubuntu1~22.04 [976 kB]
Get:37 http://security.ubuntu.com/ubuntu jammy-security/main amd64 libquadmath0 amd64 12.3.0-1ubuntu1~22.04 [154 kB]
Get:38 http://security.ubuntu.com/ubuntu jammy-security/main amd64 libgcc-11-dev amd64 11.4.0-1ubuntu1~22.04 [2517 kB]
Get:39 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 libc6 amd64 2.35-0ubuntu3.3 [3235 kB]
Get:40 http://security.ubuntu.com/ubuntu jammy-security/main amd64 gcc-11 amd64 11.4.0-1ubuntu1~22.04 [20.1 MB]
Get:41 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 libc-dev-bin amd64 2.35-0ubuntu3.3 [20.3 kB]
Get:42 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 libc6-dev amd64 2.35-0ubuntu3.3 [2100 kB]
Get:43 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 libdpkg-perl all 1.21.1ubuntu2.2 [237 kB]
Get:44 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 dpkg-dev all 1.21.1ubuntu2.2 [922 kB]
Get:45 http://archive.ubuntu.com/ubuntu jammy-updates/main amd64 libc-devtools amd64 2.35-0ubuntu3.3 [28.9 kB]
Get:46 http://security.ubuntu.com/ubuntu jammy-security/main amd64 libstdc++-11-dev amd64 11.4.0-1ubuntu1~22.04 [2101 kB]
Get:47 http://security.ubuntu.com/ubuntu jammy-security/main amd64 g++-11 amd64 11.4.0-1ubuntu1~22.04 [11.4 MB]
Fetched 79.2 MB in 5s (16.1 MB/s) 
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 212026 files and directories currently installed.)
Preparing to unpack .../libc6-dbg_2.35-0ubuntu3.3_amd64.deb ...
Unpacking libc6-dbg:amd64 (2.35-0ubuntu3.3) over (2.35-0ubuntu3.1) ...
Preparing to unpack .../gcc-12-base_12.3.0-1ubuntu1~22.04_amd64.deb ...
Unpacking gcc-12-base:amd64 (12.3.0-1ubuntu1~22.04) over (12-20220319-1ubuntu1) ...
Setting up gcc-12-base:amd64 (12.3.0-1ubuntu1~22.04) ...
(Reading database ... 212023 files and directories currently installed.)
Preparing to unpack .../libstdc++6_12.3.0-1ubuntu1~22.04_amd64.deb ...
Unpacking libstdc++6:amd64 (12.3.0-1ubuntu1~22.04) over (12-20220319-1ubuntu1) ...
Setting up libstdc++6:amd64 (12.3.0-1ubuntu1~22.04) ...
(Reading database ... 212023 files and directories currently installed.)
Preparing to unpack .../libgomp1_12.3.0-1ubuntu1~22.04_amd64.deb ...
Unpacking libgomp1:amd64 (12.3.0-1ubuntu1~22.04) over (12-20220319-1ubuntu1) ...
Preparing to unpack .../libgcc-s1_12.3.0-1ubuntu1~22.04_amd64.deb ...
Unpacking libgcc-s1:amd64 (12.3.0-1ubuntu1~22.04) over (12-20220319-1ubuntu1) ...
Setting up libgcc-s1:amd64 (12.3.0-1ubuntu1~22.04) ...
(Reading database ... 212023 files and directories currently installed.)
Preparing to unpack .../libc6_2.35-0ubuntu3.3_amd64.deb ...
Unpacking libc6:amd64 (2.35-0ubuntu3.3) over (2.35-0ubuntu3.1) ...
Setting up libc6:amd64 (2.35-0ubuntu3.3) ...
Selecting previously unselected package binutils-common:amd64.
(Reading database ... 212023 files and directories currently installed.)
Preparing to unpack .../00-binutils-common_2.38-4ubuntu2.3_amd64.deb ...
Unpacking binutils-common:amd64 (2.38-4ubuntu2.3) ...
Selecting previously unselected package libbinutils:amd64.
Preparing to unpack .../01-libbinutils_2.38-4ubuntu2.3_amd64.deb ...
Unpacking libbinutils:amd64 (2.38-4ubuntu2.3) ...
Selecting previously unselected package libctf-nobfd0:amd64.
Preparing to unpack .../02-libctf-nobfd0_2.38-4ubuntu2.3_amd64.deb ...
Unpacking libctf-nobfd0:amd64 (2.38-4ubuntu2.3) ...
Selecting previously unselected package libctf0:amd64.
Preparing to unpack .../03-libctf0_2.38-4ubuntu2.3_amd64.deb ...
Unpacking libctf0:amd64 (2.38-4ubuntu2.3) ...
Selecting previously unselected package binutils-x86-64-linux-gnu.
Preparing to unpack .../04-binutils-x86-64-linux-gnu_2.38-4ubuntu2.3_amd64.deb ...
Unpacking binutils-x86-64-linux-gnu (2.38-4ubuntu2.3) ...
Selecting previously unselected package binutils.
Preparing to unpack .../05-binutils_2.38-4ubuntu2.3_amd64.deb ...
Unpacking binutils (2.38-4ubuntu2.3) ...
Selecting previously unselected package libc-dev-bin.
Preparing to unpack .../06-libc-dev-bin_2.35-0ubuntu3.3_amd64.deb ...
Unpacking libc-dev-bin (2.35-0ubuntu3.3) ...
Selecting previously unselected package linux-libc-dev:amd64.
Preparing to unpack .../07-linux-libc-dev_5.15.0-84.93_amd64.deb ...
Unpacking linux-libc-dev:amd64 (5.15.0-84.93) ...
Selecting previously unselected package libcrypt-dev:amd64.
Preparing to unpack .../08-libcrypt-dev_4.4.27-1_amd64.deb ...
Unpacking libcrypt-dev:amd64 (1:4.4.27-1) ...
Selecting previously unselected package rpcsvc-proto.
Preparing to unpack .../09-rpcsvc-proto_1.4.2-0ubuntu6_amd64.deb ...
Unpacking rpcsvc-proto (1.4.2-0ubuntu6) ...
Selecting previously unselected package libtirpc-dev:amd64.
Preparing to unpack .../10-libtirpc-dev_1.3.2-2ubuntu0.1_amd64.deb ...
Unpacking libtirpc-dev:amd64 (1.3.2-2ubuntu0.1) ...
Selecting previously unselected package libnsl-dev:amd64.
Preparing to unpack .../11-libnsl-dev_1.3.0-2build2_amd64.deb ...
Unpacking libnsl-dev:amd64 (1.3.0-2build2) ...
Selecting previously unselected package libc6-dev:amd64.
Preparing to unpack .../12-libc6-dev_2.35-0ubuntu3.3_amd64.deb ...
Unpacking libc6-dev:amd64 (2.35-0ubuntu3.3) ...
dpkg: error processing archive /tmp/apt-dpkg-install-GnUnLv/13-cpp-11_11.4.0-1ubuntu1~22.04_amd64.deb (--unpack):
 cannot access archive '/tmp/apt-dpkg-install-GnUnLv/13-cpp-11_11.4.0-1ubuntu1~22.04_amd64.deb': No such file or directory
No apport report written because the error message indicates an issue on the local system
         No apport report written because the error message indicates an issue on the local system
                  dpkg: error processing archive /tmp/apt-dpkg-install-GnUnLv/14-gcc-11-base_11.4.0-1ubuntu1~22.04_amd64.deb (--unpack):
 cannot access archive '/tmp/apt-dpkg-install-GnUnLv/14-gcc-11-base_11.4.0-1ubuntu1~22.04_amd64.deb': No such file or directory
dpkg: error processing archive /tmp/apt-dpkg-install-GnUnLv/15-libcc1-0_12.3.0-1ubuntu1~22.04_amd64.deb (--unpack):
 cannot access archive '/tmp/apt-dpkg-install-GnUnLv/15-libcc1-0_12.3.0-1ubuntu1~22.04_amd64.deb': No such file or directory
dpkg: error processing archive /tmp/apt-dpkg-install-GnUnLv/16-libitm1_12.3.0-1ubuntu1~22.04_amd64.deb (--unpack):
 cannot access archive '/tmp/apt-dpkg-install-GnUnLv/16-libitm1_12.3.0-1ubuntu1~22.04_amd64.deb': No such file or directory
dpkg: error processing archive /tmp/apt-dpkg-install-GnUnLv/17-libatomic1_12.3.0-1ubuntu1~22.04_amd64.deb (--unpack):
 cannot access archive '/tmp/apt-dpkg-install-GnUnLv/17-libatomic1_12.3.0-1ubuntu1~22.04_amd64.deb': No such file or directory
dpkg:o apport report written because the error message indicates an issue on the local system
             No apport report written because MaxReports is reached already
                                                                           No apport report written because MaxReports is reached already
                                                         No apport report written because MaxReports is reached already
                                       m error processing archive /tmp/apt-dpkg-install-GnUnLv/18-libasan6_11.4.0-1ubuntu1~22.04_amd64.deb (--unpack):
 cannot access archive '/tmp/apt-dpkg-install-GnUnLv/18-libasan6_11.4.0-1ubuntu1~22.04_amd64.deb': No such file or directory
dpkg: error processing archive /tmp/apt-dpkg-install-GnUnLv/19-liblsan0_12.3.0-1ubuntu1~22.04_amd64.deb (--unpack):
 cannot access archive '/tmp/apt-dpkg-install-GnUnLv/19-liblsan0_12.3.0-1ubuntu1~22.04_amd64.deb': No such file or directory
dpkg: error processing archive /tmp/apt-dpkg-install-GnUnLv/20-libtsan0_11.4.0-1ubuntu1~22.04_amd64.deb (--unpack):
 cannot access archive '/tmp/apt-dpkg-install-GnUnLv/20-libtsan0_11.4.0-1ubuntu1~22.04_amd64.deb': No such file or directory
dpkg: error processing archive /tmp/apt-dpkg-install-GnUnLv/21-libubsan1_12.3.0-1ubuntu1~22.04_amd64.deb (--unpack):
 cannot access archive '/tmp/apt-dpkg-install-GnUnLv/21-libubsan1_12.3.0-1ubuntu1~22.04_amd64.deb': No such file or directory
dpkg: error processingNo apport report written because MaxReports is reached already
    No apport report written because MaxReports is reached already
                                                                  No apport report written because MaxReports is reached already
                                                No apport report written because MaxReports is reached already
                               archive /tmp/apt-dpkg-install-GnUnLv/22-libquadmath0_12.3.0-1ubuntu1~22.04_amd64.deb (--unpack):
 cannot access archive '/tmp/apt-dpkg-install-GnUnLv/22-libquadmath0_12.3.0-1ubuntu1~22.04_amd64.deb': No such file or directory
dpkg: error processing archive /tmp/apt-dpkg-install-GnUnLv/23-libgcc-11-dev_11.4.0-1ubuntu1~22.04_amd64.deb (--unpack):
 cannot access archive '/tmp/apt-dpkg-install-GnUnLv/23-libgcc-11-dev_11.4.0-1ubuntu1~22.04_amd64.deb': No such file or directory
dpkg: error processing archive /tmp/apt-dpkg-install-GnUnLv/24-gcc-11_11.4.0-1ubuntu1~22.04_amd64.deb (--unpack):
 cannot access archive '/tmp/apt-dpkg-install-GnUnLv/24-gcc-11_11.4.0-1ubuntu1~22.04_amd64.deb': No such file or directory
dpkg: error processing archive /tmp/apt-dpkg-install-GnUnLv/25-gcc_11.2.0-1ubuntu1_amd64.deb (--unpack):
 cannot access archive '/tmp/apt-dpkg-install-GnUnLv/25-gcc_11.2.0-1ubuntu1_amd64.deb': No such file or directory
dpkg: error processing archive /tmp/apt-dpkg-instaNo apport report written because MaxReports is reached already
                                No apport report written because MaxReports is reached already
              No apport report written because MaxReports is reached already
                                                                            No apport report written because MaxReports is reached already
                                                          ll-GnUnLv/26-libstdc++-11-dev_11.4.0-1ubuntu1~22.04_amd64.deb (--unpack):
 cannot access archive '/tmp/apt-dpkg-install-GnUnLv/26-libstdc++-11-dev_11.4.0-1ubuntu1~22.04_amd64.deb': No such file or directory
dpkg: error processing archive /tmp/apt-dpkg-install-GnUnLv/27-g++-11_11.4.0-1ubuntu1~22.04_amd64.deb (--unpack):
 cannot access archive '/tmp/apt-dpkg-install-GnUnLv/27-g++-11_11.4.0-1ubuntu1~22.04_amd64.deb': No such file or directory
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            No apport report written because MaxReports is reached already
                          No apport report written because MaxReports is reached already
        No apport report written because MaxReports is reached already
                                                                      dpkg: error processing archive /tmp/apt-dpkg-install-GnUnLv/28-g++_11.2.0-1ubuntu1_amd64.deb (--unpack):
 cannot access archive '/tmp/apt-dpkg-install-GnUnLv/28-g++_11.2.0-1ubuntu1_amd64.deb': No such file or directory
dpkg: error processing archive /tmp/apt-dpkg-install-GnUnLv/29-make_4.3-4.1build1_amd64.deb (--unpack):
 cannot access archive '/tmp/apt-dpkg-install-GnUnLv/29-make_4.3-4.1build1_amd64.deb': No such file or directory
dpkg: error processing archive /tmp/apt-dpkg-install-GnUnLv/30-libdpkg-perl_1.21.1ubuntu2.2_all.deb (--unpack):
 cannot access archive '/tmp/apt-dpkg-install-GnUnLv/30-libdpkg-perl_1.21.1ubuntu2.2_all.deb': No such file or directory
dpkg: error processing archive /tmp/apt-dpkg-install-GnUnLv/31-lto-disabled-list_24_all.deb (--unpack):
 cannot access archive '/tmp/apt-dpkg-install-GnUnLv/31-lto-disabled-list_24_all.deb': No such file or directory
dpkg: error processing archive /tmp/apt-dpkg-install-GnUnLv/32-dpkg-dev_1.21.1ubuntu2.2_alNo apport report written because MaxReports is reached already
                                                                        No apport report written because MaxReports is reached already
                                                      No apport report written because MaxReports is reached already
                                    No apport report written because MaxReports is reached already
                  No apport report written because MaxReports is reached already
                                                                               l.deb (--unpack):
 cannot access archive '/tmp/apt-dpkg-install-GnUnLv/32-dpkg-dev_1.21.1ubuntu2.2_all.deb': No such file or directory
dpkg: error processing archive /tmp/apt-dpkg-install-GnUnLv/33-build-essential_12.9ubuntu3_amd64.deb (--unpack):
 cannot access archive '/tmp/apt-dpkg-install-GnUnLv/33-build-essential_12.9ubuntu3_amd64.deb': No such file or directory
dpkg: error processing archive /tmp/apt-dpkg-install-GnUnLv/34-libfakeroot_1.28-1ubuntu1_amd64.deb (--unpack):
 cannot access archive '/tmp/apt-dpkg-install-GnUnLv/34-libfakeroot_1.28-1ubuntu1_amd64.deb': No such file or directory
dpkg: error processing archive /tmp/apt-dpkg-install-GnUnLv/35-fakeroot_1.28-1ubuntu1_amd64.deb (--unpack):
 cannot access archive '/tmp/apt-dpkg-install-GnUnLv/35-fakeroot_1.28-1ubuntu1_amd64.deb': No such file or directory
dpkg: error processing archive /tmp/apt-dpkg-install-GnUnLv/36-libalgorithm-diff-perl_1.201-1_all.deb (--unpack):
 cannot access archive '/tmp/apt-dpkg-instaNo apport report written because MaxReports is reached already
                         No apport report written because MaxReports is reached already
       No apport report written because MaxReports is reached already
                                                                     No apport report written because MaxReports is reached already
                                                   ll-GnUnLv/36-libalgorithm-diff-perl_1.201-1_all.deb': No such file or directory
dpkg: error processing archive /tmp/apt-dpkg-install-GnUnLv/37-libalgorithm-diff-xs-perl_0.04-6build3_amd64.deb (--unpack):
 cannot access archive '/tmp/apt-dpkg-install-GnUnLv/37-libalgorithm-diff-xs-perl_0.04-6build3_amd64.deb': No such file or directory
dpkg: error processing archive /tmp/apt-dpkg-install-GnUnLv/38-libalgorithm-merge-perl_0.08-3_all.deb (--unpack):
 cannot access archive '/tmp/apt-dpkg-install-GnUnLv/38-libalgorithm-merge-perl_0.08-3_all.deb': No such file or directory
dpkg: error processing archive /tmp/apt-dpkg-install-GnUnLv/39-libc-devtools_2.35-0ubuntu3.3_amd64.deb (--unpack):
 cannot access archive '/tmp/apt-dpkg-install-GnUnLv/39-libc-devtools_2.35-0ubuntu3.3_amd64.deb': No such file or directory
dpkg: error processing archive /tmp/apt-dpkg-install-GnUnLv/40-manpages-dev_5.10-1ubuntu1_all.deb (--unpack):
 cannot access archive '/tmp/apt-dpkg-install-GnUnLv/40-manpages-dev_5.10-1ubuntu1_all.deb': No such file or directory
Errors were encountered while processing:
 /tmp/apt-dpkg-install-GnUnLv/13-cpp-11_11.4.0-1ubuntu1~22.04_amd64.deb
 /tmp/apt-dpkg-install-GnUnLv/14-gcc-11-base_11.4.0-1ubuntu1~22.04_amd64.deb
 /tmp/apt-dpkg-install-GnUnLv/15-libcc1-0_12.3.0-1ubuntu1~22.04_amd64.deb
 /tmp/apt-dpkg-install-GnUnLv/16-libitm1_12.3.0-1ubuntu1~22.04_amd64.deb
 /tmp/apt-dpkg-install-GnUnLv/17-libatomic1_12.3.0-1ubuntu1~22.04_amd64.deb
 /tmp/apt-dpkg-install-GnUnLv/18-libasan6_11.4.0-1ubuntu1~22.04_amd64.deb
 /tmp/apt-dpkg-install-GnUnLv/19-liblsan0_12.3.0-1ubuntu1~22.04_amd64.deb
 /tmp/apt-dpkg-install-GnUnLv/20-libtsan0_11.4.0-1ubuntu1~22.04_amd64.deb
 /tmp/apt-dpkg-install-GnUnLv/21-libubsan1_12.3.0-1ubuntu1~22.04_amd64.deb
 /tmp/apt-dpkg-install-GnUnLv/22-libquadmath0_12.3.0-1ubuntu1~22.04_amd64.deb
 /tmp/apt-dpkg-install-GnUnLv/23-libgcc-11-dev_11.4.0-1ubuntu1~22.04_amd64.deb
 /tmp/apt-dpkg-install-GnUnLv/24-gcc-11_11.4.0-1ubuntu1~22.04_amd64.deb
 /tmp/apt-dpkg-install-GnUnLv/25-gcc_11.2.0-1ubuntu1_amd64.deb
 /tmp/apt-dpkg-install-GnUnLv/26-libstdc++-11-dev_11.4.0-1ubuntu1~22.04_amd64.deb
 /tmp/apt-dpkg-install-GnUnLv/27-g++-11_11.4.0-1ubuntu1~22.04_amd64.deb
 /tmp/apt-dpkg-install-GnUnLv/28-g++_11.2.0-1ubuntu1_amd64.deb
 /tmp/apt-dpkg-install-GnUnLv/29-make_4.3-4.1build1_amd64.deb
 /tmp/apt-dpkg-install-GnUnLv/30-libdpkg-perl_1.21.1ubuntu2.2_all.deb
 /tmp/apt-dpkg-install-GnUnLv/31-lto-disabled-list_24_all.deb
 /tmp/apt-dpkg-install-GnUnLv/32-dpkg-dev_1.21.1ubuntu2.2_all.deb
 /tmp/apt-dpkg-install-GnUnLv/33-build-essential_12.9ubuntu3_amd64.deb
 /tmp/apt-dpkg-install-GnUnLv/34-libfakeroot_1.28-1ubuntu1_amd64.deb
 /tmp/apt-dpkg-install-GnUnLv/35-fakeroot_1.28-1ubuntu1_amd64.deb
 /tmp/apt-dpkg-install-GnUnLv/36-libalgorithm-diff-perl_1.201-1_all.deb
 /tmp/apt-dpkg-install-GnUnLv/37-libalgorithm-diff-xs-perl_0.04-6build3_amd64.deb
 /tmp/apt-dpkg-install-GnUnLv/38-libalgorithm-merge-perl_0.08-3_all.deb
 /tmp/apt-dpkg-install-GnUnLv/39-libc-devtools_2.35-0ubuntu3.3_amd64.deb
 /tmp/apt-dpkg-install-GnUnLv/40-manpages-dev_5.10-1ubuntu1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
E: Unable to read /tmp/apt-dpkg-install-GnUnLv - opendir (2: No such file or directory)
root@ubuntu:/mnt/Downloads/ubu2204/debian# 



```

---

### Post by rmstock2 on 2023-10-04
instead of apt i tried using apt-get. that didn't help out.
so i tried to install all the develop components manually.
but what i did find out is that `apt install  build-essential'
calls on itself. that would normally be no problem. but
in this occasion  calling `build-essential' obviously bombs out :

```


Welcome to Ubuntu 22.04.1 LTS (GNU/Linux 5.15.0-43-generic x86_64)


 * Documentation:  https://help.ubuntu.com
 * Management:     https://landscape.canonical.com
 * Support:        https://ubuntu.com/advantage






The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.


Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.


ubuntu@ubuntu:~$ su -
Password: 
root@ubuntu:~# apt-get install binutils
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  binutils-common binutils-x86-64-linux-gnu libbinutils libctf-nobfd0 libctf0
Suggested packages:
  binutils-doc
The following NEW packages will be installed:
  binutils binutils-common binutils-x86-64-linux-gnu libbinutils libctf-nobfd0
  libctf0
0 upgraded, 6 newly installed, 0 to remove and 552 not upgraded.
Need to get 3425 kB of archives.
After this operation, 14.7 MB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://security.ubuntu.com/ubuntu jammy-security/main amd64 binutils-common amd64 2.38-4ubuntu2.3 [222 kB]
Get:2 http://security.ubuntu.com/ubuntu jammy-security/main amd64 libbinutils amd64 2.38-4ubuntu2.3 [662 kB]
Get:3 http://security.ubuntu.com/ubuntu jammy-security/main amd64 libctf-nobfd0 amd64 2.38-4ubuntu2.3 [107 kB]
Get:4 http://security.ubuntu.com/ubuntu jammy-security/main amd64 libctf0 amd64 2.38-4ubuntu2.3 [103 kB]
Get:5 http://security.ubuntu.com/ubuntu jammy-security/main amd64 binutils-x86-64-linux-gnu amd64 2.38-4ubuntu2.3 [2327 kB]
Get:6 http://security.ubuntu.com/ubuntu jammy-security/main amd64 binutils amd64 2.38-4ubuntu2.3 [3190 B]
Fetched 3425 kB in 1s (2952 kB/s)  
Selecting previously unselected package binutils-common:amd64.
(Reading database ... 211500 files and directories currently installed.)
Preparing to unpack .../0-binutils-common_2.38-4ubuntu2.3_amd64.deb ...
Unpacking binutils-common:amd64 (2.38-4ubuntu2.3) ...
Selecting previously unselected package libbinutils:amd64.
Preparing to unpack .../1-libbinutils_2.38-4ubuntu2.3_amd64.deb ...
Unpacking libbinutils:amd64 (2.38-4ubuntu2.3) ...
Selecting previously unselected package libctf-nobfd0:amd64.
Preparing to unpack .../2-libctf-nobfd0_2.38-4ubuntu2.3_amd64.deb ...
Unpacking libctf-nobfd0:amd64 (2.38-4ubuntu2.3) ...
Selecting previously unselected package libctf0:amd64.
Preparing to unpack .../3-libctf0_2.38-4ubuntu2.3_amd64.deb ...
Unpacking libctf0:amd64 (2.38-4ubuntu2.3) ...
Selecting previously unselected package binutils-x86-64-linux-gnu.
Preparing to unpack .../4-binutils-x86-64-linux-gnu_2.38-4ubuntu2.3_amd64.deb ...
Unpacking binutils-x86-64-linux-gnu (2.38-4ubuntu2.3) ...
Selecting previously unselected package binutils.
Preparing to unpack .../5-binutils_2.38-4ubuntu2.3_amd64.deb ...
Unpacking binutils (2.38-4ubuntu2.3) ...
Setting up binutils-common:amd64 (2.38-4ubuntu2.3) ...
Setting up libctf-nobfd0:amd64 (2.38-4ubuntu2.3) ...
Setting up libbinutils:amd64 (2.38-4ubuntu2.3) ...
Setting up libctf0:amd64 (2.38-4ubuntu2.3) ...
Setting up binutils-x86-64-linux-gnu (2.38-4ubuntu2.3) ...
Setting up binutils (2.38-4ubuntu2.3) ...
Processing triggers for libc-bin (2.35-0ubuntu3.1) ...
Processing triggers for man-db (2.10.2-1) ...
root@ubuntu:~# apt-get install binutils-common
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
binutils-common is already the newest version (2.38-4ubuntu2.3).
binutils-common set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 552 not upgraded.
root@ubuntu:~# 




root@ubuntu:~# apt-get install binutils-common
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
binutils-common is already the newest version (2.38-4ubuntu2.3).
binutils-common set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 552 not upgraded.
root@ubuntu:~#




root@ubuntu:~# apt-get install binutils-x86-64-linux-gnu
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
binutils-x86-64-linux-gnu is already the newest version (2.38-4ubuntu2.3).
binutils-x86-64-linux-gnu set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 552 not upgraded.
root@ubuntu:~# 




root@ubuntu:~# apt-get install cpp-11
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  gcc-11-base
Suggested packages:
  gcc-11-locales
The following packages will be upgraded:
  cpp-11 gcc-11-base
2 upgraded, 0 newly installed, 0 to remove and 550 not upgraded.
Need to get 10.0 MB of archives.
After this operation, 80.9 kB of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://security.ubuntu.com/ubuntu jammy-security/main amd64 cpp-11 amd64 11.4.0-1ubuntu1~22.04 [10.0 MB]
Get:2 http://security.ubuntu.com/ubuntu jammy-security/main amd64 gcc-11-base amd64 11.4.0-1ubuntu1~22.04 [20.2 kB]
Fetched 10.0 MB in 2s (6237 kB/s)     
(Reading database ... 211768 files and directories currently installed.)
Preparing to unpack .../cpp-11_11.4.0-1ubuntu1~22.04_amd64.deb ...
Unpacking cpp-11 (11.4.0-1ubuntu1~22.04) over (11.2.0-19ubuntu1) ...
Preparing to unpack .../gcc-11-base_11.4.0-1ubuntu1~22.04_amd64.deb ...
Unpacking gcc-11-base:amd64 (11.4.0-1ubuntu1~22.04) over (11.2.0-19ubuntu1) ...
Setting up gcc-11-base:amd64 (11.4.0-1ubuntu1~22.04) ...
Setting up cpp-11 (11.4.0-1ubuntu1~22.04) ...
Processing triggers for man-db (2.10.2-1) ...
root@ubuntu:~# 




root@ubuntu:~# apt-get install dpkg-dev
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  build-essential fakeroot g++ g++-11 gcc gcc-11 gcc-12-base
  libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl
  libasan6 libatomic1 libc-dev-bin libc-devtools libc6 libc6-dbg libc6-dev
  libcc1-0 libcrypt-dev libdpkg-perl libfakeroot libgcc-11-dev libgcc-s1
  libgomp1 libitm1 liblsan0 libnsl-dev libquadmath0 libstdc++-11-dev
  libstdc++6 libtirpc-dev libtsan0 libubsan1 linux-libc-dev lto-disabled-list
  make manpages-dev rpcsvc-proto
Suggested packages:
  debian-keyring g++-multilib g++-11-multilib gcc-11-doc gcc-multilib autoconf
  automake libtool flex bison gcc-doc gcc-11-multilib gcc-11-locales glibc-doc
  git bzr libstdc++-11-doc make-doc
Recommended packages:
  libnss-nis libnss-nisplus
The following NEW packages will be installed:
  build-essential dpkg-dev fakeroot g++ g++-11 gcc gcc-11
  libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl
  libasan6 libatomic1 libc-dev-bin libc-devtools libc6-dev libcc1-0
  libcrypt-dev libfakeroot libgcc-11-dev libitm1 liblsan0 libnsl-dev
  libquadmath0 libstdc++-11-dev libtirpc-dev libtsan0 libubsan1 linux-libc-dev
  lto-disabled-list make manpages-dev rpcsvc-proto
The following packages will be upgraded:
  gcc-12-base libc6 libc6-dbg libdpkg-perl libgcc-s1 libgomp1 libstdc++6
7 upgraded, 32 newly installed, 0 to remove and 543 not upgraded.
Need to get 65.6 MB/68.8 MB of archives.
After this operation, 169 MB of additional disk space will be used.
Do you want to continue? [Y/n] 



```

---

### Post by deadflowr on 2023-10-04
*Thread moved to **General Help***

Ubuntu 22.04 has been out of the development cycle for a year and a half now.

---

### Post by ajgreeny on 2023-10-05
It appears from your post #1 that you are downloading packages or at least the system is attempting to do so from the cdrom of Ubuntu-22.04.
Is this an actual fully installed system or are you running it as a live system, not from a real cdrom obviously, as that is not big enough?

I am confused!

---

### Post by MAFoElffen on 2023-10-05
Please post your /etc/apt/sources.list within CODE Tags.

---

