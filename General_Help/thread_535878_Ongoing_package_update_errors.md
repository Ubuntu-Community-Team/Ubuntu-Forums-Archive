---
title: "Ongoing package update errors"
date: 2007-08-27
forum: General Help
---

### Post by adearaujo on 2007-08-27
Somebody PLEASE HELP!! I have been getting these errors for the past 4 days, I have uninstalled and installed a fresh copy of UBUNTU and tried this and still getting the same errors. I have tried reading many posts around the internet and could not find anything. It was working fine 5 days ago. I am on the internet now and am using the ubuntu machine to write this post. I do not know what else to do. If I boot up with the install cd and open a console and try the sudo apt-get update or upgrade it will work and connect without problems. But once I install and try it once I boot up, I get these errors. Also I have tried downloading the latest .iso file. ANY SUGGESTIONS????

[HTML]alexandre@brazuca:~$ sudo apt-get update Err http://security.ubuntu.com dapper-security Release.gpg
  Connection failed
Err http://archive.ubuntu.com dapper Release.gpg
  Connection failed [IP: 91.189.88.31 80]
Ign http://security.ubuntu.com dapper-security Release
Err http://archive.ubuntu.com dapper-updates Release.gpg
  Connection failed [IP: 91.189.89.6 80]
Ign http://security.ubuntu.com dapper-security/main Packages
Ign http://archive.ubuntu.com dapper Release
Ign http://security.ubuntu.com dapper-security/restricted Packages
Ign http://archive.ubuntu.com dapper-updates Release
Ign http://security.ubuntu.com dapper-security/main Sources
Ign http://archive.ubuntu.com dapper/main Packages
Ign http://security.ubuntu.com dapper-security/restricted Sources
Ign http://archive.ubuntu.com dapper/restricted Packages
Err http://security.ubuntu.com dapper-security/main Packages
  Connection failed
Ign http://archive.ubuntu.com dapper/main Sources
Err http://security.ubuntu.com dapper-security/restricted Packages
  Connection failed
Ign http://archive.ubuntu.com dapper/restricted Sources
Err http://security.ubuntu.com dapper-security/main Sources
  Connection failed
Ign http://archive.ubuntu.com dapper-updates/main Packages
Err http://security.ubuntu.com dapper-security/restricted Sources
  Connection failed
