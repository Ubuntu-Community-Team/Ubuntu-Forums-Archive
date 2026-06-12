---
title: "trouble installing drivers for removable wifi usb"
date: 2023-11-17
forum: General Help
---

### Post by d3vestator on 2023-11-17
i have removable wifi usb that i use for my old testing machines and even though it does work for windows. it doesnt work for ubuntu. i know that it is missing drivers for ubuntu, so i downloaded the drivers on a usb and accessed the directory in the command line untill i found the install.sh, i change changed the permission to +x and ran it(./install.sh) however i get errors when i run it.

```

./install.sh line 4:$'\r': command not found
../wpa_supplicant_hostepad-0.8_rtw_r24647.20171025.tar.gz
./install.sh line 5:$'\r': command not found
./install.sh line 102:$'\r': syntax error: unexpected end of file

```

before running the install.sh, i had to extract the file and then i used file-roller for one of the sub-directorys because it was a tar file

---

### Post by Yellow Pasque on 2023-11-17
It almost looks like the .sh file is formatted with DOS/Windows line endings. Where did you download that?
What chipset does your adapter use?:
```
lsusb
```

---

### Post by d3vestator on 2023-11-17
its a dlink DWA-182
[https://support.dlink.com/ProductInfo.aspx?m=DWA-182](https://support.dlink.com/ProductInfo.aspx?m=DWA-182), the version is D1
linux(5.8.7.1)

---

### Post by Yellow Pasque on 2023-11-17
I guess it's a Realtek 8822bu chipset. The drivers on D-Link's site are too old to work with modern Ubuntu/Linux versions.

```
sudo apt install -y build-essential dkms git iw
cd ~/
```
Then see: [https://ubuntuforums.org/showthread.php?t=2487527&p=14146303#post14146303](https://ubuntuforums.org/showthread.php?t=2487527&p=14146303#post14146303)

---

### Post by d3vestator on 2023-11-17
i dont have wifi on my machine, so im using my laptop, where does the command get downloaded to, so i can put in on a usb?

---

### Post by jeremy31 on 2023-11-17
Can you use USB tethering on a smartphone to this computer?

---

### Post by d3vestator on 2023-11-17
it  was isntalling then something happened
```

andman@sandman-HP-Compaq-6005-Pro-MT-PC:~$ sudo apt install -y build-essential dkms git iw
cd ~/
[sudo] password for sandman: 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
The following additional packages will be installed:
  binutils binutils-common binutils-x86-64-linux-gnu cpp-11 cpp-12 dctrl-tools
  dpkg-dev fakeroot g++ g++-11 gcc gcc-11 gcc-11-base gcc-12 gcc-12-base
  git-man libalgorithm-diff-perl libalgorithm-diff-xs-perl
  libalgorithm-merge-perl libasan6 libasan8 libatomic1 libbinutils
  libc-dev-bin libc-devtools libc6 libc6-dbg libc6-dev libcc1-0 libcrypt-dev
  libctf-nobfd0 libctf0 libdpkg-perl liberror-perl libfakeroot
  libfile-fcntllock-perl libgcc-11-dev libgcc-12-dev libgcc-s1 libgomp1
  libitm1 liblsan0 libnsl-dev libquadmath0 libstdc++-11-dev libstdc++6
  libtirpc-dev libtsan0 libtsan2 libubsan1 linux-libc-dev lto-disabled-list
  make manpages-dev rpcsvc-proto
Suggested packages:
  binutils-doc gcc-11-locales gcc-12-locales cpp-12-doc debtags menu
  debian-keyring g++-multilib g++-11-multilib gcc-11-doc gcc-multilib autoconf
  automake libtool flex bison gcc-doc gcc-11-multilib gcc-12-multilib
  gcc-12-doc git-daemon-run | git-daemon-sysvinit git-doc git-email git-gui
  gitk gitweb git-cvs git-mediawiki git-svn glibc-doc bzr libstdc++-11-doc
  make-doc
Recommended packages:
  libnss-nis libnss-nisplus
The following NEW packages will be installed:
  binutils binutils-common binutils-x86-64-linux-gnu build-essential cpp-12
  dctrl-tools dkms dpkg-dev fakeroot g++ g++-11 gcc gcc-11 gcc-12 git git-man
  iw libalgorithm-diff-perl libalgorithm-diff-xs-perl libalgorithm-merge-perl
  libasan6 libasan8 libatomic1 libbinutils libc-dev-bin libc-devtools
  libc6-dev libcc1-0 libcrypt-dev libctf-nobfd0 libctf0 libdpkg-perl
  liberror-perl libfakeroot libfile-fcntllock-perl libgcc-11-dev libgcc-12-dev
  libitm1 liblsan0 libnsl-dev libquadmath0 libstdc++-11-dev libtirpc-dev
  libtsan0 libtsan2 libubsan1 linux-libc-dev lto-disabled-list make
  manpages-dev rpcsvc-proto
The following packages will be upgraded:
  cpp-11 gcc-11-base gcc-12-base libc6 libc6-dbg libgcc-s1 libgomp1 libstdc++6
8 upgraded, 51 newly installed, 0 to remove and 450 not upgraded.
Need to get 127 MB of archives.
After this operation, 346 MB of additional disk space will be used.
Ign:1 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 cpp-11 amd64 11.4.0-1ubuntu1~22.04
Ign:2 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 gcc-11-base amd64 11.4.0-1ubuntu1~22.04
Ign:3 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libc6-dbg amd64 2.35-0ubuntu3.4
Ign:4 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libgomp1 amd64 12.3.0-1ubuntu1~22.04
Ign:5 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 gcc-12-base amd64 12.3.0-1ubuntu1~22.04
Ign:6 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libgcc-s1 amd64 12.3.0-1ubuntu1~22.04
Ign:7 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libstdc++6 amd64 12.3.0-1ubuntu1~22.04
Ign:8 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libc6 amd64 2.35-0ubuntu3.4
Ign:9 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libcc1-0 amd64 12.3.0-1ubuntu1~22.04
Ign:10 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 binutils-common amd64 2.38-4ubuntu2.3
Ign:11 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libbinutils amd64 2.38-4ubuntu2.3
Ign:12 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libctf-nobfd0 amd64 2.38-4ubuntu2.3
Ign:13 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libctf0 amd64 2.38-4ubuntu2.3
Ign:14 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 binutils-x86-64-linux-gnu amd64 2.38-4ubuntu2.3
Ign:15 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 binutils amd64 2.38-4ubuntu2.3
Ign:16 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libitm1 amd64 12.3.0-1ubuntu1~22.04
Ign:17 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libatomic1 amd64 12.3.0-1ubuntu1~22.04
Ign:18 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libasan6 amd64 11.4.0-1ubuntu1~22.04
Ign:19 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 liblsan0 amd64 12.3.0-1ubuntu1~22.04
Ign:20 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libtsan0 amd64 11.4.0-1ubuntu1~22.04
Ign:21 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libubsan1 amd64 12.3.0-1ubuntu1~22.04
Ign:22 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libquadmath0 amd64 12.3.0-1ubuntu1~22.04
Ign:23 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libgcc-11-dev amd64 11.4.0-1ubuntu1~22.04
Ign:24 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 gcc-11 amd64 11.4.0-1ubuntu1~22.04
Ign:25 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 gcc amd64 4:11.2.0-1ubuntu1
Ign:26 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 cpp-12 amd64 12.3.0-1ubuntu1~22.04
Ign:27 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libasan8 amd64 12.3.0-1ubuntu1~22.04
Ign:28 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libtsan2 amd64 12.3.0-1ubuntu1~22.04
Ign:29 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libgcc-12-dev amd64 12.3.0-1ubuntu1~22.04
Ign:30 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 gcc-12 amd64 12.3.0-1ubuntu1~22.04
Ign:31 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libdpkg-perl all 1.21.1ubuntu2.2
Ign:32 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 make amd64 4.3-4.1build1
Ign:33 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 lto-disabled-list all 24
Ign:34 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 dpkg-dev all 1.21.1ubuntu2.2
Ign:35 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libc-dev-bin amd64 2.35-0ubuntu3.4
Ign:36 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-libc-dev amd64 5.15.0-88.98
Ign:37 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 libcrypt-dev amd64 1:4.4.27-1
Ign:38 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 rpcsvc-proto amd64 1.4.2-0ubuntu6
Ign:39 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libtirpc-dev amd64 1.3.2-2ubuntu0.1
Ign:40 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 libnsl-dev amd64 1.3.0-2build2
Ign:41 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libc6-dev amd64 2.35-0ubuntu3.4
Ign:42 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libstdc++-11-dev amd64 11.4.0-1ubuntu1~22.04
Ign:43 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 g++-11 amd64 11.4.0-1ubuntu1~22.04
Ign:44 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 g++ amd64 4:11.2.0-1ubuntu1
Ign:45 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 build-essential amd64 12.9ubuntu3
Ign:46 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 dctrl-tools amd64 2.24-3build2
Ign:47 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 dkms all 2.8.7-2ubuntu2.2
Ign:48 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 libfakeroot amd64 1.28-1ubuntu1
Ign:49 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 fakeroot amd64 1.28-1ubuntu1
Ign:50 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 liberror-perl all 0.17029-1
Ign:51 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 git-man all 1:2.34.1-1ubuntu1.10
Ign:52 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 git amd64 1:2.34.1-1ubuntu1.10
Ign:53 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 iw amd64 5.16-1build1
Ign:54 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 libalgorithm-diff-perl all 1.201-1
Ign:55 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 libalgorithm-diff-xs-perl amd64 0.04-6build3
Ign:56 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 libalgorithm-merge-perl all 0.08-3
Ign:57 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libc-devtools amd64 2.35-0ubuntu3.4
Ign:58 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 libfile-fcntllock-perl amd64 0.22-3build7
Ign:59 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 manpages-dev all 5.10-1ubuntu1
Ign:1 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 cpp-11 amd64 11.4.0-1ubuntu1~22.04
Ign:2 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 gcc-11-base amd64 11.4.0-1ubuntu1~22.04
Ign:3 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libc6-dbg amd64 2.35-0ubuntu3.4
Ign:4 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libgomp1 amd64 12.3.0-1ubuntu1~22.04
Ign:5 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 gcc-12-base amd64 12.3.0-1ubuntu1~22.04
Ign:6 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libgcc-s1 amd64 12.3.0-1ubuntu1~22.04
Ign:7 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libstdc++6 amd64 12.3.0-1ubuntu1~22.04
Ign:8 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libc6 amd64 2.35-0ubuntu3.4
Ign:9 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libcc1-0 amd64 12.3.0-1ubuntu1~22.04
Ign:10 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 binutils-common amd64 2.38-4ubuntu2.3
Ign:11 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libbinutils amd64 2.38-4ubuntu2.3
Ign:12 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libctf-nobfd0 amd64 2.38-4ubuntu2.3
Ign:13 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libctf0 amd64 2.38-4ubuntu2.3
Ign:14 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 binutils-x86-64-linux-gnu amd64 2.38-4ubuntu2.3
Ign:15 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 binutils amd64 2.38-4ubuntu2.3
Ign:16 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libitm1 amd64 12.3.0-1ubuntu1~22.04
Ign:17 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libatomic1 amd64 12.3.0-1ubuntu1~22.04
Ign:18 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libasan6 amd64 11.4.0-1ubuntu1~22.04
Ign:19 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 liblsan0 amd64 12.3.0-1ubuntu1~22.04
Ign:20 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libtsan0 amd64 11.4.0-1ubuntu1~22.04
Ign:21 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libubsan1 amd64 12.3.0-1ubuntu1~22.04
Ign:22 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libquadmath0 amd64 12.3.0-1ubuntu1~22.04
Ign:23 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libgcc-11-dev amd64 11.4.0-1ubuntu1~22.04
Ign:24 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 gcc-11 amd64 11.4.0-1ubuntu1~22.04
Ign:25 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 gcc amd64 4:11.2.0-1ubuntu1
Ign:26 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 cpp-12 amd64 12.3.0-1ubuntu1~22.04
Ign:27 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libasan8 amd64 12.3.0-1ubuntu1~22.04
Ign:28 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libtsan2 amd64 12.3.0-1ubuntu1~22.04
Ign:29 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libgcc-12-dev amd64 12.3.0-1ubuntu1~22.04
Ign:30 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 gcc-12 amd64 12.3.0-1ubuntu1~22.04
Ign:31 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libdpkg-perl all 1.21.1ubuntu2.2
Ign:32 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 make amd64 4.3-4.1build1
Ign:33 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 lto-disabled-list all 24
Ign:34 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 dpkg-dev all 1.21.1ubuntu2.2
Ign:35 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libc-dev-bin amd64 2.35-0ubuntu3.4
Ign:36 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-libc-dev amd64 5.15.0-88.98
Ign:37 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 libcrypt-dev amd64 1:4.4.27-1
Ign:38 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 rpcsvc-proto amd64 1.4.2-0ubuntu6
Ign:39 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libtirpc-dev amd64 1.3.2-2ubuntu0.1
Ign:40 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 libnsl-dev amd64 1.3.0-2build2
Ign:41 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libc6-dev amd64 2.35-0ubuntu3.4
Ign:42 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libstdc++-11-dev amd64 11.4.0-1ubuntu1~22.04
Ign:43 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 g++-11 amd64 11.4.0-1ubuntu1~22.04
Ign:44 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 g++ amd64 4:11.2.0-1ubuntu1
Ign:45 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 build-essential amd64 12.9ubuntu3
Ign:46 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 dctrl-tools amd64 2.24-3build2
Ign:47 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 dkms all 2.8.7-2ubuntu2.2
Ign:48 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 libfakeroot amd64 1.28-1ubuntu1
Ign:49 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 fakeroot amd64 1.28-1ubuntu1
Ign:50 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 liberror-perl all 0.17029-1
Ign:51 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 git-man all 1:2.34.1-1ubuntu1.10
Ign:52 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 git amd64 1:2.34.1-1ubuntu1.10
Ign:53 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 iw amd64 5.16-1build1
Ign:54 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 libalgorithm-diff-perl all 1.201-1
Ign:55 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 libalgorithm-diff-xs-perl amd64 0.04-6build3
Ign:56 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 libalgorithm-merge-perl all 0.08-3
Ign:57 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libc-devtools amd64 2.35-0ubuntu3.4
Ign:58 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 libfile-fcntllock-perl amd64 0.22-3build7
Ign:59 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 manpages-dev all 5.10-1ubuntu1
Ign:1 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 cpp-11 amd64 11.4.0-1ubuntu1~22.04
Ign:2 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 gcc-11-base amd64 11.4.0-1ubuntu1~22.04
Ign:3 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libc6-dbg amd64 2.35-0ubuntu3.4
Ign:4 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libgomp1 amd64 12.3.0-1ubuntu1~22.04
Ign:5 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 gcc-12-base amd64 12.3.0-1ubuntu1~22.04
Ign:6 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libgcc-s1 amd64 12.3.0-1ubuntu1~22.04
Ign:7 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libstdc++6 amd64 12.3.0-1ubuntu1~22.04
Ign:8 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libc6 amd64 2.35-0ubuntu3.4
Ign:9 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libcc1-0 amd64 12.3.0-1ubuntu1~22.04
Ign:10 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 binutils-common amd64 2.38-4ubuntu2.3
Ign:11 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libbinutils amd64 2.38-4ubuntu2.3
Ign:12 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libctf-nobfd0 amd64 2.38-4ubuntu2.3
Ign:13 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libctf0 amd64 2.38-4ubuntu2.3
Ign:14 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 binutils-x86-64-linux-gnu amd64 2.38-4ubuntu2.3
Ign:15 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 binutils amd64 2.38-4ubuntu2.3
Ign:16 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libitm1 amd64 12.3.0-1ubuntu1~22.04
Ign:17 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libatomic1 amd64 12.3.0-1ubuntu1~22.04
Ign:18 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libasan6 amd64 11.4.0-1ubuntu1~22.04
Ign:19 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 liblsan0 amd64 12.3.0-1ubuntu1~22.04
Ign:20 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libtsan0 amd64 11.4.0-1ubuntu1~22.04
Ign:21 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libubsan1 amd64 12.3.0-1ubuntu1~22.04
Ign:22 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libquadmath0 amd64 12.3.0-1ubuntu1~22.04
Ign:23 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libgcc-11-dev amd64 11.4.0-1ubuntu1~22.04
Ign:24 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 gcc-11 amd64 11.4.0-1ubuntu1~22.04
Ign:25 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 gcc amd64 4:11.2.0-1ubuntu1
Ign:26 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 cpp-12 amd64 12.3.0-1ubuntu1~22.04
Ign:27 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libasan8 amd64 12.3.0-1ubuntu1~22.04
Ign:28 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libtsan2 amd64 12.3.0-1ubuntu1~22.04
Ign:29 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libgcc-12-dev amd64 12.3.0-1ubuntu1~22.04
Ign:30 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 gcc-12 amd64 12.3.0-1ubuntu1~22.04
Ign:31 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libdpkg-perl all 1.21.1ubuntu2.2
Ign:32 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 make amd64 4.3-4.1build1
Ign:33 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 lto-disabled-list all 24
Ign:34 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 dpkg-dev all 1.21.1ubuntu2.2
Ign:35 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libc-dev-bin amd64 2.35-0ubuntu3.4
Ign:36 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-libc-dev amd64 5.15.0-88.98
Ign:37 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 libcrypt-dev amd64 1:4.4.27-1
Ign:38 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 rpcsvc-proto amd64 1.4.2-0ubuntu6
Ign:39 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libtirpc-dev amd64 1.3.2-2ubuntu0.1
Ign:40 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 libnsl-dev amd64 1.3.0-2build2
Ign:41 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libc6-dev amd64 2.35-0ubuntu3.4
Ign:42 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libstdc++-11-dev amd64 11.4.0-1ubuntu1~22.04
Ign:43 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 g++-11 amd64 11.4.0-1ubuntu1~22.04
Ign:44 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 g++ amd64 4:11.2.0-1ubuntu1
Ign:45 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 build-essential amd64 12.9ubuntu3
Ign:46 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 dctrl-tools amd64 2.24-3build2
Ign:47 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 dkms all 2.8.7-2ubuntu2.2
Ign:48 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 libfakeroot amd64 1.28-1ubuntu1
Ign:49 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 fakeroot amd64 1.28-1ubuntu1
Ign:50 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 liberror-perl all 0.17029-1
Ign:51 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 git-man all 1:2.34.1-1ubuntu1.10
Ign:52 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 git amd64 1:2.34.1-1ubuntu1.10
Ign:53 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 iw amd64 5.16-1build1
Ign:54 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 libalgorithm-diff-perl all 1.201-1
Ign:55 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 libalgorithm-diff-xs-perl amd64 0.04-6build3
Ign:56 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 libalgorithm-merge-perl all 0.08-3
Ign:57 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libc-devtools amd64 2.35-0ubuntu3.4
Ign:58 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 libfile-fcntllock-perl amd64 0.22-3build7
Ign:59 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 manpages-dev all 5.10-1ubuntu1
Ign:1 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 cpp-11 amd64 11.4.0-1ubuntu1~22.04
Ign:2 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 gcc-11-base amd64 11.4.0-1ubuntu1~22.04
Ign:3 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libc6-dbg amd64 2.35-0ubuntu3.4
Err:1 http://security.ubuntu.com/ubuntu jammy-updates/main amd64 cpp-11 amd64 11.4.0-1ubuntu1~22.04
  Temporary failure resolving 'ca.archive.ubuntu.com'
Ign:4 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libgomp1 amd64 12.3.0-1ubuntu1~22.04
Ign:5 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 gcc-12-base amd64 12.3.0-1ubuntu1~22.04
Err:2 http://security.ubuntu.com/ubuntu jammy-updates/main amd64 gcc-11-base amd64 11.4.0-1ubuntu1~22.04
  Temporary failure resolving 'ca.archive.ubuntu.com'
Ign:6 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libgcc-s1 amd64 12.3.0-1ubuntu1~22.04
Err:3 http://security.ubuntu.com/ubuntu jammy-updates/main amd64 libc6-dbg amd64 2.35-0ubuntu3.4
  Temporary failure resolving 'ca.archive.ubuntu.com'
Ign:7 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libstdc++6 amd64 12.3.0-1ubuntu1~22.04
Err:4 http://security.ubuntu.com/ubuntu jammy-updates/main amd64 libgomp1 amd64 12.3.0-1ubuntu1~22.04
  Temporary failure resolving 'ca.archive.ubuntu.com'
Ign:8 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libc6 amd64 2.35-0ubuntu3.4
Err:5 http://security.ubuntu.com/ubuntu jammy-updates/main amd64 gcc-12-base amd64 12.3.0-1ubuntu1~22.04
  Temporary failure resolving 'ca.archive.ubuntu.com'
Ign:9 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libcc1-0 amd64 12.3.0-1ubuntu1~22.04
Ign:10 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 binutils-common amd64 2.38-4ubuntu2.3
Err:6 http://security.ubuntu.com/ubuntu jammy-updates/main amd64 libgcc-s1 amd64 12.3.0-1ubuntu1~22.04
  Temporary failure resolving 'ca.archive.ubuntu.com'
Ign:11 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libbinutils amd64 2.38-4ubuntu2.3
Err:7 http://security.ubuntu.com/ubuntu jammy-updates/main amd64 libstdc++6 amd64 12.3.0-1ubuntu1~22.04
  Temporary failure resolving 'ca.archive.ubuntu.com'
Err:8 http://security.ubuntu.com/ubuntu jammy-updates/main amd64 libc6 amd64 2.35-0ubuntu3.4
  Temporary failure resolving 'ca.archive.ubuntu.com'
Err:9 http://security.ubuntu.com/ubuntu jammy-updates/main amd64 libcc1-0 amd64 12.3.0-1ubuntu1~22.04
  Temporary failure resolving 'ca.archive.ubuntu.com'
Err:10 http://security.ubuntu.com/ubuntu jammy-updates/main amd64 binutils-common amd64 2.38-4ubuntu2.3
  Temporary failure resolving 'ca.archive.ubuntu.com'
Err:11 http://security.ubuntu.com/ubuntu jammy-updates/main amd64 libbinutils amd64 2.38-4ubuntu2.3
  Temporary failure resolving 'ca.archive.ubuntu.com'
Ign:12 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libctf-nobfd0 amd64 2.38-4ubuntu2.3
Ign:13 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libctf0 amd64 2.38-4ubuntu2.3
Err:12 http://security.ubuntu.com/ubuntu jammy-updates/main amd64 libctf-nobfd0 amd64 2.38-4ubuntu2.3
  Temporary failure resolving 'ca.archive.ubuntu.com'
Ign:14 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 binutils-x86-64-linux-gnu amd64 2.38-4ubuntu2.3
Err:13 http://security.ubuntu.com/ubuntu jammy-updates/main amd64 libctf0 amd64 2.38-4ubuntu2.3
  Temporary failure resolving 'ca.archive.ubuntu.com'
Ign:15 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 binutils amd64 2.38-4ubuntu2.3
Err:14 http://security.ubuntu.com/ubuntu jammy-updates/main amd64 binutils-x86-64-linux-gnu amd64 2.38-4ubuntu2.3
  Temporary failure resolving 'ca.archive.ubuntu.com'
Ign:16 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libitm1 amd64 12.3.0-1ubuntu1~22.04
Err:15 http://security.ubuntu.com/ubuntu jammy-updates/main amd64 binutils amd64 2.38-4ubuntu2.3
  Temporary failure resolving 'ca.archive.ubuntu.com'
Ign:17 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libatomic1 amd64 12.3.0-1ubuntu1~22.04
Ign:18 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libasan6 amd64 11.4.0-1ubuntu1~22.04
Err:16 http://security.ubuntu.com/ubuntu jammy-updates/main amd64 libitm1 amd64 12.3.0-1ubuntu1~22.04
  Temporary failure resolving 'ca.archive.ubuntu.com'
Ign:19 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 liblsan0 amd64 12.3.0-1ubuntu1~22.04
Err:17 http://security.ubuntu.com/ubuntu jammy-updates/main amd64 libatomic1 amd64 12.3.0-1ubuntu1~22.04
  Temporary failure resolving 'ca.archive.ubuntu.com'
Ign:20 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libtsan0 amd64 11.4.0-1ubuntu1~22.04
Err:18 http://security.ubuntu.com/ubuntu jammy-updates/main amd64 libasan6 amd64 11.4.0-1ubuntu1~22.04
  Temporary failure resolving 'ca.archive.ubuntu.com'
Err:19 http://security.ubuntu.com/ubuntu jammy-updates/main amd64 liblsan0 amd64 12.3.0-1ubuntu1~22.04
  Temporary failure resolving 'ca.archive.ubuntu.com'
Ign:21 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libubsan1 amd64 12.3.0-1ubuntu1~22.04
Err:20 http://security.ubuntu.com/ubuntu jammy-updates/main amd64 libtsan0 amd64 11.4.0-1ubuntu1~22.04
  Temporary failure resolving 'ca.archive.ubuntu.com'
Ign:22 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libquadmath0 amd64 12.3.0-1ubuntu1~22.04
Err:21 http://security.ubuntu.com/ubuntu jammy-updates/main amd64 libubsan1 amd64 12.3.0-1ubuntu1~22.04
  Temporary failure resolving 'ca.archive.ubuntu.com'
Err:22 http://security.ubuntu.com/ubuntu jammy-updates/main amd64 libquadmath0 amd64 12.3.0-1ubuntu1~22.04
  Temporary failure resolving 'ca.archive.ubuntu.com'
Ign:23 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libgcc-11-dev amd64 11.4.0-1ubuntu1~22.04
Err:23 http://security.ubuntu.com/ubuntu jammy-updates/main amd64 libgcc-11-dev amd64 11.4.0-1ubuntu1~22.04
  Temporary failure resolving 'ca.archive.ubuntu.com'
Ign:24 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 gcc-11 amd64 11.4.0-1ubuntu1~22.04
Err:24 http://security.ubuntu.com/ubuntu jammy-updates/main amd64 gcc-11 amd64 11.4.0-1ubuntu1~22.04
  Temporary failure resolving 'ca.archive.ubuntu.com'
Err:25 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 gcc amd64 4:11.2.0-1ubuntu1
  Temporary failure resolving 'ca.archive.ubuntu.com'
Ign:26 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 cpp-12 amd64 12.3.0-1ubuntu1~22.04
Err:26 http://security.ubuntu.com/ubuntu jammy-updates/main amd64 cpp-12 amd64 12.3.0-1ubuntu1~22.04
  Temporary failure resolving 'ca.archive.ubuntu.com'
Ign:27 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libasan8 amd64 12.3.0-1ubuntu1~22.04
Err:27 http://security.ubuntu.com/ubuntu jammy-updates/main amd64 libasan8 amd64 12.3.0-1ubuntu1~22.04
  Temporary failure resolving 'ca.archive.ubuntu.com'
Ign:28 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libtsan2 amd64 12.3.0-1ubuntu1~22.04
Err:28 http://security.ubuntu.com/ubuntu jammy-updates/main amd64 libtsan2 amd64 12.3.0-1ubuntu1~22.04
  Temporary failure resolving 'ca.archive.ubuntu.com'
Ign:29 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libgcc-12-dev amd64 12.3.0-1ubuntu1~22.04
Err:29 http://security.ubuntu.com/ubuntu jammy-updates/main amd64 libgcc-12-dev amd64 12.3.0-1ubuntu1~22.04
  Temporary failure resolving 'ca.archive.ubuntu.com'
Ign:30 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 gcc-12 amd64 12.3.0-1ubuntu1~22.04
Err:30 http://security.ubuntu.com/ubuntu jammy-updates/main amd64 gcc-12 amd64 12.3.0-1ubuntu1~22.04
  Temporary failure resolving 'ca.archive.ubuntu.com'
Ign:31 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libdpkg-perl all 1.21.1ubuntu2.2
Err:31 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libdpkg-perl all 1.21.1ubuntu2.2
  Temporary failure resolving 'ca.archive.ubuntu.com'
Err:32 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 make amd64 4.3-4.1build1
  Temporary failure resolving 'ca.archive.ubuntu.com'
Ign:33 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 lto-disabled-list all 24
Err:33 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 lto-disabled-list all 24
  Temporary failure resolving 'ca.archive.ubuntu.com'
Ign:34 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 dpkg-dev all 1.21.1ubuntu2.2
Err:34 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 dpkg-dev all 1.21.1ubuntu2.2
  Temporary failure resolving 'ca.archive.ubuntu.com'
Ign:35 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libc-dev-bin amd64 2.35-0ubuntu3.4
Ign:36 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 linux-libc-dev amd64 5.15.0-88.98
Err:35 http://security.ubuntu.com/ubuntu jammy-updates/main amd64 libc-dev-bin amd64 2.35-0ubuntu3.4
  Temporary failure resolving 'ca.archive.ubuntu.com'
Err:36 http://security.ubuntu.com/ubuntu jammy-updates/main amd64 linux-libc-dev amd64 5.15.0-88.98
  Temporary failure resolving 'ca.archive.ubuntu.com'
Err:37 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 libcrypt-dev amd64 1:4.4.27-1
  Temporary failure resolving 'ca.archive.ubuntu.com'
Err:38 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 rpcsvc-proto amd64 1.4.2-0ubuntu6
  Temporary failure resolving 'ca.archive.ubuntu.com'
Ign:39 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libtirpc-dev amd64 1.3.2-2ubuntu0.1
Err:39 http://security.ubuntu.com/ubuntu jammy-updates/main amd64 libtirpc-dev amd64 1.3.2-2ubuntu0.1
  Temporary failure resolving 'ca.archive.ubuntu.com'
Err:40 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 libnsl-dev amd64 1.3.0-2build2
  Temporary failure resolving 'ca.archive.ubuntu.com'
Ign:41 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libc6-dev amd64 2.35-0ubuntu3.4
Err:41 http://security.ubuntu.com/ubuntu jammy-updates/main amd64 libc6-dev amd64 2.35-0ubuntu3.4
  Temporary failure resolving 'ca.archive.ubuntu.com'
Ign:42 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libstdc++-11-dev amd64 11.4.0-1ubuntu1~22.04
Err:42 http://security.ubuntu.com/ubuntu jammy-updates/main amd64 libstdc++-11-dev amd64 11.4.0-1ubuntu1~22.04
  Temporary failure resolving 'ca.archive.ubuntu.com'
Ign:43 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 g++-11 amd64 11.4.0-1ubuntu1~22.04
Err:43 http://security.ubuntu.com/ubuntu jammy-updates/main amd64 g++-11 amd64 11.4.0-1ubuntu1~22.04
  Temporary failure resolving 'ca.archive.ubuntu.com'
Err:44 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 g++ amd64 4:11.2.0-1ubuntu1
  Temporary failure resolving 'ca.archive.ubuntu.com'
Err:45 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 build-essential amd64 12.9ubuntu3
  Temporary failure resolving 'ca.archive.ubuntu.com'
Err:46 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 dctrl-tools amd64 2.24-3build2
  Temporary failure resolving 'ca.archive.ubuntu.com'
Ign:47 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 dkms all 2.8.7-2ubuntu2.2
Err:48 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 libfakeroot amd64 1.28-1ubuntu1
  Temporary failure resolving 'ca.archive.ubuntu.com'
Err:47 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 dkms all 2.8.7-2ubuntu2.2
  Temporary failure resolving 'ca.archive.ubuntu.com'
Err:49 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 fakeroot amd64 1.28-1ubuntu1
  Temporary failure resolving 'ca.archive.ubuntu.com'
Ign:50 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 liberror-perl all 0.17029-1
Err:50 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 liberror-perl all 0.17029-1
  Temporary failure resolving 'ca.archive.ubuntu.com'
Ign:51 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 git-man all 1:2.34.1-1ubuntu1.10
Err:52 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 git amd64 1:2.34.1-1ubuntu1.10
  Temporary failure resolving 'ca.archive.ubuntu.com'
Err:53 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 iw amd64 5.16-1build1
  Temporary failure resolving 'ca.archive.ubuntu.com'
Err:51 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 git-man all 1:2.34.1-1ubuntu1.10
  Temporary failure resolving 'ca.archive.ubuntu.com'
Ign:54 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 libalgorithm-diff-perl all 1.201-1
Err:55 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 libalgorithm-diff-xs-perl amd64 0.04-6build3
  Temporary failure resolving 'ca.archive.ubuntu.com'
Ign:56 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 libalgorithm-merge-perl all 0.08-3
Ign:57 http://ca.archive.ubuntu.com/ubuntu jammy-updates/main amd64 libc-devtools amd64 2.35-0ubuntu3.4
Err:54 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 libalgorithm-diff-perl all 1.201-1
  Temporary failure resolving 'ca.archive.ubuntu.com'
Err:58 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 libfile-fcntllock-perl amd64 0.22-3build7
  Temporary failure resolving 'ca.archive.ubuntu.com'
Err:57 http://security.ubuntu.com/ubuntu jammy-updates/main amd64 libc-devtools amd64 2.35-0ubuntu3.4
  Temporary failure resolving 'ca.archive.ubuntu.com'
Ign:59 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 manpages-dev all 5.10-1ubuntu1
Err:56 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 libalgorithm-merge-perl all 0.08-3
  Temporary failure resolving 'ca.archive.ubuntu.com'
Err:59 http://ca.archive.ubuntu.com/ubuntu jammy/main amd64 manpages-dev all 5.10-1ubuntu1
  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/gcc-11/cpp-11_11.4.0-1ubuntu1%7e22.04_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/gcc-11/gcc-11-base_11.4.0-1ubuntu1%7e22.04_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dbg_2.35-0ubuntu3.4_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/gcc-12/libgomp1_12.3.0-1ubuntu1%7e22.04_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/gcc-12/gcc-12-base_12.3.0-1ubuntu1%7e22.04_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/gcc-12/libgcc-s1_12.3.0-1ubuntu1%7e22.04_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/gcc-12/libstdc%2b%2b6_12.3.0-1ubuntu1%7e22.04_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.35-0ubuntu3.4_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/gcc-12/libcc1-0_12.3.0-1ubuntu1%7e22.04_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/b/binutils/binutils-common_2.38-4ubuntu2.3_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/b/binutils/libbinutils_2.38-4ubuntu2.3_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/b/binutils/libctf-nobfd0_2.38-4ubuntu2.3_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/b/binutils/libctf0_2.38-4ubuntu2.3_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/b/binutils/binutils-x86-64-linux-gnu_2.38-4ubuntu2.3_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/b/binutils/binutils_2.38-4ubuntu2.3_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/gcc-12/libitm1_12.3.0-1ubuntu1%7e22.04_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/gcc-12/libatomic1_12.3.0-1ubuntu1%7e22.04_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/gcc-11/libasan6_11.4.0-1ubuntu1%7e22.04_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/gcc-12/liblsan0_12.3.0-1ubuntu1%7e22.04_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/gcc-11/libtsan0_11.4.0-1ubuntu1%7e22.04_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/gcc-12/libubsan1_12.3.0-1ubuntu1%7e22.04_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/gcc-12/libquadmath0_12.3.0-1ubuntu1%7e22.04_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/gcc-11/libgcc-11-dev_11.4.0-1ubuntu1%7e22.04_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/gcc-11/gcc-11_11.4.0-1ubuntu1%7e22.04_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/gcc_11.2.0-1ubuntu1_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/gcc-12/cpp-12_12.3.0-1ubuntu1%7e22.04_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/gcc-12/libasan8_12.3.0-1ubuntu1%7e22.04_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/gcc-12/libtsan2_12.3.0-1ubuntu1%7e22.04_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/gcc-12/libgcc-12-dev_12.3.0-1ubuntu1%7e22.04_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/gcc-12/gcc-12_12.3.0-1ubuntu1%7e22.04_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/libdpkg-perl_1.21.1ubuntu2.2_all.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/m/make-dfsg/make_4.3-4.1build1_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/l/lto-disabled-list/lto-disabled-list_24_all.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/d/dpkg/dpkg-dev_1.21.1ubuntu2.2_all.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/glibc/libc-dev-bin_2.35-0ubuntu3.4_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_5.15.0-88.98_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/libx/libxcrypt/libcrypt-dev_4.4.27-1_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/r/rpcsvc-proto/rpcsvc-proto_1.4.2-0ubuntu6_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/libt/libtirpc/libtirpc-dev_1.3.2-2ubuntu0.1_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/libn/libnsl/libnsl-dev_1.3.0-2build2_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/glibc/libc6-dev_2.35-0ubuntu3.4_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/gcc-11/libstdc%2b%2b-11-dev_11.4.0-1ubuntu1%7e22.04_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/gcc-11/g%2b%2b-11_11.4.0-1ubuntu1%7e22.04_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/g/gcc-defaults/g%2b%2b_11.2.0-1ubuntu1_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/b/build-essential/build-essential_12.9ubuntu3_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/d/dctrl-tools/dctrl-tools_2.24-3build2_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.8.7-2ubuntu2.2_all.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/f/fakeroot/libfakeroot_1.28-1ubuntu1_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/f/fakeroot/fakeroot_1.28-1ubuntu1_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/libe/liberror-perl/liberror-perl_0.17029-1_all.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/g/git/git-man_2.34.1-1ubuntu1.10_all.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/g/git/git_2.34.1-1ubuntu1.10_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/i/iw/iw_5.16-1build1_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/liba/libalgorithm-diff-perl/libalgorithm-diff-perl_1.201-1_all.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/liba/libalgorithm-diff-xs-perl/libalgorithm-diff-xs-perl_0.04-6build3_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/liba/libalgorithm-merge-perl/libalgorithm-merge-perl_0.08-3_all.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/g/glibc/libc-devtools_2.35-0ubuntu3.4_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/libf/libfile-fcntllock-perl/libfile-fcntllock-perl_0.22-3build7_amd64.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Failed to fetch http://ca.archive.ubuntu.com/ubuntu/pool/main/m/manpages/manpages-dev_5.10-1ubuntu1_all.deb  Temporary failure resolving 'ca.archive.ubuntu.com'
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.



sandman@sandman-HP-Compaq-6005-Pro-MT-PC:~$ sudo apt install -y build-essential dkms git iw
cd ~/
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 4588 (unattended-upgr)      
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 4588 (unattended-upgr)      
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 4588 (unattended-upgr)      
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 4588 (unattended-upgr)      
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 4588 (unattended-upgr)      
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 4588 (unattended-upgr)      
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 4588 (unattended-upgr)      
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 4588 (unattended-upgr)      
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 4588 (unattended-upgr)      
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 4588 (unattended-upgr)      
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 4588 (unattended-upgr)       
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 4588 (unattended-upgr)       
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 4588 (unattended-upgr)       
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 4588 (unattended-upgr)       
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 4588 (unattended-upgr)       
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 4588 (unattended-upgr)       
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 4588 (unattended-upgr)       
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 4588 (unattended-upgr)       
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 4588 (unattended-upgr)       
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 4588 (unattended-upgr)       
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 4588 (unattended-upgr)       
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 4588 (unattended-upgr)       
Waiting for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 4588 (unattended-upgr)       
^Citing for cache lock: Could not get lock /var/lib/dpkg/lock-frontend. It is held by process 4588 (unattended-upgr)... 23s

```

---

### Post by MAFoElffen on 2023-11-18
@D3astator... 

By the prompt of this one, I see "HP-Compaq-6005-Pro-MT" ... But that couldn't be, because that is a mid-tower desktop, not a laptop. You said "laptop"... FYI, I know that mid-tower desktop did not come with wireless.

What is the make and model of the USB wireless device that you are using? How does it show up in
```

lsusb -vvv

```
Take a photo of the output


What is the make and model of this "laptop"?

---

### Post by d3vestator on 2023-11-18
its desktop(hp) thats the issue, not the laptop, the first time i said laptop was in the #5 thread, in which the command i was given by @Yellow Pasque in thread #4 required internet which the hp-compaq(the desktop im trying to use doesnt have wifi) so i asked if i could install the command i was given in #4 to my laptop because it has wifi and so then if i could carry the download to a usb, so i can run it on a hp desktop, but then @Jeremy31 suggested if i could use usb tethering to connect to the hp from my phone which worked and then i tried the commands and thats the errors.


here is the output of lsusb -vvv
i am using usb tethering

```

Bus 001 Device 003: ID 2001:331c D-Link Corp. 802.11ac NIC
Couldn't open device, some information will be missing
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.10
  bDeviceClass            0 
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x2001 D-Link Corp.
  idProduct          0x331c 
  bcdDevice            2.10
  iManufacturer           1 
  iProduct                2 802.11ac NIC
  iSerial                 3 123456
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength       0x0035
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           5
      bInterfaceClass       255 Vendor Specific Class
      bInterfaceSubClass    255 Vendor Specific Subclass
      bInterfaceProtocol    255 Vendor Specific Protocol
      iInterface              2 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x84  EP 4 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x05  EP 5 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x06  EP 6 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x87  EP 7 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               3
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x08  EP 8 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0200  1x 512 bytes
        bInterval               0


```

---

### Post by MAFoElffen on 2023-11-18
This is the info on that:
```

{USB_DEVICE(0x2001, 0x331c), RTL8822B}, /* D-Link DWA-182 rev D1 */

```
The chipset is a Realtek RTL8822B

Instructions:
```

sudo apt-get update
sudo apt-get install make gcc linux-headers-$(uname -r) build-essential git
git clone https://github.com/lwfinger/rtw88.git
cd rtw88
make
sudo make install
sudo reboot

```
After it reboots
```

lsmod | grep 'rtw'

```
Then look for it in your settings and try to connect to your wireless access point.

---

### Post by d3vestator on 2023-11-18
i see the wifi settings, but the connection is never made, the gear just keeps moving and eventually it just disappears
any idea?

---

### Post by MAFoElffen on 2023-11-18
Please post the results of (substitute the device name of your wifi device....)
```

sudo iwlist wlp3s0 scan | grep -v 'IE'
modinfo rtw
iw list

```

---

### Post by d3vestator on 2023-11-19
```

andman@sandman-HP-Compaq-6005-Pro-MT-PC:~$ sudo iwlist wlxf0b4d25b1805 scan | grep -v 'IE'
[sudo] password for sandman: 
Sorry, try again.
[sudo] password for sandman: 
wlxf0b4d25b1805  Scan completed :
          Cell 01 - Address: 26:08:F5:EC:0A:59
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"BELL665-5G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000003894f858180
                    Extra: Last beacon: 3808ms ago
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: A0:FF:70:72:20:19
                    Channel:157
                    Frequency:5.785 GHz
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000333ab6ec23
                    Extra: Last beacon: 4840ms ago
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 03 - Address: A0:FF:70:72:20:17
                    Channel:157
                    Frequency:5.785 GHz
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000333afac005
                    Extra: Last beacon: 392ms ago
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: A0:FF:70:72:20:0D
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000333ac0c003
                    Extra: Last beacon: 4192ms ago
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: A0:FF:70:72:20:11
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000333ac0c190
                    Extra: Last beacon: 4192ms ago
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 06 - Address: 62:45:B6:1D:4C:45
                    Channel:40
                    Frequency:5.2 GHz (Channel 40)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:""
                    Mode:Master
                    Extra:tsf=000000086c72b4e7
                    Extra: Last beacon: 2888ms ago
          Cell 07 - Address: xx:xx:xx:xx:xx
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000333ac0a00a
                    Extra: Last beacon: 4200ms ago
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 08 - Address: xx:xx:xx:xx:xx:xx
                    Channel:157
                    Frequency:5.785 GHz
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000333afb8c33
                    Extra: Last beacon: 340ms ago
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 09 - Address: 26:08:F5:EC:0A:5A
                    Channel:44
                    Frequency:5.22 GHz (Channel 44)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"BELL665-5G"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000388d60e303b
                    Extra: Last beacon: 7316ms ago
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 10 - Address: 1A:1E:19:0F:04:61
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"BELL665-5G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000038950b4a208
                    Extra: Last beacon: 3824ms ago
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

sandman@sandman-HP-Compaq-6005-Pro-MT-PC:~$ modinfo rtx
modinfo: ERROR: Module rtx not found.
sandman@sandman-HP-Compaq-6005-Pro-MT-PC:~$ iwlist
Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 
sandman@sandman-HP-Compaq-6005-Pro-MT-PC:~$ 

```

---

### Post by MAFoElffen on 2023-11-20
Please post the output of this
```

lsmod | grep rtw
find/usr/lib/modules -name rtx*

```

---

### Post by d3vestator on 2023-11-20
both commands gave no output, 
not sure if the rtx refers to the gpu, because were trying to figure out the problem on the hp, not my asus laptop that had previous issues before

---

### Post by Yellow Pasque on 2023-11-20
I think it was supposed to be rtw and not rtx. Don't quote me on that.

---

### Post by MAFoElffen on 2023-11-20
yes, Typo... "rtw"... Checking to ensure that driver that you installed in Post #10 is loaded to the kernel.

---

### Post by d3vestator on 2023-11-20
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293095&stc=1[/IMG]   looks like the its there

---

### Post by MAFoElffen on 2023-11-20
The rtw module is loaded to the kernel... Which one of the access point in Post #13 (Cell XX) is your Wireless Access Point?

---

### Post by d3vestator on 2023-11-20
i perfer not to say if dont have to, but i do know which one

---

### Post by d3vestator on 2023-11-23
cell 07 or cell08 not sure which conenction that i use, most likely the 2.4, so cell07

---

### Post by MAFoElffen on 2023-11-23
do 
```

ip a

```
Find your wireless device name, and use it in the next command
```

iwlist <device_name> channel | grep 'Channel 1 \|Channel 157 '

```
If it has no output, then do it without the filter
```

iwlist <device_name> channel

```
The check your wireless access point and see which channels it can be set to that are within that range and frequency.

---

### Post by d3vestator on 2023-11-24
it doesnt have a channel when i check iw <device name > info,


when i type ip a this is what it says
```

2: wlxf0b4d25b1805: <NO-CARRIER,BROADCAST,MULTICAST,UP,> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether f0:b4:d2:5b:18:05 brd ff:ff:ff:ff:ff:ff






```
it looks like my computer is not getting a ip address, as you could up top, there is no inet

---

### Post by MAFoElffen on 2023-11-25
It is dhcp... It is not going to get an Ip address until it logs into your local wifi network to get that information, right?

```

iwlist wlxf0b4d25b1805 channel
ip l set wlxf0b4d25b1805 up
rfkill list all
sudo dmesg | grep 'rtw'

```

---

### Post by d3vestator on 2023-11-25
```

sandman@sandman-HP-Compaq-6005-Pro-MT-PC:~$ iwlist wlxf0b4d25b1805 channe;
wlxf0b4d25b1805  32 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
sandman@sandman-HP-Compaq-6005-Pro-MT-PC:~$ ip l set wlxf0b4d25b1805 up
RTNETLINK answers: Operation not permitted
sandman@sandman-HP-Compaq-6005-Pro-MT-PC:~$ sudo ip l set wlxf0b4d25b1805 up
sandman@sandman-HP-Compaq-6005-Pro-MT-PC:~$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp63s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN group default qlen 1000
    link/ether 1c:c1:de:61:c6:56 brd ff:ff:ff:ff:ff:ff
5: wlxf0b4d25b1805: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether f0:b4:d2:5b:18:05 brd ff:ff:ff:ff:ff:ff
sandman@sandman-HP-Compaq-6005-Pro-MT-PC:~$ rfkill list all
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```
last command is very long, just tell me what you are looking for

---

### Post by MAFoElffen on 2023-11-25
In that case
```

sudo dmesg | grep 'rtw' | nc termbin.com 9999

```
Please post the URL

---

### Post by d3vestator on 2023-11-25
[https://termbin.com/8h3db](https://termbin.com/8h3db)
i also found the wifi disc installation but there is no drivers for linux

---

### Post by MAFoElffen on 2023-11-26
I think it still has a build error
```

[   16.700116] rtw_core: loading out-of-tree module taints kernel.
[COLOR=#ff0000][   16.700759] rtw_core: module verification failed: signature and/or required key missing - tainting kernel[/COLOR]
[   17.699247] rtw_8822bu 2-2:1.0: Firmware version 27.2.0, H2C version 13
[   18.071030] usbcore: registered new interface driver rtw_8822bu
[   18.105757] rtw_8822bu 2-2:1.0 wlxf0b4d25b1805: renamed from wlan0

```
I messaged jeremy31 to ask him if he has ideas on this error...

---

### Post by Yellow Pasque on 2023-11-26
"tainting kernel" is not something you need to worry about unless you're filing a bug report on the Linux kernel bugzilla (or somewhere else that demands kernels without external modules).

I think OP should uninstall the rtw88 driver and try the one I linked to in post #4, but maybe I don't have enough patience for troubleshooting things that don't work right away.

---

### Post by MAFoElffen on 2023-11-26
@Yellow Pasque --

Jermemy31 also confirmed that isn't a problem, just a warning message. That the module is loaded, gets a device name, is doing a scan and is "seeing things"... That there must be something else going on...

Try this first:
```

sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
echo options rtw_core disable_lps_deep=Y"|sudo tee /etc/modprobe.d/rtw_core.conf

```
Then reboot and test again. That will see if it is a problem with power management...

Jeremy31 asked that you run and post the wireless script: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by d3vestator on 2023-11-27
[https://paste.ubuntu.com/p/ZcVPpXtBbQ/](https://paste.ubuntu.com/p/ZcVPpXtBbQ/)
i rebooted the machine after trying the commands and nothing happened

i can also confirm that whenever the pc boots up it display a Time & and date not set error saying that the onboard battery might not working

---

### Post by MAFoElffen on 2023-11-28
That CMOS battery is going to need to be corrected first. That screws with any file timestamps.

---

### Post by d3vestator on 2023-11-28
are you saying i have to replace it? if thats the case im not going to bother with it. what i dont understand is why the battrey would cause any issue with the wifi. the hp desktop is dual booted with windows, and that os work fine with the wifi adapter

---

### Post by jeremy31 on 2023-11-28
Is it Windows 10 or 11?  Is the hybrid shutdown in Windows disabled?

---

### Post by d3vestator on 2023-11-28
windows 10 and disabled fast startup

---

### Post by Yellow Pasque on 2023-11-29
You should replace the battery before you have issues with BIOS/CMOS settings. It's cheap and (usually) very easy. It shouldn't affect your wireless adapter if the computer boots though.

---

### Post by d3vestator on 2023-11-29
i totally understand what you mean, however i dont use the computer enough, i have my laptop if i need to do something, i just use teh  the desktop to try things out, besides i just mostly use the optical drive in it. its a 13 year old computer and from how much i use it, its not worth replacing overthought its a cheap replacement. the last time i booted it besides last week would've been a year and a half ago.

---

