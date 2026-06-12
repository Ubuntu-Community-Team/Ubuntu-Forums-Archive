---
title: "Help please"
date: 2007-05-16
forum: General Help
---

### Post by jmemm37 on 2007-05-16
Yes, I am looking for some help. I tried to install clamav from automatix and it failed. I now get the following error message quite a bit like when I try to install updates and package software:

E:clamav-base: subprocess post-installation script returned error exit status 1

Is there anyway for me to get rid of whatever is causing this error or do I need to reinstall ubuntu from scratch? I am running ubuntu 6.06 dapper drake. Any help and suggestioins would be greatly appreciated.

Thank you.

---

### Post by zvacet on 2007-05-16
```
sudo apt-get --purge remove file_name
```

In you case file_name is exact name of clamav 

[https://help.ubuntu.com/community/ClamAV]("https://help.ubuntu.com/community/ClamAV")

---

### Post by michaeljking on 2007-05-16
thanks

---

### Post by jmemm37 on 2007-05-16
Thakn you for that suggestion. I did what you suggested and while in the terminal, it said stuff like removing file, and resolving, unpacking, etc. I didn't understand any of that but I am sure that what I needed to be done was accomplished. Only time will tell if it has been. I will let you know if I have anymore problems. Again, thanks.

---

