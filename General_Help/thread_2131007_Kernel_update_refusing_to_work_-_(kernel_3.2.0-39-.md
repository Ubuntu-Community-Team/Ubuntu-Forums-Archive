---
title: "Kernel update refusing to work - (kernel 3.2.0-39-generic)"
date: 2013-03-31
forum: General Help
---

### Post by blackbird34 on 2013-03-31
Hi again

I have been unable to update my ubuntu kernel for a few weeks now, and at a loss what to do. i also had a separate issue with updates [here]("http://ubuntuforums.org/showthread.php?t=2130885&p=12581510#post12581510"), but I could tell it was separate because after I cleared that up my failing kernel update gave the same errors as before.

```
nad@Macondo:~$ sudo apt-get install -f
[sudo] password for nad: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  linux-generic linux-image-generic
The following packages will be upgraded:
  linux-generic linux-image-generic
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0 B/4,300 B of archives.
After this operation, 2,048 B of additional disk space will be used.
Do you want to continue [Y/n]? 
Setting up linux-image-3.2.0-39-generic (3.2.0-39.62) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.2.0-39-generic /boot/vmlinuz-3.2.0-39-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-39-generic /boot/vmlinuz-3.2.0-39-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-39-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-39-generic /boot/vmlinuz-3.2.0-39-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-39-generic /boot/vmlinuz-3.2.0-39-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-39-generic /boot/vmlinuz-3.2.0-39-generic
/usr/sbin/grub-mkconfig: 37: /etc/default/grub: tmpfs: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-39-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-39-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.2.0-40-generic (3.2.0-40.64) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.2.0-40-generic /boot/vmlinuz-3.2.0-40-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-40-generic /boot/vmlinuz-3.2.0-40-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-40-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-40-generic /boot/vmlinuz-3.2.0-40-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-40-generic /boot/vmlinuz-3.2.0-40-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-40-generic /boot/vmlinuz-3.2.0-40-generic
/usr/sbin/grub-mkconfig: 37: /etc/default/grub: tmpfs: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-40-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-40-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
E: Sub-process /usr/bin/dpkg returned an error code (1)
nad@Macondo:~$ 


```
I'd never heard of depmod before. Is there something I should do with one of the files in /var/lib/dpkg ? like delete it so it re-generates?

In other threads OPs were told to use df -i or df -h to see if their /boot directories were full, but my hard drive is huge and almost empty, and I didn't do any fancy partitioning, everything is under / on the same partition.

Part of the error messages mentioned GRUB, so I also did
```
nad@Macondo:~$ sudo update-grub
[sudo] password for nad: 
/usr/sbin/grub-mkconfig: 37: /etc/default/grub: tmpfs: not found

```

Synaptic gave me this error too:
> 
E: linux-image-3.2.0-39-generic: subprocess installed post-installation script returned error exit status 2
E: linux-image-3.2.0-40-generic: subprocess installed post-installation script returned error exit status 2
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured



My computer boots and works normally for the moment apart from this. Can anyone help?

---

### Post by r.stiltskin on 2013-03-31
The file /etc/default/grub is used by update-grub to generate a grub.cfg file.  Maybe yours somehow got corrupted.  You can rename it
```
sudo mv /etc/default/grub /etc/default/grub.bak
```
to save it under another name so it won't interfere with update-grub, then replace it with a clean unaltered version:
```

sudo cp /usr/share/grub/default/grub /etc/default/
```
That will lose any modifications/customizations that you may have made to your grub configuration post-installation, but it should also eliminate whatever is preventing update-grub from completing.

Then run
```
update grub
```
If that solves the problem, you can delete the grub.bak file you created.  If it doesn't, you can delete the new /etc/default/grub and rename the backup to its original name.

---

### Post by blackbird34 on 2013-04-01
Thanks for the tip, but it didn't change anything.

Can anyone tell me what's wrong with "tmpfs"?

And if I reboot with an older kernel, can I purge the newer ones and try everything over again?

EDIT: I did reboot with an old kernel, and removed the offending one, it worked fine. Problem Solved.

---

