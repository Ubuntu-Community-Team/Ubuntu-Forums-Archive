---
title: "LVM issue ubuntu 18.04 failed to connect to lvmetad"
date: 2018-07-10
forum: General Help
---

### Post by pandajoey77 on 2018-07-10
So, today I turned on my laptop and go the error shown below./ 

WARNING: Failed to connect to lvmetad. Falling back to device scanning.
Volume group "ubunut-vg" not found
Cannot process volume group ubuntu-vg
WARNING: Failed to connect to lvmetad. Falling back to device scanning.
Reading all physical vlumes, This may take a while...
Found volume group "ubunut-vg" using metadata type lvm2
WARNING: Failed to connec to lvmetad. Falling back to device scanning.
2 logical volume(s) in volume group "ubuntu-vg" now active
/dev/mapper/ubuntu--vg-root: clean 1918966/15491072 files,. 38393280/6192544 blocks
_

The laptop gets stuck here and I can do nothing. I have looked around on google and ubuntu forums and people have also had issues with lvm, however I've not managed to find a solution to my problem.

I have tried disabling the use_lvmetad = 1 to 0, that did not work, I also tried to run fsck on /dev/mapper/ubuntu--vg-root, it gets stuck at rf kill status and never moves on.

I tried editing the fstab file to see I could map the volume but couldn't get that to work.

I think i dont have a firm understanding of what is actually happening with the error.

I looked at the following posts.

[https://ubuntuforums.org/showthread.php?t=2327801&page=2](https://ubuntuforums.org/showthread.php?t=2327801&page=2)

[https://askubuntu.com/questions/1029915/ubuntu-18-04-fails-to-boot-after-install-lvmetad](https://askubuntu.com/questions/1029915/ubuntu-18-04-fails-to-boot-after-install-lvmetad)

[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1768230](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1768230)

I am running ubuntu on a lenovo t480 and have to use encryption for work purposes.

Any help on this issue would be greatly appreciated.

Thanks!

---

### Post by Blfrg on 2018-07-24
+1 here

This started the other day after upgrading to kernel 4.15.0-29.31
```
use_lvmetad = 0
``` did not resolve the issue

For the time being I've been switching to an older kernel 4.15.0-24.26 and it boots fine.

*Note: If you don't know how to switch kernels in GRUB;*
[LIST=1]
[*]Hold shift during the boot process until grub menu appears
[*]Select 'Advanced'
[*]down-arrow to the previous kernel version and press enter
[/LIST]
---

I'm hoping a fix will come down the pipe or someone has a recommendation.

---

### Post by rsteinmetz70112 on 2018-07-24
This sounds like the configuration in initrd.img may not be correct for the default kernel. You could try rebuilding that.

---

### Post by Blfrg on 2018-08-11
@rsteinmetz70112 thank you for the suggestion, but it sounded like more effort than I wanted to put into it.

I waited for a new kernel version to arrive 4.15.0-30 but was still stuck at the same screen on boot.

Today I went searching again and found this post:
[https://askubuntu.com/questions/969917/failed-to-connect-to-lvmetad-stuck-on-boot/1003374](https://askubuntu.com/questions/969917/failed-to-connect-to-lvmetad-stuck-on-boot/1003374)
---
I don't know about you @pandajoey77 but whenever I update my kernel I **_always_** have to re-install nvidia too.
I just had not seen the error described in this thread before so I was thrown off.
The post I found above spoke to me clearly, it's the same issue I always have, just a different manifestation.
I purged and reinstalled nvidia drivers and can now boot to the most recent kernel.

As the post notes, you can use a different vt (2, 3, etc) even while stuck on that boot screen, so you don't need to go into maintenance or anything.
I hope that helps!

---

