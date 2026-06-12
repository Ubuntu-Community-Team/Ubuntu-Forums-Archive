---
title: "cannot copy files to windows partition"
date: 2007-09-29
forum: General Help
---

### Post by arveer on 2007-09-29
hello,

I am using ubuntu Dapper Drake 6.06 LTS. I have a windows partition along with linux. When I try to copy files to windows, it says permission denied. I can't do it even when i use sudo. It is a read-only file system and I am not able to change this. Any help will be appreciated. 

Thanks.

---

### Post by Lord Illidan on 2007-09-29
Ntfs support in Linux is readonly, as write support is experimental (it can wreck your ntfs harddisk), however there are ways and means to get around it.

---

### Post by jure1873 on 2007-09-29
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G")

---

### Post by andreeh on 2007-09-29
```
sudo apt-get install ntfs-3g ntfs-config
```
Then check Applications->System Tools->NTFS Configuration Tool

---

### Post by Peter Alien on 2007-09-29
i have a dual boot with WinXP Pro and Ubuntu 7.04, and i need to put files from one to another once in a while, winxp -> ubuntu i don't have problemas, but when i want to put some files from ubuntu to winXP it doesn't let me.

I heard that i can mess up it i try to write to a ntfs file system, so is it possible to put those files in a 3 1/2 disk and then i boot to windows and copy them to it?

How can i mount my 3 1/2 drive in ubuntu?

---

