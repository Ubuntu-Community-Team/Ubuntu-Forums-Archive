---
title: "Ubuntu 16.04 sudo apt-get -f install issue"
date: 2018-07-02
forum: General Help
---

### Post by flightlesskite on 2018-07-02
So I was trying to install CUDA to use with ZED camera today...

&& the command line prompted me to run [B]sudo apt-get -f install 
[/B]which I attempted and I keep getting this massive error:
```


dpkg: error processing archive /var/cache/apt/archives/linux-modules-4.15.0-24-generic_4.15.0-24.26~16.04.1_amd64.deb (--unpack):
 cannot copy extracted data for './boot/System.map-4.15.0-24-generic' to '/boot/System.map-4.15.0-24-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to unpack .../linux-image-4.15.0-24-generic_4.15.0-24.26~16.04.1_amd64.deb ...
Unpacking linux-image-4.15.0-24-generic (4.15.0-24.26~16.04.1) ...

dpkg: error processing archive /var/cache/apt/archives/linux-image-4.15.0-24-generic_4.15.0-24.26~16.04.1_amd64.deb (--unpack):
 cannot copy extracted data for './boot/vmlinuz-4.15.0-24-generic' to '/boot/vmlinuz-4.15.0-24-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                             
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to unpack .../linux-image-4.13.0-39-generic_4.13.0-39.44~16.04.1_amd64.deb ...
Examining /etc/kernel/preinst.d/
run-parts: executing /etc/kernel/preinst.d/intel-microcode 4.13.0-39-generic /boot/vmlinuz-4.13.0-39-generic
Done.
Unpacking linux-image-4.13.0-39-generic (4.13.0-39.44~16.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.13.0-39-generic_4.13.0-39.44~16.04.1_amd64.deb (--unpack):
cannot copy extracted data for './boot/vmlinuz-4.13.0-39-generic' to '/boot/vmlinuz-4.13.0-39-generic.dpkg-new': failed to write (No space left on device)
No apport report written because the error message indicates a disk full error
                                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.13.0-39-generic /boot/vmlinuz-4.13.0-39-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.13.0-39-generic /boot/vmlinuz-4.13.0-39-generic
Preparing to unpack .../linux-image-4.13.0-43-generic_4.13.0-43.48~16.04.1_amd64.deb ...
Examining /etc/kernel/preinst.d/
run-parts: executing /etc/kernel/preinst.d/intel-microcode 4.13.0-43-generic /boot/vmlinuz-4.13.0-43-generic
Done.
Unpacking linux-image-4.13.0-43-generic (4.13.0-43.48~16.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/linux-image-4.13.0-43-generic_4.13.0-43.48~16.04.1_amd64.deb (--unpack):
 cannot copy extracted data for './boot/System.map-4.13.0-43-generic' to '/boot/System.map-4.13.0-43-generic.dpkg-new': failed to write (No space left on device)
No apport report written because MaxReports has already been reached
                                                                    dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.13.0-43-generic /boot/vmlinuz-4.13.0-43-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.13.0-43-generic /boot/vmlinuz-4.13.0-43-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-modules-4.15.0-24-generic_4.15.0-24.26~16.04.1_amd64.deb
 /var/cache/apt/archives/linux-image-4.15.0-24-generic_4.15.0-24.26~16.04.1_amd64.deb
 /var/cache/apt/archives/linux-image-4.13.0-39-generic_4.13.0-39.44~16.04.1_amd64.deb
 /var/cache/apt/archives/linux-image-4.13.0-43-generic_4.13.0-43.48~16.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

after trying to find solutions online, I stumbled upon my problem in  which I'm apparently out of disk space & attempted to use commands:
**sudo apt autoremove -f**
**sudo apt autoclean **
auto remove gives me the same errors as ** apt-get -f install**

However, they aren't helping && I've attempted to remove old kernel versions to attempt to free up boot space too..
I'm just really lost on what else I can try.  Can someone please see if they can suggest something?

Thank you

---

### Post by Bashing-om on 2018-07-02
flightlesskite; Hello -

Lets start this by seeing what matches, so we know what we can remove manually.
post back:
```

uname -r
ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/
dpkg -l | grep linux-

```

[INDENT][INDENT]we put the pieces back together
[/INDENT][/INDENT]

---

### Post by deadflowr on 2018-07-02
Add
```
df -h
df -i
``` 
To that list as well.

This should give a base of what you're working with.

---

