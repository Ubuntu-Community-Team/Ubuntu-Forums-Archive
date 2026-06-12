---
title: "Dependency Issues, Can't Install Anything"
date: 2013-03-28
forum: General Help
---

### Post by shibby4555 on 2013-03-28
Trying to configure mail server on my Ubuntu Server 11.10(I think). Can't install anything using apt-get. Tried apt-get install -f. Keep getting dependency issues for linux-image-generic-pae. Can't figure this out for the life of me, can't think of anything I've tweaked, etc.. Need to solve this ASAP, got school work depending on it.


```

root@D1g1talC1tadel:/home/shibby# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.0.0-30 linux-headers-3.0.0-28 linux-headers-3.0.0-29 linux-headers-3.0.0-28-generic-pae linux-headers-3.0.0-30-generic-pae
  linux-headers-3.0.0-29-generic-pae
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-3.0.0-32-generic-pae
Suggested packages:
  fdutils linux-doc-3.0.0 linux-source-3.0.0 linux-tools
The following NEW packages will be installed:
  linux-image-3.0.0-32-generic-pae
0 upgraded, 1 newly installed, 0 to remove and 34 not upgraded.
19 not fully installed or removed.
Need to get 0 B/37.0 MB of archives.
After this operation, 118 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 203348 files and directories currently installed.)
Unpacking linux-image-3.0.0-32-generic-pae (from .../linux-image-3.0.0-32-generic-pae_3.0.0-32.50_i386.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-3.0.0-32-generic-pae_3.0.0-32.50_i386.deb (--unpack):
 failed in write on buffer copy for backend dpkg-deb during `./boot/vmlinuz-3.0.0-32-generic-pae': No space left on device
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.0.0-32-generic-pae /boot/vmlinuz-3.0.0-32-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.0.0-32-generic-pae /boot/vmlinuz-3.0.0-32-generic-pae
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.0.0-32-generic-pae_3.0.0-32.50_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```




UPDATE: If anyone else comes across this issue, My boot disk was full. Run:
```
df
```
You will see  100% /boot
 Went into /boot
Deleted all files associated with old kernals. Bam, works. Don't delete the current kernal. Know which one you are using by "uname -r"

---

### Post by thypnotist on 2013-04-02
> **shibby4555 said:**
> Trying to configure mail server on my Ubuntu Server 11.10(I think). Can't install anything using apt-get. Tried apt-get install -f. Keep getting dependency issues for linux-image-generic-pae. Can't figure this out for the life of me, can't think of anything I've tweaked, etc.. Need to solve this ASAP, got school work depending on it.


```

root@D1g1talC1tadel:/home/shibby# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.0.0-30 linux-headers-3.0.0-28 linux-headers-3.0.0-29 linux-headers-3.0.0-28-generic-pae linux-headers-3.0.0-30-generic-pae
  linux-headers-3.0.0-29-generic-pae
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-3.0.0-32-generic-pae
Suggested packages:
  fdutils linux-doc-3.0.0 linux-source-3.0.0 linux-tools
The following NEW packages will be installed:
  linux-image-3.0.0-32-generic-pae
0 upgraded, 1 newly installed, 0 to remove and 34 not upgraded.
19 not fully installed or removed.
Need to get 0 B/37.0 MB of archives.
After this operation, 118 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 203348 files and directories currently installed.)
Unpacking linux-image-3.0.0-32-generic-pae (from .../linux-image-3.0.0-32-generic-pae_3.0.0-32.50_i386.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-3.0.0-32-generic-pae_3.0.0-32.50_i386.deb (--unpack):
 failed in write on buffer copy for backend dpkg-deb during `./boot/vmlinuz-3.0.0-32-generic-pae': No space left on device
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.0.0-32-generic-pae /boot/vmlinuz-3.0.0-32-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.0.0-32-generic-pae /boot/vmlinuz-3.0.0-32-generic-pae
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.0.0-32-generic-pae_3.0.0-32.50_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```




UPDATE: If anyone else comes across this issue, My boot disk was full. Run:
```
df
```
You will see  100% /boot
 Went into /boot
Deleted all files associated with old kernals. Bam, works. Don't delete the current kernal. Know which one you are using by "uname -r"

Your a legend, Thank you
I took a good look at this last night having put it off for about 4 weeks.
I found that there are many causes of this error, but only this site seems to have solved it for me.
thanks again
David

---

