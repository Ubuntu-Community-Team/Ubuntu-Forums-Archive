---
title: "No Grub, staight to windows following holidays"
date: 2020-01-06
forum: General Help
---

### Post by fjstjohn2 on 2020-01-06
Hello,

Just seeking some insight regarding failure to get the Grub OS selection when rebooting following the recent holiday. My system was operating fine just before holiday in Ubuntu, but now only goes directly to Win10. What could have caused this?

Best,

Franz

---

### Post by oldfred on 2020-01-06
What brand/model system?
What video card/chip?

Did Windows do an update? It would reset itself as first in boot order. Major grub update or install also sets grub/ubuntu as first in boot order.

May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) &

---

### Post by fjstjohn2 on 2020-01-09
Hello oldfred,

Computer has no brand....pieced together by me. AMD FX, Gigabyte board, Nvidia Ti-720 video card.

You hit the nail on the head. Windows indicated that it was updated on the 27th. I believe this is when I returned to work and turned it on to have it go straight to Win 10. Still trying to rationalize my way through this, but I do not recall whether Grub was set to go straight to windows. I doubt that because the system build required either a Grub repair following a Windows install or a Ubuntu reinstalll following a Windows install. I assume that the last time I turned off windows it had an update requiring a reboot to finalize.

I tried several times to fix Grub with the Ubuntu live, but kept getting EFI error messages. Tried several approaches. Don't remember exactly. It's alll Greek to me. Just frustration. I made a Boot-repair boot USB disk with Rufus and that seemed to complete, but also gave a failure warning....something about a locked ESP....

What part of the pastebin content is needed to diagnose? Although the error occur ed, the result appeared to to fix Grub , but the Grub selection is very strange. Not sure how to post a picture I took of the screen.

Thanks for any help.

---

### Post by oldfred on 2020-01-09
Best not to use Boot-Repair's ISO, but just use the Ubuntu live installer and add Boot-Repair to it with the ppa.

Locked ESP could be something in UEFI settings, or corruption of FAT32 partition.
You can try this from Ubuntu live installer.

Must be unmounted & if ESP is sda1 otherwise change to your FAT32 partition.
Boot-Repair report shows all the entries in grub.cfg. Sometimes Boot-Repair add a 25_custom with additional boot options, usually not required.
sudo dosfsck -t -a -w /dev/sda1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

---

