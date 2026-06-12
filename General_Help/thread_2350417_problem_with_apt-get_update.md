---
title: "problem with apt-get update"
date: 2017-01-24
forum: General Help
---

### Post by samiaa71 on 2017-01-24
dear mates am using ubuntu server 14.04

after i ediot my network and ip and make it static

and this is mmy ip setting 
i use 2 lan cards in this server
---

# The loopback network interface
auto lo
iface lo inet loopback





# The primary network interface
auto p2p1

iface p2p1 inet static
address 192.168.1.2
netmask 255.255.255.0
network 192.168.1.1
broadcast 192.168.1.255
gateway 192.168.1.1
dns-nameservers 8.8.8.8


# The secondary network interface
auto p4p1
iface p4p1 inet static
address 192.168.0.2
netmask 255.255.255.0
network 192.168.0.1
broadcast 192.168.0.255
gateway 192.168.0.1
dns-nameservers 4.4.4.4

----

the command apt-get update not work any more


gives me this error

login as: root
root@192.168.1.2's password:
Welcome to Ubuntu 14.04.5 LTS (GNU/Linux 4.2.0-42-generic x86_64)

 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)
New release '16.04.1 LTS' available.
Run 'do-release-upgrade' to upgrade to it.

Last login: Tue Jan 24 14:31:16 2017 from 192.168.1.35
root@ubuntu:~# apt-get update
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security InRelease
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release.gpg
  Unable to connect to security.ubuntu.com:http: [IP: 2001:67c:1562::19 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages/DiffIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages/DiffIndex
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en_GB
  Unable to connect to security.ubuntu.com:http: [IP: 2001:67c:1562::19 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Translation-en
  Unable to connect to security.ubuntu.com:http: [IP: 2001:67c:1562::19 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en_GB
  Unable to connect to security.ubuntu.com:http: [IP: 2001:67c:1562::19 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Translation-en
  Unable to connect to security.ubuntu.com:http: [IP: 2001:67c:1562::19 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en_GB
  Unable to connect to security.ubuntu.com:http: [IP: 2001:67c:1562::19 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Translation-en
  Unable to connect to security.ubuntu.com:http: [IP: 2001:67c:1562::19 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en_GB
  Unable to connect to security.ubuntu.com:http: [IP: 2001:67c:1562::19 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Translation-en
  Unable to connect to security.ubuntu.com:http: [IP: 2001:67c:1562::19 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main Sources
  Unable to connect to security.ubuntu.com:http: [IP: 2001:67c:1562::19 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted Sources
  Unable to connect to security.ubuntu.com:http: [IP: 2001:67c:1562::19 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe Sources
  Unable to connect to security.ubuntu.com:http: [IP: 2001:67c:1562::19 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse Sources
  Unable to connect to security.ubuntu.com:http: [IP: 2001:67c:1562::19 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main amd64 Packages
  Unable to connect to security.ubuntu.com:http: [IP: 2001:67c:1562::19 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted amd64 Packages
  Unable to connect to security.ubuntu.com:http: [IP: 2001:67c:1562::19 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe amd64 Packages
  Unable to connect to security.ubuntu.com:http: [IP: 2001:67c:1562::19 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse amd64 Packages
  Unable to connect to security.ubuntu.com:http: [IP: 2001:67c:1562::19 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/main i386 Packages
  Unable to connect to security.ubuntu.com:http: [IP: 2001:67c:1562::19 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/restricted i386 Packages
  Unable to connect to security.ubuntu.com:http: [IP: 2001:67c:1562::19 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/universe i386 Packages
  Unable to connect to security.ubuntu.com:http: [IP: 2001:67c:1562::19 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) trusty-security/multiverse i386 Packages
  Unable to connect to security.ubuntu.com:http: [IP: 2001:67c:1562::19 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports InRelease
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release.gpg
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates Release.gpg
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports Release.gpg
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Sources/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Sources/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Sources/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Sources/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main amd64 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted amd64 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe amd64 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse amd64 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Sources/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Sources/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe Sources/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse Sources/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main amd64 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted amd64 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe amd64 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse amd64 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/main Sources/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/restricted Sources/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/universe Sources/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/multiverse Sources/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/main amd64 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/restricted amd64 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/universe amd64 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/multiverse amd64 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/main i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/restricted i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/universe i386 Packages/DiffIndex
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/multiverse i386 Packages/DiffIndex
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en_GB
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Translation-en_GB
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en_GB
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-en_GB
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Translation-en_GB
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse Translation-en_GB
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Translation-en_GB
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe Translation-en_GB
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/main Translation-en_GB
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/main Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/multiverse Translation-en_GB
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/multiverse Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/restricted Translation-en_GB
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/restricted Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/universe Translation-en_GB
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/universe Translation-en
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/main i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/restricted i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/universe i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty/multiverse i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/main i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/restricted i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/universe i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-updates/multiverse i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/main Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/restricted Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/universe Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/multiverse Sources
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/main amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/restricted amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/universe amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/multiverse amd64 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/main i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/restricted i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/universe i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) trusty-backports/multiverse i386 Packages
  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]
Err [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty InRelease

Err [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-security InRelease

Err [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates InRelease

Err [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-proposed InRelease

Err [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports InRelease

Err [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty Release.gpg
  Could not resolve 'de.archive.ubuntu.com'
Err [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-security Release.gpg
  Could not resolve 'de.archive.ubuntu.com'
Err [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-updates Release.gpg
  Could not resolve 'de.archive.ubuntu.com'
Err [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-proposed Release.gpg
  Could not resolve 'de.archive.ubuntu.com'
Err [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) trusty-backports Release.gpg
  Could not resolve 'de.archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch [http://de.archive.ubuntu.com/ubuntu/...usty/InRelease]("http://de.archive.ubuntu.com/ubuntu/dists/trusty/InRelease")

W: Failed to fetch [http://de.archive.ubuntu.com/ubuntu/...rity/InRelease]("http://de.archive.ubuntu.com/ubuntu/dists/trusty-security/InRelease")

W: Failed to fetch [http://de.archive.ubuntu.com/ubuntu/...ates/InRelease]("http://de.archive.ubuntu.com/ubuntu/dists/trusty-updates/InRelease")

W: Failed to fetch [http://de.archive.ubuntu.com/ubuntu/...osed/InRelease]("http://de.archive.ubuntu.com/ubuntu/dists/trusty-proposed/InRelease")

W: Failed to fetch [http://de.archive.ubuntu.com/ubuntu/...orts/InRelease]("http://de.archive.ubuntu.com/ubuntu/dists/trusty-backports/InRelease")

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...ty/Release.gpg]("http://security.ubuntu.com/ubuntu/dists/trusty-security/Release.gpg")  Unable to connect to security.ubuntu.com:http: [IP: 2001:67c:1562::19 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...nslation-en_GB]("http://security.ubuntu.com/ubuntu/dists/trusty-security/main/i18n/Translation-en_GB")  Unable to connect to security.ubuntu.com:http: [IP: 2001:67c:1562::19 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...Translation-en]("http://security.ubuntu.com/ubuntu/dists/trusty-security/main/i18n/Translation-en")  Unable to connect to security.ubuntu.com:http: [IP: 2001:67c:1562::19 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...nslation-en_GB]("http://security.ubuntu.com/ubuntu/dists/trusty-security/multiverse/i18n/Translation-en_GB")  Unable to connect to security.ubuntu.com:http: [IP: 2001:67c:1562::19 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...Translation-en]("http://security.ubuntu.com/ubuntu/dists/trusty-security/multiverse/i18n/Translation-en")  Unable to connect to security.ubuntu.com:http: [IP: 2001:67c:1562::19 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...nslation-en_GB]("http://security.ubuntu.com/ubuntu/dists/trusty-security/restricted/i18n/Translation-en_GB")  Unable to connect to security.ubuntu.com:http: [IP: 2001:67c:1562::19 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...Translation-en]("http://security.ubuntu.com/ubuntu/dists/trusty-security/restricted/i18n/Translation-en")  Unable to connect to security.ubuntu.com:http: [IP: 2001:67c:1562::19 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...nslation-en_GB]("http://security.ubuntu.com/ubuntu/dists/trusty-security/universe/i18n/Translation-en_GB")  Unable to connect to security.ubuntu.com:http: [IP: 2001:67c:1562::19 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...Translation-en]("http://security.ubuntu.com/ubuntu/dists/trusty-security/universe/i18n/Translation-en")  Unable to connect to security.ubuntu.com:http: [IP: 2001:67c:1562::19 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...source/Sources]("http://security.ubuntu.com/ubuntu/dists/trusty-security/main/source/Sources")  Unable to connect to security.ubuntu.com:http: [IP: 2001:67c:1562::19 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...source/Sources]("http://security.ubuntu.com/ubuntu/dists/trusty-security/restricted/source/Sources")  Unable to connect to security.ubuntu.com:http: [IP: 2001:67c:1562::19 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...source/Sources]("http://security.ubuntu.com/ubuntu/dists/trusty-security/universe/source/Sources")  Unable to connect to security.ubuntu.com:http: [IP: 2001:67c:1562::19 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...source/Sources]("http://security.ubuntu.com/ubuntu/dists/trusty-security/multiverse/source/Sources")  Unable to connect to security.ubuntu.com:http: [IP: 2001:67c:1562::19 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...amd64/Packages]("http://security.ubuntu.com/ubuntu/dists/trusty-security/main/binary-amd64/Packages")  Unable to connect to security.ubuntu.com:http: [IP: 2001:67c:1562::19 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...amd64/Packages]("http://security.ubuntu.com/ubuntu/dists/trusty-security/restricted/binary-amd64/Packages")  Unable to connect to security.ubuntu.com:http: [IP: 2001:67c:1562::19 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...amd64/Packages]("http://security.ubuntu.com/ubuntu/dists/trusty-security/universe/binary-amd64/Packages")  Unable to connect to security.ubuntu.com:http: [IP: 2001:67c:1562::19 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...amd64/Packages]("http://security.ubuntu.com/ubuntu/dists/trusty-security/multiverse/binary-amd64/Packages")  Unable to connect to security.ubuntu.com:http: [IP: 2001:67c:1562::19 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...-i386/Packages]("http://security.ubuntu.com/ubuntu/dists/trusty-security/main/binary-i386/Packages")  Unable to connect to security.ubuntu.com:http: [IP: 2001:67c:1562::19 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...-i386/Packages]("http://security.ubuntu.com/ubuntu/dists/trusty-security/restricted/binary-i386/Packages")  Unable to connect to security.ubuntu.com:http: [IP: 2001:67c:1562::19 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...-i386/Packages]("http://security.ubuntu.com/ubuntu/dists/trusty-security/universe/binary-i386/Packages")  Unable to connect to security.ubuntu.com:http: [IP: 2001:67c:1562::19 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/di...-i386/Packages]("http://security.ubuntu.com/ubuntu/dists/trusty-security/multiverse/binary-i386/Packages")  Unable to connect to security.ubuntu.com:http: [IP: 2001:67c:1562::19 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...ty/Release.gpg]("http://archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...es/Release.gpg]("http://archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...ts/Release.gpg]("http://archive.ubuntu.com/ubuntu/dists/trusty-backports/Release.gpg")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...nslation-en_GB]("http://archive.ubuntu.com/ubuntu/dists/trusty/main/i18n/Translation-en_GB")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...Translation-en]("http://archive.ubuntu.com/ubuntu/dists/trusty/main/i18n/Translation-en")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...nslation-en_GB]("http://archive.ubuntu.com/ubuntu/dists/trusty/multiverse/i18n/Translation-en_GB")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...Translation-en]("http://archive.ubuntu.com/ubuntu/dists/trusty/multiverse/i18n/Translation-en")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...nslation-en_GB]("http://archive.ubuntu.com/ubuntu/dists/trusty/restricted/i18n/Translation-en_GB")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...Translation-en]("http://archive.ubuntu.com/ubuntu/dists/trusty/restricted/i18n/Translation-en")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...nslation-en_GB]("http://archive.ubuntu.com/ubuntu/dists/trusty/universe/i18n/Translation-en_GB")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...Translation-en]("http://archive.ubuntu.com/ubuntu/dists/trusty/universe/i18n/Translation-en")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...nslation-en_GB]("http://archive.ubuntu.com/ubuntu/dists/trusty-updates/main/i18n/Translation-en_GB")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...Translation-en]("http://archive.ubuntu.com/ubuntu/dists/trusty-updates/main/i18n/Translation-en")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...nslation-en_GB]("http://archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/i18n/Translation-en_GB")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...Translation-en]("http://archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/i18n/Translation-en")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...nslation-en_GB]("http://archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/i18n/Translation-en_GB")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...Translation-en]("http://archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/i18n/Translation-en")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...nslation-en_GB]("http://archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/i18n/Translation-en_GB")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...Translation-en]("http://archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/i18n/Translation-en")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...nslation-en_GB]("http://archive.ubuntu.com/ubuntu/dists/trusty-backports/main/i18n/Translation-en_GB")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...Translation-en]("http://archive.ubuntu.com/ubuntu/dists/trusty-backports/main/i18n/Translation-en")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...nslation-en_GB]("http://archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/i18n/Translation-en_GB")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...Translation-en]("http://archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/i18n/Translation-en")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...nslation-en_GB]("http://archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/i18n/Translation-en_GB")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...Translation-en]("http://archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/i18n/Translation-en")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...nslation-en_GB]("http://archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/i18n/Translation-en_GB")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...Translation-en]("http://archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/i18n/Translation-en")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...source/Sources]("http://archive.ubuntu.com/ubuntu/dists/trusty/main/source/Sources")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...source/Sources]("http://archive.ubuntu.com/ubuntu/dists/trusty/restricted/source/Sources")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...source/Sources]("http://archive.ubuntu.com/ubuntu/dists/trusty/universe/source/Sources")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...source/Sources]("http://archive.ubuntu.com/ubuntu/dists/trusty/multiverse/source/Sources")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...amd64/Packages]("http://archive.ubuntu.com/ubuntu/dists/trusty/main/binary-amd64/Packages")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...amd64/Packages]("http://archive.ubuntu.com/ubuntu/dists/trusty/restricted/binary-amd64/Packages")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...amd64/Packages]("http://archive.ubuntu.com/ubuntu/dists/trusty/universe/binary-amd64/Packages")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...amd64/Packages]("http://archive.ubuntu.com/ubuntu/dists/trusty/multiverse/binary-amd64/Packages")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...-i386/Packages]("http://archive.ubuntu.com/ubuntu/dists/trusty/main/binary-i386/Packages")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...-i386/Packages]("http://archive.ubuntu.com/ubuntu/dists/trusty/restricted/binary-i386/Packages")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...-i386/Packages]("http://archive.ubuntu.com/ubuntu/dists/trusty/universe/binary-i386/Packages")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...-i386/Packages]("http://archive.ubuntu.com/ubuntu/dists/trusty/multiverse/binary-i386/Packages")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...source/Sources]("http://archive.ubuntu.com/ubuntu/dists/trusty-updates/main/source/Sources")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...source/Sources]("http://archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/source/Sources")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...source/Sources]("http://archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/source/Sources")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...source/Sources]("http://archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/source/Sources")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...amd64/Packages]("http://archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-amd64/Packages")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...amd64/Packages]("http://archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/binary-amd64/Packages")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...amd64/Packages]("http://archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/binary-amd64/Packages")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...amd64/Packages]("http://archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/binary-amd64/Packages")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...-i386/Packages]("http://archive.ubuntu.com/ubuntu/dists/trusty-updates/main/binary-i386/Packages")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...-i386/Packages]("http://archive.ubuntu.com/ubuntu/dists/trusty-updates/restricted/binary-i386/Packages")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...-i386/Packages]("http://archive.ubuntu.com/ubuntu/dists/trusty-updates/universe/binary-i386/Packages")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...-i386/Packages]("http://archive.ubuntu.com/ubuntu/dists/trusty-updates/multiverse/binary-i386/Packages")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...source/Sources]("http://archive.ubuntu.com/ubuntu/dists/trusty-backports/main/source/Sources")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...source/Sources]("http://archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/source/Sources")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...source/Sources]("http://archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/source/Sources")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...source/Sources]("http://archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/source/Sources")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...amd64/Packages]("http://archive.ubuntu.com/ubuntu/dists/trusty-backports/main/binary-amd64/Packages")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...amd64/Packages]("http://archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/binary-amd64/Packages")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...amd64/Packages]("http://archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/binary-amd64/Packages")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...amd64/Packages]("http://archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/binary-amd64/Packages")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...-i386/Packages]("http://archive.ubuntu.com/ubuntu/dists/trusty-backports/main/binary-i386/Packages")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...-i386/Packages]("http://archive.ubuntu.com/ubuntu/dists/trusty-backports/restricted/binary-i386/Packages")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...-i386/Packages]("http://archive.ubuntu.com/ubuntu/dists/trusty-backports/universe/binary-i386/Packages")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dis...-i386/Packages]("http://archive.ubuntu.com/ubuntu/dists/trusty-backports/multiverse/binary-i386/Packages")  Unable to connect to archive.ubuntu.com:http: [IP: 2001:67c:1360:8001::21 80]

W: Failed to fetch [http://de.archive.ubuntu.com/ubuntu/...ty/Release.gpg]("http://de.archive.ubuntu.com/ubuntu/dists/trusty/Release.gpg")  Could not resolve 'de.archive.ubuntu.com'

W: Failed to fetch [http://de.archive.ubuntu.com/ubuntu/...ty/Release.gpg]("http://de.archive.ubuntu.com/ubuntu/dists/trusty-security/Release.gpg")  Could not resolve 'de.archive.ubuntu.com'

W: Failed to fetch [http://de.archive.ubuntu.com/ubuntu/...es/Release.gpg]("http://de.archive.ubuntu.com/ubuntu/dists/trusty-updates/Release.gpg")  Could not resolve 'de.archive.ubuntu.com'

W: Failed to fetch [http://de.archive.ubuntu.com/ubuntu/...ed/Release.gpg]("http://de.archive.ubuntu.com/ubuntu/dists/trusty-proposed/Release.gpg")  Could not resolve 'de.archive.ubuntu.com'

W: Failed to fetch [http://de.archive.ubuntu.com/ubuntu/...ts/Release.gpg]("http://de.archive.ubuntu.com/ubuntu/dists/trusty-backports/Release.gpg")  Could not resolve 'de.archive.ubuntu.com'

W: Some index files failed to download. They have been ignored, or old ones used instead.
root@ubuntu:~#

---

### Post by ajgreeny on 2017-01-24
Duplicate of post at [https://ubuntuforums.org/showthread.php?t=2350415&p=13598549#post13598549](https://ubuntuforums.org/showthread.php?t=2350415&p=13598549#post13598549)

Closed.

---

