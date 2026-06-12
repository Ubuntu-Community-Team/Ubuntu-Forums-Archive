---
title: "Disk has been mounted 30 times without being checked,disk check forced"
date: 2006-11-03
forum: General Help
---

### Post by Coop on 2006-11-03
Sometimes when I start my ubuntu 6.06 a black screen like the terminal and Windows' scandisk/checkdisk comes which says:> dev/hda2 has been mounted 30 times without being checked,disk check forcedIs this bad?

---

### Post by 23meg on 2006-11-03
No, it's  a regular disk check.

---

### Post by ~LoKe on 2006-11-03
It'll do that as it says, every 30 startups.  It's just to make sure everything's in working order.

---

### Post by Coop on 2006-11-03
Thank you for your help.

---

### Post by Charles Hand on 2006-11-20
When it gets to the 30'th boot, you gotta do the check, the system won't boot without it. Naturally, this always happens when I don't have an extra seven minutes to get my machine booted. Is there any other configuration possible? Can I make it, say, give me one or two grace boots? Or perhaps tell me when the 30th boot is approaching so I can do a check manually before 30 boots is up (and reset the 30-boot counter)?

---

### Post by dcstar on 2006-11-20
> **Charles Hand said:**
> When it gets to the 30'th boot, you gotta do the check, the system won't boot without it. Naturally, this always happens when I don't have an extra seven minutes to get my machine booted. Is there any other configuration possible? Can I make it, say, give me one or two grace boots? Or perhaps tell me when the 30th boot is approaching so I can do a check manually before 30 boots is up (and reset the 30-boot counter)?

[http://ubuntuforums.org/showthread.php?t=300477](http://ubuntuforums.org/showthread.php?t=300477)

---

### Post by kc8hr on 2006-12-03
Isn't it possible to convert '/' to EXT3, which does not require this periodic annoyance? If so, how is this done?

Tim

---

### Post by atoponce on 2006-12-03
> **kc8hr said:**
> Isn't it possible to convert '/' to EXT3, which does not require this periodic annoyance? If so, how is this done?

Tim

EXT3 requires the same.  It's not a file system feature, it's a kernel feature.

---

### Post by kc8hr on 2006-12-03
> **atoponce said:**
> EXT3 requires the same.  It's not a file system feature, it's a kernel feature.Sorry, I think you are mistaken here.

The EXT3 filesystem is a journaling filesystem that does not require a periodic check. A number of distros use EXT3 as the default filesystem for this very reason,

Thanks,
Tim

---

### Post by atoponce on 2006-12-03
It is a journaling file system.  Of course.  However, it seems to be that this is enabled/disabled in the kernel, not an option with the file system itself, which is controlled by the kernel, whether or not it is required.  Please correct me if I am wrong, but how else do you disable the check outside of the kernel?

---

### Post by speedman on 2006-12-03
The automatic file system check is set as a file system option with the tune2fs command.

For example this will set the file system to request a check every 100 mounts as opposed to the default 30:

tune2fs -c 100 /dev/sda1

Replace /dev/sda1 with the appropriate dev entry for your filesystem.

man tune2fs for more information.


Regards,

SM

---

### Post by atoponce on 2006-12-03
Good to know.  Thank you.

---

### Post by dugh on 2007-08-04
You can also see this bug report if you do not like the current behavior of forced disk checks:
[https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/22460](https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/22460)

---

