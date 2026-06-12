---
title: "Permission denied after installing java-8-openjdk"
date: 2020-04-18
forum: General Help
---

### Post by chiques on 2020-04-18
I'm unable to update Ubuntu. Every time I run my apt-get dist-upgrade -y I get this error:

```

charlie@hooptie-server:~$ sudo -s
root@hooptie-server:/home/charlie# apt-get dist-upgrade -y
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  google-chrome-stable libasound2 libasound2-data thunderbird
  thunderbird-gnome-support thunderbird-locale-en thunderbird-locale-en-us
7 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/111 MB of archives.
After this operation, 505 kB of additional disk space will be used.
Setting up install-info (6.6.0.dfsg.1-2ubuntu2) ...
/usr/sbin/update-info-dir: 2: /etc/environment: /usr/lib/jvm/java-8-openjdk-amd64: Permission denied
dpkg: error processing package install-info (--configure):
 installed install-info package post-installation script subprocess returned error exit status 126
Errors were encountered while processing:
 install-info
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@hooptie-server:/home/charlie# 


charlie@hooptie-server:/usr/sbin$ sudo chmod 775 update-info-dir 

```

I've tried changing the permissions of ```
/usr/sbin/update-info-dir:
```using 

```
charlie@hooptie-server:/usr/sbin$ sudo chmod 775 update-info-dir 
```

but I still get the 'Permission denied' error.

Any ideas?

---

### Post by lvm on 2020-04-19
It says that post-installation script returned an error, so you should figure out what's wrong with it. Control information including postinst script can be extracted from a debian package file with 'dpkg -e package.deb', package will be in your apt cache (/var/cache/apt/archives) or can be downloaded from packages.ubuntu.com. I don't think this is caused by permissions on the script, probably it encounters a file it cannot process which is unusual given that the script is run as root.

---

