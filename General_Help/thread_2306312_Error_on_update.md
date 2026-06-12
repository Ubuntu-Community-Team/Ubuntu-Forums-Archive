---
title: "Error on update"
date: 2015-12-14
forum: General Help
---

### Post by lsutiger on 2015-12-14
As I was doing normal software updates through the software updater, I received a message that 'The package system is broken'. Within this message it stated that this is caused by third party repositories and to disable them(Other Software tab), which I did. Update and retry, same error. I then open a terminal and give the command : sudo apt-get install -f, which returned this:
```
The following NEW packages will be installed:
  libbind9-90
0 upgraded, 1 newly installed, 0 to remove and 13 not upgraded.
Need to get 22.1 kB of archives.
After this operation, 110 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main libbind9-90 amd64 1:9.9.5.dfsg-3ubuntu0.5 [22.1 kB]
Fetched 22.1 kB in 0s (30.6 kB/s)      
dpkg: error: parsing file '/var/lib/dpkg/status' near line 45633 package 'audacious':
 'Depends' field, missing architecture name, or garbage where architecture name expected
E: Sub-process /usr/bin/dpkg returned an error code (2)

```
Sooo...is this something wrong with the repositories or is there something wrong on my end?

---

### Post by ian-weisser on 2015-12-14
Look closely at the error message.

> **lsutiger said:**
> dpkg: error: parsing file '/var/lib/dpkg/status' near line 45633 package 'audacious':
 'Depends' field, missing architecture name, or garbage where architecture name expected

See how it's trying to parse a local file? And failing?
That means the problem is on your end.

Happily, it's usually not difficult to fix.
dpkg keeps a backup of the status file, just in case of various possible failures. Let's try that.

```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status    ## Overwrite the corrupt with the backup
sudo apt update
sudo apt upgrade
```

---

### Post by lsutiger on 2015-12-14
Thank you for the quick reply!
That seemed to have worked to get the updates working. 
When I run Software Updater now I get a title bar with an empty grey box. Attached is an example.

---

### Post by ian-weisser on 2015-12-14
If updates work properly using shell, then reinstall the 'update-manager' package.

---

### Post by lsutiger on 2015-12-14
Thanks!

---

