---
title: "Kernel upgrade problem."
date: 2008-05-26
forum: General Help
---

### Post by Th3Professor on 2008-05-26
I received the following error after an auto-update:

"An error occured

The following details are provided:
```

E: linux-image-2.6.24-17-generic: subprocess post-installation script returned error exit status 1
E: linux-image-2.6.24-17-rt: subprocess post-installation script returned error exit status 1
E: linux-ubuntu-modules-2.6.24-17-generic: dependency problems - leaving unconfigured
E: linux-ubuntu-modules-2.6.24-17-rt: dependency problems - leaving unconfigured
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-2.6.24-17-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured
E: linux-restricted-modules-2.6.24-17-rt: dependency problems - leaving unconfigured
E: linux-image-rt: dependency problems - leaving unconfigured
E: linux-restricted-modules-rt: dependency problems - leaving unconfigured
E: linux-rt: dependency problems - leaving unconfigured
```The change is from -16 to -17 in both generic and rt.

I'm concerned there may be a problem at my next boot/restart or that it actually did not complete the change to -17.

How do I get the kernel upgrade to complete without error?

What is this mention of "dependency problems" throughout?

Is there a way I can readily resolve the dependency problems?

EDIT:

Here are more details:

```

Preconfiguring packages ...
Selecting previously deselected package linux-image-2.6.24-17-generic.
(Reading database ... 144041 files and directories currently installed.)
Unpacking linux-image-2.6.24-17-generic (from .../linux-image-2.6.24-17-generic_2.6.24-17.31_i386.deb) ...
Done.
Selecting previously deselected package linux-image-2.6.24-17-rt.
Unpacking linux-image-2.6.24-17-rt (from .../linux-image-2.6.24-17-rt_2.6.24-17.31_i386.deb) ...
Done.
Selecting previously deselected package linux-ubuntu-modules-2.6.24-17-generic.
Unpacking linux-ubuntu-modules-2.6.24-17-generic (from .../linux-ubuntu-modules-2.6.24-17-generic_2.6.24-17.25_i386.deb) ...
Selecting previously deselected package linux-ubuntu-modules-2.6.24-17-rt.
Unpacking linux-ubuntu-modules-2.6.24-17-rt (from .../linux-ubuntu-modules-2.6.24-17-rt_2.6.24-17.25_i386.deb) ...
Preparing to replace python-problem-report 0.108.1 (using .../python-problem-report_0.108.2_all.deb) ...
Unpacking replacement python-problem-report ...
Preparing to replace python-apport 0.108.1 (using .../python-apport_0.108.2_all.deb) ...
Unpacking replacement python-apport ...
Preparing to replace apport 0.108.1 (using .../apport_0.108.2_all.deb) ...
Unpacking replacement apport ...
Preparing to replace apport-gtk 0.108.1 (using .../apport-gtk_0.108.2_all.deb) ...
Unpacking replacement apport-gtk ...
Preparing to replace gdm 2.20.6-0ubuntu1 (using .../gdm_2.20.6-0ubuntu2_i386.deb) ...
Unpacking replacement gdm ...
Preparing to replace gnome-keyring 2.22.1-1 (using .../gnome-keyring_2.22.1-1ubuntu1_i386.deb) ...
Unpacking replacement gnome-keyring ...
Preparing to replace libgnome-keyring0 2.22.1-1 (using .../libgnome-keyring0_2.22.1-1ubuntu1_i386.deb) ...
Unpacking replacement libgnome-keyring0 ...
Preparing to replace libpam-gnome-keyring 2.22.1-1 (using .../libpam-gnome-keyring_2.22.1-1ubuntu1_i386.deb) ...
Unpacking replacement libpam-gnome-keyring ...
Preparing to replace linux-generic 2.6.24.16.18 (using .../linux-generic_2.6.24.17.19_i386.deb) ...
Unpacking replacement linux-generic ...
Preparing to replace linux-image-generic 2.6.24.16.18 (using .../linux-image-generic_2.6.24.17.19_i386.deb) ...
Unpacking replacement linux-image-generic ...
Preparing to replace linux-restricted-modules-common 2.6.24.12-16.34 (using .../linux-restricted-modules-common_2.6.24.12-17.36_all.deb) ...
Unpacking replacement linux-restricted-modules-common ...
Selecting previously deselected package linux-restricted-modules-2.6.24-17-generic.
Unpacking linux-restricted-modules-2.6.24-17-generic (from .../linux-restricted-modules-2.6.24-17-generic_2.6.24.12-17.36_i386.deb) ...
Preparing to replace linux-restricted-modules-generic 2.6.24.16.18 (using .../linux-restricted-modules-generic_2.6.24.17.19_i386.deb) ...
Unpacking replacement linux-restricted-modules-generic ...
Selecting previously deselected package linux-headers-2.6.24-17.
Unpacking linux-headers-2.6.24-17 (from .../linux-headers-2.6.24-17_2.6.24-17.31_all.deb) ...
Selecting previously deselected package linux-headers-2.6.24-17-generic.
Unpacking linux-headers-2.6.24-17-generic (from .../linux-headers-2.6.24-17-generic_2.6.24-17.31_i386.deb) ...
Preparing to replace linux-headers-generic 2.6.24.16.18 (using .../linux-headers-generic_2.6.24.17.19_i386.deb) ...
Unpacking replacement linux-headers-generic ...
Selecting previously deselected package linux-restricted-modules-2.6.24-17-rt.
Unpacking linux-restricted-modules-2.6.24-17-rt (from .../linux-restricted-modules-2.6.24-17-rt_2.6.24.12-17.36_i386.deb) ...
Preparing to replace linux-rt 2.6.24.16.18 (using .../linux-rt_2.6.24.17.19_i386.deb) ...
Unpacking replacement linux-rt ...
Preparing to replace linux-restricted-modules-rt 2.6.24.16.18 (using .../linux-restricted-modules-rt_2.6.24.17.19_i386.deb) ...
Unpacking replacement linux-restricted-modules-rt ...
Preparing to replace linux-image-rt 2.6.24.16.18 (using .../linux-image-rt_2.6.24.17.19_i386.deb) ...
Unpacking replacement linux-image-rt ...
Setting up linux-image-2.6.24-17-generic (2.6.24-17.31) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-17-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.24-17-rt
Found kernel: /vmlinuz-2.6.24-17-generic
Found kernel: /vmlinuz-2.6.24-16-rt
Found kernel: /vmlinuz-2.6.24-16-generic
Found kernel: /memtest86+.bin

(((grub's menu.lst was updated here after a 3-way merge)))

Merging changes into the new version
User postinst hook script [/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.24-17-generic (--configure):
 subprocess post-installation script returned error exit status 1
Setting up linux-image-2.6.24-17-rt (2.6.24-17.31) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-17-rt
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.24-17-rt
Found kernel: /vmlinuz-2.6.24-17-generic
Found kernel: /vmlinuz-2.6.24-16-rt
Found kernel: /vmlinuz-2.6.24-16-generic
Found kernel: /memtest86+.bin
Merging changes into the new version
User postinst hook script [/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.24-17-rt (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-17-generic:
 linux-ubuntu-modules-2.6.24-17-generic depends on linux-image-2.6.24-17-generic; however:
  Package linux-image-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-17-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-17-rt:
 linux-ubuntu-modules-2.6.24-17-rt depends on linux-image-2.6.24-17-rt; however:
  Package linux-image-2.6.24-17-rt is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-17-rt (--configure):
 dependency problems - leaving unconfigured
Setting up python-problem-report (0.108.2) ...

Setting up python-apport (0.108.2) ...

Setting up apport (0.108.2) ...

Setting up apport-gtk (0.108.2) ...

Setting up gdm (2.20.6-0ubuntu2) ...
 * Reloading GNOME Display Manager configuration...
 * Changes will take effect when all current X sessions have ended.
   ...done.

Setting up gnome-keyring (2.22.1-1ubuntu1) ...

Setting up libgnome-keyring0 (2.22.1-1ubuntu1) ...

Setting up libpam-gnome-keyring (2.22.1-1ubuntu1) ...
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.24-17-generic; however:
  Package linux-image-2.6.24-17-generic is not configured yet.
 linux-image-generic depends on linux-ubuntu-modules-2.6.24-17-generic; however:
  Package linux-ubuntu-modules-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-restricted-modules-common (2.6.24.12-17.36) ...

dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-17-generic:
 linux-restricted-modules-2.6.24-17-generic depends on linux-image-2.6.24-17-generic; however:
  Package linux-image-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-17-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.24-17-generic; however:
  Package linux-restricted-modules-2.6.24-17-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.17.19); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.24.17.19); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-2.6.24-17 (2.6.24-17.31) ...
Setting up linux-headers-2.6.24-17-generic (2.6.24-17.31) ...

Setting up linux-headers-generic (2.6.24.17.19) ...
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-17-rt:
 linux-restricted-modules-2.6.24-17-rt depends on linux-image-2.6.24-17-rt; however:
  Package linux-image-2.6.24-17-rt is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-17-rt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-rt:
 linux-image-rt depends on linux-image-2.6.24-17-rt; however:
  Package linux-image-2.6.24-17-rt is not configured yet.
 linux-image-rt depends on linux-ubuntu-modules-2.6.24-17-rt; however:
  Package linux-ubuntu-modules-2.6.24-17-rt is not configured yet.
dpkg: error processing linux-image-rt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-rt:
 linux-restricted-modules-rt depends on linux-restricted-modules-2.6.24-17-rt; however:
  Package linux-restricted-modules-2.6.24-17-rt is not configured yet.
dpkg: error processing linux-restricted-modules-rt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-rt:
 linux-rt depends on linux-image-rt (= 2.6.24.17.19); however:
  Package linux-image-rt is not configured yet.
 linux-rt depends on linux-restricted-modules-rt (= 2.6.24.17.19); however:
  Package linux-restricted-modules-rt is not configured yet.
dpkg: error processing linux-rt (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 linux-image-2.6.24-17-generic
 linux-image-2.6.24-17-rt
 linux-ubuntu-modules-2.6.24-17-generic
 linux-ubuntu-modules-2.6.24-17-rt
 linux-image-generic
 linux-restricted-modules-2.6.24-17-generic
 linux-restricted-modules-generic
 linux-generic
 linux-restricted-modules-2.6.24-17-rt
 linux-image-rt
 linux-restricted-modules-rt
 linux-rt
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-image-2.6.24-17-rt (2.6.24-17.31) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-17-rt
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.24-17-rt
Found kernel: /vmlinuz-2.6.24-17-generic
Found kernel: /vmlinuz-2.6.24-16-rt
Found kernel: /vmlinuz-2.6.24-16-generic
Found kernel: /memtest86+.bin
Merging changes into the new version
User postinst hook script [/sbin/update-grub] exited with value 1
dpkg: error processing linux-image-2.6.24-17-rt (--configure):
 subprocess post-installation script returned error exit status 1
Setting up linux-image-2.6.24-17-generic (2.6.24-17.31) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-17-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.24-17-rt
Found kernel: /vmlinuz-2.6.24-17-generic
Found kernel: /vmlinuz-2.6.24-16-rt
Found kernel: /vmlinuz-2.6.24-16-generic
Found kernel: /memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-17-rt:
 linux-ubuntu-modules-2.6.24-17-rt depends on linux-image-2.6.24-17-rt; however:
  Package linux-image-2.6.24-17-rt is not configured yet.
dpkg: error processing linux-ubuntu-modules-2.6.24-17-rt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-rt:
 linux-image-rt depends on linux-image-2.6.24-17-rt; however:
  Package linux-image-2.6.24-17-rt is not configured yet.
 linux-image-rt depends on linux-ubuntu-modules-2.6.24-17-rt; however:
  Package linux-ubuntu-modules-2.6.24-17-rt is not configured yet.
dpkg: error processing linux-image-rt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.24-17-rt:
 linux-restricted-modules-2.6.24-17-rt depends on linux-image-2.6.24-17-rt; however:
  Package linux-image-2.6.24-17-rt is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.24-17-rt (--configure):
 dependency problems - leaving unconfigured
Setting up linux-ubuntu-modules-2.6.24-17-generic (2.6.24-17.25) ...
update-initramfs: Generating /boot/initrd.img-2.6.24-17-generic

dpkg: dependency problems prevent configuration of linux-rt:
 linux-rt depends on linux-image-rt (= 2.6.24.17.19); however:
  Package linux-image-rt is not configured yet.
dpkg: error processing linux-rt (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-generic (2.6.24.17.19) ...
Setting up linux-restricted-modules-2.6.24-17-generic (2.6.24.12-17.36) ...

Setting up linux-restricted-modules-generic (2.6.24.17.19) ...
dpkg: dependency problems prevent configuration of linux-restricted-modules-rt:
 linux-restricted-modules-rt depends on linux-restricted-modules-2.6.24-17-rt; however:
  Package linux-restricted-modules-2.6.24-17-rt is not configured yet.
dpkg: error processing linux-restricted-modules-rt (--configure):
 dependency problems - leaving unconfigured
Setting up linux-generic (2.6.24.17.19) ...
Errors were encountered while processing:
 linux-image-2.6.24-17-rt
 linux-ubuntu-modules-2.6.24-17-rt
 linux-image-rt
 linux-restricted-modules-2.6.24-17-rt
 linux-rt
 linux-restricted-modules-rt
```

