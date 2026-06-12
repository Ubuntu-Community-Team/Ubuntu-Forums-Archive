---
title: "Grub menu not seen anymore!"
date: 2008-05-27
forum: General Help
---

### Post by srihari_ravi on 2008-05-27
Hi

I had a successfully running dual boot XP and Ubuntu machine with a Grub menu (for OS selection) at boot. Yesterday, I had to reinstall Windows XP as it had caught virus. I reinstalled XP onto the same drive as it was earlier.

After I did this, I **don't see the Grub** menu anymore! The machine directly logs on to Windows XP which means I can no longer use Ubuntu...

Kindly advice on how I can fix this situation & get back Grub to show both Windows XP and Ubuntu...

Thanks in advance!
Ravi.

---

### Post by mattress on 2008-05-27
That's because your XP installation has overwritten Grub in the MBR. You'll need to boot from your LiveCD, mount your Ubuntu partition and rerun grub / grub-install

1. mount /dev/sdX /mnt/ubuntu
2. chroot /mnt/ubuntu /bin/bash
3. source /etc/profile
4. grub-install /dev/sda
   Or
   grub --no-floppy
   root (hd0,1)
   setup (hd0)
   (you will need to tweak these settings to  your system)

HTH

m

---

### Post by forestpixie on 2008-05-27
The reinstall grub process is well documented here -

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by srihari_ravi on 2008-05-28
Hi ForestPixie & Mattress, thanks very much for immediately suggesting a solution. However, none of these methods worked for completely...

Using the procedure told by you, I was able to install Grub fine, but when I selected Ubuntu in the Grub menu, I got the following message:
"Error 17: Unable to mount partition. Press any key to continue..."

So I went through the process of reinstalling Ubuntu over again. Surprisingly, it didn't format the partition and hence all the settings and applications which I had previously were all there safe except for Azureus.

Thanks again!
Ravi.

---

