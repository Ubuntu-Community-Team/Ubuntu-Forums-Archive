---
title: "Nemo will not open a drive"
date: 2019-05-31
forum: General Help
---

### Post by crosschk on 2019-05-31
I am running Ubuntu 18.04.2 

This is an odd one and I dont know where to look for the answer

I've used NEMO file manager for years in ubuntu. recently it has been acting strange. 

I have 6 hard drives 4 external 1 os and 1 internal data drive. 

When I browse to /.../media/Data in nemo it opens, same thing with 3 of the 4 usb drives

if I browse to /.../media/ExtMov02 nemo will not open it. The address bar doesnt even look like it is trying. I have tried deleting and recreating the partition. 

 Here is the weirder part, it will browse/open a link to the drive. just not open the drive itself. 

Has anyone ever seen this before?

---

### Post by TheFu on 2019-06-02
What file system does the partition have? You need to create that if you deleted the partition and the file system needs to be supported by the libraries on your system.  ext4 will be supports. Other file systems may or may not be supported.

---

