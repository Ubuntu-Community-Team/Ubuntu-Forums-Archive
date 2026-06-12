---
title: "Search NTFS Drive from Ubuntu"
date: 2008-03-05
forum: General Help
---

### Post by Officer Dibble on 2008-03-05
How do I search for a specific file on an NTFS mounted drive, please?

I'm trying to search through an XP Partition for a file called TCPIP.SYS. I open Nauti, click on the drive, (entering password) click on the search button, I enter the file name and Nauti doesn't do anything... doesn't even try to look... :confused:

---

### Post by kpkeerthi on 2008-03-05
Assuming the NTFS drive is mounted on /media/windows ...
```
find /media/windows -iname 'TCPIP.SYS'
```

---

