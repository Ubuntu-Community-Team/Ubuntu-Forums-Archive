---
title: "I'm trying to mount a spanned partition. ldmtools not recognizing UUID"
date: 2021-07-27
forum: General Help
---

### Post by stretch4 on 2021-07-27
Hello. I have a 4TB partition across 2 2TB HDD's via Windows.

I'm trying to mount the partition (sdc1) in Kubuntu using ldmtools, but the UUID does not seem to work:

```
stretch@Marvin-Kubuntu:~$ sudo blkid
/dev/sda4: UUID="5d36ba04-64a2-4cc1-89dd-28d1f0f25721" BLOCK_SIZE="4096" TYPE="ext4" PARTUUID="16e22c58-3723-4803-9ab6-9f7592200edd"
/dev/sda1: UUID="D8BE-E8CD" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="f8fb8f22-fe7c-493f-9777-139841ef0b0f"
/dev/sda3: BLOCK_SIZE="512" UUID="FE1EC74C1EC6FD21" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="268a9547-b446-4f3f-bc00-690b4dc3d81c"
/dev/sdb2: LABEL="Backup" UUID="32B9-8E60" BLOCK_SIZE="512" TYPE="exfat" PARTLABEL="Basic data partition" PARTUUID="be4b65ad-b3e2-474c-9d22-c7e82c864e71"
/dev/sdc1: LABEL="Alpha Storage (HDD)" BLOCK_SIZE="512" UUID="C2C6A815C6A80C2B" TYPE="ntfs"
/dev/sde1: LABEL="Games" BLOCK_SIZE="512" UUID="EE90ADA790AD76AD" TYPE="ntfs" PARTUUID="ab094ce9-01"
/dev/sde2: LABEL="Skyrim" BLOCK_SIZE="512" UUID="043EFE4E3EFE37EE" TYPE="ntfs" PARTUUID="ab094ce9-02"
/dev/sda2: PARTLABEL="Microsoft reserved partition" PARTUUID="283cf900-7e77-4c89-b842-762ec087fdcd"
/dev/sdb1: PARTLABEL="Microsoft reserved partition" PARTUUID="11a25c7b-a30f-45b5-bc6c-f49762e457eb"
/dev/sdd1: PARTLABEL="LDM metadata partition" PARTUUID="afe55d0a-969a-11eb-bacb-8c89a5e0edac"
/dev/sdd2: PARTLABEL="Microsoft reserved partition" PARTUUID="afe55d0b-969a-11eb-bacb-8c89a5e0edac"
/dev/sdd3: PARTLABEL="LDM data partition" PARTUUID="afe55d0e-969a-11eb-bacb-8c89a5e0edac"
stretch@Marvin-Kubuntu:~$ ldmtool create volume C2C6A815C6A80C2B Alpha
No such disk group: C2C6A815C6A80C2B
stretch@Marvin-Kubuntu:~$ ldmtool create volume afe55d0a-969a-11eb-bacb-8c89a5e0edac Alpha
No such disk group: afe55d0a-969a-11eb-bacb-8c89a5e0edac


```

How can I get the partition mounted? Thanks!

---

### Post by yancek on 2021-07-28
You will need to be more specific about the problem than saying 'did not work'.  How did you try to mount it, what specific command and what were the exact results, errror/warning messages?  Are you manually mounting or do you have an entry in /etc/fstab to mount on boot?

---

