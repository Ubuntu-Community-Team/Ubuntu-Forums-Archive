---
title: "Need help with a RAID question"
date: 2007-12-06
forum: General Help
---

### Post by hawk1278 on 2007-12-06
I have done some searches and did not come across any answers so I thought I would throw this question out.


I currently have a PC with Windows XP and a hardware based RAID 5. XP is loaded on it's own drive.  I want to get rid of XP and install Ubuntu.  I don't want is to lose any of the data on the RAID,  and I want to load SAMBA so that I can share the RAID out to users. 

Sorry if this is a trivial task but I wanted to ask before I proceded.

Thanks!




:guitar:

---

### Post by HermanAB on 2007-12-07
Coming from Windows, i would assume that it is a hardware based RAID and NTFS.  You need to investigate whether Linux has a device driver for the hardware RAID adaptor.

NTFS is OK, since you can handle that with the ntfs-3g driver, but the RAID driver would be the killer.

Cheers,

Herman

---

