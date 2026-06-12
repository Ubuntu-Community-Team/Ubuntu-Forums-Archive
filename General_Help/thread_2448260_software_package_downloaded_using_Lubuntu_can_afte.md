---
title: "software package downloaded using Lubuntu can after be used in others Ubuntu distros?"
date: 2020-08-05
forum: General Help
---

### Post by aug7744 on 2020-08-05
Using Lubuntu 20.04 any software package downloaded if correctly copied in correct package folder in others Ubuntu distros can be installed without problems ?
I wait to download some softwares and I use metered internet access thus need avoid download any software all again.

---

### Post by Impavidus on 2020-08-05
If it's the same release of a different Ubuntu flavour (like Lubuntu 20.04 versus Kubuntu 20.04), then yes, the packages come from the same repositories, so they are the same. When talking about different releases, the packages usually contain different versions of the software, but there are exceptions. Pay attention to the version strings. For example,```
apt-cache policy firefox
firefox:
  Installed: 79.0+build1-0ubuntu0.20.04.1
  Candidate: 79.0+build1-0ubuntu0.20.04.1
  Version table:
 *** 79.0+build1-0ubuntu0.20.04.1 500
        500 http://nl.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages
        100 /var/lib/dpkg/status
     75.0+build3-0ubuntu1 500
        500 http://nl.archive.ubuntu.com/ubuntu focal/main amd64 Packages

```tells me that my Xubuntu 20.04 uses Firefox version 79.0+build1-0ubuntu0.20.04.1 (currently installed), which is specifically built for Ubuntu 20.04. A different Ubuntu release would also use Firefox 79.0, but built against different versions of libraries. You can check this information also for packages that are not installed, but that the package manager knows about. There are ways to automate this on a local network, but there are people here who know more about that than I do.

---

### Post by aug7744 on 2020-08-13
Thanks very much.

---

