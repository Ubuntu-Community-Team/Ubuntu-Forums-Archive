---
title: "errors with updates"
date: 2013-03-02
forum: General Help
---

### Post by dpwilson on 2013-03-02
While trying to install updates, or anytime I install an app, I get a message that [I]Package operation failed
The installation or removal of a software package failed[/I], with the following code:  Any advice what to do to fix this?
Currently running  ubuntu 12.04

```
installArchives() failed: (Reading database ... 
(Reading database ... 5%%
(Reading database ... 10%%
(Reading database ... 15%%
(Reading database ... 20%%
(Reading database ... 25%%
(Reading database ... 30%%
(Reading database ... 35%%
(Reading database ... 40%%
(Reading database ... 45%%
(Reading database ... 50%%
(Reading database ... 55%%
(Reading database ... 60%%
(Reading database ... 65%%
(Reading database ... 70%%
(Reading database ... 75%%
(Reading database ... 80%%
(Reading database ... 85%%
(Reading database ... 90%%
(Reading database ... 95%%
(Reading database ... 100%%
(Reading database ... 296981 files and directories currently installed.)
Preparing to replace google-chrome-stable 24.0.1312.70-r181759 (using .../google-chrome-stable_25.0.1364.97-r183676_i386.deb) ...
Unpacking replacement google-chrome-stable ...
Preparing to replace libgl1-mesa-dri 8.0.4-0ubuntu0.3 (using .../libgl1-mesa-dri_8.0.4-0ubuntu0.4_i386.deb) ...
Unpacking replacement libgl1-mesa-dri ...
Preparing to replace libgl1-mesa-glx 8.0.4-0ubuntu0.3 (using .../libgl1-mesa-glx_8.0.4-0ubuntu0.4_i386.deb) ...
Unpacking replacement libgl1-mesa-glx ...
Preparing to replace libglapi-mesa 8.0.4-0ubuntu0.3 (using .../libglapi-mesa_8.0.4-0ubuntu0.4_i386.deb) ...
Unpacking replacement libglapi-mesa ...
Preparing to replace libxatracker1 8.0.4-0ubuntu0.3 (using .../libxatracker1_8.0.4-0ubuntu0.4_i386.deb) ...
Unpacking replacement libxatracker1 ...
Preparing to replace unity-greeter 0.2.9-0ubuntu1 (using .../unity-greeter_0.2.9-0ubuntu1.1_i386.deb) ...
Unpacking replacement unity-greeter ...
Preparing to replace libglu1-mesa 8.0.4-0ubuntu0.3 (using .../libglu1-mesa_8.0.4-0ubuntu0.4_i386.deb) ...
Unpacking replacement libglu1-mesa ...
Preparing to replace adobe-flash-properties-gtk 11.2.202.270-0precise1 (using .../adobe-flash-properties-gtk_11.2.202.273-0precise1_i386.deb) ...
Unpacking replacement adobe-flash-properties-gtk ...
Preparing to replace adobe-flashplugin 11.2.202.270-0precise1 (using .../adobe-flashplugin_11.2.202.273-0precise1_i386.deb) ...
Unpacking replacement adobe-flashplugin ...
Preparing to replace software-center 5.2.7 (using .../software-center_5.2.9_all.deb) ...
Unpacking replacement software-center ...
Preparing to replace xserver-xorg-video-nouveau 1:0.0.16+git20111201+b5534a1-1build2 (using .../xserver-xorg-video-nouveau_1%%3a0.0.16+git20111201+b5534a1-1build3_i386.deb) ...
Unpacking replacement xserver-xorg-video-nouveau ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for man-db ...
Processing triggers for libglib2.0-0 ...
Processing triggers for hicolor-icon-theme ...
Setting up linux-image-3.2.0-34-generic-pae (3.2.0-34.53) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-34-generic-pae /boot/vmlinuz-3.2.0-34-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-34-generic-pae
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-34-generic-pae /boot/vmlinuz-3.2.0-34-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-34-generic-pae /boot/vmlinuz-3.2.0-34-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-34-generic-pae /boot/vmlinuz-3.2.0-34-generic-pae
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-34-generic-pae.postinst line 1010.
dpkg: error processing linux-image-3.2.0-34-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.2.0-35-generic-pae (3.2.0-35.55) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-35-generic-pae /boot/vmlinuz-3.2.0-35-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-35-generic-pae
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-35-generic-pae /boot/vmlinuz-3.2.0-35-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-35-generic-pae /boot/vmlinuz-3.2.0-35-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-35-generic-pae /boot/vmlinuz-3.2.0-35-generic-pae
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-35-generic-pae.postinst line 1010.
dpkg: error processing linux-image-3.2.0-35-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.2.0-37-generic-pae (3.2.0-37.58) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-37-generic-pae /boot/vmlinuz-3.2.0-37-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-37-generic-pae
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-37-generic-pae /boot/vmlinuz-3.2.0-37-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-37-generic-pae /boot/vmlinuz-3.2.0-37-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-37-generic-pae /boot/vmlinuz-3.2.0-37-generic-pae
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-37-generic-pae.postinst line 1010.
dpkg: error processing linux-image-3.2.0-37-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.2.0-38-generic-pae (3.2.0-38.61) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-38-generic-pae /boot/vmlinuz-3.2.0-38-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-38-generic-pae
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-38-generic-pae /boot/vmlinuz-3.2.0-38-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-38-generic-pae /boot/vmlinuz-3.2.0-38-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-38-generic-pae /boot/vmlinuz-3.2.0-38-generic-pae
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-38-generic-pae.postinst line 1010.
dpkg: error processing linux-image-3.2.0-38-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up grub-pc (1.99-21ubuntu3.9) ...
No apport report written because MaxReports is reached already
/var/lib/dpkg/info/grub-pc.config: 11: /etc/default/grub: splash: not found
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-3.2.0-34-generic-pae; however:
  Package linux-image-3.2.0-34-generic-pae is not configured yet.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.34.37); however:
  Package linux-image-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
Setting up google-chrome-stable (25.0.1364.97-r183676) ...
Setting up libgl1-mesa-dri (8.0.4-0ubuntu0.4) ...
Setting up libglapi-mesa (8.0.4-0ubuntu0.4) ...
Setting up libgl1-mesa-glx (8.0.4-0ubuntu0.4) ...
Setting up libxatracker1 (8.0.4-0ubuntu0.4) ...
Setting up unity-greeter (0.2.9-0ubuntu1.1) ...
Setting up libglu1-mesa (8.0.4-0ubuntu0.4) ...
Setting up adobe-flashplugin (11.2.202.273-0precise1) ...
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/mozilla/plugins/flashplugin-alternative.so (mozilla-flashplugin) in auto mode.
Setting up adobe-flash-properties-gtk (11.2.202.273-0precise1) ...
Setting up software-center (5.2.9) ...
Updating software catalog...this may take a moment.
INFO:softwarecenter.db.pkginfo_impl.aptcache:aptcache.open()
Software catalog update was successful.
Setting up xserver-xorg-video-nouveau (1:0.0.16+git20111201+b5534a1-1build3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 linux-image-3.2.0-34-generic-pae
 linux-image-3.2.0-35-generic-pae
 linux-image-3.2.0-37-generic-pae
 linux-image-3.2.0-38-generic-pae
 grub-pc
 linux-image-generic-pae
 linux-generic-pae
Error in function: 
Setting up linux-image-3.2.0-37-generic-pae (3.2.0-37.58) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-37-generic-pae /boot/vmlinuz-3.2.0-37-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-37-generic-pae
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-37-generic-pae /boot/vmlinuz-3.2.0-37-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-37-generic-pae /boot/vmlinuz-3.2.0-37-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-37-generic-pae /boot/vmlinuz-3.2.0-37-generic-pae
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-37-generic-pae.postinst line 1010.
dpkg: error processing linux-image-3.2.0-37-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.2.0-35-generic-pae (3.2.0-35.55) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-35-generic-pae /boot/vmlinuz-3.2.0-35-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-35-generic-pae
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-35-generic-pae /boot/vmlinuz-3.2.0-35-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-35-generic-pae /boot/vmlinuz-3.2.0-35-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-35-generic-pae /boot/vmlinuz-3.2.0-35-generic-pae
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-35-generic-pae.postinst line 1010.
dpkg: error processing linux-image-3.2.0-35-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.2.0-38-generic-pae (3.2.0-38.61) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-38-generic-pae /boot/vmlinuz-3.2.0-38-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-38-generic-pae
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-38-generic-pae /boot/vmlinuz-3.2.0-38-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-38-generic-pae /boot/vmlinuz-3.2.0-38-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-38-generic-pae /boot/vmlinuz-3.2.0-38-generic-pae
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-38-generic-pae.postinst line 1010.
dpkg: error processing linux-image-3.2.0-38-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.2.0-34-generic-pae (3.2.0-34.53) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-34-generic-pae /boot/vmlinuz-3.2.0-34-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-34-generic-pae
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-34-generic-pae /boot/vmlinuz-3.2.0-34-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-34-generic-pae /boot/vmlinuz-3.2.0-34-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-34-generic-pae /boot/vmlinuz-3.2.0-34-generic-pae
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-34-generic-pae.postinst line 1010.
dpkg: error processing linux-image-3.2.0-34-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up grub-pc (1.99-21ubuntu3.9) ...
/var/lib/dpkg/info/grub-pc.config: 11: /etc/default/grub: splash: not found
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-3.2.0-34-generic-pae; however:
  Package linux-image-3.2.0-34-generic-pae is not configured yet.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.34.37); however:
  Package linux-image-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured

```

