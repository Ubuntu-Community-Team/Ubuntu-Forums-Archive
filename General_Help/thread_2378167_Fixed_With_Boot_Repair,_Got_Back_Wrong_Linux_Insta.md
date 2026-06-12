---
title: "Fixed With Boot Repair, Got Back Wrong Linux Install"
date: 2017-11-20
forum: General Help
---

### Post by webmanoffesto on 2017-11-20
My laptop was working fine running my second Linux install, running Ubuntu Gnome 16. Then that became un-bootable. I repaired it using Boot Repair Disk. But that put me back to my first linux install. How do I get to my second Linux install, the one I had an liked, the one which became unbootable?

---

### Post by oldfred on 2017-11-20
If you just did auto-fix, Boot-Repair chose whichever it saw first.
Use Boot-Repair's advanced options and choose the install to want as default boot.

UEFI or BIOS?
You should be able to boot into second install from the first install's grub.
And then just reinstall that boot loader to MBR.
If drive is sda.
       sudo grub-install /dev/sda

---

### Post by webmanoffesto on 2017-11-21
Thank you for the advice. But I'm now back to the init.exe error I started with.  

My partitions.
/dev/sda1, which is 926 GB, now my Home partition, has an old install of Debian Gnu/Linux 7: This is the old install that I don't want. 
Also, how do I remove this, so it doesn't take up space, and because I don't want to use it.

And

/dev/sda5, which is 20 GB, has Ubuntu 16.100
This is the install I want. But when I use Boot Repair Disk (advanced options) to select it I go back to my original problem of the init.exe error.
"end kernel panic - not syncing: No working init found. Try passing init = option to kernel. See Linux Documentation/init.txt for guidance."

After I get sda5 working I will want to know how to remove the old install which is still on /dev/sda1, which is 926 GB, now my Home partition.

If it's relevant, I was trying to create VMs in Oracle VirtualBox before this init.exe error appeared.

---

### Post by oldfred on 2017-11-21
If sda1 is your home partition why do you want to delete it?

Have you in Boot-Repair tried the full uninstall/reinstall of grub and include updating to newest kernel option?

---

### Post by webmanoffesto on 2017-11-21
> If sda1 is your home partition why do you want to delete it?
I don't want to delete it, I  want to remove the Linux install which I no longer use


> Have you in Boot-Repair tried the full uninstall/reinstall of grub and include updating to newest kernel option?
No I haven't. How does updating Grub to a version with the newest kernel resolve the init.exe error problem?

---

### Post by oldfred on 2017-11-21
Full reinstall of grub should update everything and may fix your issue.

Difficult to extract an install from a partition leaving just /home.
Easier if you have room to shrink the partition, move /home to a new partition. Then you could delete the install.

       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

