---
title: "Auto-mounting and adding the icon to the Desktop"
date: 2007-02-12
forum: General Help
---

### Post by azazel00 on 2007-02-12
I just installed Ubuntu on my sisters' computer. They are hooked on ubuntu.

Thing is, when I installed ubuntu on my machine, it autodetected all NTFS and FAT32 partitions. those partitions are automounted in my machine and they have a nice icon on my desktop.

In their case, it didnt detect the Windows partition and never mounted it. They want to be able to access their windows files (music, photos, and God knows what other girl stuff).

I've searched and I know how to mount my windows partition using the "mount" command. But I dont want to have to mount it manually every time.

So, how do I automount partitions at startup like my ubuntu machine does?
Second, how do I add those nice icons on the desktop that point directly to the mount point? I tried checking the "Properties" of the existing icons I have on my desktop, but unlike the ones I've created, I see no "command" that I can copy and paste on another link. They also have the "unmount" option on right-click.

Regards,
az

---

### Post by dcstar on 2007-02-12
> **azazel00 said:**
> I just installed Ubuntu on my sisters' computer. They are hooked on ubuntu.

Thing is, when I installed ubuntu on my machine, it autodetected all NTFS and FAT32 partitions. those partitions are automounted in my machine and they have a nice icon on my desktop.

In their case, it didnt detect the Windows partition and never mounted it. They want to be able to access their windows files (music, photos, and God knows what other girl stuff).

I've searched and I know how to mount my windows partition using the "mount" command. But I dont want to have to mount it manually every time.

So, how do I automount partitions at startup like my ubuntu machine does?
Second, how do I add those nice icons on the desktop that point directly to the mount point? I tried checking the "Properties" of the existing icons I have on my desktop, but unlike the ones I've created, I see no "command" that I can copy and paste on another link. They also have the "unmount" option on right-click.

Regards,
az

Assuming you are using 6.10 and Gnome, install the **pysdm** package and then you will have a tool to set up auto-mounting of other drives on the system.

---

