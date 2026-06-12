---
title: "apt-get refuses to install anything due to &quot;unmet dependencies&quot;"
date: 2015-10-08
forum: General Help
---

### Post by ddm999 on 2015-10-08
Been using Xubuntu (12.04 Precise) on my Asus Flip Chromebook, and everything was going fine until I tried to build SDL1.2 for something I was trying to install. It failed, and seemed to do so because of my Chromebook being ARM. I didn't really care that much about installing the game, put it down to the library just not supporting my Chromebook, and gave up.

Now, whenever I try and use apt-get it always fails, telling me that libsdl1.2-dev depends on libglu1-mesa-dev but it is not going to be installed, and then fails with "unmet dependencies".

apt-get autoremove / remove / purge all do nothing, apt-get install libglu1-mesa-dev depends on something else, which depends on something else, which depends on yet another thing and nothing works on any of them...

apt-get -f install fails, which is why the problem has arisen. So while I'd prefer for it to actually succeed and work, I'd also like to know how to stop apt-get from getting stuck like this. There's every chance that something that simply won't compile on my hardware is in apt-get, and if it completely prevents me from using it, that's not really a good thing.

```
(precise-xiwi)ddm@localhost:~$ sudo apt-get install libsdl1.2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libsdl1.2-dev is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libsdl1.2-dev : Depends: libglu1-mesa-dev but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
(precise-xiwi)ddm@localhost:~$ sudo apt-get install libglu1-mesa-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libglu1-mesa-dev : Depends: libgl1-mesa-dev or
                             libgl1-mesa-dev-lts-quantal but it is not going to be installed or
                             libgl1-mesa-dev-lts-raring but it is not installable or
                             libgl1-mesa-dev-lts-saucy but it is not installable or
                             libgl1-mesa-dev-lts-trusty but it is not installable or
                             libgl-dev
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
(precise-xiwi)ddm@localhost:~$ sudo apt-get install libgl1-mesa-dev 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libgl1-mesa-dev : Depends: mesa-common-dev (= 8.0.4-0ubuntu0.7) or
                            mesa-common-dev-lts-quantal but it is not going to be installed or
                            mesa-common-dev-lts-raring but it is not installable or
                            mesa-common-dev-lts-saucy but it is not installable or
                            mesa-common-dev-lts-trusty but it is not installable
 libsdl1.2-dev : Depends: libglu1-mesa-dev but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
(precise-xiwi)ddm@localhost:~$ sudo apt-get install mesa-common-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libsdl1.2-dev : Depends: libglu1-mesa-dev but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
(precise-xiwi)ddm@localhost:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libjpeg-turbo-progs libjpeg-progs
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libgl1-mesa-dev libglu1-mesa-dev mesa-common-dev
The following NEW packages will be installed:
  libgl1-mesa-dev libglu1-mesa-dev mesa-common-dev
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/418 kB of archives.
After this operation, 2356 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 65110 files and directories currently installed.)
Unpacking mesa-common-dev (from .../mesa-common-dev_8.0.4-0ubuntu0.7_armhf.deb) ...
xz: /usr/lib/arm-linux-gnueabihf/liblzma.so.5: version `XZ_5.2' not found (required by xz)
dpkg-deb (subprocess): subprocess data returned error exit status 1
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/mesa-common-dev_8.0.4-0ubuntu0.7_armhf.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
No apport report written because the error message indicates an issue on the local system
                                                                                         Unpacking libgl1-mesa-dev (from .../libgl1-mesa-dev_8.0.4-0ubuntu0.7_armhf.deb) ...
xz: /usr/lib/arm-linux-gnueabihf/liblzma.so.5: version `XZ_5.2' not found (required by xz)
dpkg-deb (subprocess): subprocess data returned error exit status 1
dpkg-deb: error: subprocess <decompress> returned error exit status 2
No apport report written because the error message indicates an issue on the local system
                                                                                         dpkg: error processing /var/cache/apt/archives/libgl1-mesa-dev_8.0.4-0ubuntu0.7_armhf.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
Unpacking libglu1-mesa-dev (from .../libglu1-mesa-dev_8.0.4-0ubuntu0.7_armhf.deb) ...
xz: /usr/lib/arm-linux-gnueabihf/liblzma.so.5: version `XZ_5.2' not found (required by xz)
dpkg-deb (subprocess): subprocess data returned error exit status 1
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/libglu1-mesa-dev_8.0.4-0ubuntu0.7_armhf.deb (--unpack):
 subprocess dpkg-deb --fsys-tarfile returned error exit status 2
No apport report written because the error message indicates an issue on the local system
                                                                                         Errors were encountered while processing:
 /var/cache/apt/archives/mesa-common-dev_8.0.4-0ubuntu0.7_armhf.deb
 /var/cache/apt/archives/libgl1-mesa-dev_8.0.4-0ubuntu0.7_armhf.deb
 /var/cache/apt/archives/libglu1-mesa-dev_8.0.4-0ubuntu0.7_armhf.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

The issues with liblzma are also a concern considering I actually built xz-5.2.2 myself, and it works perfectly fine with other programs.
Not only that, but I've built SDL-1.2.15 myself without any problems. The issue is only with apt-get.

---

