---
title: "What's going on with this failure to unmount on an SD Card?"
date: 2016-02-03
forum: General Help
---

### Post by 777funk on 2016-02-03
I've had an issue with SD Cards not unmounting in Xubuntu. I wouldn't care but when I pull the card, take more pictures then pop it back in, the new photo files are not shown and cannot be accessed until after a reboot.

Is there a way to fix this error? I've never had this happen until Xubuntu. I've reformated the SD Card to no effect. See the screenshot of this error below.

[ATTACH=CONFIG]267103[/ATTACH]

---

### Post by blueridgedog on 2016-02-03
There may be an error in the path it thinks it is mounted.

Next time it is inserted, issue the following in a terminal:

```
mount
```

This will show you where it is mounted.  From there you can manually unmount it as an alternative.

---

### Post by 777funk on 2016-02-04
Thanks. Just did that and I don't think I have an error. But not sure. Here's that drive.

> /dev/sdd1 on /media/bill/583E-26A6 type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks2)



---

### Post by yancek on 2016-02-04
Your initial post shows the error unable to unmount because the drive is not mounted.  Also, the mount point is /media/nick.
In your last post, you show the mount point is /media/bill.

My experience is that if user nick puts the ssd/flash drive in and opens it, then ejects or safely removes, then removes the ssd/flash drive and logs in as another user, the drive will be available to the second user when it is plugged in.   Failing to do that will give a "Could not open media" error.  

Not sure this is your problem.  How do you get this error?  Trying to eject or safely remove?

---

