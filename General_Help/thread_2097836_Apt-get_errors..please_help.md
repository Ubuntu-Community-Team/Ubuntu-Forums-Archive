---
title: "Apt-get errors..please help"
date: 2012-12-24
forum: General Help
---

### Post by isac630728 on 2012-12-24
Hello All, 

I'm trying to install snmp and snmpd services, But I get these errors.. Please help me fix this.

Ubuntu Version 3.2.0-32-generic
temp_account@**server_001**:~$ sudo apt-get install snmp snmpd
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-server : Depends: linux-image-3.2.0-34-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

What happens if I try apt-get -f ? Will install those packages without installing that linux-imgae-3.2.0.34-generic? OR Will it do something else? It's a Production server and I can't afford any downtime. Any workaround for this?

I do have one more server with a similar error message.. here is the output

Ubuntu version 3.2.0-33-generic
temp_account@**server_002**:~$ sudo apt-get install snmp snmpd
Reading package lists... Done
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 linux-headers-3.2.0-34-generic : Depends: linux-headers-3.2.0-34 but it is not going to be installed
 snmp : Depends: libsnmp15 (>= 5.4.3~dfsg) but it is not going to be installed
 snmpd : Depends: libsnmp15 (>= 5.4.3~dfsg) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Here is another old version Ubuntu server output