---

### Post by u-noob-tu on 2013-03-02
try "sudo dpkg --configure"
if that doesnt work, try "sudo apt-get install -f"
the first command should fix your problem, though.

---

### Post by dpwilson on 2013-03-02
> **u-noob-tu said:**
> try "sudo dpkg --configure"
if that doesnt work, try "sudo apt-get install -f"
the first command should fix your problem, though. 

Will give it a try and post response.   Thanks for the quick reply.

---

### Post by u-noob-tu on 2013-03-02
correction: the command should be "sudo dpkg --configure -a"
My mistake.

---

### Post by dpwilson on 2013-03-03
No change with "dpkg --configure -a"

```
wilson@wilson-1204:~$ sudo dpkg --configure -a
[sudo] password for wilson: 
Setting up linux-image-3.2.0-37-generic-pae (3.2.0-37.58) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-37-generic-pae /boot/vmlinuz-3.2.0-37-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-37-generic-pae
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-37-generic-pae /boot/vmlinuz-3.2.0-37-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-37-generic-pae /boot/vmlinuz-3.2.0-37-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-37-generic-pae /boot/vmlinuz-3.2.0-37-generic-pae
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-37-generic-pae.postinst line 1010.
dpkg: error processing linux-image-3.2.0-37-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.2.0-35-generic-pae (3.2.0-35.55) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-35-generic-pae /boot/vmlinuz-3.2.0-35-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-35-generic-pae
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-35-generic-pae /boot/vmlinuz-3.2.0-35-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-35-generic-pae /boot/vmlinuz-3.2.0-35-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-35-generic-pae /boot/vmlinuz-3.2.0-35-generic-pae
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-35-generic-pae.postinst line 1010.
dpkg: error processing linux-image-3.2.0-35-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.2.0-38-generic-pae (3.2.0-38.61) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-38-generic-pae /boot/vmlinuz-3.2.0-38-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-38-generic-pae
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-38-generic-pae /boot/vmlinuz-3.2.0-38-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-38-generic-pae /boot/vmlinuz-3.2.0-38-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-38-generic-pae /boot/vmlinuz-3.2.0-38-generic-pae
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-38-generic-pae.postinst line 1010.
dpkg: error processing linux-image-3.2.0-38-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.2.0-34-generic-pae (3.2.0-34.53) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-34-generic-pae /boot/vmlinuz-3.2.0-34-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-34-generic-pae
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-34-generic-pae /boot/vmlinuz-3.2.0-34-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-34-generic-pae /boot/vmlinuz-3.2.0-34-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-34-generic-pae /boot/vmlinuz-3.2.0-34-generic-pae
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-34-generic-pae.postinst line 1010.
dpkg: error processing linux-image-3.2.0-34-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up grub-pc (1.99-21ubuntu3.9) ...
/var/lib/dpkg/info/grub-pc.config: 11: /etc/default/grub: splash: not found
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-3.2.0-34-generic-pae; however:
  Package linux-image-3.2.0-34-generic-pae is not configured yet.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.34.37); however:
  Package linux-image-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.2.0-37-generic-pae
 linux-image-3.2.0-35-generic-pae
 linux-image-3.2.0-38-generic-pae
 linux-image-3.2.0-34-generic-pae
 grub-pc
 linux-image-generic-pae
 linux-generic-pae

```

