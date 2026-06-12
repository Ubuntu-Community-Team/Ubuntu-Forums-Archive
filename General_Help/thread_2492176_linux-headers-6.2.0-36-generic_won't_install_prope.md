---
title: "linux-headers-6.2.0-36-generic won't install properly, broken rtl88x2bu driver"
date: 2023-11-02
forum: General Help
---

### Post by pgratz on 2023-11-02
I recently did an apt dist-upgrade that installed 6.2.0-36 in my 23.04 kubuntu system.  It seems to have installed the kernel but the headers were not installed properly leaving the system not bootable (I was able to get booted on 6.2.0-35 through the advanced option in grub.  Trying to do an apt-get install -f it tries reinstalling the headers.  This is the output:

```
[FONT=monospace][COLOR=#000000]Setting up linux-headers-6.2.0-36-generic (6.2.0-36.37) ...[/COLOR]
/etc/kernel/header_postinst.d/dkms:
 * dkms: running auto installation service for kernel 6.2.0-36-generic

hid-asus-rog.ko:
Running module version sanity check.
Module version  for hid-asus-rog.ko
exactly matches what is already found in kernel 6.2.0-36-generic.
DKMS will not replace this module.
You may override by specifying --force.
depmod...
Sign command: /usr/bin/kmodsign
Signing key: /var/lib/shim-signed/mok/MOK.priv
Public certificate (MOK): /var/lib/shim-signed/mok/MOK.der

Building module:
Cleaning build area...
'./driverctl' make all.......(bad exit status: 2)
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/rtl88x2bu-dkms.0.crash'
Error! Bad return status for module build on kernel: 6.2.0-36-generic (x86_64)
Consult /var/lib/dkms/rtl88x2bu/5.13.1/build/make.log for more information.
dkms autoinstall on 6.2.0-36-generic/x86_64 succeeded for acpi-call acpi-call hid-asus-rog hid-asus-rog hid-asus-rog hid-asus-rog hid-asus-rog hid-asus-rog hid-asus-r
og hid-asus-rog hid-asus-rog hid-asus-rog hid-asus-rog hid-asus-rog hid-asus-rog hid-asus-rog hid-asus-rog hid-asus-rog hid-asus-rog hid-asus-rog hid-asus-rog hid-asu
s-rog hid-asus-rog hid-asus-rog hid-asus-rog hid-asus-rog hid-asus-rog hid-asus-rog hid-asus-rog hid-asus-rog hid-asus-rog hid-asus-rog nvidia nvidia tp_smapi tp_smap
i tp_smapi tp_smapi tp_smapi tp_smapi tp_smapi tp_smapi tp_smapi tp_smapi tp_smapi tp_smapi hid-asus-rog
dkms autoinstall on 6.2.0-36-generic/x86_64 failed for rtl88x2bu(10)
Error! One or more modules failed to install during autoinstall.
Refer to previous errors for more information.
 * dkms: autoinstall for kernel 6.2.0-36-generic
   ...fail!
run-parts: /etc/kernel/header_postinst.d/dkms exited with return code 11
dpkg: error processing package linux-headers-6.2.0-36-generic (--configure):
 installed linux-headers-6.2.0-36-generic package post-installation script subprocess returned error exit status 1

[/FONT]
```

Looking into the log file it points at I see this at the end of the file:

```
/var/lib/dkms/rtl88x2bu/5.13.1/build/os_dep/linux/wifi_regd.c: In function &#8216;rtw_regd_init&#8217;:/var/lib/dkms/rtl88x2bu/5.13.1/build/os_dep/linux/wifi_regd.c:409:36: error: &#8216;REGULATORY_IGNORE_STALE_KICKOFF&#8217; undeclared (first use in this function)
  409 |         wiphy->regulatory_flags |= REGULATORY_IGNORE_STALE_KICKOFF;
      |                                    ^~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
/var/lib/dkms/rtl88x2bu/5.13.1/build/os_dep/linux/wifi_regd.c:409:36: note: each undeclared identifier is reported only once for each function it appears in
make[2]: *** [scripts/Makefile.build:260: /var/lib/dkms/rtl88x2bu/5.13.1/build/os_dep/linux/wifi_regd.o] Error 1
make[2]: *** Waiting for unfinished jobs....
make[1]: *** [Makefile:2026: /var/lib/dkms/rtl88x2bu/5.13.1/build] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-6.2.0-36-generic'
make: *** [Makefile:2506: modules] Error 2



```

I'm not sure how to fix this but I did find this error discussed on the main kernel logs some months ago.   How should I proceed to make the system bootable, is it safe for me to just remove that kernel version (and how?)
Thanks!

---

### Post by Yellow Pasque on 2023-11-03
You're going to need a later version of the rtl88x2bu module if you want it build on newer kernels: [https://github.com/RinCat/RTL88x2BU-Linux-Driver/commit/57e50db8bfa6d662c098095a251bb42d457fa984](https://github.com/RinCat/RTL88x2BU-Linux-Driver/commit/57e50db8bfa6d662c098095a251bb42d457fa984)

---

### Post by MAFoElffen on 2023-11-03
Which kernel are you booted from? 
```

uname -r

```
Nevermind. Read it, -35...

---

