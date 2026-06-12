---
title: "Permissions Question"
date: 2013-01-27
forum: General Help
---

### Post by bigb0ss on 2013-01-27
I recently purchased a 1-TB Seagate Backup Plus @ Costco the other day, LOVE IT.

I have a mac & chromebook with Linux Ubuntu. 

Problem: When I plug the HD into the MAC i'am able to drag and drop into the HD.

* When i plug it into the Ubuntu, it recognizes, I can open the files on the Ubuntu, but CANNOT drag and drop files onto the HD.....

"Error while copying to "Seagate 1-TB"
This destination is read-only.


I would like to be able to drag and drop from both my mac and Ubuntu.....Possible?


Thanks

---

### Post by claracc on 2013-01-27
I think you will have to mount the external drive as read and write.

Following link [https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB), can help you to do the task.

---

### Post by 3rdalbum on 2013-01-27
A couple of things:

1. If you formatted the drive on the Mac, as HFS+ you will either need to use the Mac to turn off journaling on the disk's filesystem, or reformat to something more cross-platform. Ubuntu can't write to journalled HFS+ as far as I know


2. Check that the mount point of the drive has the permissions that you want the drive to have - change them as necessary.

---

### Post by bigb0ss on 2013-01-27
i am not really too technical when it comes to Hard Drives (1st one). 

I thought this would be a little easier fix...please help

---

