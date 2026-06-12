---
title: "Installing other OS without losing MBR info"
date: 2013-05-19
forum: General Help
---

### Post by SirLouen on 2013-05-19
I need to install Windows in a new hard disk drive I've recently bought, but from previous experiences I know that Windows installations destroy the MBR info so it is nearly impossible to run back Ubuntu.

I know I can create some type of "rescue" disk to restore the MBR with GRUB so I can come back to Ubuntu after installing Windows, and then updating GRUB I can add an extra line so I can boot Windows when needed from GRUB.

I've been looking for info but I've not found anything to do this previouly of doing the Windows install task (instead most helpful topics are made to create recovery disk with RescaTux when people have already lost their MBR).

Any tips for performing this well?

Kind Regards

---

### Post by Cheesemill on 2013-05-19
It's not 'nearly impossible' at all, just boot from a Ubuntu CD after you've installed Windows and run [boot-repair]("https://help.ubuntu.com/community/Boot-Repair").

---

### Post by SirLouen on 2013-05-21
> **Cheesemill said:**
> It's not 'nearly impossible' at all, just boot from a Ubuntu CD after you've installed Windows and run [boot-repair]("https://help.ubuntu.com/community/Boot-Repair").

I forgot that if you install windows in a new hard drive you dont kill the mbr of the linux hd, by chaging bios boot options you can go back to grub and configure it to reload the new win install (update-grub)
Easy as a cake

---

