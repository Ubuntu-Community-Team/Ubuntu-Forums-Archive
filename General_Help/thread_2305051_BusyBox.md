---
title: "BusyBox"
date: 2015-12-02
forum: General Help
---

### Post by asearle on 2015-12-02
Hallo Everyone,

I installed Ubuntu 12.04 on a friend's PC and now (several months later) wanted to run an update but (after an incomplete update) found that the system will no longer boot.  I get this message ...

```
BusyBox v1.21.1 (Ubuntu 1:1.21.0-1ubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs) ... [flashing cursor]
```

I have trawled the web and have tried out three proposed solutions which I couldn't get to work.  Arrgghh.

Can anyone help me here?  Maybe point me towards a solution which has actually worked for you.

And I would be interested to know the cause of this problem:  Linux is normally soooo stable but this is the second time that this has happened to me:  The first time I gave up and reformatted the disk.  This time I can't do that because I need to recover the friend's environment.

Any tips would be a GREAT help.

Many thanks,
Alan
Cologne, Germany

---

### Post by ian-weisser on 2015-12-02
Please describe the 'incomplete update' in a bit more detail. That could mean several different problems.

The cause is usually either a dying hard drive or a misconfigured GRUB. Could be several other rarer things.

---

### Post by asearle on 2015-12-03
The update stopped with (I think) a message about installing the video-driver.  I had to click that away and then, after waiting a while, I clicked away the update window (both were frozen).

I would be very pleased if the problem were a defective drive (I would simply replace it) but when I ran ```
sudo e2fsck /dev/sda1
``` the message was that the drive was "clean".  Is there another test that I could run?

And I tried reinstalling grub using this procedure ...

```
from root

1) blkid
< find the partition you installed ubuntu on
2) mount /dev/sdax /mnt <<< where x is partion # containing ubuntu and 'a' assumes this is your first hard drive (if have > 1)
3) mount --bind /sys /mnt/sys
4) mount --bind /dev /mnt/dev
5) mount --bind /proc /mnt/proc
6) chroot /mnt
7)update-grub
8) grub-install /dev/sda <assumes the you want grub to be installed on your first hard drive ('a')
9) reboot
```

But that didn't fix it.

By the way, the first message to come (before BusyBox) is ...

```
udevadm trigger is not permitted while udev is unconfigured
```

Is this significant?

As mentioned, I would be very happy to find a clear problem, even if that meant replacing the hard disk.

Thanks for any tips you can give.

Yours,
Alan Searle
Cologne, Germany

---

### Post by matt_symes on 2015-12-03
Hi

> I have trawled the web and have tried out three proposed solutions which I couldn't get to work. 

It would be useful for you to mention these solutions you have tried so that those trying to help you don't waste their time, or your time for that matter, covering ground you've already tried.

> udevadm trigger is not permitted while udev is unconfigured

Is this significant?

Maybe. 

You may have to rebuild your initramfs for your currently installed kernel.

Can you boot into an older kernel from the grub menu ? If not then you may need to rebuild it from a LiveCD/USB.

Kind regards

---

