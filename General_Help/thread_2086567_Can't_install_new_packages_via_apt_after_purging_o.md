---
title: "Can't install new packages via apt after purging old kernel files"
date: 2012-11-21
forum: General Help
---

### Post by juliushibert63 on 2012-11-21
I recently purged all the unused kernel files off my Ubuntu box to try and clear some space off my disk drive. I used the following command I'd found online to do this.

```
dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge
```

However now when I try and install a new package via apt-get install I get a whole load of errors saysing that apt can't clear out the kernel files. Here's a snapshopt of the errors.


```
                                                                    Removing linux-image-3.2.0-30-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-30-generic /boot/vmlinuz-3.2.0-30-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-30-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-30-generic /boot/vmlinuz-3.2.0-30-generic
/usr/sbin/grub-mkconfig: 37: /etc/default/grub: usbcore.autosuspend=-1: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.2.0-30-generic.postrm line 328.
dpkg: error processing linux-image-3.2.0-30-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Removing linux-image-3.2.0-31-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.2.0-31-generic /boot/vmlinuz-3.2.0-31-generic
update-initramfs: Deleting /boot/initrd.img-3.2.0-31-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.2.0-31-generic /boot/vmlinuz-3.2.0-31-generic
/usr/sbin/grub-mkconfig: 37: /etc/default/grub: usbcore.autosuspend=-1: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.2.0-31-generic.postrm line 328.
dpkg: error processing linux-image-3.2.0-31-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 linux-image-2.6.38-12-generic
 linux-image-3.0.0-12-generic
 linux-image-3.0.0-13-generic
 linux-image-3.0.0-14-generic
 linux-image-3.0.0-15-generic
 linux-image-3.0.0-16-generic
 linux-image-3.0.0-17-generic
 linux-image-3.0.0-19-generic
 linux-image-3.0.0-20-generic
 linux-image-3.2.0-24-generic
 linux-image-3.2.0-25-generic
 linux-image-3.2.0-26-generic
 linux-image-3.2.0-27-generic
 linux-image-3.2.0-29-generic
 linux-image-3.2.0-30-generic
 linux-image-3.2.0-31-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I've tried using apt-get clean, apt-get autoclean. apt-get remove and apt-get autoremove without any luck as to clearing this issue.

---

### Post by juliushibert63 on 2012-12-01
Bump

I'm still encountering this problem. If anyone's got any ideas it'd be really helpful!

---

