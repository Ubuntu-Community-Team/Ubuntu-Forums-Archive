---
title: "Can't install git..."
date: 2013-02-06
forum: General Help
---

### Post by z0mghii on 2013-02-06
```

michael@michael-HP-EliteBook-8460p:~$ sudo apt-get install git
[sudo] password for michael: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-29 linux-headers-3.2.0-29-generic
Use 'apt-get autoremove' to remove them.
Suggested packages:
  git-daemon-run git-daemon-sysvinit git-doc git-el git-arch git-cvs git-svn
  git-email git-gui gitk gitweb
The following NEW packages will be installed:
  git
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/6,087 kB of archives.
After this operation, 14.0 MB of additional disk space will be used.
(Reading database ... 182764 files and directories currently installed.)
Unpacking git (from .../git_1%3a1.7.9.5-1_amd64.deb) ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:4>: data error'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/git_1%3a1.7.9.5-1_amd64.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
No apport report written because the error message indicates an issue on the local system
         Errors were encountered while processing:
 /var/cache/apt/archives/git_1%3a1.7.9.5-1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```any ideas?

---

