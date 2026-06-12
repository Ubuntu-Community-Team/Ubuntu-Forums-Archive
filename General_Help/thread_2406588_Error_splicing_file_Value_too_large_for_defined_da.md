---
title: "Error splicing file: Value too large for defined data type"
date: 2018-11-22
forum: General Help
---

### Post by confused322 on 2018-11-22
Hello,

I get an "Error while copying" with information "Error splicing file: Value too large for defined data type" when I try to copy a file of 1.6gb from one NTFS formatted external drive to any other. I even get this error when I attempt to copy (duplicate) the file on the same HD.

I looked and found this: [https://askubuntu.com/questions/112309/error-splicing-file-value-too-large-for-defined-data-type](https://askubuntu.com/questions/112309/error-splicing-file-value-too-large-for-defined-data-type) But I do not understand the solution. The drive just auto mounts. I checked for the drive UUID with "ls /dev/disk/by-uuid -lt" and it is not shown in the /etc/fstab file. 

I used to have no problems with large files. Could it be that the file is corrupt? 

I got the error on both Xubuntu 16.04 and Linux Mint 19.

Thanks!

---

