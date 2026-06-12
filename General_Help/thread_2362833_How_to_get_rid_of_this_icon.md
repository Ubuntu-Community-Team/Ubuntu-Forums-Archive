---
title: "How to get rid of this icon ?"
date: 2017-06-02
forum: General Help
---

### Post by linuxyogi on 2017-06-02
[ATTACH=CONFIG]275412[/ATTACH]

When I did apt-get update / upgrade there's nothing left to do same with [COLOR=#282828][FONT=InconsolataMedium]apt-get -f install. How do I get rid of this icon ?

[/FONT][/COLOR]```
$ sudo apt-get update [sudo] password for mypc: 
Get:1 http://security.ubuntu.com/ubuntu zesty-security InRelease [89.2 kB]
Hit:2 http://in.archive.ubuntu.com/ubuntu zesty InRelease                      
Get:3 http://in.archive.ubuntu.com/ubuntu zesty-updates InRelease [89.2 kB]    
Get:4 http://in.archive.ubuntu.com/ubuntu zesty-backports InRelease [89.2 kB]
Get:5 http://in.archive.ubuntu.com/ubuntu zesty-updates/main amd64 DEP-11 Metadata [41.8 kB]
Get:6 http://in.archive.ubuntu.com/ubuntu zesty-updates/main DEP-11 64x64 Icons [14.0 kB]
Get:7 http://in.archive.ubuntu.com/ubuntu zesty-updates/universe amd64 DEP-11 Metadata [54.1 kB]
Get:8 http://in.archive.ubuntu.com/ubuntu zesty-updates/universe DEP-11 64x64 Icons [43.5 kB]
Get:9 http://in.archive.ubuntu.com/ubuntu zesty-updates/multiverse amd64 DEP-11 Metadata [2,464 B]
Get:10 http://in.archive.ubuntu.com/ubuntu zesty-backports/universe amd64 DEP-11 Metadata [3,976 B]
Fetched 427 kB in 2s (210 kB/s)                                        
Reading package lists... Done



```[COLOR=#282828][FONT=InconsolataMedium]

[/FONT][/COLOR]```
$ sudo apt-get upgrade Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
```[COLOR=#282828][FONT=InconsolataMedium]

[/FONT][/COLOR]```
$ sudo apt-get -f installReading package lists... Done
Building dependency tree       
Reading state information... Done

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```[COLOR=#282828][FONT=InconsolataMedium]


[/FONT][/COLOR]

---

### Post by linuxyogi on 2017-06-03
Any ideas ?

---

