---
title: "I get errors when doing  &quot;apt update&quot;"
date: 2020-09-20
forum: General Help
---

### Post by Hankbonk on 2020-09-20
When doing
```
sudo apt update
```

I get these results :
```
henk@~$ sudo apt update[sudo] password for henk: 
Hit:1 http://archive.canonical.com/ubuntu bionic InRelease
Hit:2 http://be.archive.ubuntu.com/ubuntu bionic InRelease                                                                                        
Get:3 http://be.archive.ubuntu.com/ubuntu bionic-updates InRelease [88,7 kB]                                                                      
Get:4 http://be.archive.ubuntu.com/ubuntu bionic-backports InRelease [74,6 kB]                                                                    
Hit:5 http://ppa.launchpad.net/deadsnakes/ppa/ubuntu bionic InRelease                                                                             
Get:6 http://ppa.launchpad.net/oibaf/graphics-drivers/ubuntu bionic InRelease [20,8 kB]                                                           
Hit:7 http://ppa.launchpad.net/teejee2008/ppa/ubuntu bionic InRelease                                                                             
Hit:8 http://dl.google.com/linux/chrome/deb stable InRelease                                                                                      
Hit:9 http://download.mono-project.com/repo/debian wheezy InRelease                                                                               
Hit:10 http://packages.microsoft.com/repos/vscode stable InRelease                                                                                
Get:11 http://be.archive.ubuntu.com/ubuntu bionic-security InRelease [88,7 kB]                                                                    
Hit:12 https://repo.skype.com/deb stable InRelease                                                                                                
Ign:13 https://dl.bintray.com/aluxian/deb beta InRelease                                                                                          
Hit:14 http://ppa.launchpad.net/ubuntuhandbook1/lives/ubuntu bionic InRelease                                                                     
Hit:15 https://download.mono-project.com/repo/ubuntu stable-bionic InRelease                                                                      
Err:16 https://dl.bintray.com/aluxian/deb beta Release                                                                                            
  404  Not Found [IP: 3.127.63.161 443]
Ign:17 http://ppa.launchpad.net/webupd8team/unstable/ubuntu bionic InRelease                                                                      
Hit:18 https://dl.winehq.org/wine-builds/ubuntu bionic InRelease                                                                                  
Hit:19 http://download.virtualbox.org/virtualbox/debian bionic InRelease                                      
Err:20 http://ppa.launchpad.net/webupd8team/unstable/ubuntu bionic Release                                    
  404  Not Found [IP: 2001:67c:1560:8008::15 80]
Get:21 https://mega.nz/linux/MEGAsync/xUbuntu_18.04 ./ InRelease [2473 B]               
Get:22 http://be.archive.ubuntu.com/ubuntu bionic-updates/main amd64 DEP-11 Metadata [295 kB]
Get:23 http://be.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 DEP-11 Metadata [285 kB]
Get:24 http://be.archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 DEP-11 Metadata [2468 B] 
Get:25 http://be.archive.ubuntu.com/ubuntu bionic-backports/universe amd64 DEP-11 Metadata [9288 B]
Get:26 http://be.archive.ubuntu.com/ubuntu bionic-security/main amd64 DEP-11 Metadata [48,9 kB]      
Get:27 http://be.archive.ubuntu.com/ubuntu bionic-security/universe amd64 DEP-11 Metadata [55,9 kB]
Get:28 http://be.archive.ubuntu.com/ubuntu bionic-security/multiverse amd64 DEP-11 Metadata [2464 B]   
Err:21 https://mega.nz/linux/MEGAsync/xUbuntu_18.04 ./ InRelease                                       
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 03C3AD3A7F068E5D
Reading package lists... Done
E: The repository 'https://dl.bintray.com/aluxian/deb beta Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/webupd8team/unstable/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
N: Skipping acquire of configured file 'contrib/binary-i386/Packages' as repository 'http://download.virtualbox.org/virtualbox/debian bionic InRelease' doesn't support architecture 'i386'
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: https://mega.nz/linux/MEGAsync/xUbuntu_18.04 ./ InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 03C3AD3A7F068E5D



```

I have had issues earlier on this year with the automated software updates, which didn't run successfully 

Anyone up for this ?

:guitar:
Hank.

---

