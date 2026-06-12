---
title: "libgl1-mesa-dev won't install, nvidia drivers are broken :("
date: 2008-03-17
forum: General Help
---

### Post by besseriym on 2008-03-17
I am using Ubuntu Hardy Heron with an AMD64 CPU and an nVidia GeForce 9600 GS.

I recently applied some updates which went smooth except for the libgl1-mesa-dev package. It showed up as a broken package and told me i should fix it with the command "sudo apt-get -f install" which did not work.

The error message i get when i try to install the package is as follows: 
```
besseriym@besseriym:~$ sudo apt-get install libgl1-mesa-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libqt4-qt3support comerr-dev libkrb5-dev liblcms1-dev libglitz-glx1
  libpcrecpp0 libssl-dev libglitz1 libqt4-sql libaudio-dev libpq-dev libkadm55
  libmng-dev libsqlite0-dev
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  libgl1-mesa-dev
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B/27.3kB of archives.
After this operation, 73.7kB of additional disk space will be used.
(Reading database ... 283843 files and directories currently installed.)
Unpacking libgl1-mesa-dev (from .../libgl1-mesa-dev_7.0.3~rc2-1ubuntu2_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libgl1-mesa-dev_7.0.3~rc2-1ubuntu2_all.deb (--unpack):
 error creating symbolic link `./usr/lib/libGL.so': No such file or directory
Errors were encountered while processing:
 /var/cache/apt/archives/libgl1-mesa-dev_7.0.3~rc2-1ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I can no longer start compiz, and i am afraid to reboot my computer. If anyone knows how to fix this, I would appreciate any help very much.

Thanks,
besseriym

*EDIT* It might be worthy to mention that I am currently using the Official NVidia drivers, and NOT the glx drivers.

---

### Post by besseriym on 2008-03-18
-bump-

help! :(

---

### Post by besseriym on 2008-03-20
:( I have searched the forums for similar problems and found a few proposed fixes, but none of them work for me. I triggered the openGL and it crashed the XServer and I was forced to restart. Of course, upon restart I couldn't log into a session because of the libgl1-mesa-dev package being removed.

I am without a "real" desktop for the moment, as I am writing this from an old Compaq I had from the early 90's :(

If anyone has any ideas at all, I would seriously appreciate any of them :)

Thanks.

---

