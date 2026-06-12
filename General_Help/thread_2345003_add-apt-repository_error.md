---
title: "add-apt-repository error"
date: 2016-11-29
forum: General Help
---

### Post by crslp on 2016-11-29
I am trying to install some software for which I have to add repositorys. But for some reason, I can't add repositorys. See example below:

```
chris@mCL:~$ sudo add-apt-repository ppa:stefansundin/truecryptTraceback (most recent call last):
  File "/usr/bin/lsb_release", line 98, in <module>
    main()
  File "/usr/bin/lsb_release", line 62, in main
    distinfo = lsb_release.get_distro_information(options.upstream)
  File "/usr/lib/python3/dist-packages/lsb_release.py", line 344, in get_distro_information
    distinfo = guess_debian_release()
  File "/usr/lib/python3/dist-packages/lsb_release.py", line 239, in guess_debian_release
    get_distro_info(distinfo['ID'])
  File "/usr/lib/python3/dist-packages/lsb_release.py", line 41, in get_distro_info
    RELEASES_ORDER.sort(key=lambda n: float(n[0]))
  File "/usr/lib/python3/dist-packages/lsb_release.py", line 41, in <lambda>
    RELEASES_ORDER.sort(key=lambda n: float(n[0]))
ValueError: could not convert string to float: '16.04 LTS'
Traceback (most recent call last):
  File "/usr/bin/lsb_release", line 98, in <module>
    main()
  File "/usr/bin/lsb_release", line 62, in main
    distinfo = lsb_release.get_distro_information(options.upstream)
  File "/usr/lib/python3/dist-packages/lsb_release.py", line 344, in get_distro_information
    distinfo = guess_debian_release()
  File "/usr/lib/python3/dist-packages/lsb_release.py", line 239, in guess_debian_release
    get_distro_info(distinfo['ID'])
  File "/usr/lib/python3/dist-packages/lsb_release.py", line 41, in get_distro_info
    RELEASES_ORDER.sort(key=lambda n: float(n[0]))
  File "/usr/lib/python3/dist-packages/lsb_release.py", line 41, in <lambda>
    RELEASES_ORDER.sort(key=lambda n: float(n[0]))
ValueError: could not convert string to float: '6.06 LTS'
Traceback (most recent call last):
  File "/usr/bin/lsb_release", line 98, in <module>
    main()
  File "/usr/bin/lsb_release", line 62, in main
    distinfo = lsb_release.get_distro_information(options.upstream)
  File "/usr/lib/python3/dist-packages/lsb_release.py", line 344, in get_distro_information
    distinfo = guess_debian_release()
  File "/usr/lib/python3/dist-packages/lsb_release.py", line 239, in guess_debian_release
    get_distro_info(distinfo['ID'])
  File "/usr/lib/python3/dist-packages/lsb_release.py", line 41, in get_distro_info
    RELEASES_ORDER.sort(key=lambda n: float(n[0]))
  File "/usr/lib/python3/dist-packages/lsb_release.py", line 41, in <lambda>
    RELEASES_ORDER.sort(key=lambda n: float(n[0]))
ValueError: could not convert string to float: '6.06 LTS'
 TrueCrypt 7.1a package with the following patches:
1) The standard tray icon has been replaced with an application indicator.
2) A bash completion script is included.
3) TrueCrypt is automatically added to your Startup Applications.


To install:
sudo apt-get install dmsetup
sudo add-apt-repository ppa:stefansundin/truecrypt
sudo apt-get update
sudo apt-get install truecrypt


dmsetup will be added as a dependency in the next release.


To automatically grant TrueCrypt root privileges to mount volumes, run `sudo visudo` and add this to the end of the file:
your_username ALL=(ALL) NOPASSWD:/usr/bin/truecrypt


To remove:
sudo apt-get remove truecrypt
sudo apt-add-repository --remove ppa:stefansundin/truecrypt
sudo apt-get update
rm -r ~/.TrueCrypt


https://github.com/stefansundin/truecrypt.deb


Release feed: https://github.com/stefansundin/truecrypt.deb/releases.atom
 Mehr Informationen: https://launchpad.net/~stefansundin/+archive/ubuntu/truecrypt
Drücken Sie [ENTER], um fortzufahren oder Strg-c, um das Hinzufügen abzubrechen



```

This error happens everytime on add-apt-repository. No matter what repository it is.

_Things I've already done_
doesn't work: [https://ubuntuforums.org/showthread.php?t=2210474&highlight=add-apt-repository](https://ubuntuforums.org/showthread.php?t=2210474&highlight=add-apt-repository) 

I've purged ca.certificates, I purged [FONT=gotham]software-properties-common ... nothing worked. 

[/FONT]I appreciate every hint. Thanks a lot!

Oh, I am running ubuntu 16.04.1 x64

---

