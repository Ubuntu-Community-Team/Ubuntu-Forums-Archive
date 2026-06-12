---
title: "Out of space /boot"
date: 2013-01-31
forum: General Help
---

### Post by kr651129 on 2013-01-31
I compiled a new kernel last night but when I tried to install it I'm being told /boot is out of space.  I've never run into this problem in the past with Ubuntu.

A quick df -h tells me /boot has a total 228MB of space, 181 MB free.  My disk is encrypted so I really don't want to have to boot from a live disk to resize the parition.  Is there an easy solution for this?

---

### Post by ibjsb4 on 2013-01-31
Remove some old kernels.  Synaptic PM works good for this.

---

### Post by kr651129 on 2013-01-31
Thanks for the reply, the problem is I only have one kernel on my machine.  So I can't remove any old kernels.

---

### Post by ibjsb4 on 2013-01-31
> **kr651129 said:**
> Thanks for the reply, the problem is I only have one kernel on my machine.  So I can't remove any old kernels.

Really ?!?

Whats in your boot?

```
l /boot
```

---

### Post by kr651129 on 2013-01-31
Weird right?!  I'm not sure off hand because I'm at work, I'll post the contents of /boot later tonight.

---

### Post by oldos2er on 2013-01-31
> **kr651129 said:**
> A quick df -h tells me /boot has a total 228MB of space, 181 MB free. 

Why so small? I don't see how you can get around this problem other than to enlarge that partition.

---

### Post by kr651129 on 2013-01-31
Not sure, I went with the default options on the install for an encryped lvm volume.  How hard will it be to resize this from a live usb image with it being encrypted?

---

### Post by kr651129 on 2013-01-31
Contents of /boot:

```

-rw-r--r--  1 root root   844882 Oct  9 14:54 abi-3.5.0-17-generic
-rw-r--r--  1 root root   147884 Oct  9 14:54 config-3.5.0-17-generic
drwxr-xr-x  5 root root     1024 Jan 31 07:53 grub
-rw-r--r--  1 root root 23059435 Jan 31 07:46 initrd.img-3.5.0-17-generic
drwxr-xr-x  2 root root    12288 Jan 30 21:57 lost+found
-rw-r--r--  1 root root   176764 Jan  3 16:48 memtest86+.bin
-rw-r--r--  1 root root   178944 Jan  3 16:48 memtest86+_multiboot.bin
-rw-------  1 root root  2901710 Oct  9 14:54 System.map-3.5.0-17-generic
-rw-r--r--  1 root root  5129040 Oct 17 04:04 vmlinuz-3.5.0-17-generic

```

---

### Post by SeijiSensei on 2013-02-01
That shows you have plenty of space and is consistent with 181/223 MB free.

How big is the kernel that you compiled?  Did you strip all the debugging information from it?  Is is compressed?  Your vmlinuz should be about the same size as the one above, 5 MB.

---

