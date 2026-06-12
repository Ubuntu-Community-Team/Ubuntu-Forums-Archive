---
title: "How do I mount the ubuntu initrd?"
date: 2006-08-25
forum: General Help
---

### Post by nadavvin on 2006-08-25
How do I mount the ubuntu initrd?

I try:
sudo mount -o loop -t ext2 initrd.img-2.6.15-23-386 a
sudo mount -o loop -t cramfs initrd.img-2.6.15-23-386 a

and I get:
```

mount: wrong fs type, bad option, bad superblock on /dev/loop2,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


```

Which filesystem the initrd is?

---

### Post by tormod on 2006-08-25
They are gzip'ed cpio archives:

```
mkdir tmp
cd tmp
gzip -dc /somepath/initrd.gz | cpio -id

# do the edits on the files

find . | cpio --quiet --dereference -o -H newc | gzip -9 > /somepath/new-initrd.gz

```

---

### Post by mvdberg112 on 2008-01-14
Thanks. The last reply from tormod has been tremendously helpful to me, althought the tread is already 16 months old. It worked right off the bet.
After doing this:
   gzip -dc /somepath/initrd.gz | cpio -id
the package will be unpacked in the current directory.
In that directory there will be a file (actually a symbolic link, which refers to another file) with the name init. That is the file that is run by the kernel just after the 'grub' (or whatever bootloader you might be using)  loaded the kernel. From there the total system will be started. To change the boot process, one need to edit this /init file, with for example:
  vi init

Thanks again.
Michael

---

### Post by tormod on 2008-01-15
Glad to hear that. For reference, I wrote it up on the wiki: [https://wiki.ubuntu.com/CustomizeLiveInitrd](https://wiki.ubuntu.com/CustomizeLiveInitrd)
(or just search for "initrd" in the wiki)

---

