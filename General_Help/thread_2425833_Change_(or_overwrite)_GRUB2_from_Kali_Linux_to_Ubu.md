---
title: "Change (or overwrite) GRUB2 from Kali Linux to Ubuntu"
date: 2019-08-31
forum: General Help
---

### Post by mrbean04 on 2019-08-31
Hi everyone!
I have this problem.
As the title says I want to change my grub from Kali Linux to Ubuntu.
I have multiple hard drives, with triple boot between Kali, windows 7 and Ubuntu 18.04.3 LTS

[FONT=arial]The first OS I installed on my computer was windows 7.
Then I installed Kali Linux, where I was asked to install GRUB2.
Later I installed Ubuntu, without GRUB2.
Now I want to install Ubuntu GRUB2 and overwrite Kali Linux GRUB2.
(The reason why I am making this is because I am thinking about removing kali linux completely from my machine(because I am not using kali at all))

There is anything I can do?

Thanks.[/FONT]:smile:

---

### Post by mrbean04 on 2019-08-31
Hi everyone!
I have this problem.
As the title says I want to change my grub from Kali Linux to Ubuntu.
I have multiple hard drives, with triple boot between Kali, windows 7 and Ubuntu 18.04.3 LTS

[FONT=arial]The first OS I installed on my computer was windows 7.
Then I installed Kali Linux, where I was asked to install GRUB2.
Later I installed Ubuntu, without GRUB2.
Now I want to install Ubuntu GRUB2 and overwrite Kali Linux GRUB2.
(The reason why I am making this is because I am thinking about removing  kali linux completely from my machine(because I am not using kali at  all))

There is anything I can do?

Thanks.[/FONT]:smile:

---

### Post by mrbean04 on 2019-08-31
Sorry this isn't the right sub-forum for this problem.

---

### Post by guiverc on 2019-08-31
Boot into Ubuntu, and `sudo grub-install /dev/sdX`  where sdX is the drive/device where you want the MBR or master-boot-record (first 512 bytes of disk).  The MBR is the first stage of grub, and is primarily a pointer to later stages (stored in /boot/grub/) and usually your BIOS controls which disk's MBR is used.  Note: it's a drive/device and not a partition you use.

See "Re-installing GRUB 2" in [https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by mrbean04 on 2019-08-31
Ok, seems to be that I installed correctly grub2.
I only need to write the following command to update grub2:
```
sudo dpkg-reconfigure grub-pc
```

and select from the list the hard disk that is booted at the beginning.

Hope this helps someone! :)

---

### Post by coffeecat on 2019-08-31
Duplicate threads merged. Please do not post duplicates in different parts of the forum. This causes confusion and dilution of community effort.

And yes the first thread was in the wrong sub-forum. You posted it in Ubuntu, Linux and OS Chat, which is for chat, not support, hence the large red banner there.

---

