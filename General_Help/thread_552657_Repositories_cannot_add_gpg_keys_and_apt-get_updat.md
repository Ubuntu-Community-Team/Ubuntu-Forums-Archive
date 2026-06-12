---
title: "Repositories cannot add gpg keys and apt-get update"
date: 2007-09-16
forum: General Help
---

### Post by true_friend on 2007-09-16
Hi folks
I was getting errors for many days. Some of the repositories were seemed to be closed (ubuntu official ones). Whenever I updated (apt-get update) some repositories were unable to be fetched. Yesterday I changed the whole list by adding new repositories from the online repository list of Ubuntu. Now gpg keys are creating problem. this is the output of apt-get update
> ss@ss-desktop:~$ sudo apt-get update
Password:
Get:1 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release.gpg [189B]
Get:2 [http://mirror2.ubuntulinux.nl](http://mirror2.ubuntulinux.nl) feisty-seveas Release.gpg [307B]
Get:3 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) feisty Release.gpg [191B]
Get:4 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]
Get:5 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release.gpg [191B]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://kubuntu.org](http://kubuntu.org) feisty Release.gpg
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Translation-en_US
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Translation-en_US
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://mirror2.ubuntulinux.nl](http://mirror2.ubuntulinux.nl) feisty-seveas/all Translation-en_US
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_US
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Translation-en_US
Ign [http://kubuntu.org](http://kubuntu.org) feisty/main Translation-en_US
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty Release
Hit [http://mirror2.ubuntulinux.nl](http://mirror2.ubuntulinux.nl) feisty-seveas Release
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release
Err [http://mirror2.ubuntulinux.nl](http://mirror2.ubuntulinux.nl) feisty-seveas Release

Err [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release

Get:7 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release [2195B]
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
  Error reading from server - read (104 Connection reset by peer)
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) feisty/restricted Translation-en_US
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) feisty/universe Translation-en_US
  Error reading from server - read (104 Connection reset by peer)
Get:8 [http://mirror2.ubuntulinux.nl](http://mirror2.ubuntulinux.nl) feisty-seveas Release [20.3kB]
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages
Ign [http://kubuntu.org](http://kubuntu.org) feisty Release
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) feisty/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Get:9 [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) feisty/main Packages [1100B]
Ign [http://kubuntu.org](http://kubuntu.org) feisty/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Get:10 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) feisty-updates/main Translation-en_US
Err [http://kubuntu.org](http://kubuntu.org) feisty/main Packages
  404 Not Found
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Get:11 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages [5483B]
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Ign [http://mirror2.ubuntulinux.nl](http://mirror2.ubuntulinux.nl) feisty-seveas Release
Hit [http://mirror2.ubuntulinux.nl](http://mirror2.ubuntulinux.nl) feisty-seveas/all Packages
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) feisty-updates/universe Translation-en_US
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) feisty-updates/multiverse Translation-en_US
  Error reading from server - read (104 Connection reset by peer)
Get:12 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages [2849B]
Get:13 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) feisty-backports Release.gpg [191B]
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) feisty-backports/main Translation-en_US
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) feisty-backports/restricted Translation-en_US
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) feisty-backports/universe Translation-en_US
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) feisty-backports/multiverse Translation-en_US
  Error reading from server - read (104 Connection reset by peer)
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) feisty Release
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) feisty-updates Release
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) feisty-backports Release
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) feisty/main Packages
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) feisty/restricted Packages
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) feisty/universe Packages
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) feisty/multiverse Packages
Get:14 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) feisty-updates Release [32.4kB]
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) feisty-updates Release
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) feisty-backports/main Packages
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) feisty-backports/restricted Packages
Ign [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) feisty-backports/universe Packages
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) feisty-backports/multiverse Packages
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) feisty-updates/multiverse Packages
Get:15 [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) feisty-backports/universe Packages [49.1kB]
99% [Working]                                                       31.7kB/s 0s
gzip: stdin: not in gzip format
Err [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) feisty-backports/universe Packages
  Sub-process gzip returned an error code (1)
Fetched 65.1kB in 9s (7102B/s)
Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2](http://pk.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/i18n/Translation-en_US.bz2](http://pk.archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/i18n/Translation-en_US.bz2)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_US.bz2)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/i18n/Translation-en_US.bz2](http://pk.archive.ubuntu.com/ubuntu/dists/feisty-backports/multiverse/i18n/Translation-en_US.bz2)  Error reading from server - read (104 Connection reset by peer)
Failed to fetch [http://kubuntu.org/packages/amarok-latest/dists/feisty/main/binary-i386/Packages.gz](http://kubuntu.org/packages/amarok-latest/dists/feisty/main/binary-i386/Packages.gz)  404 Not Found
Failed to fetch [http://pk.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/binary-i386/Packages.gz](http://pk.archive.ubuntu.com/ubuntu/dists/feisty-backports/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: GPG error: [http://mirror2.ubuntulinux.nl](http://mirror2.ubuntulinux.nl) feisty-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466
W: GPG error: [http://pk.archive.ubuntu.com](http://pk.archive.ubuntu.com) feisty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

I tried all gpg keys but not a single one I could grab through pgp (or the command line programme) the out put is as follows:::
> ss@ss-desktop:~$ gpg --keyserver hkp://subkeys.pgp.net --recv-keys 0C5A2783
gpg: requesting key 0C5A2783 from hkp server subkeys.pgp.net
gpgkeys: HTTP fetch error 6: Couldn't resolve host 'subkeys.pgp.net'
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

Any ideas?
I want to get updated as Gusty is coming and I would have to get a whole upgrade also but it seems I could not be able to install latest amarok also.
:(
Regards

---

