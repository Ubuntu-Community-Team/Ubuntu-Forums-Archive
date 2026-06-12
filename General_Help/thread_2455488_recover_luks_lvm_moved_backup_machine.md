---
title: "recover luks lvm moved backup machine"
date: 2020-12-20
forum: General Help
---

### Post by dgermann on 2020-12-20
Friends--

Production environment.

The problem: On bootup, luks will not accept my correct passphrase.

What I did: I unplugged the machine from one location, plugged it into another. On boot, problem occurs.

My system: LVM inside a luks container on 20.04 ubuntu server. There are three data hdd @ 10 T each (8% full each), plus a boot hdd @ 250G. This is my backup machine for the business. It has been running OK, with reboots and upgrade from ubuntu 18.04, for 4 1/2 months. The data drives are opened automatically after boot by way of the crypttab file. The boot disk is also encrypted via luks.

I do have the header .img file and the keyfile.

I also have a spare 2T external drive I can plug into it.

What I tried: 1. decrypting from ssh via dropbear; 2. decrypting from the console; 3. using the 18.04 install usb in rescue mode. In the last case, since I cannot get it to open the boot disk, I cannot verify the fstab and crypttab files are still in line with whatever the boot disk is now called.

(I had this problem early on before I had much data on it, so I blew it all away and started over. My theory is that somehow the system has assigned new identifiers for the drives and so does not associate the passphrase with the drive. All 4 drives use the same passphrase.)

Where it stands now: I cannot open it up enough to check the files and restore the luks header file, which I suspect is what I need to do. Or somehow have it associate the passphrase with this drive. Perhaps I need to blow it all away again, but if so, how do I prevent this from happening the next power outage we have? And I wonder if there is some better live usb I can use, instead of the 18.04 server install usb.

Thanks!

:- Doug.

---

### Post by TheFu on 2020-12-21
> **dgermann said:**
>  

What I did: I unplugged the machine from one location, plugged it into another. On boot, problem occurs.


Was the system shutdown or did you test a power-outage situation and get corrupted disks?
Are the drives connected to the exact same ports now as before?
Are the drive mounted using device names or UUIDs or LVM VG+LV paths?

Whenever using encryption, perfect backups are required.

If the OS is running 20.04, use a 20.04 flash drive to boot and look around.  I use Ubuntu-Mate installer whenever I need a recovery OS.  It has LVM and LUKS/dm-crypt included.  Caja knows how to open LUKS encrypted storage - or it did last time I needed it.  From the 20.04 Ubuntu-Mate "Try Ubuntu" environment, you should be able to fix anything.

If I had wasted 30 minutes or more, I'd wipe the OS, do a fresh install and restore from my backups. Call it done.  In 30-45 minutes, the system would be back where it was before and only the huge data stuff would need to be added. Restoring the first 30-50G would happen in that 45 minutes. Most of my systems use less than that amount of storage. Just a few are in the multi-TB sizes. One has about 36TB connected, but the OS and most data that is special for it can be restored within 45 minutes.  I know - had to do that in June after the OS disk failed.

And yes, I backup my backup server too - just not the backup storage for systems. I keep backup storage really simple. I never span partitions to make a single LV.  I split at 4TB boundaries, always, even with disks that are larger than 4TB.  Fancy stuff on backup storage is the enemy of easy restores, at least to me.

---

