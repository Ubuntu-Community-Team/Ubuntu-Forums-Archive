---
title: "How booting works????"
date: 2007-02-03
forum: General Help
---

### Post by rdoolen on 2007-02-03
I have a question about how my computer boots.  This is just for information, I don't really have any problems.

First, here is the history. I had a computer with Windows 2000. It had two hard drives with Win2000 on C: (duh). The first drive had 4 partitions and the second had two. Then I installed Ubuntu Dapper. I installed it at the beginngn of the second drive, the swap at the beginng anf then the /root. So in my Ubunutu world the Windows drive is /dev/hda and Unbuntu is /dev/hdb.  

So how does booting work? The BIOS go to /dev/hda to read the MBR. That directs it to GRUB on /dev/hdb? Then I choose OS?

Does this mean if I unplug /dev/hda my computer won't boot because there is no mbr found? or if I unplug /dev/hdb it won't boot because its loking for GRUB?

I just want to better understand how this works (before I start unplugging things to confirm them). The only thing I might want to do someday is get rid of my Windows and just run VMware in Ubuntu (when there is no way to avoid it).

Thanks!

---

### Post by Topsiho on 2007-02-03
Usually, not necessarily, grub is installed in the MBR: the Master Boot Record, of the disk from which the computer boots. This is usually the first hard disk, /dev/hda, the MBR being the first sector on this disk.
The MBR contains among other things the partition table, without which the computer can not do anything (can not find anything).
And if it contains grub also, it needs this MBR for getting instruction which OS it should boot.

So if you remove hda, then the computer will not boot at all.

You could put grub some other place such as in the boot sector (the first sector) of a removable medium (USB- stick, CD-Rom) or in the boot sector of the active partition.

But then you still need the partition table.

I am not sure, but I think this partition table is copied, as a backup, in other (boot)sectors, as it is very important. You may find this out for yourself :)

O ja: if you remove hdb you have no Linux, so that's the last thing to do ...

Topsiho

---

### Post by rdoolen on 2007-02-03
So, to boot the Ubuntu it sounds like I need both drives. hda (the windows drive) has the MBR and hdb has Ubuntu. 

But to Boot Windows, do I need hdb? It seems that grub is going to direct things over to hdb to find menu.lst and stage1 etc.... or if I unplug hdb, do I just get windows the it was before installing Ubuntu?

I am sure there must be guides to completely rid yourself on the Windows install, but I haven't looked...yet.

One last question, if I start powering off, disconnecting drivers, and trying to boot, will I screw things up permantently? or will everthing go back to normal when I put it all together correctly?

By the way, don't you just feel like I am about to break something. :)

---

### Post by dcstar on 2007-02-04
> **rdoolen said:**
> So, to boot the Ubuntu it sounds like I need both drives. hda (the windows drive) has the MBR and hdb has Ubuntu. 

But to Boot Windows, do I need hdb? It seems that grub is going to direct things over to hdb to find menu.lst and stage1 etc.... or if I unplug hdb, do I just get windows the it was before installing Ubuntu?

I am sure there must be guides to completely rid yourself on the Windows install, but I haven't looked...yet.

One last question, if I start powering off, disconnecting drivers, and trying to boot, will I screw things up permantently? or will everthing go back to normal when I put it all together correctly?

By the way, don't you just feel like I am about to break something. :)

You shouldn't need hdb to boot Windows, AFAIK GRUB will reside in the boot sector is was installed in (soley on the first drive). You can test this by unplugging your second drive and seeing if Grub loads (and then try Windows).

You should only need to install Grub onto your second drive, and then change you BIOS to boot from that drive, to lose the Windows drive for good (I think there are HOWTOs on this somewhere in the forum).

---

