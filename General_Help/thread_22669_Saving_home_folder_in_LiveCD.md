---
title: "Saving home folder in LiveCD"
date: 2005-03-29
forum: General Help
---

### Post by vaskark on 2005-03-29
This maybe a dumb question but is there any way to save my home folder to my hard drive when I'm using Hoary LiveCD, so that the next time I use the cd I can somehow load my home folder with all my settings intact? Right now I'm making an archive of my home folder and uploading it to my ftp space, but it's getting a little bothersome ;-).

Thanks.

---

### Post by localzuk on 2005-03-29
The easiest way to do this would be to install ubuntu on your hard disk and dual boot with windows.

However, if you don't wish to do that you should create a partition on the hard disk to which you can save work.

Have a look at partitioning tools in linux (such as fdisk or cfdisk) or the hard disk manger in windows xp (if you are running that), or for an even easier partitioning tool try partition magic - you have to pay for it though. WARNING: Be careful - back up anything on your disk before you attempt to do this.

Once you have an empty partition and you know its /dev/hdaX path, run mkfs.ext3 /dev/hdaX and this will format the partition using the linux parititon type: ext3.

In linux you should now be able to go to /mnt/hdaX as Ubuntu should find the partition for you...

---

