---
title: "Synapse crashes at keyboard input"
date: 2017-10-13
forum: General Help
---

### Post by checoimg on 2017-10-13
Everytime I try to use Synapse it crashes

I ran this command that I found in a post ```
apt-cache policy synapse ; apt-cache depends synapse | tail -n+2 | grep Dep | tr -s ' ' ' ' | cut -d' ' -f 3 | xargs -IX apt-cache policy X
```

And it outputs: lic6, libglib2.0-0 and libgtk-3-0 seem to be mismatched

```
libc6:
  Installed: 2.23-0ubuntu9
  Candidate: 2.23-0ubuntu9
  Version table:
 *** 2.23-0ubuntu9 500
        500 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu xenial-security/main amd64 Packages
        100 /var/lib/dpkg/status
     2.23-0ubuntu3 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
libcairo2:
  Installed: 1.14.6-1
  Candidate: 1.14.6-1
  Version table:
 *** 1.14.6-1 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
libgdk-pixbuf2.0-0:
  Installed: 2.32.2-1ubuntu1.3
  Candidate: 2.32.2-1ubuntu1.3
  Version table:
 *** 2.32.2-1ubuntu1.3 500
        500 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu xenial-security/main amd64 Packages
        100 /var/lib/dpkg/status
     2.32.2-1ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
libgee-0.8-2:
  Installed: 0.18.0-1
  Candidate: 0.18.0-1
  Version table:
 *** 0.18.0-1 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
libglib2.0-0:
  Installed: 2.48.2-0ubuntu1
  Candidate: 2.48.2-0ubuntu1
  Version table:
 *** 2.48.2-0ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     2.48.0-1ubuntu4 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
libgtk-3-0:
  Installed: 3.18.9-1ubuntu3.3
  Candidate: 3.18.9-1ubuntu3.3
  Version table:
 *** 3.18.9-1ubuntu3.3 500
        500 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     3.18.9-1ubuntu3 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
libjson-glib-1.0-0:
  Installed: 1.1.2-0ubuntu1
  Candidate: 1.1.2-0ubuntu1
  Version table:
 *** 1.1.2-0ubuntu1 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
libkeybinder-3.0-0:
  Installed: 0.3.1-1
  Candidate: 0.3.1-1
  Version table:
 *** 0.3.1-1 500
        500 http://archive.ubuntu.com/ubuntu xenial/universe amd64 Packages
        100 /var/lib/dpkg/status
libnotify4:
  Installed: 0.7.6-2svn1
  Candidate: 0.7.6-2svn1
  Version table:
 *** 0.7.6-2svn1 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
libpango-1.0-0:
  Installed: 1.38.1-1
  Candidate: 1.38.1-1
  Version table:
 *** 1.38.1-1 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
libpangocairo-1.0-0:
  Installed: 1.38.1-1
  Candidate: 1.38.1-1
  Version table:
 *** 1.38.1-1 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
libzeitgeist-2.0-0:
  Installed: 0.9.16-0ubuntu4
  Candidate: 0.9.16-0ubuntu4
  Version table:
 *** 0.9.16-0ubuntu4 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd64 Packages
        100 /var/lib/dpkg/status
```

---

### Post by again? on 2017-10-13
In the terminal try running 
```
GTK_IM_MODULE='' synapse
```

If that works, refer to this thread to change the command in the synapse launcher.
[https://ubuntu-mate.community/t/synapse-crashes-in-16-04/5348/8](https://ubuntu-mate.community/t/synapse-crashes-in-16-04/5348/8)

or probably easier to change your startup command to
```
sh -c 'GTK_IM_MODULE="" synapse --startup'
```
[https://bugs.launchpad.net/synapse-project/+bug/1219314](https://bugs.launchpad.net/synapse-project/+bug/1219314)

---

### Post by checoimg on 2017-10-14
> **guber2 said:**
> In the terminal try running 
```
GTK_IM_MODULE='' synapse
```

If that works, refer to this thread to change the command in the synapse launcher.
[https://ubuntu-mate.community/t/synapse-crashes-in-16-04/5348/8](https://ubuntu-mate.community/t/synapse-crashes-in-16-04/5348/8)

or probably easier to change your startup command to
```
sh -c 'GTK_IM_MODULE="" synapse --startup'
```
[https://bugs.launchpad.net/synapse-project/+bug/1219314](https://bugs.launchpad.net/synapse-project/+bug/1219314)

I decided to make a fresh install since I suspect installing nm-applet-complete (don't remember the exact name) pulled a lot of dependecies and I don't find the package to purge it and see if that rolls back dependencies. I almost got all dependencies corrected except one, libgtk-3-0.

---

### Post by checoimg on 2017-10-14
The package In wanted to purge was: indicator-applet-complete

---

