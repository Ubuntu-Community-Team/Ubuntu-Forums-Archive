---
title: "NTFS what Do I do?"
date: 2008-02-09
forum: General Help
---

### Post by mrchaos101 on 2008-02-09
I got a box i use kind of like my file server.

Currently,  it is set up with with 3 HDD on windows XP.

C:  is NTFS and is my OS drive  it is an EIDE drive

E and F  are NTFS and are SATA drives.

I want to use Ubuntu on this box I also want to have SHARES on the E and F drive so that windows users on my network can access those drives  (one of thim holds all my mp3's)

I plan to DISCONNECT the SATA cable from the E and F drives and then install Ubuntu on the Eidie.

I then want to hook the cbls back up and mount those drives.

WILL this os be able to see my data on those drives if they are in NTFS?

---

### Post by Rocket2DMn on 2008-02-09
Yes, there is a driver called ntfs-3g which comes pre-installed on Gutsy that allows you to read/write NTFS partitions.  You will have to setup Samba to share with windows users - start here: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

---

### Post by mrchaos101 on 2008-02-09
> **Rocket2DMn said:**
> Yes, there is a driver called ntfs-3g which comes pre-installed on Gutsy that allows you to read/write NTFS partitions.  You will have to setup Samba to share with windows users - start here: [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

WOW! Thanks for the fast reply!

 Im gonna start on this project now.  Im still dependent on windows, so wish me luck.

---

### Post by Rocket2DMn on 2008-02-09
Good luck!  We're here to help if you have more problems.

---