Some issues that stand out, examples at least (there are multiple occurrences of these)...
dpkg: error processing linux-image-2.6.24-17-rt (--configure):
 dpkg: dependency problems prevent configuration of linux-ubuntu-modules-2.6.24-17-rt:

---

### Post by oldos2er on 2008-05-26
Check System, Admin, Software Sources to be sure all repositories are enabled.

---

### Post by drs305 on 2008-05-26
You can also check to see if your designated server is working, or change with "Select Best Server" in Synaptic, Settings, Repositories, Download From, Other.

---

### Post by Th3Professor on 2008-05-26
Good to know info... I went ahead and doublechecked repos... they're all enabled (except source). I did the server switch too - I didn't know it could actually scan for the best one, pretty neat.

I wasn't sure what to do to try to fix the dependency problems so I tried synaptic's "edit>fix broken packages" and it responded almost immediately with "successfully fixed dependency problems"... so fast that I'm not sure it did anything with the kernel changes.

I tried "system>admin>update manager" and did a "check" on it, though it just responded with "your system is up-to-date".

(Hoping that the kernel change works out.)

---

### Post by xfran on 2008-06-06
Did you check the space in your /boot partition?
try to see with: df -h

If it is full, you must remove/move some of the old versions of the kernel and run then:
sudo dpkg --configure -a

That was my problem ...

---

### Post by Th3Professor on 2008-06-07
That did it... :)

I totally forgot that I put a separate partition aside (only 100MB) into /boot.

---

