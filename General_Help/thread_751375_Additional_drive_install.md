---
title: "Additional drive install"
date: 2008-04-10
forum: General Help
---

### Post by ScottMartin on 2008-04-10
In trying to install an additional SATA HD, I have encountered problem at boot.

The system has 
-U7.10 (the only OS)
-160GB SATA (sda)
-40GB IDE (sdb)

I installed an additional 250GB SATA drive. 

GParted displayed the drive as sdb (sames as the IDE?, IDE became sdc)

I was able to create a ext3 partition on the drive and all seemed well.

When I rebooted, GRUB just hangs. Disconnecting the new drive and things are back to normal.

Are there additional steps that need to be taken? changes to fstab?
Is the previous define for sdb/IDE interferring?

Any help is appreciated to help correct this.

Regards,
Scott.

---

### Post by hellblade on 2008-04-11
Grub has nothing to do with fstab as it doesnt know anything about your OS configuration but since I've faced some problems with HD additions/removals+grub I'd like to inform you that grub is very sensitive in how it recognises your disks. In my case, hd0 is always the one that is set as boot device in the bios, not the primary master or anything like that. Thus in order to boot, plugin your new disk and when you get to the grub sceen, select you boot option and press 'e' to edit the line that contains your boot options. Change X to X+1 etc. in (hdX,Y) and try to boot. Try different values until then one that works for you and then go make that change in /etc/grub/menu.lst in order to save it. Something else you can do is use the uuid of your boot partition which is a value that never changes. You can find it by this command in a console

ls -l /dev/disk/by-uuid/

check for the line that looks like that:
lrwxrwxrwx 1 root root 10 2008-04-11 16:02 673414ae-58e2-4915-8386-07568f9c1db5 -> ../../sdb1

in that example, assuming that /dev/sdb1 is your root partition, you would put root=UUID=673414ae-58e2-4915-8386-07568f9c1db5

---

