---
title: "failed hd, question about dd_rescue"
date: 2007-12-22
forum: General Help
---

### Post by ctsiow on 2007-12-22
I have a failed hd that I ran dd_rescue on, following the instructions here [http://www.debianadmin.com/recover-data-from-a-damaged-hard-disk-using-dd_rhelp.html]("http://www.debianadmin.com/recover-data-from-a-damaged-hard-disk-using-dd_rhelp.html")
but I am unable to mount the image at the stage
> Now you need to check the backup image consistency this will check for is there any problems with this image.

#fsck -y /dev/sda2/backup.img

If you are using ubuntu linux use the following command

sudo fsck -y /dev/sda2/backup.img

After finishing this checking you need to mount your disk image in to your other hard disk

#mount /dev/sda2/backup.img /mnt/recoverydata

If you are using ubuntu linux use the following command

sudo mount /dev/sda2/backup.img /mnt/recoverydata

This will mount all the data from the backup.img under /mnt/recoverydata now you can try to access the data it should
work without any problem.

I have made a mountpoint but all I see on that point after the mount is a lost+found directory. I am currently doing a nother install after a grub error 24 problem and will catch the responses later and add them to this post but if anyone has any experience of dd_rescue I would appreciate some pointers.
Thanks a lot
Mark

---

### Post by Pumalite on 2007-12-22
You can also use TestDisk: [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

### Post by ctsiow on 2007-12-22
Thanks, I will give it a go. I used apt-get and will play with it later.
Mark

---

### Post by Pumalite on 2007-12-22
Good luck!

---

