---
title: "Trying to test old kernels"
date: 2013-07-05
forum: General Help
---

### Post by checoimg on 2013-07-05
I tried downloading the kernel from the reporsitories sites but installation fails. How can I install old kernels  ? A command would be pefect but the ones I tried won't work.  Thank you for your time

---

### Post by checoimg on 2013-07-05
I tried :  sudo apt-get install linux-*   and got thi : Reading package lists... Building dependency tree... Reading state information... libselinux1 is already the newest version. linux-firmware is already the newest version. linux-sound-base is already the newest version. pptp-linux is already the newest version. syslinux is already the newest version. syslinux-common is already the newest version. syslinux-legacy is already the newest version. util-linux is already the newest version. linux-generic is already the newest version. linux-headers-3.8.0-19 is already the newest version. linux-headers-3.8.0-19-generic is already the newest version. linux-headers-3.8.0-25 is already the newest version. linux-headers-3.8.0-25-generic is already the newest version. linux-headers-generic is already the newest version. linux-image-3.8.0-19-generic is already the newest version. linux-image-3.8.0-25-generic is already the newest version. linux-image-extra-3.8.0-19-generic is already the newest version. linux-image-extra-3.8.0-25-generic is already the newest version. linux-image-generic is already the newest version. linux-image-generic set to manually installed. linux-libc-dev is already the newest version. linux-source is already the newest version. linux-source-3.8.0 is already the newest version. linux-source-3.8.0 set to manually installed. Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming. The following information may help to resolve the situation:  The following packages have unmet dependencies:  grub-linuxbios : Depends: grub-coreboot (= 2.00-13ubuntu3)  selinux : PreDepends: grub-pc  selinux-policy-ubuntu : Conflicts: selinux-policy-default E: Unable to correct problems, you have held broken packages.

---

### Post by checoimg on 2013-07-05
I tried :  sudo apt-get install linux-* and got this :  Reading package lists... Building dependency tree... Reading state information... libselinux1 is already the newest version. linux-firmware is already the newest version. linux-sound-base is already the newest version. pptp-linux is already the newest version. syslinux is already the newest version. syslinux-common is already the newest version. syslinux-legacy is already the newest version. util-linux is already the newest version. linux-generic is already the newest version. linux-headers-3.8.0-19 is already the newest version. linux-headers-3.8.0-19-generic is already the newest version. linux-headers-3.8.0-25 is already the newest version. linux-headers-3.8.0-25-generic is already the newest version. linux-headers-generic is already the newest version. linux-image-3.8.0-19-generic is already the newest version. linux-image-3.8.0-25-generic is already the newest version. linux-image-extra-3.8.0-19-generic is already the newest version. linux-image-extra-3.8.0-25-generic is already the newest version. linux-image-generic is already the newest version. linux-image-generic set to manually installed. linux-libc-dev is already the newest version. linux-source is already the newest version. linux-source-3.8.0 is already the newest version. linux-source-3.8.0 set to manually installed. Some packages could not be installed. This may mean that you have requested an impossible situation or if you are using the unstable distribution that some required packages have not yet been created or been moved out of Incoming. The following information may help to resolve the situation:  The following packages have unmet dependencies:  grub-linuxbios : Depends: grub-coreboot (= 2.00-13ubuntu3)  selinux : PreDepends: grub-pc  selinux-policy-ubuntu : Conflicts: selinux-policy-default   E: Unable to correct problems, you have held broken packages.

---

### Post by checoimg on 2013-07-05
Since the post won't get the new lines here's a file with the output from : sudo apt-get install linux-*

---

### Post by Doug S on 2013-07-05
I would copy the .deb files from the [kernel ppa site]("http://kernel.ubuntu.com/~kernel-ppa/mainline/"). Then install them manually using, for example:```
sudo dpkg -i linux-headers-3.10.0-031000rc4_3.10.0-031000rc4.201306020443_all.deb
sudo dpkg -i linux-headers-3.10.0-031000rc4-generic_3.10.0-031000rc4.201306020443_amd64.deb
sudo dpkg -i linux-image-3.10.0-031000rc4-generic_3.10.0-031000rc4.201306020443_amd64.deb
```Then it should be in the grub list on your next re-boot.

