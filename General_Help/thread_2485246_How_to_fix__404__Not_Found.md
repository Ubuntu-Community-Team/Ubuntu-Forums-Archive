---
title: "How to fix  404  Not Found"
date: 2023-03-24
forum: General Help
---

### Post by satimis on 2023-03-24
Hi,

Ubuntu 22.04

On Terminal running update

$ sudo apt update```

Hit:1 https://dl.google.com/linux/chrome/deb stable InRelease
Hit:2 http://security.ubuntu.com/ubuntu jammy-security InRelease
Hit:3 http://hk.archive.ubuntu.com/ubuntu jammy InRelease                      
Hit:4 http://hk.archive.ubuntu.com/ubuntu jammy-updates InRelease              
Hit:5 https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu jammy InRelease
Hit:6 http://hk.archive.ubuntu.com/ubuntu jammy-backports InRelease            
Ign:7 https://ppa.launchpadcontent.net/videolan/stable-daily/ubuntu jammy InRelease
Err:8 https://ppa.launchpadcontent.net/videolan/stable-daily/ubuntu jammy Release
  404  Not Found [IP: 185.125.190.52 443]
Reading package lists... Done                              
E: The repository 'https://ppa.launchpadcontent.net/videolan/stable-daily/ubuntu jammy Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

Please advise how to fix this problem ?  Thanks

Regards

---

### Post by yancek on 2023-03-24
The link below explains why you get this error when using a third party repository and gives a suggestion to eliminate the error.  Basically, deleting the entry from the sources.list file.  You could also comment it out by putting a # at the beginning of the line so that line is not read.

 [https://itsfoss.com/repository-does-not-have-release-file-error-ubuntu/](https://itsfoss.com/repository-does-not-have-release-file-error-ubuntu/)

---

### Post by satimis on 2023-03-24
> **yancek said:**
> The link below explains why you get this error when using a third party repository and gives a suggestion to eliminate the error.  Basically, deleting the entry from the sources.list file.  You could also comment it out by putting a # at the beginning of the line so that line is not read.

 [https://itsfoss.com/repository-does-not-have-release-file-error-ubuntu/](https://itsfoss.com/repository-does-not-have-release-file-error-ubuntu/)
Thanks for your advice and link

Performed following steps

1) Activities -> Update
2) -> Other Software
select -> ttps://ppa.launchpadcontent.net/videolan/stable-daily/ubuntu/jammy main
-> Remove

It also removes 
[https://ppa.launchpadcontent.net/videolan/stable-daily/ubuntu/jammy](https://ppa.launchpadcontent.net/videolan/stable-daily/ubuntu/jammy) main (Source Code)

Cache Fresh

Now running
$ sudo apt update

the problem gone

Regards

---