### Post by guiverc on 2020-09-20
If you open up 
[https://dl.bintray.com/aluxian/deb](https://dl.bintray.com/aluxian/deb) in a browser, you'll just get errors.
I don't know why it was added, but it looks wrong.

[http://ppa.launchpad.net/webupd8team/unstable/ubuntu/dists/](http://ppa.launchpad.net/webupd8team/unstable/ubuntu/dists/)

is a 3rd party repo, so all security checks are on you (is it maintained? appropriate for your release? from trusted source? etc)  Given it's support ended early 2017 (with 17.04), and it doesn't support *bionic* or 18.04, it should not have been added to your system, and should be removed in my opinion.

---

### Post by Hankbonk on 2020-09-20
Thanks Guiverc,

I removed both repositories, then Updates & Software does an update :
It starts to run correctly, but then I get a connection error, like I don't have my internet connected ....?

---

### Post by ajgreeny on 2020-09-20
I believe the webupd8 ppa repos have all stopped now so they must be removed; I've  never heard of the bintray repo; what was it for?

For your wireless problem see Wireless-info in my signature and run the script there then post the output back here; our experts may be able to help more than I can.

---

### Post by Hankbonk on 2020-09-20
Hello ajgreeny,

I don't know how those  webupd8 repos got in my system .

And as for the download that interrupts, It does do a couple of downloads ( I can see that under the "Details" button) but suddenly says no internet  connection !

And I am not using a wireless connection : it's a ethernet connected from Desktop to modem .

---

### Post by ajgreeny on 2020-09-20
Ah!  OK, forget my wireless-info script idea in that case.

Problems with ethernet are unusual but try running command ```
ping -c 10 172.217.169.78
``` and the follow with ```
ping -c 10 google.com
```
These two are pinging the same URL so should give the same result; if they are very different it suggests a DNS problem.

Can you also look to see what servers you are using for the updates; are they local to your location, ie, in the same country?

---

### Post by Hankbonk on 2020-09-22
dear ajgreeny,

I did both pings :

1st one :

> henk@~$ ping -c 10 172.217.169.78
PING 172.217.169.78 (172.217.169.78) 56(84) bytes of data.
64 bytes from 172.217.169.78: icmp_seq=1 ttl=114 time=19.4 ms
64 bytes from 172.217.169.78: icmp_seq=2 ttl=114 time=27.2 ms
64 bytes from 172.217.169.78: icmp_seq=3 ttl=114 time=23.6 ms
64 bytes from 172.217.169.78: icmp_seq=4 ttl=114 time=20.3 ms
64 bytes from 172.217.169.78: icmp_seq=5 ttl=114 time=21.3 ms
64 bytes from 172.217.169.78: icmp_seq=6 ttl=114 time=24.2 ms
64 bytes from 172.217.169.78: icmp_seq=7 ttl=114 time=21.1 ms
64 bytes from 172.217.169.78: icmp_seq=8 ttl=114 time=22.6 ms
64 bytes from 172.217.169.78: icmp_seq=9 ttl=114 time=21.4 ms
64 bytes from 172.217.169.78: icmp_seq=10 ttl=114 time=18.7 ms
--- 172.217.169.78 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9013ms
rtt min/avg/max/mdev = 18.777/22.035/27.296/2.396 ms


2nd :
> henk@~$ ping -c 10 google.comPING google.com(ams16s29-in-x0e.1e100.net (2a00:1450:400e:804::200e)) 56 data bytes
64 bytes from ams16s29-in-x0e.1e100.net (2a00:1450:400e:804::200e): icmp_seq=1 ttl=118 time=16.5 ms
64 bytes from ams16s29-in-x0e.1e100.net (2a00:1450:400e:804::200e): icmp_seq=2 ttl=118 time=16.2 ms
64 bytes from ams16s29-in-x0e.1e100.net (2a00:1450:400e:804::200e): icmp_seq=3 ttl=118 time=15.0 ms
64 bytes from ams16s29-in-x0e.1e100.net (2a00:1450:400e:804::200e): icmp_seq=4 ttl=118 time=20.0 ms
64 bytes from ams16s29-in-x0e.1e100.net (2a00:1450:400e:804::200e): icmp_seq=5 ttl=118 time=14.6 ms
64 bytes from ams16s29-in-x0e.1e100.net (2a00:1450:400e:804::200e): icmp_seq=6 ttl=118 time=16.0 ms
64 bytes from ams16s29-in-x0e.1e100.net (2a00:1450:400e:804::200e): icmp_seq=7 ttl=118 time=19.8 ms
64 bytes from ams16s29-in-x0e.1e100.net (2a00:1450:400e:804::200e): icmp_seq=8 ttl=118 time=16.0 ms
64 bytes from ams16s29-in-x0e.1e100.net (2a00:1450:400e:804::200e): icmp_seq=9 ttl=118 time=15.8 ms
64 bytes from ams16s29-in-x0e.1e100.net (2a00:1450:400e:804::200e): icmp_seq=10 ttl=118 time=15.0 ms


--- google.com ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9016ms
rtt min/avg/max/mdev = 14.699/16.547/20.021/1.787 ms




---

