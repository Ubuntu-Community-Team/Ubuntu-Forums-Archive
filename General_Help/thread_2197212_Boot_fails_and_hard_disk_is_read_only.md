---
title: "Boot fails and hard disk is read only"
date: 2014-01-02
forum: General Help
---

### Post by tv0571 on 2014-01-02
I'm really stuck.

Trying to boot in 11.1 kernel 3.00-24 from previously working system.  Ubuntu splash screen is followed by log of what is going with boot which terminates with  *starting Timidity... [OK]" and then just stops.  Nothing happens.  Rebooting and using Grub to rollback to a previous kernel (2.6.24-22-386 recovery), I see the log fly by, and it starts running into problems with "failed to create pty" messages, and finally fails with "General error mounting filesystems." 
Sure enough... I cannot "touch" a file.  DF -h shows  
/dev/sda1    with 21G available mounted on /
udev            wiuth 1.7G available mounted on /dev
tmpfs           with 21G available mounted on /run

This seems weird to me.

As background, this is HDD #2 which was previously hooked up behind HDD1.  HDD #1 which was the previous boot device now gives me message "Reboot and Select proper Boot device or insert media..." and doesn't seem to boot at all if HDD2 is not hooked up.  If both HDD1 and HDD2 are hooked up, it appears that the boot goes to HDD2, so perhaps HDD1 has been failing for some time now and I haven't noticed until HDD2 started having these problems.

Thanks for help.

---

### Post by deadflowr on 2014-01-02
Upgrade to a supported version of Ubuntu.
That stated, try running [boot repair]("https://help.ubuntu.com/community/Boot-Repair").
At the very least, if it doesn't work, you can post the link to the generated pastebin.

---

### Post by tv0571 on 2014-01-02
Thanks deadflowr.   That did it.  

I remember now that I lost the system as I was trying to upgrade to 12.04LTS.  The boot repair found it on HDD1 and everything seems to work fine now.

I think that will be the last time I upgrade for a long while.

Thanks again.

---

