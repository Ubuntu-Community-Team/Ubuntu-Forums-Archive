---
title: "Stuck in emergency mode"
date: 2018-12-19
forum: General Help
---

### Post by a_guenther on 2018-12-19
Hi,
I'm on Kubuntu 18.04 and since yesterday my system boots only into emergency mode. I had some updates, I assume something broke there.

In an effort to repair it the easy way, I installed via LiveUSB Kubuntu 18.10 new (wanted to update anyways soon), this was successful. After the reboot: Still emergency mode.

I formatted only the partition with / (sda8), and assigned my old /home partition with all the data back to /home (sda9). I have a bunch of other partitions (Windows which I haven't booted into since months and some original recovery partitions which I never erased...). Basically, all relevant data is on sda9 and can be access via the live system. Of course I could format everything, but maybe there is a way to get around this?

If I go through journalctl -xb, I have a few red lines, I guess the files system ones are the ones which are relevant:
```
fsck failed with exit status 4.
Failed to start File System Check on /dev/disk/by-uuid/948....f2.
```

In fstab, I see the following (I short the UUIDs a bit to avoid typing, let me know if you miss something)
```
# / was on /dev/sda8 during installation
UUID=1c39... / ext4 errors=remount-ro 0 1
# /boot/efi was on /dev/sda2 during installation
UUID=76FE... /boot/efi vfat umask=0077 0 1
# /exchange was on /dev/sda7 during installation
UUID=6793... /exchange nfts defaults,umask=007,gid=46 0 0
# /home was on /dev/sda9 during installation
UUID=948b... /home ext4 defaults 0 2
# /swap was on /dev/sda6 during installation
UUID=2df8... none swap sw 0 0

```

So I guess something isn't ok with my /home partition (sda9), which would explain why I have the same error after the new installation. Could you please help me?

Thanks!

---

### Post by TheFu on 2018-12-19
Run fsck from a live-boot.

BTW, if a system is broken, I've never seen an upgrade make it better. Usually, it breaks the upgrade and leaves the system is a half-old/half-new situation which requires wiping completely.

Also, shortening the UUIDs removes some Windows vs Linux file system knowledge from the post.  Windows (FAT/NTFS) have much shorter UUIDs.  Whereas Linux file systems have 4-5 chunks inside their UUIDs.

---

### Post by a_guenther on 2018-12-19
> **TheFu said:**
> Run fsck from a live-boot.

Thanks, this was what I was looking for. I let it perform a few autorepair on sda9, and now it boots!

> 
BTW, if a system is broken, I've never seen an upgrade make it better. Usually, it breaks the upgrade and leaves the system is a half-old/half-new situation which requires wiping completely.
It was actually a new installation, just with the old /home, not a real upgrade. But yes, your right.

> 
Also, shortening the UUIDs removes some Windows vs Linux file system knowledge from the post.  Windows (FAT/NTFS) have much shorter UUIDs.  Whereas Linux file systems have 4-5 chunks inside their UUIDs.
Good to know, wasn't aware of this.

Thanks!

---

