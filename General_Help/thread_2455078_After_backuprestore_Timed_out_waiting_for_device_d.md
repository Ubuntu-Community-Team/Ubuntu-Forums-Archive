---
title: "After backup/restore: Timed out waiting for device /dev/disk/by-uuid/"
date: 2020-12-11
forum: General Help
---

### Post by ygoe on 2020-12-11
Hello,

I'm testing the backup and restore procedure of a new server running Ubuntu 20.04. While the machine did boot after restoring, I found this in the journal syslog after the boot (it wasn't there after the previous boot):

```
12-11 23:07:48.251 systemd &#9474; Finished Wait for Network to be Configured.
12-11 23:09:13.784 systemd &#9474; dev-disk-by\x2duuid-c78b9e55\x2d7684\x2d445d\x2da0b2\x2dba98a6d8718d.device: Job dev-disk-by\x2duuid-c78b9e55\x2d7684\x2d445d\x2da0b2\x2dba98a6d8718d.device/start timed out.
12-11 23:09:13.784 systemd &#9474; Timed out waiting for device /dev/disk/by-uuid/c78b9e55-7684-445d-a0b2-ba98a6d8718d.
12-11 23:09:13.785 systemd &#9474; Dependency failed for /boot.
12-11 23:09:13.786 systemd &#9474; Dependency failed for Unattended Upgrades Shutdown.
12-11 23:09:13.786 systemd &#9474; unattended-upgrades.service: Job unattended-upgrades.service/start failed with result 'dependency'.
12-11 23:09:13.786 systemd &#9474; Dependency failed for Local File Systems.
12-11 23:09:13.786 systemd &#9474; local-fs.target: Job local-fs.target/start failed with result 'dependency'.
12-11 23:09:13.786 systemd &#9474; boot.mount: Job boot.mount/start failed with result 'dependency'.
12-11 23:09:13.786 systemd &#9474; dev-disk-by\x2duuid-c78b9e55\x2d7684\x2d445d\x2da0b2\x2dba98a6d8718d.device: Job dev-disk-by\x2duuid-c78b9e55\x2d7684\x2d445d\x2da0b2\x2dba98a6d8718d.device/start failed with result 'timeout'.

```

I've tried to find out what that means but wasn't successful. I believe it has something to do with the UUIDs of the file systems and that they might have changed because of the full restore of the system. But I'm unable to find out any more details, like whether the data in fstab is correct. Here's the fstab contents:

```
proc /proc proc defaults 0 0
# /dev/md/0
UUID=c78b9e55-7684-445d-a0b2-ba98a6d8718d /boot ext3 defaults 0 0
# /dev/md/1 belongs to LVM volume group 'vg0'
/dev/vg0/swap  swap  swap  defaults 0 0
/dev/vg0/root  /  ext4  defaults,usrjquota=aquota.user,jqfmt=vfsv0,nodelalloc 0 0
```

Please ask for any information from my system that you need to analyse this, I cannot provide anything helpful in advance.

The backup was made with Borg Backup. The server is running in the hetzner.de data centre and uses a RAID0 and LVM for the root filesystem. All files were restored from the original server. First the provided installimage script sets up RAID0 and LVM exactly like before and copies all default OS files. I then delete these files and restore everything from the backup (entire filesystem plus mounted /boot). These are the steps I perform after restoring all files:

```
# Chroot into the restored system to install the bootloader
mount -o bind /dev /mnt/dev
mount -o bind /sys /mnt/sys
mount -t proc /proc /mnt/proc
chroot /mnt /bin/bash

# Update UUIDs of RAID in initramdisk and bootloader
cp -p /etc/mdadm/mdadm.conf /etc/mdadm/mdadm.conf.bak
grep -ve '^ARRAY ' /etc/mdadm/mdadm.conf.bak >/etc/mdadm/mdadm.conf
mdadm --detail --scan >>/etc/mdadm/mdadm.conf
update-initramfs -ck all
update-grub

cd /
mklost+found

# Exit chroot and reboot into restored system
exit
reboot
```

This is the current output of mdadm --detail --scan:

```
ARRAY /dev/md/0 metadata=1.2 name=rescue:0 UUID=f0bd24f8:5d181402:b1dfdeb2:e196b5fe
ARRAY /dev/md/1 metadata=1.2 name=rescue:1 UUID=465d0b80:fb1bcda2:91a87ea7:23c5aef7
```

These two lines also show up at the end of /etc/mdadm/mdadm.conf as updated after restore (see above). Not sure if any of those UUIDs should match with something else, I don't even know what they mean.

Update: I repeated this backup&restore loop a second time (I needed to evaluate a different backup storage location) and did exactly the same this time. But now the server doesn't boot anymore. (No more details available, I dodn't have much time now to do forensics.) So this restore process clearly isn't working. I think it still worked with the previous system (Ubuntu 18.04) but I'm not sure because I never needed to do it a second time. It certainly worked with Ubuntu 14.04 when I last checked it.

---

### Post by ygoe on 2020-12-12
I found the issue. The fstab entry for /boot uses a UUID that has  changed after the new setup as part of the restore. I hadn't updated  that entry so after the first restore and boot, the /boot filesystem  wasn't found anymore. The system did still boot but wrote syslog  entries. And on the second backup and restore, all files in /boot were  missing (because it wasn't mounted anymore then). That's why the system  then didn't boot anymore, no matter how much I tried to fix any UUIDs &#8211;  the kernel, initrd and stuff was simply missing.

My conclusion is  to not use UUIDs but change everything to classic device names. Those  have never changed whereas UUIDs are different every time. I can't rely  on that.

---

### Post by TheFu on 2020-12-12
> **LonelyPixel said:**
> I found the issue. 
...

My conclusion is  to not use UUIDs but change everything to classic device names. Those  have never changed whereas UUIDs are different every time. I can't rely  on that.

Glad you figured it out. 

Using device files directly is dangerous and more dangerous the more storage devices involved. I see just 2 devices swap back and forth at reboot all the time. Not every time, but enough that using UUIDs is still a good idea.  Also, if two devices with the same UUID are connected at boot time, flip a coin as to which actually gets used each boot.  That's a known problem with image-based backups.

Either use UUIDs in the fstab or use the generated-at-boot symbolic links which pont to the correct device **always**.  if using logical volume management, there are some other options for the symlinks, like what is already being used above.

To help the community, please use the "Thread Tools" button to mark this thread as SOLVED so people seeking answers find answers and helpers don't waste time on SOLVED questions.

---

