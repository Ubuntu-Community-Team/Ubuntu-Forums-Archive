---
title: "Apt-get broken after package install"
date: 2007-05-10
forum: General Help
---

### Post by mikkoko on 2007-05-10
Hello all, I'd like some advice on this..

I installed varnish (a reverse proxy available in universe) via "apt-get install varnish" and now my apt-get is broken.. every time I try to perform any task with apt-get (install or remove or update one or several packages) I get this an error message related to varnish. Here is an example:


```

$ sudo apt-get install transcode
Reading package lists... Done
Building dependency tree       
Reading state information... Done
transcode is already the newest version.
transcode set to manual installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up varnish (1.0.2-2) ...
Starting HTTPd accelerator: /usr/bin/ld: crti.o: No such file: No such file or directory
collect2: ld returned 1 exit status
pclose=256
Internal error: GCC returned 0x0100
invoke-rc.d: initscript varnish, action "start" failed.
dpkg: error processing varnish (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 varnish
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Varnish seems to be working fine...

Any tips? I already tried apt-get clean / autoclean, no change.

---

### Post by mikkoko on 2007-05-10
Sorry all, I just noticed that the forum information still states that I'm using 5.10.. Infact I am using **Ubuntu 7.04**.

---

### Post by blackened on 2007-05-10
This is a known dependency error with varnish. First you should sudo apt-get remove varnish, then sudo apt-get install libc6-dev (or libc6-dev-amd64 if relevant), then sudo apt-get install varnish.

---

### Post by mikkoko on 2007-05-10
Thank you, installing libc6-dev helped.

---

