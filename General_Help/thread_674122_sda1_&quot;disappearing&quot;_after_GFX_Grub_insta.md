---
title: "sda1 &quot;disappearing&quot; after GFX Grub install?"
date: 2008-01-21
forum: General Help
---

### Post by natelessard on 2008-01-21
Hello,

I have a dual-boot setup of Windows XP, and UbuntuStudio. I have them on separate partitions (obviously) of the same hard drive. I've always been able to read the ntfs partition (sda1, in this case), which is where I kept all of the music and other documents I had before switching to Linux. Things were working fine, and sda1 was able to be mounted without a problem, until now.

I attempted to install GFX Grub, using a tutorial found at UnixTutorials: [http://www.unix-tutorials.com/go.php?id=3588](http://www.unix-tutorials.com/go.php?id=3588) . The installation seems to have worked out fine, as I now have GFX Grub instead of the normal, nongraphical Grub bootloader, but now when I booted, I noticed that the shortcut to sda1 was not on the desktop anymore. I opened up a nautilus window, and instead of the normal sda1, it was shown as "68.4 GB Volume." I tried to open it, but got an error message. Here's what it said.
> [SIZE="3"]Cannot mount volume.[/SIZE]
Unable to mount volume.

mount: wrong fs type, bad option, bad superblock on /dev/sda1, missing codepage or other error In some cases useful info is found in syslog - try dmesg | tail or so
I tried to open up syslog, but I don't know what exactly it is that I'm looking for. I also tried using Gparted, and the disk is recognized as an ntfs partition, but it is still unable to be mounted. I really hope that this doesn't mean that I lost everything on the partition. :-?

Anybody have any ideas what might be going on here? I greatly appreciate any advice or tips.

Thanks a whole bunch!
Nate


Oh, and I'm sorry if this is posted in the wrong forum

---

### Post by natelessard on 2008-01-21
top.

---

### Post by Holonet on 2008-01-21
I'm still green to linux myself, so I don't know if this will help, but I've had issues with partitioning, such that afterwards, my sda1 disappears, but I don't think there was any volume detected at all...either way...  Try booting up in Windows and letting it shut down successfully.  If you did something in Windows it might be that simple...only other thing I know of is run chkdsk in Windows (use /f and do it on the reboot).  If, in the process, anything gets out of whack even a little, I notice linux doesn't want to pick it up anymore.

---

### Post by natelessard on 2008-01-21
Thanks for the advice Holonet, but I can't even get into Windows from the bootloader. The option is still there, but if I try to start it, all it does is go back to the bootloader screen.

I'm currently upgrading to Gutsy, so maybe that might help me? I doubt it, but maybe.

I was also thinking, maybe I could reinstall GRUB, and this time do it correctly? I'm not quite sure how I would go about doing that, however.

---

### Post by natelessard on 2008-01-21
top.

---

### Post by logos34 on 2008-01-21
You can run checkdisk from the XP install CD.  Boot into the **Recovery Console** (press 'R') and type at the prompt

**chkdsk /r**

it will check and attempt to repair any bad sectors.

If you want to reinstall the regular grub bootloader, try
[B]
sudo grub-install /dev/sda[/B]

---

