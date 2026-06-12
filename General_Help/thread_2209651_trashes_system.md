---
title: "trashes system"
date: 2014-03-06
forum: General Help
---

### Post by ericaslakson on 2014-03-06
Hi,

After a message that a package wasn't being use, and the fact that my server running 12.04 has no wireless interface, I did a 'sudo apt-get remove wireless-regdb'.  The command and it's effect follows:

```
era@poemdb41:~$ sudo apt-get remove wireless-regdb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  crda linux-generic linux-image-3.2.0-60-generic linux-image-generic
  wireless-regdb
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
After this operation, 150 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 51853 files and directories currently installed.)
Removing linux-generic ...
Removing linux-image-generic ...
Removing linux-image-3.2.0-60-generic ...
WARN: Proceeding with removing running kernel image.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-60-generic /boot/vmlinuz-3.2.0-60-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-60-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-60-generic /boot/vmlinuz-3.2.0-60-generic
Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found memtest86+ image: /boot/memtest86+.bin
done
The link /vmlinuz is a damaged link
Removing symbolic link vmlinuz 
 you may need to re-run your boot loader[grub]
The link /initrd.img is a damaged link
Removing symbolic link initrd.img 
 you may need to re-run your boot loader[grub]
Removing crda ...
Removing wireless-regdb ...
Processing triggers for man-db ...
era@poemdb41:~$ sudo update-grub
Generating grub.cfg ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found memtest86+ image: /boot/memtest86+.bin
done
```

Rendering my system unbeatable.  I missed the pending removal of **linux-generic linux-image-3.2.0-60-generic linux-image-generic** , [SIZE=2]but s[/SIZE]urely this is an error?  How to recover?  And how can I remove wireless-regdb without trashing my boot files?

Thanks in advance

---

### Post by howefield on 2014-03-06
Thread closed, duplicate here : [http://ubuntuforums.org/showthread.php?t=2209644](http://ubuntuforums.org/showthread.php?t=2209644)

---

