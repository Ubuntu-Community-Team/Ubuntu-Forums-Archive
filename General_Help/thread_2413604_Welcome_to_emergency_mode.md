---
title: "Welcome to emergency mode"
date: 2019-02-27
forum: General Help
---

### Post by danielsender on 2019-02-27
On a Dell M6500 I run a dual boot system, that is Ubuntu 16.04 (/dev/sdb1) and windows 10 (/dev/sda). The graphic card failed so I replaced by an M7820. Windows 10 is running fine now but on the Ubuntu side I always get the "Welcome to emergency mode" message. With a live CD I ran fsck -y on the unmounted /dev/sdb1 and got the message "clean", etc. However when I boot from the system I still get the "Welcome message". Can some guru help me?

Thanks

---

### Post by Autodave on 2019-02-27
What video card failed?  Were drivers installed for that card or for your replacement card?

---

### Post by danielsender on 2019-02-27
> **Autodave said:**
> What video card failed?  Were drivers installed for that card or for your replacement card?

The failing card doesn't have a label but I think it was the Nvidia Quadro FX 2800M. I had the Ubuntu's supplied driver for it that was working fine until it conked out. Apparently these cards fail with the "dark" problem. The new one I installed (M7820/VYGKK) seems to be working fine as seen when I boot windows. I didn't install its driver in Ubuntu yet because my system is refusing to boot normally.

---

### Post by danielsender on 2019-02-27
Just in case the drivers for the old card were causing the trouble, I apt purged nvidia-* but the welcome issue remains.

---

### Post by danielsender on 2019-02-27
I found the problem. Reading through lines in the journal I saw that there was a message saying that it couldn't mount windows, that was in the fstab file for accessing those files in the windows system. It mentioned something about hibernating, so as the first experiment I commented out the line in fstab that mounts windows, and the problem went away! Apparently in windows there is a file related to hibernation that remains there unless you shut off windows by pressing the shift key at the same time that you click on the power icon.

---