Ign http://archive.ubuntu.com dapper-updates/restricted Packages
Ign http://archive.ubuntu.com dapper-updates/main Sources
Ign http://archive.ubuntu.com dapper-updates/restricted Sources
Err http://archive.ubuntu.com dapper/main Packages
  Connection failed [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com dapper/restricted Packages
  Connection failed [IP: 91.189.89.6 80]
Err http://archive.ubuntu.com dapper/main Sources
  Connection failed [IP: 91.189.89.8 80]
Err http://archive.ubuntu.com dapper/restricted Sources
  Connection failed [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com dapper-updates/main Packages
  Connection failed [IP: 91.189.89.6 80]
Err http://archive.ubuntu.com dapper-updates/restricted Packages
  Connection failed [IP: 91.189.89.8 80]
Err http://archive.ubuntu.com dapper-updates/main Sources
  Connection failed [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com dapper-updates/restricted Sources
  Connection failed [IP: 91.189.89.6 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Connection failed [IP: 91.189.88.31 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg  Connection failed
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg  Connection failed [IP: 91.189.89.6 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-amd64/Packages.gz  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-amd64/Packages.gz  Connection failed
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz  Connection failed
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-amd64/Packages.gz  Connection failed [IP: 91.189.88.31 80]
Failed to fetch http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz  Connection failed
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-amd64/Packages.gz  Connection failed [IP: 91.189.89.6 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz  Connection failed [IP: 91.189.89.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz  Connection failed [IP: 91.189.88.31 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-amd64/Packages.gz  Connection failed [IP: 91.189.89.6 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-amd64/Packages.gz  Connection failed [IP: 91.189.89.8 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz  Connection failed [IP: 91.189.88.31 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz  Connection failed [IP: 91.189.89.6 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.[/HTML]

---

### Post by SPr on 2007-08-27
Hi,

I'm afraid I can't help directly but I was wondering if you can ping the IPs in the log you posted.

---

### Post by adearaujo on 2007-08-27
Here are the pinging results:

[HTML]
alexandre@brazuca:~$ ping 91.189.89.6
PING 91.189.89.6 (91.189.89.6) 56(84) bytes of data.
64 bytes from 91.189.89.6: icmp_seq=1 ttl=53 time=169 ms
64 bytes from 91.189.89.6: icmp_seq=2 ttl=53 time=169 ms
64 bytes from 91.189.89.6: icmp_seq=3 ttl=53 time=168 ms
64 bytes from 91.189.89.6: icmp_seq=4 ttl=53 time=168 ms
64 bytes from 91.189.89.6: icmp_seq=5 ttl=53 time=169 ms

--- 91.189.89.6 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4015ms
rtt min/avg/max/mdev = 168.648/169.228/169.559/0.362 ms


alexandre@brazuca:~$ ping 91.189.89.8
PING 91.189.89.8 (91.189.89.8) 56(84) bytes of data.
64 bytes from 91.189.89.8: icmp_seq=1 ttl=53 time=167 ms
64 bytes from 91.189.89.8: icmp_seq=2 ttl=53 time=167 ms
64 bytes from 91.189.89.8: icmp_seq=3 ttl=53 time=167 ms
64 bytes from 91.189.89.8: icmp_seq=4 ttl=53 time=167 ms
64 bytes from 91.189.89.8: icmp_seq=5 ttl=53 time=167 ms

--- 91.189.89.8 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4012ms
rtt min/avg/max/mdev = 167.327/167.610/167.897/0.566 ms


alexandre@brazuca:~$ ping 91.189.88.31
PING 91.189.88.31 (91.189.88.31) 56(84) bytes of data.
64 bytes from 91.189.88.31: icmp_seq=1 ttl=54 time=162 ms
64 bytes from 91.189.88.31: icmp_seq=2 ttl=54 time=160 ms
64 bytes from 91.189.88.31: icmp_seq=3 ttl=54 time=162 ms
64 bytes from 91.189.88.31: icmp_seq=4 ttl=54 time=160 ms
64 bytes from 91.189.88.31: icmp_seq=5 ttl=54 time=160 ms
64 bytes from 91.189.88.31: icmp_seq=6 ttl=54 time=160 ms

--- 91.189.88.31 ping statistics ---
6 packets transmitted, 6 received, 0% packet loss, time 5019ms
rtt min/avg/max/mdev = 160.045/161.040/162.528/1.028 ms

[/HTML]

---

### Post by SPr on 2007-08-27
Well, I don't know what the problem is then. Hopefully someone else can help :) (Though your times do seem a little slow compared to those I'm getting - 30 something miliseconds.)

---

### Post by adearaujo on 2007-08-27
Somebody please help!!!

---

### Post by oldos2er on 2007-08-27
Are you installing Feisty (v7.04)? Wondering why your sources.list is showing Dapper. You could try going here: [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/) to generate a new sources.list.

---

### Post by adearaujo on 2007-08-27
Im installing Dapper. The Feisty won't even boot up with the live cd. It keeps giving errors because it cannot find my bcm4311 driver for wireless card.

---

### Post by adearaujo on 2007-08-27
I am getting so frustrated with this crap, I dont know what else to do. I have searched and tried everything I can. Thank you for the ones that tried to reply and help, but nothing is working. I guess no ubuntu for me, without the updates I can't install my wireless connection and other drivers.

---

### Post by SPr on 2007-08-28
Hi,

sorry you haven't solved this yet :(

I have a silly question though; are the dapper repos still available? How many versions do they keep online?

---

### Post by adearaujo on 2007-08-28
I thought they would still be available? I remember seeing on the main page that dapper had support untill 2010 while feisty had support until 2008 if I am correct. By having support until 2010, wouldn't you think the repos would still be available? Is anybody else having problems with those?

---

