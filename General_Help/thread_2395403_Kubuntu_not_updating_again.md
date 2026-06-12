---
title: "Kubuntu not updating again"
date: 2018-07-01
forum: General Help
---

### Post by alan35 on 2018-07-01
My computer stopped updating probably four or five months ago. I had this issues over a year ago, I went back to that post and tried again and it didn't work.
I suspect its something to do with the sources for the update.  I am using Kubuntu.


```
 uname -a
Linux dad-Aspire-ZC-102 4.10.0-42-generic #46-Ubuntu SMP Mon Dec 4 14:38:01 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
```


```
sudo apt update
[sudo] password for dad: 
Ign:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty InRelease
Ign:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security InRelease
Ign:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-updates InRelease
Err:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty Release
  404  Not Found [IP: 2001:67c:1562::19 80]
Err:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) zesty-updates Release
  404  Not Found [IP: 2001:67c:1562::19 80]
Err:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) zesty-security Release
  404  Not Found [IP: 2001:67c:1560:8001::14 80]
Hit:7 [https://repo.skype.com/deb](https://repo.skype.com/deb) stable InRelease
Reading package lists... Done
E: The repository 'http://us.archive.ubuntu.com/ubuntu zesty Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://us.archive.ubuntu.com/ubuntu zesty-updates Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://security.ubuntu.com/ubuntu zesty-security Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
dad@dad-Aspire-ZC-102:~$ 
```

Thanks Alan

---

### Post by deadflowr on 2018-07-01
17.04 is no longer supported and the archives have moved.
You need to upgrade to a new version.
Best to upgrade cleanly with a fresh install to 18.04 as the next release after 17.04, 17.10 is about to suffer the same fate as 17.04.
In all cases, backup what you need to backup and download the new version.
That's the easiest route to go with.

---

### Post by alan35 on 2018-07-01
Wow, I guess it has been awhile.
Thanks Deadflowr

---

