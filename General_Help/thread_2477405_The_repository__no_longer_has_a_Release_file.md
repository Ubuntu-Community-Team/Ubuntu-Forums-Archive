---
title: "The repository  no longer has a Release file"
date: 2022-07-24
forum: General Help
---

### Post by oygle on 2022-07-24
Kubuntu 21.10 (impish)

[code}sudo apt update[/code]

> Ign:1 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) impish InRelease
Ign:2 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) impish-updates InRelease
Ign:3 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) impish-backports InRelease
Err:4 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) impish Release
  404  Not Found [IP: 202.158.214.106 80]
Err:5 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) impish-updates Release
  404  Not Found [IP: 202.158.214.106 80]
Err:6 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) impish-backports Release
  404  Not Found [IP: 202.158.214.106 80]
Ign:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) impish-security InRelease
Err:8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) impish-security Release 
  404  Not Found [IP: 91.189.91.38 80]
Ign:9 [https://www.scootersoftware.com](https://www.scootersoftware.com) bcompare4 InRelease
Hit:10 [https://www.scootersoftware.com](https://www.scootersoftware.com) bcompare4 Release
Reading package lists... Done
E: The repository 'http://au.archive.ubuntu.com/ubuntu impish Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://au.archive.ubuntu.com/ubuntu impish-updates Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://au.archive.ubuntu.com/ubuntu impish-backports Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'http://security.ubuntu.com/ubuntu impish-security Release' no longer has a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

some searching, and the only hint/s are problems with the sources list, in that a PPA may be incorrectly defined. Yet even though I do have a few PPA's defined, I cannot find them in the sources.list ? Theree are no "impish" paths at [http://au.archive.ubuntu.com/ubuntu/dists/](http://au.archive.ubuntu.com/ubuntu/dists/) either ??

---

### Post by deadflowr on 2022-07-24
21.10 hit end of life last week and the repositories have now been removed.
See: [https://lists.ubuntu.com/archives/ubuntu-security-announce/2022-July/006681.html]("https://lists.ubuntu.com/archives/ubuntu-security-announce/2022-July/006681.html")

---

### Post by oygle on 2022-07-24
> **deadflowr said:**
> 21.10 hit end of life last week and the repositories have now been removed.
See: [https://lists.ubuntu.com/archives/ubuntu-security-announce/2022-July/006681.html]("https://lists.ubuntu.com/archives/ubuntu-security-announce/2022-July/006681.html")

Okay thank you.

---

### Post by guiverc on 2022-07-24
The following will help you find where the main archive *moved* - [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Do note:   You're using the AARNET mirror with your *au.archive.ubuntu.com*, and *mirrors* are free to *drop* the archive any time post-EOL (*most drop only after the main archive move occurs*).

A full list of the mirrors can be found here - [https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)
though I verified who hosted it via

```
guiverc@dc780-deb:/de2900/lubuntu_64$   ping au.archive.ubuntu.com
PING mirror.aarnet.edu.au (202.158.214.106) 56(84) bytes of data.
64 bytes from mirror.aarnet.edu.au (202.158.214.106): icmp_seq=1 ttl=55 time=11.7 ms
```

If you change to use the old-releases are per *EOLUpgrades* link, don't forget to drop the 'au.' part, as country mirrors don't exist for *old-releases*.

---

### Post by oygle on 2022-07-24
Thanks for your help and those tips re the **.au **side of things. As I prefer a fresh insall, am now downloading Kubuntu 22.04

Time to backup. I have a tailored 'install' instruction procedures, which makes it nice and easy.

---

