---
title: "GRUB hijacked my Windows 7"
date: 2013-02-03
forum: General Help
---

### Post by heide on 2013-02-03
Hey!

Yesterday i decided to install Ubuntu 12.10 on an external harddrive, so that i could use the same OS on 2 computers. And so i did. And it worked great. When installing i physically disconnected all other harddrives from the computer, as i wanted GRUB to only concern itself about the Ubuntu, seeing how i was going to put the external disc at the top of the boot-order in BIOS, so that it would always boot Ubuntu when that disc was connected, but Windows when it was nont. And it worked great. On both machines. 

Then suddenly as i was turning on my computer this morning, with the external harddrive disconnected, attempting to get into Windows, i got suddenly got to GRUB rescue screen straight after BIOS. And i have no idea why. It worked perfectly yesterday, and it still works on my 2nd computer. 

I know that Windows is still there. I've been able to access it after adding it to grub.cfg (after the first boot problem, so that's not it.), and accessing the GRUB menu when booting.

So, what i presume has happend, is that Windows suddenly thinks it has to boot from GRUB. But why has this suddenly happend? And how can i fix it?

Note:
Only Windows 7 is installed on the actual harddrives of the computer. GRUB is only on the external harddrive. 

Thanks!

---

### Post by prodigy_ on 2013-02-03
Follow this HOWTO to repair your Windows installation:
[Restore Windows 7 MBR](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

Then follow this HOWTO to reinstall Grub:
[Recovering Ubuntu After Installing Windows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
You'll need to install Grub on your external drive. 

---

Finally you can add Linux to your Windows 7 bootloader:
[Dual Boot Windows 7 And Linux Using BCDEdit](http://www.iceflatline.com/2009/09/how-to-dual-boot-windows-7-and-linux-using-bcdedit/)
This will let you boot into Linux without having to choose external USB from the boot devices list every time.

---

### Post by afoin on 2013-02-03
One possibility is that there was a kernel update. Grub is automatically updated and installed on the internal hd ...

---

### Post by prodigy_ on 2013-02-03
Good point about updates. With ```
sudo dpkg-reconfigure grub-pc
``` command you can choose where new versions of Grub will be installed. Deselect all internal HDDs and your Windows MBR won't be overwritten anymore.

---

