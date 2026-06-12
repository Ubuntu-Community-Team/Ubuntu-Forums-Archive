---
title: "Booting problems"
date: 2008-07-02
forum: General Help
---

### Post by Drugs on 2008-07-02
I just reformatted and installed a fresh copy of Windows XP Professional SP3 integrated N edition and then installed Ubuntu as a partition on the same drive. Booted to Ubuntu and everything is fine.

Went to reboot to Windows and selected XP at the boot menu. Usually, you'll see the quick "Starting up..." and XP will start but for some reason it just sits there. "Starting up..." and that's it.

Not sure why it's doing this, I previously had Windows XP on my 200 GB HDD master and Ubuntu on my 80 GB HDD slave and that worked fine. I formatted both before reinstalling. I just wanted to use the 80 GB as a backup drive and do both OS's on my master.

Any idea it just sits there? I know I could pop in my XP CD and go to recovery console and type "fixmbr" and boot to Windows but then I don't know how to add Ubuntu back to it.

---

### Post by VMC on 2008-07-02
> **Drugs said:**
> I just reformatted and installed a fresh copy of Windows XP Professional SP3 integrated N edition and then installed Ubuntu as a partition on the same drive. Booted to Ubuntu and everything is fine.

Went to reboot to Windows and selected XP at the boot menu. Usually, you'll see the quick "Starting up..." and XP will start but for some reason it just sits there. "Starting up..." and that's it.

Not sure why it's doing this, I previously had Windows XP on my 200 GB HDD master and Ubuntu on my 80 GB HDD slave and that worked fine. I formatted both before reinstalling. I just wanted to use the 80 GB as a backup drive and do both OS's on my master.

Any idea it just sits there? I know I could pop in my XP CD and go to recovery console and type "fixmbr" and boot to Windows but then I don't know how to add Ubuntu back to it.

After you reformated and installed XP did you boot into Windows first before you installed ubuntu. That should have been the first course of action.

If your sure ubuntu boots okay, and Windows is trying to start but can't, then I would suggest fixing Windows bootloader with rescue disk. Putting Grub back after you get Windows fixed is a snap.

From Terminal type this:

```
sudo fdisk -l
```Save it or print it out. You'll need it later.

Then fix Windows with 'fixmbr'. Once Windows is running correctly then come back with ubuntu livecd booted up. Make sure the fdisk -l command wasn't changed by Windows for some reason.

---

