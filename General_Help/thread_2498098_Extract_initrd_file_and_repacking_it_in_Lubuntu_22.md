---
title: "Extract initrd file and repacking it in Lubuntu 22.04 (Jammy)"
date: 2024-05-30
forum: General Help
---

### Post by scmarko on 2024-05-30
What is the correct way to extract initrd file in Ubuntu/Lubuntu 22.04 Jammy? 

It seems to be hard to find information related to this. 

I have found out that unmkinitramfs seems to be able to extract the initrd file, but is it the correct way? After extraction, the following directories appear:

```
early
early2
main
```

I need to modify a script in the initrd file and repack it.

What is the correct way to recreate the initrd file? There seems not to be any official information related to this. I found some examples elsewhere which worked, but after recreation of the initrd file use those commands, it wasn't the same size anymore, size difference were several megabytes if I recall and command "binwalk initrd" also gives completely different output.

---

### Post by currentshaft on 2024-05-30
The sizes could be due to different compression algorithms being used. Check /etc/initramfs-tools/initramfs.conf then:

mkinitramfs -o /boot/initrd.img-<kernel-version> <kernel-version>

---

### Post by karthikkp on 2024-10-15
Did you manage to extract, modify, and repack the `initrd` successfully? I attempted to use `unmkinitramfs`, but I didn’t make any changes to the `initrd` contents. When I repacked it using the command `find . | cpio -o -H newc | gzip -9 > ../initrd-net-24`, I encountered an error: "vfs: cannot open root device '/dev/ram0' or unknown-block(0,0): error -6."

---