---

### Post by checoimg on 2013-07-05
dpkg: error processing linux-image-2.6.33-02063305-generic (--install):  subprocess installed post-installation script returned error exit status 17 Errors were encountered while processing:  linux-image-2.6.33-02063305-generic

---

### Post by Doug S on 2013-07-05
From your earlier postings, I did not realize that you wanted to go back that far. I'm not surprised that it doesn't work.

---

### Post by checoimg on 2013-07-05
How could you know that ?. I am testing old kernels to see if one works with hibernation to then do a bisect.

---

### Post by checoimg on 2013-07-05
> **Doug S said:**
> I would copy the .deb files from the [kernel ppa site]("http://kernel.ubuntu.com/~kernel-ppa/mainline/"). Then install them manually using, for example:```
sudo dpkg -i linux-headers-3.10.0-031000rc4_3.10.0-031000rc4.201306020443_all.deb sudo dpkg -i linux-headers-3.10.0-031000rc4-generic_3.10.0-031000rc4.201306020443_amd64.deb sudo dpkg -i linux-image-3.10.0-031000rc4-generic_3.10.0-031000rc4.201306020443_amd64.deb
```Then it should be in the grub list on your next re-boot.  How do I uninstall ?  Thanks

---

### Post by deadflowr on 2013-07-05
> **checoimg said:**
> How do I uninstall ?  Thanks

Replace the -i with -r, or -p or --remove, or --purge.

```
man dpkg
```

I think you need to remove the package name, and not the package name.deb.
So instead of linux-headers-numberscheme.deb, it'll be linux-headers-numberscheme.
Something like that.

---

