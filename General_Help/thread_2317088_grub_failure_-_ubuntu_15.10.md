---
title: "grub failure - ubuntu 15.10"
date: 2016-03-13
forum: General Help
---

### Post by hezy2 on 2016-03-13
error: no such device: 21a258b9-4d53-92de-5d9c3f3cf010.
Entering reescue mode...
grub rescue>

I've tried several ways suggested in YT but it's not seems to be a usual case. Thanks,
Hezy.

---

### Post by yancek on 2016-03-13
With the extremely limited information you posted, there is nothing to do but guess.  What changes did you make?  The error you posted indicated the system is looking for a specific partition with the UUID you posted and it doesn't exist.  Open a terminal and run the command:  sudo blkid  Post the output or take a look at it and see if you have a partition which exists with the UUID you got in the error message.  Compare that output to the contents of /etc/fstab and /boot/grub/grub.cfg or post that info here.

---

