---
title: "Update Grub Segmentation Fault"
date: 2015-01-16
forum: General Help
---

### Post by Abhisek Maiti on 2015-01-16
When I try to run
```
# update-grub
```

It gives thefollowing output. Please Help to resolve this.

```

Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-44-generic
Found initrd image: /boot/initrd.img-3.13.0-44-generic
Found linux image: /boot/vmlinuz-3.13.0-24-generic
Found initrd image: /boot/initrd.img-3.13.0-24-generic
[B]Segmentation fault
Segmentation fault[/B]
Adding boot menu entry for EFI firmware configuration
done

```

I attached my **grub file below.**

:confused::confused::confused:

---

### Post by oldfred on 2015-01-16
The os-prober is searching for boot files and other partitions. So either a file is corrupted or a partition.
Or did you leave Windows with fast boot or always on hibernation set. Then os-prober cannot open those NTFS partitions to look for files, even though with UEFI it really only needs to look at efi partition.

Just to see a lot more details of configuration.
       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Abhisek Maiti on 2015-01-16
Thanks for the suggestions ):P. Boot Repair really helped to fix the problem. :guitar:

---

