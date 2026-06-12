---
title: "bikeshed - purge-old-kernels not installed"
date: 2016-03-01
forum: General Help
---

### Post by siennalizard on 2016-03-01
Please feel free to move this to a more relevant forum - I'm not sure that I should even be using it to request information about a specific PPA package, but here goes.

I've found an interesting effect. I installed the bikeshed package in Wily in order to take advantage of the purge-old-kernels script there. Strangely, although the package installed, this file (and possibly others) were not installed. This series of commands and their output shows what's happened:

```
james@zircon:~$ apt-file search '/usr/bin/purge-old-kernels'
bikeshed: /usr/bin/purge-old-kernels
james@zircon:~$ sudo apt-get install --reinstall bikeshed
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 1 reinstalled, 0 to remove and 69 not to upgrade.
Need to get 0 B/21.0 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 712325 files and directories currently installed.)
Preparing to unpack .../bikeshed_1.65-0ubuntu1~wily_all.deb ...
Unpacking bikeshed (1.65-0ubuntu1~wily) over (1.65-0ubuntu1~wily) ...
Processing triggers for man-db (2.7.4-1) ...
Setting up bikeshed (1.65-0ubuntu1~wily) ...
james@zircon:~$ ll /usr/bin/purge-old-kernels
ls: cannot access /usr/bin/purge-old-kernels: No such file or directory
```

So you can see that I've used apt-file to identify that I should expect the script to be installed with that package. I've then reinstalled the package for good measure, but the file is not to be found! What am I doing wrong?

In addition, I'm quite surprised that the bikeshed package is listed as containing this file, but it isn't installed. So the package database and apt-file are consistent, but what actually ends up in my system is not the same:

[http://packages.ubuntu.com/search?suite=wily&arch=any&mode=filename&searchon=contents&keywords=purge-old-kernels](http://packages.ubuntu.com/search?suite=wily&arch=any&mode=filename&searchon=contents&keywords=purge-old-kernels)

In the end, I downloaded the bikeshed package as a .deb archive and extracted the script I wanted.

I also note that several of the other files are installed, but the man page(s) and for the script I want are not:

 [http://packages.ubuntu.com/wily/all/bikeshed/filelist](http://packages.ubuntu.com/wily/all/bikeshed/filelist)

This is the first time in 10 years I've seen this kind of strange behaviour from apt - generally what I ask for gets installed! Any ideas?

---

