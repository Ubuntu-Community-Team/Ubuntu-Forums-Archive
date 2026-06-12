---
title: "How To Delete Lunbuntu Completely?"
date: 2020-09-24
forum: General Help
---

### Post by tomsubt on 2020-09-24
Hello   How to UNINSTALL  Lubuntu on an old laptop and I may give it away, but i want to uninstall the OS Lubuntu first,  How do i go about it? Thanks
ps: there is No other OS on this lap top

---

### Post by TheFu on 2020-09-24
Boot from a flash storage device with a "Try Ubuntu" environment.  Then run
```
sudo dd if=/dev/urandom of=/dev/sda bs=4M 
```
overnight until it completes.  May need to change the /dev/sda to something different. It depends on your system.
If you are paranoid, run it twice.

If you get the of= wrong, it can be a very bad day for you. This **will** write random data to whatever storage device is named there. It will start from the beginning and go through to the end.  All data, all partitions, all partition tables will be overwritten with random data, so be 100% certain this is what you want. Get that device wrong and you'll overwrite the flash storage device you booted from.

If you want more handholding, use **dban**.

In the future, the easy answer is to use whole disk encryption for your OS installation on all laptops.  Then you can just give the laptop to anyone without the decryption passphrase and they can wipe it themselves. The math for LUKS and dmcrypt is solid, assuming the passphrase is unguessable.

---

### Post by tomsubt on 2020-09-24
quote>>If you want more handholding, use dban. What kind of TALK is that?

I cannot use the dban disk the laptop does not have a working dvd., i suppose i could try a flash drive with the deban on it.
and see if will take it. will let you know and Thanks

---

### Post by tomsubt on 2020-09-25
Solved:   I used a large electric magnet on both sides of the harddrive and it erased the whole drive in 10seconds. it is now ready for the installation of a new OS. Hope this helps some one else too!!!

---

