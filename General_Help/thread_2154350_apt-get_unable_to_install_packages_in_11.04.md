---
title: "apt-get unable to install packages in 11.04"
date: 2013-06-14
forum: General Help
---

### Post by wind_clouds on 2013-06-14
Hi,

I am unable to install packages in Ubuntu 11.04 getting below error.

Install these packages without verification [y/N]? y
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty/main nmap i386 5.21-1
  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/n/nmap/nmap_5.21-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/n/nmap/nmap_5.21-1_i386.deb)  404  Not Found [IP: 91.189.92.156 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Even i have tried --fix-missing with apt-get install

---

### Post by sandyd on 2013-06-14
> **wind_clouds said:**
> Hi,

I am unable to install packages in Ubuntu 11.04 getting below error.

Install these packages without verification [y/N]? y
Err [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) natty/main nmap i386 5.21-1
  404  Not Found [IP: 91.189.92.156 80]
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/n/nmap/nmap_5.21-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/n/nmap/nmap_5.21-1_i386.deb)  404  Not Found [IP: 91.189.92.156 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Even i have tried --fix-missing with apt-get install

Ubuntu 11.04 has already reached End of Life, and as a result, the repositories have been moved. At the moment, your release does not receive any security updates, and it is reccomended that you upgrade to a supported release such as Ubuntu 12.04.

---

