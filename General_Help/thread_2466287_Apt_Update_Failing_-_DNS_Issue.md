---
title: "Apt Update Failing - DNS Issue"
date: 2021-08-24
forum: General Help
---

### Post by Alan5127 on 2021-08-24
Hi All,

I am getting the following error when running 'apt update' on my Ubuntu 20.04.3 LTS machine:

```
The repository 'http://security.ubuntu.com/ubuntu focal-security Release' no longer has a Release file.
```

I looked up what it means by 'focal' and that translates into Ubuntu 20.04 (which is the most current LTS release at the time of posting) which I believe should be supported for five years, so I don't believe that it the actual issue.

This is the full output from ```
sudo apt update
``` and ```
lsb_release -a
```:

```
$ sudo apt update
[sudo] password for administrator: 

Hit:1 http://nz.archive.ubuntu.com/ubuntu focal InRelease                                                                                           
Get:2 http://nz.archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]                                                                          
Get:3 http://nz.archive.ubuntu.com/ubuntu focal-backports InRelease [101 kB]                                                                                                  
Get:4 http://nz.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages [1,170 kB]                                                                                                        
Ign:5 http://security.ubuntu.com/ubuntu focal-security InRelease                                                                                                          
Get:6 http://nz.archive.ubuntu.com/ubuntu focal-updates/main amd64 DEP-11 Metadata [282 kB]                                                                               
Get:7 http://nz.archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages [851 kB]                                      
Ign:8 http://ppa.launchpad.net/certbot/certbot/ubuntu focal InRelease                                                 
Hit:9 http://archive.canonical.com/ubuntu bionic InRelease                                                            
Err:10 http://security.ubuntu.com/ubuntu focal-security Release                                                                
  404  Not Found [IP: 31.170.160.150 80]
Get:11 http://nz.archive.ubuntu.com/ubuntu focal-updates/universe amd64 DEP-11 Metadata [351 kB]                               
Get:12 http://nz.archive.ubuntu.com/ubuntu focal-updates/multiverse amd64 DEP-11 Metadata [944 B]                 
Get:13 http://nz.archive.ubuntu.com/ubuntu focal-backports/universe amd64 DEP-11 Metadata [10.3 kB]
Err:14 http://ppa.launchpad.net/certbot/certbot/ubuntu focal Release                                                        
  404  Not Found [IP: 91.189.95.85 80]
Reading package lists... Done
E: The repository 'http://security.ubuntu.com/ubuntu focal-security Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://ppa.launchpad.net/certbot/certbot/ubuntu focal Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

$ lsb_release -a

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 20.04.3 LTS
Release:    20.04
Codename:   focal
```

The IP shown above for security.ubuntu.com (31.170.160.150 80) does not appear to be correct.

If I check the name resolution manually I get the same result if I query it locally on my machine and if I query Google's DNS (8.8.8.8) being 91.189.91.38 and 91.189.91.39:

```
$ dig @8.8.8.8 -t any security.ubuntu.com

; <<>> DiG 9.16.1-Ubuntu <<>> @8.8.8.8 -t any security.ubuntu.com
; (1 server found)
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 64332
;; flags: qr rd ra; QUERY: 1, ANSWER: 4, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 512
;; QUESTION SECTION:
;security.ubuntu.com.       IN  ANY

;; ANSWER SECTION:
security.ubuntu.com.    59  IN  AAAA    2001:67c:1562::18
security.ubuntu.com.    59  IN  AAAA    2001:67c:1562::15
security.ubuntu.com.    59  IN  A   91.189.91.38
security.ubuntu.com.    59  IN  A   91.189.91.39

;; Query time: 288 msec
;; SERVER: 8.8.8.8#53(8.8.8.8)
;; WHEN: Mon Aug 23 22:25:57 NZST 2021
;; MSG SIZE  rcvd: 136
```

```
$ dig -t any security.ubuntu.com

; <<>> DiG 9.16.1-Ubuntu <<>> -t any security.ubuntu.com
;; global options: +cmd
;; Got answer:
;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 10286
;; flags: qr rd ra; QUERY: 1, ANSWER: 2, AUTHORITY: 0, ADDITIONAL: 1

;; OPT PSEUDOSECTION:
; EDNS: version: 0, flags:; udp: 65494
;; QUESTION SECTION:
;security.ubuntu.com.       IN  ANY

;; ANSWER SECTION:
security.ubuntu.com.    19  IN  A   91.189.91.39
security.ubuntu.com.    19  IN  A   91.189.91.38

;; Query time: 16 msec
;; SERVER: 127.0.0.53#53(127.0.0.53)
;; WHEN: Mon Aug 23 22:30:44 NZST 2021
;; MSG SIZE  rcvd: 80
```


Not sure where to go from here, but it *appears* that apt is using a different name resolution than my default system settings?  How do I get apt to lookup correctly?


Thanks,

Alan.

---

### Post by GhX6GZMB on 2021-08-24
In such cases, switch to a different repository server. It seems the New Zealand one has problems.

---

### Post by Alan5127 on 2021-08-24
Hi ml9104,

> **ml9104 said:**
> In such cases, switch to a different repository server. It seems the New Zealand one has problems.

I just tried from a different machine, albeit running 20.04.2 (rather than 20.04.3), and it seems to be fine:

```
$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 20.04.2 LTS
Release:	20.04
Codename:	focal


$ sudo apt update

Hit:1 http://nz.archive.ubuntu.com/ubuntu focal InRelease
Get:2 http://nz.archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]
Get:3 http://nz.archive.ubuntu.com/ubuntu focal-backports InRelease [101 kB]
Get:4 http://nz.archive.ubuntu.com/ubuntu focal-security InRelease [114 kB]
Get:5 http://nz.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages [1,170 kB]
Get:6 http://nz.archive.ubuntu.com/ubuntu focal-updates/main amd64 c-n-f Metadata [13.9 kB]
Get:7 http://nz.archive.ubuntu.com/ubuntu focal-updates/universe amd64 Packages [851 kB]
Get:8 http://nz.archive.ubuntu.com/ubuntu focal-backports/universe amd64 Packages [5,812 B]
Get:9 http://nz.archive.ubuntu.com/ubuntu focal-security/main amd64 Packages [828 kB]
Get:10 http://nz.archive.ubuntu.com/ubuntu focal-security/main amd64 c-n-f Metadata [8,440 B]
Fetched 3,205 kB in 1s (4,849 kB/s)                               
Reading package lists... Done
Building dependency tree       
Reading state information... Done
89 packages can be upgraded. Run 'apt list --upgradable' to see them.

```

However, that doesn't seem to try hitting 'security.ubuntu.com', only NZ servers?

I am happy to try changing to servers other than NZ if you think it might help - how would I do that?


Thanks,

Alan.

---

### Post by Alan5127 on 2021-08-24
> **Alan5127 said:**
> However, that doesn't seem to try hitting 'security.ubuntu.com', only NZ servers?



Looking at the original output from 'apt update' it actually looks like all the NZ servers worked find, but there was an issue with the non-NZ servers?

That still raises the question of how apt is resolving the hostnames?


Alan.

---

