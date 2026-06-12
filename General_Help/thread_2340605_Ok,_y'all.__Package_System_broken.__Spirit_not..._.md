---
title: "Ok, y'all.  Package System broken.  Spirit not... yet."
date: 2016-10-20
forum: General Help
---

### Post by artdentus on 2016-10-20
Package system is broken and I can't install a single thing.  Worrisome to say the least.  Usually can crawl out of some deep mud on my own, but here I am... 

Here's what the ol' girl  says about it:

dpkg: error processing package linux-generic-lts-xenial (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-3.19.0-73-generic
 linux-image-extra-3.19.0-73-generic
 linux-image-generic-lts-vivid
 linux-generic-lts-vivid
 linux-image-4.4.0-45-generic
 linux-image-extra-4.4.0-45-generic
 linux-image-generic-lts-xenial
 linux-generic-lts-xenial
E: Sub-process /usr/bin/dpkg returned an error code (1)

Ok, go!

---

### Post by Zero_Bytes on 2016-10-20
Have you tried to fix it with ```

sudo apt-get install -f
```else post your content of: ```
cat /etc/apt/sources.list
```

---

### Post by Impavidus on 2016-10-20
The complete output of **sudo apt-get -f install** would be helpful to determine the root cause of that error.

---

### Post by Bucky Ball on 2016-10-20
> **Impavidus said:**
> The complete output of **sudo apt-get -f install** would be helpful to determine the root cause of that error.

+1. Also, from your output:

```
No apport report written because MaxReports is reached already
```

Welcome. You have a full log file somewhere? What you do have is a mishmash of kernels (you have Vivid and Xenial kernels installed). Best to give as much info as possible in the first post so we don't have to ask later ... which release and flavour of Ubuntu are you actually using? 

Run these three commands, presuming you're running 16.04.

```
sudo apt update
sudo apt full-upgrade
```

Reboot. You also give no idea about what it is you're trying to install, whatever it is, try again. Please post the output of all this *between code tags* (see green link in my signature). Thanks.

Lastly, have you upgraded this from an older release to a new one? Answering the questions I've asked will help you get support.

---

