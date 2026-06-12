---
title: "Frustrating crypt, lvm or initramfs issue"
date: 2021-08-14
forum: General Help
---

### Post by luca1729+ on 2021-08-14
When my computer boots it can't find volume "some-name" eventually it enters busybox. At the initramfs prompt  I can enter cryptsetup luksOpen /dev/partition some-name. I then enter my password and it is accepted. When I exit busybox my computer boots correctly. 


I run Ubuntu 20.04 (upgraded from 16.04 which might have been upgraded from 12.04) with disc encryption. I recently resized the boot partition and broke something (possibly a UUID changed with re-sizing). I have fixed most issues but my computer no longer boots correctly. It is possible that I broke something when "fixing" it, or that  it wasn't 100% correctly installed, there is evidence that I changed the volume name at some point and also I don't think I used the default disc encryption when I installed 12.04 and I can't remember if I am using a clean install (of 16.04 since updated to 20.04) or that 16.04 was in turn an upgrade.


I think /etc/crypttab is correct, it has the UUID of the partition within the volume, anything else reports a Source mismatch error when I run ```
sudo update-initramfs -u
``` Similarly I think /etc/fstab is correct:-
```
/dev/mapper/some--name-root /               ext4    errors=remount-ro 0       1

```I have tried, the following and a few varients```
 sudo update-grub
```

Both of the above ran with no errors, but still no boot. If anyone can point me in the right direction I would be most grateful.

---

### Post by TheFu on 2021-08-14
It is possible to resize 1 partition and have it overwrite the following partition's headers by accident. I'd like to think there would be a warning, but without seeing the disk layout from parted -l, I cannot say.

Resizing any PV inside an encrypted LUKS container is asking for problems. There isn't any programmatic validation for sizes.  Resizing LVs should be 100% fine. I've done that plenty of times.

---

### Post by luca1729+ on 2021-08-16
Thanks, it is possible i damaged the headers on the boot partition which isn't inside LVM and isn't encrypted. I didn't touch the encrypted partition and I think it is okay as I can unlock it from initramfs and then it mounts correctly. I think I have something missing in grub.conf , fstab crypttab, or similar, but I've compared these with my similarly configured laptop and I can't see anything.

---

### Post by TheFu on 2021-08-16
Sorry if I wasn't clear. Making the boot partition larger could overlap into the next partition. At the beginning of every partition, there is a little header. If that gets damaged, be it LVM or LUKS, then everything supposed to be contained by those partitions could be corrupted.

Output from **parted -l** would clearly show this issue.

Whenever using encryption, excellent backups are mandatory. There is little that can be correct if a critical, encrypted, block, becomes failed. If the block contains the decryption key header, everything would be lost.

---

### Post by luca1729+ on 2021-08-17
There is an error I am struggling to understand in the output of parted -l
Everything is as I expect for the hardware discs and then there is an entry for dev/mapper/[FONT=Amazon Ember, Arial, sans-serif][COLOR=#333333]some--name-root and also [/COLOR][/FONT]dev/mapper/[FONT=Amazon Ember, Arial, sans-serif][COLOR=#333333]some--name-swap both described as (linear) (dm) and partition table loop.
But then I see 
[/COLOR][/FONT]Error: /dev/mapper/some-name: unrecognised disk labelModel: Linux device-mapper (crypt) (dm)                                   
Disk /dev/mapper/some-name: 499GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown

---

