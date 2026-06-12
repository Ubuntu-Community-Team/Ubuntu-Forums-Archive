---
title: "Using 2nd HD for storage"
date: 2020-06-24
forum: General Help
---

### Post by Autodave on 2020-06-24
I have several machines setup like this, but never this issue.  PC has a 120G SSD and a 250G spinner HD.  I cannot copy anything to the 250 nor can I create a folder on it.  I can mount it by clicking on the icon, but that's about it.  It says it is mounted at /media/gac/xxxxxxxxxxxxx.  Under permissions, it says root.  It is formatted to ext4.

How can I get access to this drive?

---

### Post by Tadaen_Sylvermane on 2020-06-24
Terminal makes this easy as hell. Look up mounting drives, fstab, and chown command. Be very cautious with chown as you can blast your system with it easily. Im sure there is a gui way but terminal is exponentially faster. Also look up symlinks in the process.

---

### Post by tea for one on 2020-06-24
I suspect that you may have used gparted to format the drive and you are therefore not the owner (yet)?

Usual caveat, when playing around with ownership and drives, you have backed up important data?

I have used **chown** on drives previously formatted with gparted to create an ext4 file system.

You have to change both user and group.

For, example:-

User name is Autodave
Group name is Autodave

```
sudo chown -R  Autodave:Autodave /media/Autodave/device_name/
```

---

### Post by SeijiSensei on 2020-06-24
Just in case, check the filesystem's integrity.
```
sudo e2fsck /dev/sdb1
```
or whatever device and partition you're actually using.

Linux won't mount unclean filesystems.

That said, I think the permissions issue is more the likely candidate.

---

### Post by Impavidus on 2020-06-24
I'd mount it with fstab, not with a click. Then it will mount automatically at boot. And don't put it in /media, which is for removable drives.

---

### Post by tea for one on 2020-06-24
> **Impavidus said:**
> I'd mount it with fstab, not with a click. Then it will mount automatically at boot. And don't put it in /media, which is for removable drives.

Ah, yes, good point.

I thoughtlessly did not consider that the drive was going to be permanent.

---

