---
title: "Persistent USB"
date: 2013-01-14
forum: General Help
---

### Post by anon_private on 2013-01-14
I have been told that all I need to do to make my Lubuntu Live USB persistent is to make a folder in root called casper-rw and when booting use persistent before --

I have some difficulty booting and it does not seem to work.

Can anyone advise?

Thanks

---

### Post by oldfred on 2013-01-14
[https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)


Is persistence the issue or something else?

---

### Post by C.S.Cameron on 2013-01-14
I've never heard about just making a folder named casper-rw.
I know making an ext(2,3 or 4) partition named casper-rw works.

If you overwrite syslinux.cfg with the following:

```
    default live
    label live
      say Booting an Ubuntu Live session...
      kernel /casper/vmlinuz
      append  file=/cdrom/preseed/ubuntu.seed boot=casper persistent initrd=/casper/initrd.lz quiet splash noprompt --
```

It will remove the try/install and language screens and use the persistent partition.

---

