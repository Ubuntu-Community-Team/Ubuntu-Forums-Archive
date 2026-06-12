---
title: "broken kernel upgrades in 16.04"
date: 2016-08-06
forum: General Help
---

### Post by Drone4four on 2016-08-06
Kernel updates for the past few months have been failing to install when I invoke sudo apt-get upgrade or even sudo aptitude upgrade. Here is the traceback:

```
19:29:46 $ sudo aptitude install calibre\* 
Couldn't find any package whose name or description matched "calibre*"
Couldn't find any package whose name or description matched "calibre*"
The following partially installed packages will be configured:
  grub-pc linux-generic linux-image-4.4.0-28-generic linux-image-4.4.0-31-generic linux-image-extra-4.4.0-28-generic linux-image-extra-4.4.0-31-generic linux-image-generic 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/57.6 MB of archives. After unpacking 0 B will be used.
Setting up grub-pc (2.02~beta2-36ubuntu3.2) ...
/var/lib/dpkg/info/grub-pc.config: 26: /etc/default/grub: Syntax error: newline unexpected
dpkg: error processing package grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-4.4.0-31-generic (4.4.0-31.50) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
/usr/sbin/grub-mkconfig: 26: /etc/default/grub: Syntax error: newline unexpected
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-31-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-31-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-31-generic:
 linux-image-extra-4.4.0-31-generic depends on linux-image-4.4.0-31-generic; however:
  Package linux-image-4.4.0-31-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.4.0-31-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-4.4.0-31-generic; however:
  Package linux-image-4.4.0-31-generic is not configured yet.
 linux-image-generic depends on linux-image-extra-4.4.0-31-generic; however:
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because MaxReports is reached already
                                                                                                                                                                          Package linux-image-extra-4.4.0-31-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 4.4.0.31.33); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: error processing package linux-image-4.4.0-22-generic (--configure):
 package linux-image-4.4.0-22-generic is not ready for configuration
 cannot configure (current status 'half-installed')
Setting up linux-image-4.4.0-28-generic (4.4.0-28.47) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-28-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
/usr/sbin/grub-mkconfig: 26: /etc/default/grub: Syntax error: newline unexpected
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-28-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-28-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: error processing package linux-image-extra-4.4.0-22-generic (--configure):
 package linux-image-extra-4.4.0-22-generic is not ready for configuration
 cannot configure (current status 'half-installed')
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-28-generic:
 linux-image-extra-4.4.0-28-generic depends on linux-image-4.4.0-28-generic; however:
  Package linux-image-4.4.0-28-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.4.0-28-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            Errors were encountered while processing:
 grub-pc
 linux-image-4.4.0-31-generic
 linux-image-extra-4.4.0-31-generic
 linux-image-generic
 linux-generic
 linux-image-4.4.0-22-generic
 linux-image-4.4.0-28-generic
 linux-image-extra-4.4.0-22-generic
 linux-image-extra-4.4.0-28-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
Failed to perform requested operation on package.  Trying to recover:
Setting up grub-pc (2.02~beta2-36ubuntu3.2) ...
/var/lib/dpkg/info/grub-pc.config: 26: /etc/default/grub: Syntax error: newline unexpected
dpkg: error processing package grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-4.4.0-31-generic (4.4.0-31.50) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
/usr/sbin/grub-mkconfig: 26: /etc/default/grub: Syntax error: newline unexpected
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-31-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-31-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-4.4.0-28-generic (4.4.0-28.47) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-28-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
/usr/sbin/grub-mkconfig: 26: /etc/default/grub: Syntax error: newline unexpected
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 2
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-28-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-28-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-4.4.0-31-generic; however:
  Package linux-image-4.4.0-31-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-28-generic:
 linux-image-extra-4.4.0-28-generic depends on linux-image-4.4.0-28-generic; however:
  Package linux-image-4.4.0-28-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.4.0-28-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-31-generic:
 linux-image-extra-4.4.0-31-generic depends on linux-image-4.4.0-31-generic; however:
  Package linux-image-4.4.0-31-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.4.0-31-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 4.4.0.31.33); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 grub-pc
 linux-image-4.4.0-31-generic
 linux-image-4.4.0-28-generic
 linux-image-generic
 linux-image-extra-4.4.0-28-generic
 linux-image-extra-4.4.0-31-generic
 linux-generic
                                         
19:31:12 $ 
```
I have been getting errors like this pretty much any time I attempt to install any application for that matter. This has been an issue for me for months.  Only today I am sitting down to resolve it.

[This guide]("http://ubuntuhandbook.org/index.php/2016/05/remove-old-kernels-ubuntu-16-04/") which I found through Google suggests purging my existing kernel, but I can't:
```
19:35:44 $ sudo dpkg --purge linux-image-4.4.0-24-generic  
dpkg: dependency problems prevent removal of linux-image-4.4.0-24-generic:
 linux-image-extra-4.4.0-24-generic depends on linux-image-4.4.0-24-generic.

dpkg: error processing package linux-image-4.4.0-24-generic (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-image-4.4.0-24-generic
19:39:18 $ 
```

```
$ uname -a
Linux gnosis 4.4.0-24-generic #43-Ubuntu SMP Wed Jun 8 19:27:37 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

```

What other information can I provide to help you help me trouble shoot this?

Thanks for your attention.

---

### Post by Impavidus on 2016-08-07
> **Drone4four said:**
> Kernel updates for the past few months have been failing to install when I invoke sudo apt-get upgrade or even sudo aptitude upgrade. Here is the traceback:

```

Setting up grub-pc (2.02~beta2-36ubuntu3.2) ...
/var/lib/dpkg/info/grub-pc.config: 26: **/etc/default/grub: Syntax error: newline unexpected**
dpkg: error processing package grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 2

```

What other information can I provide to help you help me trouble shoot this?

Thanks for your attention.
There seems to be a syntax error in your /etc/default/grub. Could you post the contents of that file?

---

### Post by Drone4four on 2016-08-07
Thank you, **AgoImpavidus**, for your reply.

Now that you mention grub, I recall make some changes a while ago to enable a graphical boot splash. Here it is: ```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset video=uvesafb:mode_option=>>1280x800-24<<,mtrr=3,scroll=ywrap"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=>>1280x800-24<<

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

Notice the line with, "GRUB_CMDLINE_LINUX_DEFAULT", should I just keep 'nomodeset' and remove the rest?

---

### Post by Drone4four on 2016-08-09
I invoked, sudo grub-mkconfig, rebooted, and the sudo apt-get update && sudo apt-get upgrade downloaded and installed the newer kernels no problem. Thank you **Impavidus** for directing my attention to the problem with grub in the traceback.

---

