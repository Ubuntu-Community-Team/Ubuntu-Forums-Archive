---
title: "Ubuntu 10.10 vim install from aptitude dpkg -- internal gzip read error"
date: 2012-10-18
forum: General Help
---

### Post by ashgromnies on 2012-10-18
I'm running Ubuntu 10.10(yea, I know -- old box and it's not getting upgraded any time soon sadly) and having trouble getting vim installed from aptitude.

```
$ sudo apt-get install vim
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  vim-runtime
Suggested packages:
  ctags vim-doc vim-scripts
The following NEW packages will be installed:
  vim vim-runtime
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 6,563kB of archives.
After this operation, 27.1MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://us.archive.ubuntu.com/ubuntu/ maverick/main vim-runtime all 2:7.2.330-1ubuntu4 [5,707kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ maverick/main vim i386 2:7.2.330-1ubuntu4 [856kB]
Fetched 6,563kB in 1s (4,331kB/s)
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: invalid distance too far back'
tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now
dpkg-deb: subprocess tar returned error exit status 2
dpkg: error processing /var/cache/apt/archives/vim-runtime_2%3a7.2.330-1ubuntu4_all.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
(Reading database ... 145060 files and directories currently installed.)
Unpacking vim (from .../vim_2%3a7.2.330-1ubuntu4_i386.deb) ...
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: invalid distance too far back'
dpkg-deb: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/vim_2%3a7.2.330-1ubuntu4_i386.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./usr/bin/vim.basic'
Errors were encountered while processing:
 /var/cache/apt/archives/vim-runtime_2%3a7.2.330-1ubuntu4_all.deb
 /var/cache/apt/archives/vim_2%3a7.2.330-1ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Any thoughts?

---

### Post by ashgromnies on 2012-10-19
Bumping this

---

