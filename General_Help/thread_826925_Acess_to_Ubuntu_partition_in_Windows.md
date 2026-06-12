---
title: "Acess to Ubuntu partition in Windows"
date: 2008-06-12
forum: General Help
---

### Post by dropscience on 2008-06-12
Hello, i wonder if there is a way for me to access my Ubuntu files from Windows. I've heard of some kind of software that can make this happen.

---

### Post by ubersolid on 2008-06-12
There is, if you formatted your partitons as ext2 / ext3. Check out [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by dropscience on 2008-06-12
Ok, can i format my Ubuntu drive using this?

---

### Post by avtolle on 2008-06-12
> **dropscience said:**
> Ok, can i format my Ubuntu drive using this?
No, the link is to a Windows app that allows Windows to read files formatted in ext/2 or ext/3. If you have already installed Ubuntu, the installer, if you accepted the defaults, has already formatted the /partition as ext/3. The app will let you read the files thereon from Windows.

---

### Post by ubersolid on 2008-06-12
What do you want to achieve? 
If you simply want get rid of the ubuntu partition / format it as FAT or NTFS, ou can do this easily via Windows Disk Management:
Right click on "My Computer", Select "Manage", Double click on "Storage", Double click on "Disk Management". From there you are able to format your hardrives / partitions.Mind that if you delete the ubuntu partion, it might kill the bootloader too, making your system unbootable. How to fix that I do not know. Someone else probably does...

---

