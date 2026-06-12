---
title: "Chrony on Ubuntu"
date: 2019-11-12
forum: General Help
---

### Post by linuxenthusiast on 2019-11-12
Hello

I am looking to install the Chrony NTP service in order to synchronize time on my Ubuntu machine.

Is Chrony available on Ubuntu? Any steps on how to get it easily?

Thanks

---

### Post by howefield on 2019-11-12
Chrony can be found in the Ubuntu repositories..

```
apt-cache show chrony
Package: chrony
Architecture: amd64
Version: 3.5-2ubuntu2
Priority: extra
Section: admin
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Vincent Blut <vincent.debian@free.fr>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 519
Provides: time-daemon
Pre-Depends: init-system-helpers (>= 1.54~)
Depends: adduser, iproute2, libcap2-bin, ucf, libc6 (>= 2.29), libcap2 (>= 1:2.10), libedit2 (>= 2.11-20080614-0), libnettle6 (>= 3.4~), libseccomp2 (>= 2.2.3-3~)
Suggests: dnsutils, networkd-dispatcher
Conflicts: ntp, time-daemon
Replaces: time-daemon
Filename: pool/main/c/chrony/chrony_3.5-2ubuntu2_amd64.deb
Size: 220756
MD5sum: 3d718616efae97171180412943496302
SHA1: 686a61f1fe7da7f82e43d4c1ec7f0be181f42498
SHA256: d9420d903a64dae47f7da48c6721a0528e42689dd2161858f489d008084531da
Homepage: https://chrony.tuxfamily.org
Description-en: Versatile implementation of the Network Time Protocol
 It consists of a pair of programs:
 .
 chronyd:  This is a daemon which runs in background on the system.
 It obtains measurements (e.g. via the network) of the system's offset
 relative to other systems and adjusts the system time accordingly. For
 isolated systems, the user can periodically enter the correct time by
 hand (using 'chronyc'). In either case 'chronyd' determines the rate
 at which the computer gains or loses time, and compensates for this.
 Chronyd implements the NTP protocol and can act as either a client or
 a server.
 .
 chronyc: This is a command-line driven control and monitoring program.
 An administrator can use this to fine-tune various parameters within
 the daemon, add or delete servers etc whilst the daemon is running.
Description-md5: f0bbbeab28dbc2e9fe201d3d79df8c96
Supported: 9m

```

---

