---
title: "Kubuntu 7.10 crashes on startup!  HELP please!"
date: 2007-11-17
forum: General Help
---

### Post by CoolRat33 on 2007-11-17
Hi
I'm a new diehard Linux user. But now I really need help.

Something happened yesterday when I was fiddling in fstab trying to get the system to recognize my external NTFS drives.  

Now the system won't boot up at all.
It begins to boot, the Kubuntu splash screen appears, but it stops after a short time and the error messages appear:

udevd event [4096] run_program: exe of program
'lib/udev/usb_device_name' fail
'lib/udev/check-ptp-camera' fail
'/sbin/modprobe
'lib/udev' fail
'lib/udev/usb_id' fail
'lib/udev/path_id' fail
'lib/udev/usb_device_name' fail
'lib/udev/path' fail

I'm not sure why this happened nor do I know how to fix it. :confused: I'm using XP for the time being.. ugg!:(

Please help me to solve this.  I'm quite new, so I need pretty clear instructions on what to type etc!

Thanks very much!:KS

---

### Post by TidusBlade on 2007-11-17
I had loads of problems in the past with installations. I dont have a solution for your problem though, but I would suggest using ntfsS-3g from adept manager to detect external drives.

---

### Post by Arwen on 2007-11-17
That is to say your fstab is probably messed up,you can find it and post it by running a LiveCD.Or wait for a quicker solution.You can also do some [reading]("http://ubuntuforums.org/showthread.php?t=283131") on fstab.
Good luck!

---

### Post by CoolRat33 on 2007-11-18
Thank you VERY MUCH for your replies!

If it wasn't for these forums, many new people would not be able to switch OS. Thanks so much for your contribution of time and effort! :)

Booting into recovery would not work.
So I used a live CD and started Kubuntu. But it wouldn't give me access to my old ext3 partitions with my installation on it. I had to fiddle around a lot with System Settings - Disk and File Systems to enable access to my Kubuntu ext3 partition.
Why am I haveing such trouble mounting partitions?

Then when I had access, I found that I DID have a backup of fstab.  But I couldnt' rename it because I lacked permissions.  So I changed permissions on my <mount point> folder so that anyone could read and write.  (Was this i a huge mistake? How can I fix it?)
Then I renamed the backup to fstab.  I renamed the faulty fstab too.

Kubuntu rebooted after this nasty process!

---

