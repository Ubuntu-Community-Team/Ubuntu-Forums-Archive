---
title: "cannot boot"
date: 2014-07-07
forum: General Help
---

### Post by Alexandre_Crete on 2014-07-07
Hi,

Ive just installed for the very first time Ubuntu everthing went fine. But computer dosent want to boot I am receiving a booting error ´´Reboot and Select proper Boot device or Insert Media in selected Boot device_´´
I did make sure everything was well set in the bios after that I tried to do a Boot-repair with the live CD and it didnt work so here is the boot repair result: [http://paste.ubuntu.com/7761811/](http://paste.ubuntu.com/7761811/)

---

### Post by yancek on 2014-07-07
You have Grub in the master boot record pointing to the core.img file which is where it should be.  I don't see anything wrong with the menuentries for Ubuntu.  They are pointing to the correct partition and the UUIDs is correct.  The error message you posted commonly occurs when booting from a CD/DVD drive with no bootable medium in the drive.  Check the boot priority again, may be the change didn't save.  If you have a CD/DVD in the drive, take it out.  Don't know if this will help but I can't think of any other possibilities.

---

