---
title: "Nedd to move server to larger hard drive..."
date: 2007-10-16
forum: General Help
---

### Post by mikey5555 on 2007-10-16
Hello, 

I have a small server installation, RedHat Enterprise 4, that I want to move to a new, larger hard drive.  I've read several How-Tos, but did not see a method describing how to do what I'd like to do:

1: Install new drive into PC with running install of RHEL4.
2: Partition new drive with larger boot partition (from about1.4 to 3GB), and the rest to the user partition (about 250GB).
3: Duplicate each partition's content from original drive/partition to new drive/partition.
4: Shutdown system, remove original drive and connect new drive as primary, and reboot.

I would expect the system to reboot onto the new drive and be ready to go without any problems.
Can this be done?   What command or utility do I need to accomplish this task with as little hassle as possible?
It is important that I get this done ASAP, as my main drive is "acting up", and will most likely fail very soon.  

Regards...

mikey5555

---

### Post by kidders on 2007-10-17
Hi there,

I would suggest booting from a CD -- well, any OS other than the one you want to copy -- and simply copying the contents of your source filesystems to the destination ones.[LIST]
[*]Avoid utilities with GUIs like the plague. I would strongly recommend partitioning your new disk, creating your filesystems & duplicating your files with a terminal emulator ... it's the only way you can be 100% sure everything is happening exactly the way it's supposed to.
[*]Since your current hard disk is playing up, keep an eye out for I/O errors in your system logs. If your source disk hiccups in the middle of a copy, you'll want to know it!
[*]I suggest taking another look at your partitioning scheme. 1.4 - 3GiB is *waaay* too big for a boot partition. Normally, anything over 100MiB is completely unjustifiable.[/LIST]Once your copying is all done, I would suggest thinking through your boot process, one step at a time, making any necessary alterations to your /etc/fstab, and other configuration files. Once you're done, reinstall your bootloader. Personally, I would do that by chrooting into the new OS, so I could set the bootloader up the way I'm most used to doing it. Since your system will fail to boot if you make even a small mistake with your bootloader setup, it's best to do it from a familiar environment.

Lastly, I recommend being prepared for your new system to screw up, *somewhere* along the boot process. It's remarkably easy to overlook something small (eg boot-time kernel parameters in your bootloader config file, changes to your partition table layout in /etc/fstab). Also, since you'll be adding & removing hard disks (or maybe swapping them around), your filesystems' /dev names may change ... which can get confusing. If you refer to your filesystems by UUID (instead of /dev node name), you can get around that though, for the mostpart. Anyhow, the point is not to be phased by weird errors & lock-ups during boot.

I hope that helps.

---

