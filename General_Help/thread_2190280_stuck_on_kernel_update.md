---
title: "stuck on kernel update"
date: 2013-11-26
forum: General Help
---

### Post by sdowney717 on 2013-11-26
just hanging. I thought to update version by following here
[http://ubuntuhandbook.org/index.php/2013/11/install-upgrade-kernel-3-11-ubuntu-mint/](http://ubuntuhandbook.org/index.php/2013/11/install-upgrade-kernel-3-11-ubuntu-mint/)

It hung so closed terminal tried again with 3.12, it hung up in terminal.

```
scott@scott-P5QC:~$ sudo apt-get purge linux-headers-3.11.7-* linux-image-3.11.7-*
[sudo] password for scott: 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 


scott@scott-P5QC:~$ sudo dpkg --configure -a
Setting up linux-image-3.11.7-031107-generic (3.11.7-031107.201311040853) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.11.7-031107-generic /boot/vmlinuz-3.11.7-031107-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.11.7-031107-generic /boot/vmlinuz-3.11.7-031107-generic
Error! Could not locate dkms.conf file.
File:  does not exist.
ERROR (dkms apport): kernel package linux-headers-3.11.7-031107-generic is not supported
Error! Bad return status for module build on kernel: 3.11.7-031107-generic (x86_64)
Consult /var/lib/dkms/nvidia-current/313.09/build/make.log for more information.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.11.7-031107-generic /boot/vmlinuz-3.11.7-031107-generic
update-initramfs: Generating /boot/initrd.img-3.11.7-031107-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.11.7-031107-generic /boot/vmlinuz-3.11.7-031107-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.11.7-031107-generic /boot/vmlinuz-3.11.7-031107-generic
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.11.7-031107-generic /boot/vmlinuz-3.11.7-031107-generic
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.7.0-030700-generic...
P: Writing config for /boot/vmlinuz-3.6.9-030609-generic...
P: Writing config for /boot/vmlinuz-3.5.0-18-generic...
P: Writing config for /boot/vmlinuz-3.2.0-35-generic...
P: Writing config for /boot/vmlinuz-3.2.0-34-generic...
P: Writing config for /boot/vmlinuz-3.2.0-29-generic...
P: Writing config for /boot/vmlinuz-3.12.0-031200-generic...
P: Writing config for /boot/vmlinuz-3.11.7-031107-generic...


```

Anyway I was getting dkms file errors.
So I know if it reboot it wont boot those kernels. 
I tried doing the remove, but it wont because the process was interrupted.

Running 
manually run 'sudo dpkg --configure -a' 
to correct the problem is not working.

---

### Post by sdowney717 on 2013-11-26
I removed the lock
then ran synaptic to purge 3.11 and 3.12 kernels

what else should I do?
So I can not upgrade kernels?
scott@scott-P5QC:~$ sudo rm /var/lib/apt/lists/lock
[sudo] password for scott: 
scott@scott-P5QC:~$ gksu synaptic

---

### Post by sdowney717 on 2013-11-26
synaptic is stuck

So what to do?

---

### Post by sdowney717 on 2013-11-26
I rebooted and then was able to fix by running that command.

---

### Post by sdowney717 on 2013-11-26
bummer that it can run 3.12 kernel, but my 8400 gs nvidia card is not supported in the driver.
I am having to stick with kernel 3.7 to have nvidia driver loaded.

Is that something Nvidia will fix or have they dropped all support now? fly by night the card has always worked fine.

---

