---
title: "HP laptop won't load Ubuntu 24.04.1 LTS"
date: 2024-11-23
forum: General Help
---

### Post by YMS_1975 on 2024-11-23
Hello,

I have an HP laptop (Model : 15fd0xxx). This is a brand new laptop, so I doubt my problem is hardware related. 

Anyways, installing Ubuntu 24.04.1 LTS & after what appears to be a successful installation, I get the following error message : 

"Gave up waiting for root file system device. Common problems : 

- Boot args (cat /proc/cmdline)
- Check rootdelay= (did the system wait long enough?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! UUID=ccbc63a3-f209-42e1-aad6-68a26dd8c7ff does not exist. Dropping to a shell!

BusyBox v1.30.1 (Ubuntu 1:1.30.1-7ubuntu3.1) built-in shell (ash) 
Enter 'help' for a list of built-in commands.

(initramfs)"

Now, initially I tried with a Bootable live version of Ubuntu 24.04.1 LTS using Rufus. But after a reboot, I got that error
message. Then I tried formatting my USB stick & simply burning the ISO image to my USB stick. Same result.

Then I tried an older version of Ubuntu (22.04.5 LTS) & I got the same result.

If it helps, I disabled Secure Boot in the BIOS & my Boot preference is USB drive & then OS Loader (Hard Drive).

Can someone please help me? I've got no use of my laptop!

---

