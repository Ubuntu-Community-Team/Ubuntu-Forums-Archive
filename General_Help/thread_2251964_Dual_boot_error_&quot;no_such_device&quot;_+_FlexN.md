---
title: "Dual boot error: &quot;no such device&quot; + FlexNet issue"
date: 2014-11-08
forum: General Help
---

### Post by feba2 on 2014-11-08
I have trouble with my dual boot (Win7/Ubuntu14.04). The original problem was, out of the blue, the "no such device" error which takes you straight to grub rescue mode. I tried several things. I did lilo, which allowed me to boot Windows, but still not give me an option to boot Ubuntu. I run boot-rescue, but I don't seem to be able to change my boot order in BIOS (the list of hard disks is not interactive at all, nor does it list sda or sdb, only "HDD1" and "HDD2"). I reinstalled grub, which brought me back to the original error. This is also where the Sector 32 FlexNet warning came up. I'm familiar with this thread: [http://ubuntuforums.org/showthread.php?t=1661254](http://ubuntuforums.org/showthread.php?t=1661254) but I'm not confident enough to run the commands on my own on my laptop (I'm fairly new to linux!). 
Here's my latest boot-rescue record [http://paste.ubuntu.com/8877936/](http://paste.ubuntu.com/8877936/)

If someone could please help me out with this, I'd greatly appreciate it!

---

### Post by oldfred on 2014-11-09
Grub now writes around the "flexnet" error. 

But since you have two drives you should just keep Windows boot loader on sda and only have grub installed to sdb. Do not run auto repair as that just installs grub to every drive's MBR.
You can use advanced options in Boot-Repair to choose Windows and drive sda. And choose Ubuntu and drive sdb.
Then from BIOS set to boot from sdb by default and sda as second choice. If issues with grub then you can manually choose sda from BIOS or one time boot key to directly boot Windows.

Grub was installed to sdb.

Reinstall the GRUB of sdb5 into the MBR of sdb
Installing for i386-pc platform.
Installation finished. No error reported.
grub-install /dev/sdb: exit code of grub-install /dev/sdb:0

---

### Post by feba2 on 2014-11-10
Thanks oldfred. My BIOS doesn't allow me to change the boot order between sda and sdb (several people have tried).

> **oldfred said:**
> 
Grub was installed to sdb.

Reinstall the GRUB of sdb5 into the MBR of sdb
Installing for i386-pc platform.
Installation finished. No error reported.
grub-install /dev/sdb: exit code of grub-install /dev/sdb:0

I don't quite understand what you're saying here. Would you mind giving me the exact command line? I'd appreciate that, I've never worked with grub commands before.

---

### Post by oldfred on 2014-11-10
If yours is an old system that will not boot sdb or is one of those where sdb is a caddy which is only a data drive then you have to install grub to sda.
But Boot-Repair also said it correctly installed to sda and wrote around the flexnet sector.

Your sda2 partition is full, Windows NTFS really needs 30% free and at 10% free you do not have room to run defrag. You have 1% free:
       /dev/sda2      fuseblk     60G   59G  1.1G  99% /mnt/boot-sav/sda2
    
But you have some very strange errors. 
You have a Samba error and a read error on a mp3 file and mpeg file? It should not be doing any of that as part of its update?
Is Windows trying to auto launch something, or do you have a virus?

---

