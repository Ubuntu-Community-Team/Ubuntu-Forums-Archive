---
title: "Font Manager, can't reinstall, update, or remove"
date: 2017-05-06
forum: General Help
---

### Post by CLCressman on 2017-05-06
When I try to update or remove Font Manager (installed from PPA [http://ppa.launchpad.net/font-manager/staging/ubuntu/](http://ppa.launchpad.net/font-manager/staging/ubuntu/)) I get an error or a message that I need to reinstall. When I try to reinstall I get ```
chester@Brown:~$ sudo apt-get install --reinstall font-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  nautilus-font-manager
The following packages will be upgraded:
  font-manager
1 upgraded, 0 newly installed, 0 to remove and 75 not upgraded.
1 not fully installed or removed.
Need to get 0 B/66.6 kB of archives.
After this operation, 0 B of additional disk space will be used.
Selecting previously unselected package font-manager.
(Reading database ... 563821 files and directories currently installed.)
Preparing to unpack .../font-manager_0.7.3~201702220159~ubuntu16.04.1_amd64.deb ...
Unpacking font-manager (0.7.3~201702220159~ubuntu16.04.1) over (0.7.3~201611272346~ubuntu16.04.1) ...
/var/lib/dpkg/info/font-manager.postrm: 24: /var/lib/dpkg/info/font-manager.postrm: glib-compile-schemas: not found
dpkg: warning: subprocess old post-removal script returned error exit status 127
dpkg: trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: 24: /var/lib/dpkg/tmp.ci/postrm: glib-compile-schemas: not found
dpkg: error processing archive /var/cache/apt/archives/font-manager_0.7.3~201702220159~ubuntu16.04.1_amd64.deb (--unpack):
 subprocess new post-removal script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: 24: /var/lib/dpkg/tmp.ci/postrm: glib-compile-schemas: not found
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 127
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for libglib2.0-0:i386 (2.48.2-0ubuntu1) ...
Processing triggers for libglib2.0-0:amd64 (2.48.2-0ubuntu1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/font-manager_0.7.3~201702220159~ubuntu16.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


``` Where do I go from here?
I have Synaptic installed and it won't let me update anything.
Thank you.

---

### Post by &amp;KyT$0P# on 2017-05-06
Please post the output from running each of these commands in Terminal -
```
lsb_release -a
uname -a
dpkg-query -l libglib2.0-bin
dpkg-query -W | grep -i libglib2.0
```

---

### Post by CLCressman on 2017-05-06
```
chester@Brown:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:        16.04
Codename:       xenial
chester@Brown:~$ uname -a
Linux Brown 4.4.0-72-generic #93-Ubuntu SMP Fri Mar 31 14:07:41 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux
chester@Brown:~$ dpkg-query -l libglib2.0-bin
dpkg-query: no packages found matching libglib2.0-bin
chester@Brown:~$ dpkg-query -W | grep -i libglib2.0
libglib2.0-0:amd64      2.48.2-0ubuntu1
libglib2.0-0:i386       2.48.2-0ubuntu1
libglib2.0-data 2.48.2-0ubuntu1

```

---

### Post by &amp;KyT$0P# on 2017-05-06
See if this helps -
```
sudo apt-get install libglib2.0-bin
```

---

### Post by CLCressman on 2017-05-08
```
chester@Brown:~$ sudo apt-get install libglib2.0-bin
[sudo] password for chester: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  font-manager
Suggested packages:
  nautilus-font-manager
The following NEW packages will be installed:
  libglib2.0-bin
The following packages will be upgraded:
  font-manager
1 upgraded, 1 newly installed, 0 to remove and 75 not upgraded.
1 not fully installed or removed.
Need to get 39.4 kB/106 kB of archives.
After this operation, 311 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libglib2.0-bin amd64 2.48.2-0ubuntu1 [39.4 kB]
Fetched 39.4 kB in 0s (107 kB/s)         
(Reading database ... 563821 files and directories currently installed.)
Preparing to unpack .../font-manager_0.7.3~201702220159~ubuntu16.04.1_amd64.deb ...
Unpacking font-manager (0.7.3~201702220159~ubuntu16.04.1) over (0.7.3~201611272346~ubuntu16.04.1) ...
/var/lib/dpkg/info/font-manager.postrm: 24: /var/lib/dpkg/info/font-manager.postrm: glib-compile-schemas: not found
dpkg: warning: subprocess old post-removal script returned error exit status 127
dpkg: trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: 24: /var/lib/dpkg/tmp.ci/postrm: glib-compile-schemas: not found
dpkg: error processing archive /var/cache/apt/archives/font-manager_0.7.3~201702220159~ubuntu16.04.1_amd64.deb (--unpack):
 subprocess new post-removal script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: 24: /var/lib/dpkg/tmp.ci/postrm: glib-compile-schemas: not found
dpkg: error while cleaning up:
 subprocess new post-removal script returned error exit status 127
Selecting previously unselected package libglib2.0-bin.
Preparing to unpack .../libglib2.0-bin_2.48.2-0ubuntu1_amd64.deb ...
Unpacking libglib2.0-bin (2.48.2-0ubuntu1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for libglib2.0-0:i386 (2.48.2-0ubuntu1) ...
Processing triggers for libglib2.0-0:amd64 (2.48.2-0ubuntu1) ...
Errors were encountered while processing:                                                                                  
 /var/cache/apt/archives/font-manager_0.7.3~201702220159~ubuntu16.04.1_amd64.deb                                           
E: Sub-process /usr/bin/dpkg returned an error code (1)                                                                    

```

---

### Post by &amp;KyT$0P# on 2017-05-08
Gak.  Can you install it this way? -
```
apt-get download libglib2.0-bin
sudo dpkg -i ./libglib2.0-bin*.deb
```

---

### Post by CLCressman on 2017-05-08
I don't see any errors with that. What next?```
chester@Brown:~$ apt-get download libglib2.0-bin                                                                           
Get:1 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 libglib2.0-bin amd64 2.48.2-0ubuntu1 [39.4 kB]
Fetched 39.4 kB in 0s (88.2 kB/s)       
chester@Brown:~$ sudo dpkg -i ./libglib2.0-bin*.deb
[sudo] password for chester: 
(Reading database ... 563844 files and directories currently installed.)
Preparing to unpack .../libglib2.0-bin_2.48.2-0ubuntu1_amd64.deb ...
Unpacking libglib2.0-bin (2.48.2-0ubuntu1) over (2.48.2-0ubuntu1) ...
Setting up libglib2.0-bin (2.48.2-0ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...


```

---

### Post by &amp;KyT$0P# on 2017-05-08
Great!  Now try reinstalling font-manager again.

---

### Post by CLCressman on 2017-05-08
It worked. Thanks alot.```
chester@Brown:~$ sudo apt-get install --reinstall font-manager
[sudo] password for chester: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  nautilus-font-manager
The following packages will be upgraded:
  font-manager
1 upgraded, 0 newly installed, 0 to remove and 75 not upgraded.
1 not fully installed or removed.
Need to get 0 B/66.6 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 563844 files and directories currently installed.)
Preparing to unpack .../font-manager_0.7.3~201702220159~ubuntu16.04.1_amd64.deb ...
Unpacking font-manager (0.7.3~201702220159~ubuntu16.04.1) over (0.7.3~201611272346~ubuntu16.04.1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for libglib2.0-0:i386 (2.48.2-0ubuntu1) ...
Processing triggers for libglib2.0-0:amd64 (2.48.2-0ubuntu1) ...
Setting up font-manager (0.7.3~201702220159~ubuntu16.04.1) ...


```

---

### Post by &amp;KyT$0P# on 2017-05-08
You're welcome. :KS

---

