---
title: "Upgrading Pendrive"
date: 2018-04-07
forum: General Help
---

### Post by anon_private on 2018-04-07
Hello,

I have ubuntu ver 12. on a pendrive.

Can it be upgraded?

If so, can you tell me the procedure?

Thanks

---

### Post by sudodus on 2018-04-07
Do you want the upgrade the hardware or software?

- move the Ubuntu system to a new (and better) USB pendrive, or

- install a new Ubuntu system into the same USB pendrive

The version 12.04 LTS (as well as the version 12.10) is very old, and it is easier, faster and generally better to make a fresh installation of a current version of Ubuntu.

Upgrading will be complicated and likely to fail, because it must be done via several steps to 16.04.1 LTS, 16.04.4 LTS, 17.10.1 or Bionic Beaver (to be released as 18.04 LTS soon).

---

### Post by anon_private on 2018-04-07
Upgrade the software

How is this a solution: 'move the Ubuntu system to a new (and better) USB pendrive'. It would upgrade the pendrive, but it is only a storage medium.

Thanks

---

### Post by sudodus on 2018-04-07
OK.

Is it an installed system (installed like into an internal drive), or is it a persistent live system?

In both cases I suggest that you copy all files, that you want to keep to another drive (backup), and after that install a new version of Ubuntu. 

- Ubuntu 16.04.1 LTS, 16.04.4 LTS are supported until April 2021 (5 years LTS).
- Ubuntu 17.10.1 is supported until July 2018 (a very short time)
- Ubuntu Bionic, 18.04 LTS will be supported until April 2023 (5 years).

The LTS support for the Ubuntu community flavours (Kubuntu, Lubuntu, ... Xubuntu) is 'only' 3 years.

---

### Post by C.S.Cameron on 2018-04-07
If it is a persistent system, only the casper-rw file has changed since new.
Unfortunately a casper-rw file does not work from one version of Ubuntu to the next.
If your persistent system uses casper-rw and home-rw files or partitions, the home-rw one can be copied from one version of Ubuntu to the next.
You should be able to do a fresh Persistent install and rsync the old home folder data to the new install. Consider using a home-rw file or folder next time.

If it is a Full install, just do a version upgrade 12.04 to 14.04 to 16.04, or a fresh install with a /home copy.

---

