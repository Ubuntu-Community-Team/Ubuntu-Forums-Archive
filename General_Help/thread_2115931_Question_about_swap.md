---
title: "Question about swap"
date: 2013-02-14
forum: General Help
---

### Post by MourningsEnd on 2013-02-14
I have Xubuntu 12.10 installed, and I wanted to install Ubuntu 12.10 as well.  Can I just use one swap area, or do I need to create different ones for different distributions?  

Thanks for any help.

---

### Post by howefield on 2013-02-14
Yes, you can use the same swap partition for both installs.

---

### Post by MourningsEnd on 2013-02-14
> **howefield said:**
> Yes, you can use the same swap partition for both installs.

Thank you.

---

### Post by Bufeu on 2013-02-14
> **MourningsEnd said:**
> I have Xubuntu 12.10 installed, and I wanted to install Ubuntu 12.10 as well.  Can I just use one swap area, or do I need to create different ones for different distributions?  

Thanks for any help.
All Linux-based operating systems will, as default, use the swap partition on the disk, there's therefore no need to create two swap partitions.

---

### Post by tgalati4 on 2013-02-14
Be mindful, that if you put your machine into hibernate--RAM-to-Disk--then it will store a snapshot into your single swap.  When you try to boot into another distro, you may have some issues--trying to boot with a snapshot that doesn't match the distro you are booting into.  Also, if you have 32-bit and 64-bit distros installed on the same machine, swap can be problematic--you may have to reissue the *swapon* command when switching.

These are edge cases, but that seems to be 80% of the help requests on these forums.

---

