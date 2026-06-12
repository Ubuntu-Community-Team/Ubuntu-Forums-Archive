---
title: "apt-get error when attempting to upgrade"
date: 2013-09-08
forum: General Help
---

### Post by dwhitney67 on 2013-09-08
A few weeks ago I had trouble updating the Kernel for Kubuntu 12.04 LTS.  At first I thought it was because my system's /boot partition was full, and new kernel content could not be added.

So I manually removed some old kernel files, leaving only the last 3 revisions.  (Btw, normally I would expect the apt-get/kernel installer to take care of this matter, but apparently it does not always work).

Anyhow, this the output generated when updating the system:
```

$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up linux-image-3.2.0-52-generic (3.2.0-52.78) ...
Internal Error: Could not find image (/boot/vmlinuz-3.2.0-52-generic)
dpkg: error processing linux-image-3.2.0-52-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-52-generic; however:
  Package linux-image-3.2.0-52-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.52.62); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                    Errors were encountered while processing:
 linux-image-3.2.0-52-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Any ideas on how to clear the apt-get cache of this anomaly?

P.S.  In case this is helpful:
```

$ ls -1 /boot
abi-3.2.0-41-generic
abi-3.2.0-44-generic
abi-3.2.0-51-generic
config-3.2.0-41-generic
config-3.2.0-44-generic
config-3.2.0-51-generic
grub
initrd.img-3.2.0-41-generic
initrd.img-3.2.0-44-generic
initrd.img-3.2.0-51-generic
lost+found
memtest86+.bin
memtest86+_multiboot.bin
System.map-3.2.0-41-generic
System.map-3.2.0-44-generic
System.map-3.2.0-51-generic
vmlinuz-3.2.0-41-generic
vmlinuz-3.2.0-44-generic
vmlinuz-3.2.0-51-generic

$ uname -r
3.2.0-51-generic

```

---

### Post by linuxonbute on 2013-09-08
Did you run 
```

sudo apt-get update

```
first?

---

### Post by dwhitney67 on 2013-09-08
Yes I did.

---

### Post by Gyokuro on 2013-09-08
What happens if you issue following:

apt-get clean  && apt-get autoremove && apt-get update && apt-get distupgrade

I can not remember but there was already a discussion about to autoremove old kernels but it did not happend (I think).

---

### Post by carlwsnyder on 2013-09-08
Old kernels are not auto-removed to allow for the possibility that the new kernel would not work on your machine.  You can remove them manually using Synaptic or Ubuntu-Tweak after you have re-booted and confirmed that there are no kernel regressions.

To fix the packages so they will install run the following:```
sudo apt-get update
sudo apt-get -f install
sudo apt-get dist-upgrade
```

---

### Post by dwhitney67 on 2013-09-08
> **Gyokuro said:**
> What happens if you issue following:

apt-get clean  && apt-get autoremove && apt-get update && apt-get distupgrade

I can not remember but there was already a discussion about to autoremove old kernels but it did not happend (I think).

Thanks, your suggestion did not fully work, although I did get an updated kernel out of it (3.2.0-53-generic).  However, I still kept getting the nagging error I reported earlier -- even after a reboot.  [btw, I figured out it is dist-upgrade, not distupgrade].

After I Googled a little bit more, and this led me to an unorthodox solution:  edit the /var/lib/dpkg/status file to remove anything related to the "unconfigured" package, in my case, kernel 3.2.0-52.

Anyhow, again, thank you.

---

