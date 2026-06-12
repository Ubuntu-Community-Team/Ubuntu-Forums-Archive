---
title: "have I messed up apt?"
date: 2007-06-15
forum: General Help
---

### Post by singedwings on 2007-06-15
I have been messing around trying to get my graphics working, in the process I removed a few packages. Trouble is **nvidia-glx** is marked for removal but apt will not remove it. When I do **sudo apt-get install -f** I get:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  nvidia-glx
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 15.7MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 112668 files and directories currently installed.)
Removing nvidia-glx ...
dpkg-divert: rename involves overwriting `/usr/lib/libGL.so.1.2' with
  different file `/usr/lib/nvidia/libGL.so.1.2.xlibmesa', not allowed
dpkg: error processing nvidia-glx (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 nvidia-glx
E: Sub-process /usr/bin/dpkg returned an error code (1)

I cannot unselect it for removal so I am stuck, please help!

---

### Post by smithman89 on 2007-06-15
The thing is, i think you either need nvidia-glx, or nvidia-settings for your card to be supported.  If you install nvidia-settings, it will in the process remove the glx package.

---

### Post by singedwings on 2007-06-15
Unfortunately if I try to install any package apt still tries to resolve the nvidia-glx first and thus fails with the above error.

---

### Post by singedwings on 2007-06-15
I have also tried **sudo apt-get install nvidia-glx** but I get the same result.

---

### Post by foxmulder881 on 2007-06-17
I too am having the same sort of problem.

Whenever I try to install anything at all, I get the error message...

```
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

There's seems to be no fix for it. I have launched a bug report.

---

