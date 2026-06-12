---
title: "/dev/sda1 file system unknown in gparted"
date: 2017-03-17
forum: General Help
---

### Post by ronlewis7 on 2017-03-17
My laptop is a system 76 Kudo Pro running Ubuntu 16.04LTS
The system is running great and it boots ok. I had a general question as to why the /dev/sda1 partition is listed as unknown in gparted.
Here is the information listed in gparted:
```

Partition      Name          file system         mount point          size            used           unused           flags

/dev/sda1    primary        unknown           (blank)                  1.00MB      -----             ------               bios_grub

/dev/sda2    (blank)         ext4                    /                        927.51GIB    31.62GIB     896.89GIB    (blank)

/dev/sda3    primary       linux-swap          (blank)                4.00GIB        0.00GIB       4.00GIB       (blank)

```
Again, the system has no performance problems and does boot ok, just wondering why the sda1 is not mounted and does need to be mounted for the system to run properly.

Thanks in advance for any info on this. I am new to Linux Ubuntu and trying to understand the system better. Thanks again.

Ron

---

### Post by sudodus on 2017-03-17
In a GUID partition table, GPT, Ubuntu uses a small 'bios_grub' partition intended for code, that belongs to the bootloader grub, and that partition should *not* contain a file system or any other 'structure'. I think gparted should 'know' about that, and not print a confusing message.

---

### Post by Bashing-om on 2017-03-17
ronlewis7; Hello;

In addition you might get a better idea of the file system from the terminal command:
```

sudo parted -l

```

Keep in mind in your adventures in learning:
[INDENT][INDENT]the right tool for the right job[/INDENT][/INDENT]

---

### Post by ronlewis7 on 2017-03-17
Thanks for the quick reply sudodus and bashing-om

This explains the unknown file system message. With the information you gave me i searched the Ubuntu man pages for the GUID GPT info
Very interesting reading.
The link is:
[http://manpages.ubuntu.com/manpages/xenial/man8/gdisk.8.html](http://manpages.ubuntu.com/manpages/xenial/man8/gdisk.8.html)

The part that pertains to my question  (i think), is as follows:

    *****      Some boot loaders for BIOS-based systems make use of a _BIOS_ _Boot_
              _Partition_  (**gdisk**  internal code 0xEF02), in which the secondary
              boot loader  is  stored,  possibly  without  the  benefit  of  a
              filesystem.  (GRUB2  may  optionally use such a partition.) This
              partition can typically be quite small (roughly 32 to 200  KiB),
              but  you  should  consult  your  boot  loader  documentation for
              details.

Thanks again for the info. Currently i am working my way through the book "Linux Command Line and Shell Scripting Bible" 3rd edition. Very good book.
Ron

---

