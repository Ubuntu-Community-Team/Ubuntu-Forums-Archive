---
title: "trashes system"
date: 2014-03-06
forum: General Help
---

### Post by ericaslakson on 2014-03-06
Hi,

After a message that a package wasn't being use, and the fact that my server running 12.04 has no wireless interface, I did a 'sudo apt-get remove wireless-regdb'.  The command and it's effect follows:

[SIZE=2]```
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

Rendering my system unbeatable.  I missed the pending removal of **linux-generic linux-image-3.2.0-60-generic linux-image-generic** , but surely this is an error?  How to recover?  And how can I remove wireless-regdb without trashing my boot files?

Thanks in advance[/SIZE]

---

### Post by Impavidus on 2014-03-06
Interesting that it gives a warning about uninstalling the running kernel only *after* giving you the only chance to abort. That's a design fault.

Try booting from a live disk, mount your install, chroot into it and reinstall those packages. I've never done it, but there are some tutorials around telling how to use chroot to fix an install.

---

### Post by cariboo on 2014-03-06
> **Impavidus said:**
> Interesting that it gives a warning about uninstalling the running kernel only *after* giving you the only chance to abort. That's a design fault.

Try booting from a live disk, mount your install, chroot into it and reinstall those packages. I've never done it, but there are some tutorials around telling how to use chroot to fix an install.

Actually if you read the output again, you'll see that it does say that the kernel will be removed, and it does give you the chance to abort the operation before doing anything.

> The following packages will be REMOVED:
  crda linux-generic linux-image-3.2.0-60-generic linux-image-generic
  wireless-regdb
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
After this operation, 150 MB disk space will be freed.
Do you want to continue [Y/n]? y

I've done the same thing on my testing install a couple of times. To re-install the kernel, you need to boot from your installation media, and select repair an installation from the menu, then once at the prompt run the following commands:

sudo mount /dev/sda1 /mnt
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /sys /mnt/sys
sudo mount -o bind /proc /mnt/proc
sudo chroot /mnt

then

sudo apt-get install linux-generic

---

### Post by Impavidus on 2014-03-06
If you read carefully, you see it first says 'This will remove linux-image-blabla', just a package name, no warning that it's the running kernel &#8211; although anyone with enough Linux experience can see it's uninstalling a kernel, which should trigger some alarm bells. Then it asks whether you want to continue, and after that is the first time it actually says 'WARNING, removing the running kernel'. A bit late, better to move the *explicit* warning a few lines up. It's rather useless down there.

Anyway, good that you have the exact commands to fix it.

---

