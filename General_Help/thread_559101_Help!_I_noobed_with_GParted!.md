---
title: "Help! I noobed with GParted!"
date: 2007-09-24
forum: General Help
---

### Post by Akdor 1154 on 2007-09-24
So, I've been getting reasonably familiar with Linux thanks to Ubuntu, getting over-confident... so one late night, delirious from fatigue crossed with caffiene intake, it seemed like a smart idea to delete an unused FAT32 partition in front of my / partition, which of course renumbered it. But Hah! I was smarter than that (:rolleyes:), I can go and fix GRUB myself! So, mounted my root partition, fixed up menu.lst... and the second bout of idiocy:
grub> setup (hd0,0) (hd0,5)
So now my Windows NTFS partition is borked. From Googling away it seems this can be fixed, though, and I'm not especially worried about it.

Now, a few more Grub Error 22's later, I realize my mistake, and use the GParted LiveCD to boot to my first hard drive partition - success! My menu! And what's more, Ubuntu boots, decides the hard drive last check is x million years in the future, reboots, and this time loads up absolutely perfectly. Now, I'm getting happier at this point as I think I know what I've got to do: grub> setup (hd0) (hd0,5). Reboot, grub shows up by itself this time, try to boot Ubuntu... Scroll Lock and Caps Lock lights flash. It takes editing the grub boot commands to remove the Kubuntu splash to see that this means a kernel panic.
Under normal boot, just without the splash screen, the log reads:
```
/init: /init: 148: divide by zero.
Kernel panic - not syncing: attempted to kill init!
```
And with the above, but adding debug to the command:
```
Capability LSM initialized.
Kernel panic - not syncing: attempted to kill init!
```

So.. how screwed am I? :)

EDIT: I'm currently using my system with the help of a Puppy Linux Live CD, so I do have access to mounting and further screwing with my data if need be.

---

### Post by p_quarles on 2007-09-24
Have you tried using the Ubuntu live disk to reinstall GRUB? That's where I would start.

---

### Post by Akdor 1154 on 2007-09-24
Well I already tried that (with GParted instead of Ubuntu), and it didn't help much. :(

Yay! Turns out the problem was actually reasonably simple to fix - I had set "kopt=root=dev/hda6". Of course, update-grub copied this error across to all of my Ubuntu boot entries, which is what was leading to the kernel panics. Changing it to root=/dev/hda6 in all entries fixed it wonderfully.

Also, I fixed my NTFS using testdisk, kudos to Microsoft for including a backup boot sector in their specification. :)

---