---

### Post by dpwilson on 2013-03-03
Also, error with sudo apt-get install -f

```
wilson@wilson-1204:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
7 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up linux-image-3.2.0-34-generic-pae (3.2.0-34.53) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-34-generic-pae /boot/vmlinuz-3.2.0-34-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-34-generic-pae
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-34-generic-pae /boot/vmlinuz-3.2.0-34-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-34-generic-pae /boot/vmlinuz-3.2.0-34-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-34-generic-pae /boot/vmlinuz-3.2.0-34-generic-pae
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-34-generic-pae.postinst line 1010.
dpkg: error processing linux-image-3.2.0-34-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.2.0-35-generic-pae (3.2.0-35.55) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-35-generic-pae /boot/vmlinuz-3.2.0-35-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-35-generic-pae
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-35-generic-pae /boot/vmlinuz-3.2.0-35-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-35-generic-pae /boot/vmlinuz-3.2.0-35-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-35-generic-pae /boot/vmlinuz-3.2.0-35-generic-pae
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-35-generic-pae.postinst line 1010.
dpkg: error processing linux-image-3.2.0-35-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up linux-image-3.2.0-37-generic-pae (3.2.0-37.58) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-37-generic-pae /boot/vmlinuz-3.2.0-37-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-37-generic-pae
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-37-generic-pae /boot/vmlinuz-3.2.0-37-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-37-generic-pae /boot/vmlinuz-3.2.0-37-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-37-generic-pae /boot/vmlinuz-3.2.0-37-generic-pae
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-37-generic-pae.postinst line 1010.
dpkg: error processing linux-image-3.2.0-37-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up linux-image-3.2.0-38-generic-pae (3.2.0-38.61) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-38-generic-pae /boot/vmlinuz-3.2.0-38-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-38-generic-pae
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-38-generic-pae /boot/vmlinuz-3.2.0-38-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-38-generic-pae /boot/vmlinuz-3.2.0-38-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-38-generic-pae /boot/vmlinuz-3.2.0-38-generic-pae
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-38-generic-pae.postinst line 1010.
dpkg: error processing linux-image-3.2.0-38-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up grub-pc (1.99-21ubuntu3.9) ...
/var/lib/dpkg/info/grub-pc.config: 11: /etc/default/grub: splash: not found
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-3.2.0-34-generic-pae; however:
  Package linux-image-3.2.0-34-generic-pae is not configured yet.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.34.37); however:
  Package linux-image-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-3.2.0-34-generic-pae
 linux-image-3.2.0-35-generic-pae
 linux-image-3.2.0-37-generic-pae
 linux-image-3.2.0-38-generic-pae
 grub-pc
 linux-image-generic-pae
 linux-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by dpwilson on 2013-03-04
If I run sudo apt-get remove --purge linux-image-3.2.0-34-generic-pae , I get:
```
wilson@wilson-1204:~$ sudo apt-get remove --purge linux-image-3.2.0-34-generic-pae
[sudo] password for wilson: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-3.2.0-34-generic-pae
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 113 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 283847 files and directories currently installed.)
Removing linux-image-3.2.0-34-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-34-generic-pae /boot/vmlinuz-3.2.0-34-generic-pae
update-initramfs: Deleting /boot/initrd.img-3.2.0-34-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-34-generic-pae /boot/vmlinuz-3.2.0-34-generic-pae
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.2.0-34-generic-pae.postrm line 328.
dpkg: error processing linux-image-3.2.0-34-generic-pae (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-3.2.0-34-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by dino99 on 2013-03-04
run the usual cleaning commands first:

sudo apt-get clean
sudo apt-get autoclean
sudo apt-get autoremove

then purge & reinstall grub-pc
sudo apt-get purge grub-pc grub-common
sudo grub-install /dev/sda
sudo update-grub

sudo apt-get update
sudo apt-get install -f
sudo dpkg-reconfigure -phigh -a
(be patient as it can take a while to proceed, dont stop it yourself)

logout/in

then if it still fails, post the output of :
cat /etc/apt/sources.list

---

### Post by dpwilson on 2013-03-04
after the grub purge, when running sudo grub-install /dev/sda 

```
wilson@wilson-1204:~$ sudo grub-install /dev/sda
[sudo] password for wilson: 
sudo: grub-install: command not found
```

---