Ubuntu Version 2.6.35-22-server
temp_account@**server_003**:~$ sudo apt-get install snmp snmpd
Reading package lists... Done
Building dependency tree
Reading state information... Done
snmpd is already the newest version.
The following NEW packages will be installed:
  snmp
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 180kB of archives.
After this operation, 618kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  snmp
Install these packages without verification [y/N]? y
Err [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main snmp amd64 5.4.3~dfsg-1ubuntu3
  404  Not Found [IP: 91.189.91.15 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/n/net-snmp/snmp_5.4.3~dfsg-1ubuntu3_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/n/net-snmp/snmp_5.4.3~dfsg-1ubuntu3_amd64.deb)  404  Not Found [IP: 91.189.91.15 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

I did try apt-get update (although I was not sure what it updates) and I got lot of  dead maverick link errors. 
What does apt-get update do? Does it update only the source list? or will it update all installed packages?
Please help me with all these errors. I have more than 14 servers with the same errors.


temp_account@**server_003**:~$ sudo apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main amd64 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted amd64 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe amd64 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse amd64 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main amd64 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted amd64 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe amd64 Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse amd64 Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main amd64 Packages
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted amd64 Packages
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe amd64 Packages
  404  Not Found
Err [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse amd64 Packages
  404  Not Found
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main amd64 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted amd64 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe amd64 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse amd64 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main amd64 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted amd64 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe amd64 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse amd64 Packages/DiffIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main amd64 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted amd64 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe amd64 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse amd64 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main amd64 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted amd64 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe amd64 Packages
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse amd64 Packages
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse amd64 Packages
  404  Not Found [IP: 91.189.91.13 80]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/main/binary-amd64/Packages.gz)  404  Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/restricted/binary-amd64/Packages.gz)  404  Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/universe/binary-amd64/Packages.gz)  404  Not Found

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-amd64/Packages.gz](http://security.ubuntu.com/ubuntu/dists/maverick-security/multiverse/binary-amd64/Packages.gz)  404  Not Found

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted/source/Sources.gz)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/source/Sources.gz)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/source/Sources.gz)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-amd64/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/maverick/main/binary-amd64/Packages.gz)  404  Not Found [IP: 91.189.91.13 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted](http://us.archive.ubuntu.com/ubuntu/dists/maverick/restricted)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/b](http://us.archive.ubuntu.com/ubuntu/dists/maverick/universe/b)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse](http://us.archive.ubuntu.com/ubuntu/dists/maverick/multiverse)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/ma](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/ma)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/re](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/re)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/un](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/un)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/mu](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/mu)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/ma](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/ma)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/re](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/re)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/un](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/un)

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/mu](http://us.archive.ubuntu.com/ubuntu/dists/maverick-updates/mu)

E: Some index files failed to download, they have been ignored, or old ones used

---

### Post by oldos2er on 2012-12-24
*apt-get update* refreshes all source lists, /etc/apt/sources.list and any lists in /etc/apt/sources.list.d/

You're seeing the 404 errors because Maverick is no longer supported; it's repositories have been moved to old-releases.

*apt-get install -f* attempts to fix broken packages. From the man page: 

Fix; attempt to correct a system with broken dependencies in place. This option, when used with install/remove, can omit any packages to permit APT to deduce a likely solution. If packages are specified, these have to completely correct the problem. The option is sometimes necessary when running APT for the first            time; APT itself does not allow broken package dependencies to exist on a system. It is possible that a system's dependency structure can be so corrupt as to require manual intervention (which usually means using dselect(1) or dpkg --remove to eliminate some of the offending packages). Use of this option together with -m may produce an error in some situations. Configuration Item: APT::Get::Fix-Broken.

Have you run *apt-get update* on this system lately?

---

### Post by deadflowr on 2012-12-24
> You're seeing the 404 errors because Maverick is no longer supported; it's repositories have been moved to old-releases.

Here's how to switch from the dead maverick repos to the old-release repos.

[http://superuser.com/questions/339537/where-can-i-get-therepositories-for-old-ubuntu-versions]("http://superuser.com/questions/339537/where-can-i-get-therepositories-for-old-ubuntu-versions")

Or you could upgrade to a newer, supported release.

---

### Post by isac630728 on 2012-12-24
> **oldos2er said:**
> *apt-get update* refreshes all source lists, /etc/apt/sources.list and any lists in /etc/apt/sources.list.d/

You're seeing the 404 errors because Maverick is no longer supported; it's repositories have been moved to old-releases.

*apt-get install -f* attempts to fix broken packages. From the man page: 

Fix; attempt to correct a system with broken dependencies in place. This option, when used with install/remove, can omit any packages to permit APT to deduce a likely solution. If packages are specified, these have to completely correct the problem. The option is sometimes necessary when running APT for the first            time; APT itself does not allow broken package dependencies to exist on a system. It is possible that a system's dependency structure can be so corrupt as to require manual intervention (which usually means using dselect(1) or dpkg --remove to eliminate some of the offending packages). Use of this option together with -m may produce an error in some situations. Configuration Item: APT::Get::Fix-Broken.

Have you run *apt-get update* on this system lately?

Yes I did try apt-get update on those systems. It was successful in Server_001 and Server_002. Still I cannot install snmp and snmpd. So Shall I just try apt-get install -f snmp snmpd ?

It wont bring down the server or any services right?

---

### Post by isac630728 on 2012-12-24
> **deadflowr said:**
> Here's how to switch from the dead maverick repos to the old-release repos.

[http://superuser.com/questions/339537/where-can-i-get-therepositories-for-old-ubuntu-versions]("http://superuser.com/questions/339537/where-can-i-get-therepositories-for-old-ubuntu-versions")

Or you could upgrade to a newer, supported release.

Here is my sources list.. can you tell me what all needs to be replaced here?

I tried replacing all us.archive.ubuntu.com to old-releases.ubuntu.com using the vi editor. But When I ran apt-get install snmp snmpd I got this message

temp_account@server_003:~$sudo apt-get install snmp snmpd
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package snmp is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libsnmp15

E: Package 'snmp' has no installation candidate


temp_account@server_003:/etc/apt$ sudo cat sources.list
#
# deb cdrom:[Ubuntu-Server 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted

#deb cdrom:[Ubuntu-Server 10.10 _Maverick Meerkat_ - Release amd64 (20101007)]/ maverick main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

## Uncomment the following two lines to add software from Ubuntu's
## 'extras' repository.
## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
# deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main
# deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) maverick-security multiverse

---

### Post by snowpine on 2012-12-24
For example change this:

```
deb http://us.archive.ubuntu.com/ubuntu/ maverick main restricted
```

to this:

```
deb http://old-releases.ubuntu.com/ubuntu/ maverick main restricted
```

**Do this for educational/experimental purposes only!** "End of life" releases should never be used for a production server, there is no security support at all.

---

### Post by isac630728 on 2012-12-24
> **snowpine said:**
> For example change this:

```
deb http://us.archive.ubuntu.com/ubuntu/ maverick main restricted
```

to this:

```
deb http://old-releases.ubuntu.com/ubuntu/ maverick main restricted
```

**Do this for educational/experimental purposes only!** "End of life" releases should never be used for a production server, there is no security support at all.

Okay. Should I change only deb [http://*](http://*) or should I change deb scr http:/? as well? If I change both, I get this error..

temp_account@server_003:~$sudo apt-get install snmp snmpd
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package snmp is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
libsnmp15

E: Package 'snmp' has no installation candidate

---

### Post by snowpine on 2012-12-24
You must use

```
sudo apt-get update
```

first to refresh your package lists. Then you can attempt to install the unsupported package.

---

### Post by isac630728 on 2012-12-24
> **snowpine said:**
> You must use

```
sudo apt-get update
```

first to refresh your package lists. Then you can attempt to install the unsupported package.

That worked. Thanks a lot. 
Now I just have to wait for a confirmation from the other user or someone regarding the "apt-get install -f snmp snmpd" as I'm not sure if it removes something that affects the server?

---

### Post by snowpine on 2012-12-24
The thing that's weird about your error is that Maverick did not use a 3.2 kernel, so I'm not sure why you are being prompted to install it.

---

### Post by lisati on 2012-12-24
*Thread moved to **General Help**.*

---

