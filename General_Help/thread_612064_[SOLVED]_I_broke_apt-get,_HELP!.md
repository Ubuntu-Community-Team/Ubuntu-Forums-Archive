---
title: "[SOLVED] I broke apt-get, HELP!"
date: 2007-11-13
forum: General Help
---

### Post by anaconda on 2007-11-13
I broke apt-get on my reliable ubuntu edgy eft(6.10) installation. Now whatever I try to do with apt-get, or aptitude or synaptic the result is the following error message:

I was just trying to install k3d. And it installed, and even works, but apt-get doesnt. 

> anaconda@rd1:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 85 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up k3d (0.5.12.0-1ubuntu2) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1348, in ?
    main()
  File "/usr/bin/pycentral", line 1342, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 865, in run
    pkg.read_version_info()
  File "/usr/bin/pycentral", line 535, in read_version_info
    raise PyCentralError, "package has no field Python-Version"
__main__.PyCentralError: package has no field Python-Version
dpkg: error processing k3d (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 k3d
E: Sub-process /usr/bin/dpkg returned an error code (1)

Here is a list of commands I have tried (several times) always with the same error message as above..
```
sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get update
sudo apt-get -f install
sudo apt-get check
sudo apt-get remove --purge k3d
sudo dpkg --remove --force-remove-reinstreq k3d
sudo dpkg --clear-avail
sudo dpkg --remove --force-depends --force-remove-reinstreq k3d
sudo apt-get -f install k3d
sudo apt-get -f remove k3d
sudo apt-get autoremove
```

---

### Post by anaconda on 2007-11-13
found an EXTREME solution.. wasn't sure if this would be wise, but because nothing else worked I took the risk :)

[http://ubuntuforums.org/showthread.php?t=39563&page=2](http://ubuntuforums.org/showthread.php?t=39563&page=2)

And now apt-get doesn't complain anymore..

---

### Post by bwgolling on 2007-12-13
Thanks for the info. your solution is what I figured I would have to do to solve this problem.  I then worried that I'd have one little thing here and there go wrong, so I solved the whole damn problem by reinstalling the system.
thanks

---

