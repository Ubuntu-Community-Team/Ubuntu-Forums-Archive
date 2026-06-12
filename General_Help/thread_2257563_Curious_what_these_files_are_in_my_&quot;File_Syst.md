---
title: "Curious what these files are in my &quot;File System&quot;"
date: 2014-12-20
forum: General Help
---

### Post by michael-piziak on 2014-12-20
When clicking my Home Folder, then clicking "File System," I'm curious what these last four files are that aren't in folders.

See image.

---

### Post by oldfred on 2014-12-20
Those are just links to the most current kernel and second most current one.

That way you can manually boot without knowing specific kernel, and can create boot stanzas in grub to boot most current kernel in another install without having to update settings with every kernel update.

This type of manual boot uses those links.
 set prefix=(hd0,5)/boot/grub
set root=(hd0,5)
linux (hd0,5)/vmlinuz root=/dev/sda5 ro
initrd (hd0,5)/initrd.img
boot

More details on using links to create boot stanza

 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

---

### Post by michael-piziak on 2014-12-20
Thanks!

Marking this thread as solved.

---

### Post by bapoumba on 2014-12-20
Please do not delete them !
vmlinuz is the kernel executable.
initrd is used to temp mount a root file system on boot.
[http://www.linfo.org/vmlinuz.html](http://www.linfo.org/vmlinuz.html)
[https://kernel-handbook.alioth.debian.org/ch-initramfs.html](https://kernel-handbook.alioth.debian.org/ch-initramfs.html)

Edit: that is not even being ninja'd, that is next time I have a reply open for some time doing some other things, I'll just close it without submitting :)

---

### Post by michael-piziak on 2014-12-20
Thanks, I sure won't delete them !

---

