---
title: "Cannot apt-get update, missing packages prevents this"
date: 2016-03-30
forum: General Help
---

### Post by kevin_2 on 2016-03-30
Hello all, 

I recently installed some packages to do cross compilation on arm devices. Bellow is the code I ran. 

```

sudo apt-get g++-arm-linux-gnueabi g++-arm-linux-gnueabihf binutils-arm-linux-gnueabi gcc-arm-linux-gnueabi gcc-arm-linux-gnueabihf

```

Now when I try and apt-get update this is the output and error I get.

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libstdc++-4.8-dev-armhf-cross : Depends: libstdc++6-armhf-cross (>= 4.8.4-2ubuntu1~14.04.1cross0.11.1) but 4.8.2-16ubuntu4cross0.11 is installed
 libstdc++6-armhf-cross : Depends: gcc-4.8-arm-linux-gnueabihf-base (= 4.8.2-16ubuntu4cross0.11) but 4.8.4-2ubuntu1~14.04.1cross0.11.1 is installed
E: Unmet dependencies. Try using -f.
kevin@kevin-ThinkPad:~$ ^C
kevin@kevin-ThinkPad:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libstdc++-4.8-dev-armhf-cross : Depends: libstdc++6-armhf-cross (>= 4.8.4-2ubuntu1~14.04.1cross0.11.1) but 4.8.2-16ubuntu4cross0.11 is installed
 libstdc++6-armhf-cross : Depends: gcc-4.8-arm-linux-gnueabihf-base (= 4.8.2-16ubuntu4cross0.11) but 4.8.4-2ubuntu1~14.04.1cross0.11.1 is installed
E: Unmet dependencies. Try using -f.



```

Next I tried the suggesting in the above output, I get

```


sudo apt-get -f install 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libstdc++6-armhf-cross
The following packages will be upgraded:
  libstdc++6-armhf-cross
1 upgraded, 0 newly installed, 0 to remove and 9 not upgraded.
4 not fully installed or removed.
Need to get 0 B/210 kB of archives.
After this operation, 77.8 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
WARNING: The following packages cannot be authenticated!
  libstdc++6-armhf-cross
Install these packages without verification? [y/N] y
(Reading database ... 299815 files and directories currently installed.)
Preparing to unpack .../libstdc++6-armhf-cross_4.8.4-2ubuntu1~14.04.1cross0.11.1_all.deb ...
Unpacking libstdc++6-armhf-cross (4.8.4-2ubuntu1~14.04.1cross0.11.1) over (4.8.2-16ubuntu4cross0.11) ...
dpkg: error processing archive /var/cache/apt/archives/libstdc++6-armhf-cross_4.8.4-2ubuntu1~14.04.1cross0.11.1_all.deb (--unpack):
 trying to overwrite '/usr/share/gcc-4.8/python/libstdcxx/__init__.py', which is also in package libstdc++6:amd64 4.8.4-2ubuntu1~14.04.1
Errors were encountered while processing:
 /var/cache/apt/archives/libstdc++6-armhf-cross_4.8.4-2ubuntu1~14.04.1cross0.11.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

What should I do?

---

### Post by v3.xx on 2016-03-31
I ran your install list (i did include the "install" part of the command) on 16.04 and it installed without error.  What version are you using?

---

### Post by slickymaster on 2016-03-31
See [bug 1557205]("https://bugs.launchpad.net/ubuntu/+source/gcc-4.8-armhf-cross/+bug/1557205")

A temporary fix is```
sudo apt-get -o Dpkg::Options::="--force-overwrite" install -f
```

---

### Post by kevin_2 on 2016-03-31
> **slickymaster said:**
> See [bug 1557205]("https://bugs.launchpad.net/ubuntu/+source/gcc-4.8-armhf-cross/+bug/1557205")

A temporary fix is```
sudo apt-get -o Dpkg::Options::="--force-overwrite" install -f
```



Awesome that worked perfectly, what would be the permanent fix?

---

### Post by kevin_2 on 2016-03-31
> **v3.xx said:**
> I ran your install list (i did include the "install" part of the command) on 16.04 and it installed without error.  What version are you using?

I am using ubuntu 14.04 lts with unity as my DE

---

### Post by slickymaster on 2016-04-01
gcc-4.8-armhf-cross is already accepted into trusty-proposed and it will be available in the -proposed repository in a few hours.

---

