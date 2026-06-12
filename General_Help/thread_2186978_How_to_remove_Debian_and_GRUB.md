---
title: "How to remove Debian and GRUB?"
date: 2013-11-10
forum: General Help
---

### Post by Stevensthunar on 2013-11-10
So i dual-booted Ubuntu 12.04 and Debian 7, but now i don't really need Debian, i just don't know how to remove it.I want to remove GRUB too.

Ubuntu is on my first Hard Disk.
Debain is on my second Hard Disk.

---

### Post by philinux on 2013-11-10
Moved to General Help.

---

### Post by Bucky Ball on 2013-11-10
Where is grub?

To remove Debian on the second hard disk you'd just boot into Ubuntu, launch Gparted, right click the Debian partitions and unmount them, delete.

---

### Post by Lars Noodén on 2013-11-10
You can see which partitions Ubuntu installation is using by running df.

```

 df -h | grep '^/dev'

```

Then you can run gparted and erase the Debian partition -- if you have no data there.  Either way, be sure to back up your data first, just in case an accident happens. 

Then after it is gone, you can run  update-grub using sudo.

As far as removing grub, I'm not sure if that can be done and still run Ubuntu.

---

### Post by buzzingrobot on 2013-11-10
> **Lars Noodén said:**
> 
As far as removing grub, I'm not sure if that can be done and still run Ubuntu.

Yes, don't remove Grub.  It's the bootloader.  I.e., the bit that picks up from the BIOS and launchs the kernel.

---

### Post by Impavidus on 2013-11-10
Indeed, you can't simply remove grub, but you can make the menu disappear, making grub invisible. This may be the intention of the OP. The computer will boot a few seconds faster, but it may be slightly more complicated to access the menu in case you have to solve some problem. Open /etc/default/grub, find the line ```
GRUB_TIMEOUT=<some number>
``` change it into ```
GRUB_TIMEOUT=0
``` and save the file. You'll need root permission. Then run **sudo update-grub**.

---

### Post by jeanjd63 on 2013-11-10
Hello 

You have first to know what is the grub installed in your boot disk. Il it is the ubuntu one, no problèm, you have only to format or remove debian partition.
If it is the débian grub, you have to install the ubuntu grub before rebooting. You can do that with the command :
**sudo  grub-install  /dev/sda  ** from the install ubuntu.

Bye

---

### Post by Stevensthunar on 2013-11-11
I deleted Debian partitions and did update-grub,restarted and it shows This:

Error:no such device: 1233639b-c2f4-4070-82ad-14bd1617e31a.
Entering rescue  mode....

And i cant do anything..

---

### Post by Bucky Ball on 2013-11-11
Boot from a LiveCD and 
```

sudo grub-install /dev/sda
```

We could have helped prevent this if you'd have told us where you had grub installed in the first place, as requested in post #3. We can now guess it was the Debian partition, which is why I asked for clarification originally. ;)

If the above doesn't work, you can try boot repair.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Stevensthunar on 2013-11-11
Thanks, it worked.

---

### Post by Bucky Ball on 2013-11-11
Great news. Enjoy! ;)

---

