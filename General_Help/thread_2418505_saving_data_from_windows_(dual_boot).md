---
title: "saving data from windows (dual boot)"
date: 2019-05-07
forum: General Help
---

### Post by acefromspace on 2019-05-07
My mother has a computer with dual boot (windows 7 and ubuntu 16.04) She forgot her password for windows, but doesn't use it anyway. Is there a way to use ubuntu to access her data on windows?

---

### Post by oldfred on 2019-05-07
Unless encrypted, you do not need password to get data from Windows NTFS.
And if Windows 7, it normally would not be hibernated, nor have the Windows 10 fast start up which sets hibernation flag and prevents the Linux NTFS driver from auto mounting read/write. Even if hibernated you can manually mount read only.

So from Ubuntu just click on NTFS partition and it should mount and let you browse it and then copy data.

---

### Post by acefromspace on 2019-05-08
It worked fine. Thank you. it seems that a recovery was done and windows has not been used anyway. There was no data to save. It was all backed up before. Good news is my mom finally (after years) tried ubuntu and doesn't need windows anymore. She just still wanted it on there "just in case".

---