### Post by Doug S on 2013-07-06
> **deadflowr said:**
> I think you need to remove the package name, and not the package name.deb.
So instead of linux-headers-numberscheme.deb, it'll be linux-headers-numberscheme.
Something like that.Exactly. I can never remember, nor type things correctly, so I look at the list of packages and then cut and paste what I want to do. Example:```
doug@s15:~/temp$ [COLOR=#ff0000]dpkg -l | grep linux-[/COLOR]
ii  linux-firmware                         1.79.4                                     Firmware for Linux kernel drivers
ii  linux-firmware-image                   3.10.0-rc7-doug04-12                       Linux kernel firmware, version 3.10.0-rc7-doug04
ii  linux-headers-3.10.0-rc7+              3.10.0-rc7+-10                             Linux kernel headers for 3.10.0-rc7+ on amd64
ii  linux-headers-3.10.0-rc7-dirk01        3.10.0-rc7-dirk01-11                       Linux kernel headers for 3.10.0-rc7-dirk01 on amd64
ii  linux-headers-3.10.0-rc7-doug04        3.10.0-rc7-doug04-12                       Linux kernel headers for 3.10.0-rc7-doug04 on amd64
ii  linux-headers-3.2.0-44                 3.2.0-44.69                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-44-generic         3.2.0-44.69                                Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.0-48                 3.2.0-48.74                                Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-48-generic         3.2.0-48.74                                Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-server                   3.2.0.48.58                                Linux kernel headers on Server Equipment.
rc  linux-image-3.10.0-031000rc4-generic   3.10.0-031000rc4.201306020443              Linux kernel image for version 3.10.0 on 64 bit x86 SMP
rc  linux-image-3.10.0-rc4+                3.10.0-rc4+-1                              Linux kernel, version 3.10.0-rc4+
rc  linux-image-3.10.0-rc5                 3.10.0-rc5-2                               Linux kernel, version 3.10.0-rc5
rc  linux-image-3.10.0-rc5+                3.10.0-rc5+-4                              Linux kernel, version 3.10.0-rc5+
rc  linux-image-3.10.0-rc5-doug01          3.10.0-rc5-doug01-6                        Linux kernel, version 3.10.0-rc5-doug01
rc  linux-image-3.10.0-rc6+                3.10.0-rc6+-7                              Linux kernel, version 3.10.0-rc6+
rc  linux-image-3.10.0-rc6-doug02          3.10.0-rc6-doug02-8                        Linux kernel, version 3.10.0-rc6-doug02
rc  linux-image-3.10.0-rc6-doug03          3.10.0-rc6-doug03-9                        Linux kernel, version 3.10.0-rc6-doug03
ii  linux-image-3.10.0-rc7+                3.10.0-rc7+-10                             Linux kernel, version 3.10.0-rc7+
ii  linux-image-3.10.0-rc7-dirk01          3.10.0-rc7-dirk01-11                       Linux kernel, version 3.10.0-rc7-dirk01
ii  linux-image-3.10.0-rc7-doug04          3.10.0-rc7-doug04-12                       Linux kernel, version 3.10.0-rc7-doug04
rc  linux-image-3.2.0-39-generic           3.2.0-39.62                                Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-40-generic           3.2.0-40.64                                Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-41-generic           3.2.0-41.66                                Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-43-generic           3.2.0-43.68                                Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-44-generic           3.2.0-44.69                                Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-48-generic           3.2.0-48.74                                Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.22+                    3.2.22+-2                                  Linux kernel, version 3.2.22+
rc  linux-image-3.2.23+                    3.2.23+-4                                  Linux kernel, version 3.2.23+
ii  linux-image-server                     3.2.0.48.58                                Linux kernel image on Server Equipment.
ii  linux-libc-dev                         3.2.0-48.74                                Linux Kernel Headers for development
ii  linux-server                           3.2.0.48.58                                Complete Linux kernel on Server Equipment.
doug@s15:~/temp$
doug@s15:~/temp$ [COLOR=#ff0000]sudo dpkg -r linux-image-3.10.0-rc7-doug04[/COLOR]
[sudo] password for doug:
(Reading database ... 192239 files and directories currently installed.)
Removing linux-image-3.10.0-rc7-doug04 ...
update-initramfs: Deleting /boot/initrd.img-3.10.0-rc7-doug04
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.10.0-rc7+
Found initrd image: /boot/initrd.img-3.10.0-rc7+
Found linux image: /boot/vmlinuz-3.10.0-rc7-dirk01
Found initrd image: /boot/initrd.img-3.10.0-rc7-dirk01
Found linux image: /boot/vmlinuz-3.2.0-48-generic
Found initrd image: /boot/initrd.img-3.2.0-48-generic
Found linux image: /boot/vmlinuz-3.2.0-44-generic
Found initrd image: /boot/initrd.img-3.2.0-44-generic
Found memtest86+ image: /memtest86+.bin
Found Microsoft Windows XP Home Edition on /dev/sdb1
done
doug@s15:~/temp$ [COLOR=#ff0000]sudo dpkg -r linux-headers-3.10.0-rc7-doug04[/COLOR]
(Reading database ... 187728 files and directories currently installed.)
Removing linux-headers-3.10.0-rc7-doug04 ...
doug@s15:~/temp$
```

---

### Post by checoimg on 2013-07-06
> **deadflowr said:**
> Replace the -i with -r, or -p or --remove, or --purge.  ```
man dpkg
```  I think you need to remove the package name, and not the package name.deb. So instead of linux-headers-numberscheme.deb, it'll be linux-headers-numberscheme. Something like that.  Well I installed synaptic and uninstalled the kernels from there from there.

---

### Post by deadflowr on 2013-07-06
Synaptic works fine as well.
I just thought, since you installed through dpkg, you'd like to know how to uninstall through dpkg.
If you asked if uninstall through synaptics is possible, I would have just said yes.

---

