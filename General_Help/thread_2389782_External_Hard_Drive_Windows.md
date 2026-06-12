---
title: "External Hard Drive Windows"
date: 2018-04-21
forum: General Help
---

### Post by cmcanulty on 2018-04-21
I have an external hard drive partitioned into 2 ext4 file systems and one ntfs partition. In my double boot xubuntu 16.04 and windows 10 home, I copied all my desktop and documents from the ext4 partition to the ntfs partition. Then I wanted to go to my windows double boot and copy those 2 folders to my user account. So I unmounted and removed  the hard drive and rebooted into windows and hooked up the external hard drive. The windows doesn't see the external drive at all, even in disk management. I even have the ntfs as the first partition on the external hard drive. I have 200GB to get onto the windows boot. Is there a way to force windows to see the external hard drive ntfs partition? Thank you

---

### Post by leunam12 on 2018-04-21
I don't know the answer to your question; WIndows sometimes doesn't recognize external drives (happened to me this
 week), but... why don't you just boot Xubuntu and then mount the Windows partition from there and copy the files/folders
 directly?

---

### Post by cmcanulty on 2018-04-21
Thanks that's a better idea and I think it is working now!

---

### Post by oldrocker99 on 2018-04-21
Here: [https://www.howtogeek.com/112888/3-ways-to-access-your-linux-partitions-from-windows/](https://www.howtogeek.com/112888/3-ways-to-access-your-linux-partitions-from-windows/). This will, despite appearances, access ext4 partitions.

---

### Post by cmcanulty on 2018-04-21
which one on that page do you recommend? I have had problems with some apps claiming to do that

---

### Post by cmcanulty on 2018-04-22
PS one problem with your method. I copied all the desktop files and I guess a few had names not accepted by windows. It put win partition in unsafe space and I had to disable hibernate in win to mount it and sift through a ton of files to delete the bad named ones. I wish there was a filter for bad file names as when copying a bunch of them it just kicks out an error invalid file name but doesn't say what file.

---

