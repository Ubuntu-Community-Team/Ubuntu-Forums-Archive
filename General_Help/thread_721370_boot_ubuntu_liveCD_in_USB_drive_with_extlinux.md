---
title: "boot ubuntu liveCD in USB drive with extlinux"
date: 2008-03-11
forum: General Help
---

### Post by jamesjames on 2008-03-11
I am trying to copy the contents of ubuntu livecd into a USB drive and install a bootloader to make a 'liveUSB'. 
Since I want to use ext3 file system, I choose extlinux as the bootloader. What I have done is as followed.

1. copy all the content of livecd iso to the usb drive (say sdb1)
2. install extlinux to root of sdb1
3. cat mbr.bin into sdb1
4.copy the isolinux.cfg to root and rename to extlinux.conf

After that, I assumed the liveUSB should boot. But unforturnately, it stuck in initramfs. 

I tried syslinux as the bootloader in the similiar way, and it is ok. But I still need to use ext3 filesystem.

Anyone tried extlinux to boot liveUSB?? 

Thanks a lot.

---

### Post by justleen on 2008-03-11
the only bootable USB disk i was able to make was using grub.. there are several guides on how to install the Livecd on a USB stick though.. (but i think they all use grub..)

any general how to on creating boot disks with extlnux should work though

---

