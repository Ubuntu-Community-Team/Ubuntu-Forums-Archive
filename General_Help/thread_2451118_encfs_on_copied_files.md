---
title: "encfs on copied files"
date: 2020-09-27
forum: General Help
---

### Post by asb3 on 2020-09-27
I copied all the files from one hard drive to another using rsync.
rsync -avxHAX /mnt/HD1/data /mnt/HD2/data/

The file /mnt/HD1/data/.enctest is a file encrypted with encfs.
If I type
>encfs /mnt/HD1/.enctest   /mnt/HD1/enctest
I get a prompt to enter a password, and when I enter the correct password, the unencrypted file appears in /mnt/HD1/enctest

If I type
>encfs /mnt/HD2/.enctest  /mnt/HD2/enctest
nothing happens.

How can I get encfs to decrypt the files on HD2?

---

### Post by asb3 on 2020-09-27
Problem had nothing to do with encfs.  The files were copied to a USB raid1 device comprising two hard drives, and one of the was unplugged.  Oops!

---

