---
title: "Changed nvme parameter, how to fix in fstab?"
date: 2024-04-18
forum: General Help
---

### Post by von Stalhein on 2024-04-18
Hi,
I accidentally changed a parameter in Disks on the LV that contains Ubuntu in this dual boot PC. From memory, I think I lost authorisation to do anything to it, and then rebooted - I should've left it until I did some research.

From my reading I think I can restore it to previous by making sure the correct UUID is referenced in the fstab? I've live booted and have full access to the drive that way but I'm not sure where to go from here. From what I can see the UUID in the blkid cmd below isn't in the fstab.

It will boot to the GRUB menu and I can select the Win11 entry without issue.

If Ubuntu is selected, it states that the "nvme failed to set apst feature" and that syslog won't start.

 If I manually mount it from the live disk, in Disks it says it's ```
/dev/ubuntu-vg/ubuntu-lv
```at ```
/mnt/0d8b97c8-55f2-4649-be57-600fd5184d8f
```

blkid:
```
ubuntu@ubuntu:~$ blkid
/dev/mapper/ubuntu--vg-ubuntu--lv: UUID="0d8b97c8-55f2-4649-be57-600fd5184d8f" BLOCK_SIZE="4096" TYPE="ext4"
/dev/nvme0n1p1: UUID="047E-E394" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="b638ef09-2838-4d16-9daa-7c948838fdff"
/dev/nvme0n1p3: BLOCK_SIZE="512" UUID="F4EA88B3EA887420" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="956bc493-2965-4e14-967f-a1a0b1ec1c24"
/dev/nvme0n1p4: BLOCK_SIZE="512" UUID="EED83851D8381A73" TYPE="ntfs" PARTUUID="a8bdbff2-d8a5-4980-9f86-16933a825d3d"
/dev/sda1: LABEL="Data" BLOCK_SIZE="512" UUID="5A23552B27173CB5" TYPE="ntfs" PARTUUID="e87b1878-01"
/dev/sdb1: UUID="9632-A285" BLOCK_SIZE="512" TYPE="vfat" PARTUUID="da54da7c-e7bc-47a2-b9ef-7b17dd09fc41"
/dev/sdb2: UUID="e0dfc130-726c-43b9-93cd-d12a7f78ed57" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="dd8b231d-e43b-4510-bd5b-14eec2dd190b"
/dev/sdc1: BLOCK_SIZE="2048" UUID="2024-02-20-19-39-27-00" LABEL="Ubuntu 22.04.4 LTS amd64" TYPE="iso9660" PARTLABEL="ISO9660" PARTUUID="abbd44c4-640c-4cea-acca-ca38273f602e"
/dev/sdb3: UUID="rFmwln-B8pd-EfJE-jRpk-7WN4-ebbZ-zRWu9b" TYPE="LVM2_member" PARTUUID="e2d88fbd-9273-4a30-a795-19c99555132d"
/dev/sdc2: SEC_TYPE="msdos" LABEL_FATBOOT="ESP" LABEL="ESP" UUID="927C-33D8" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="Appended2" PARTUUID="abbd44c4-640c-4cea-acc9-ca38273f602e"
/dev/sdc4: LABEL="writable" UUID="acf238a8-fff5-4a2d-b6ad-a6116e761175" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="96ad1366-f80d-0b4c-af6b-b94dd2c8826f"

```

fstab:

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/ubuntu-vg/ubuntu-lv during curtin installation
/dev/disk/by-id/dm-uuid-LVM-SLExFlmH9KAvU4rQEDWXkLnK0XlDIUAxInHUc47NfYoFLcP97RXWS97BfXcybofA / ext4 defaults 0 1
# /boot was on /dev/sdb2 during curtin installation
/dev/disk/by-uuid/e0dfc130-726c-43b9-93cd-d12a7f78ed57 /boot ext4 defaults 0 1
# /boot/efi was on /dev/sdb1 during curtin installation
/dev/disk/by-uuid/9632-A285 /boot/efi vfat defaults 0 1
/swap.img    none    swap    sw    0    0
/dev/disk/by-uuid/F4EA88B3EA887420 /mnt/F4EA88B3EA887420 auto nosuid,nodev,nofail,x-gvfs-show 0 0
/dev/disk/by-uuid/5A23552B27173CB5 /mnt/5A23552B27173CB5 auto nosuid,nodev,nofail,x-gvfs-show 0 0
/dev/disk/by-id/wwn-0x5000c500edb423f0-part2 /mnt/wwn-0x5000c500edb423f0-part2 auto nosuid,nodev,nofail,x-gvfs-show 0 0
```

Thanks for any assistance.

---

### Post by aljames2 on 2024-04-18
What were you changing with Disks and for what reason/goal? Would this be the root LV you changed, what parameter?  I've never had to fiddle with my fstab on a perfectly good running root on LVM system, other than perhaps when adding additional storage that I wanted to automatically mount.  Normally, your essential system LV's are mounted in fstab using the logically mapped address, for example my root LV is this:  /dev/mapper/LVG-root.  Or, in your case, it is (or was):  **/dev/ubuntu-vg/ubuntu-lv** which originally would have worked reliably to mount that LV on each boot.  I don't have a dual boot system, but I suspect if you could elaborate some on what you did then you may get some more feedback.

---

### Post by von Stalhein on 2024-04-18
I was on the phone & had a USB in the slot looking for some files. I'd found what I wanted and copied them to the Ubuntu SSD. Still on the phone, I didn't realise I'd changed drives and I'm pretty sure I fiddled with the "start at boot" parameter, but I'm not 100% sure on that. Whatever it was it required me putting in the system password to change it (I thought it was the USB).

I got "not authorised" after that while in that dialogue and rebooted - that's the time I should've stopped and done some research!

I tried to change it back with a live USB to boot at start but it just gives ```
nvme:nvme0: failed to set apst feature (2)
``` regardless. It then sits there for a bit before a message comes up that syslog failed to start.

---

