---
title: "WARNING: VG raid1vg is missing PV 3tzceI-HYoK-3YIo-safD-TPAI-S0ow-K9r0L1"
date: 2022-07-22
forum: General Help
---

### Post by rsteinmetz70112 on 2022-07-22
I ran a routine update on one of my computers and got these warnings:
```
WARNING: VG raid1vg is missing PV 3tzceI-HYoK-3YIo-safD-TPAI-S0ow-K9r0L1 (last written to /dev/sdg3).
WARNING: Couldn't find device with uuid 3tzceI-HYoK-3YIo-safD-TPAI-S0ow-K9r0L1.
WARNING: VG raid1vg is missing PV 3tzceI-HYoK-3YIo-safD-TPAI-S0ow-K9r0L1 (last written to /dev/sdg3).

```

There is no /dev/sdg3. /dev/sdg is a media reader which generally has not media in it.
I'm wondering if the missing PV or UUID is a problem. As you can see this is a Raid 1 on LVM. I'm not that experienced with running RAID on LVM, this is my first install of that.
 
running lsblk I get this:
```
sdc                                8:32   0   3.7T  0 disk
&#9500;&#9472;sdc1                             8:33   0     4M  0 part
&#9500;&#9472;sdc2                             8:34   0   508M  0 part
&#9492;&#9472;sdc3                             8:35   0   3.7T  0 part
  &#9500;&#9472;raid1vg-root_rmeta_0         253:7    0     4M  0 lvm
  &#9474; &#9492;&#9472;raid1vg-root               253:13   0    50G  0 lvm
  &#9500;&#9472;raid1vg-root_rimage_0        253:8    0    50G  0 lvm
  &#9474; &#9492;&#9472;raid1vg-root               253:13   0    50G  0 lvm
  &#9500;&#9472;raid1vg-tmp_rmeta_0          253:14   0     4M  0 lvm
  &#9474; &#9492;&#9472;raid1vg-tmp                253:20   0    10G  0 lvm
  &#9500;&#9472;raid1vg-tmp_rimage_0         253:15   0    10G  0 lvm
  &#9474; &#9492;&#9472;raid1vg-tmp                253:20   0    10G  0 lvm
  &#9500;&#9472;raid1vg-var_rmeta_0          253:21   0     4M  0 lvm
  &#9474; &#9492;&#9472;raid1vg-var                253:27   0    10G  0 lvm
  &#9500;&#9472;raid1vg-var_rimage_0         253:22   0    10G  0 lvm
  &#9474; &#9492;&#9472;raid1vg-var                253:27   0    10G  0 lvm
  &#9500;&#9472;raid1vg-swap_rmeta_0         253:28   0     4M  0 lvm
  &#9474; &#9492;&#9472;raid1vg-swap               253:34   0    16G  0 lvm
  &#9500;&#9472;raid1vg-swap_rimage_0        253:29   0    16G  0 lvm
  &#9474; &#9492;&#9472;raid1vg-swap               253:34   0    16G  0 lvm
  &#9500;&#9472;raid1vg-www_rmeta_0          253:35   0     4M  0 lvm
  &#9474; &#9492;&#9472;raid1vg-www                253:41   0    10G  0 lvm
  &#9500;&#9472;raid1vg-www_rimage_0         253:36   0    10G  0 lvm
  &#9474; &#9492;&#9472;raid1vg-www                253:41   0    10G  0 lvm
  &#9500;&#9472;raid1vg-home_rmeta_0         253:42   0     4M  0 lvm
  &#9474; &#9492;&#9472;raid1vg-home               253:48   0   3.6T  0 lvm   /home
  &#9492;&#9472;raid1vg-home_rimage_0        253:43   0   3.6T  0 lvm
    &#9492;&#9472;raid1vg-home               253:48   0   3.6T  0 lvm   /home
sdd                                8:48   0   3.7T  0 disk
&#9492;&#9472;sdd1                             8:49   0   3.7T  0 part  /backup
sr0                               11:0    1  1024M  0 rom
raid1vg-root_rmeta_1-missing_0_0 253:9    0     4M  0 lvm
&#9492;&#9472;raid1vg-root_rmeta_1           253:10   0     4M  0 lvm
  &#9492;&#9472;raid1vg-root                 253:13   0    50G  0 lvm
raid1vg-root_rimage_1-missing_0_0
&#9474;                                253:11   0    50G  0 lvm
&#9492;&#9472;raid1vg-root_rimage_1          253:12   0    50G  0 lvm
  &#9492;&#9472;raid1vg-root                 253:13   0    50G  0 lvm
raid1vg-tmp_rmeta_1-missing_0_0  253:16   0     4M  0 lvm
&#9492;&#9472;raid1vg-tmp_rmeta_1            253:17   0     4M  0 lvm
  &#9492;&#9472;raid1vg-tmp                  253:20   0    10G  0 lvm
raid1vg-tmp_rimage_1-missing_0_0 253:18   0    10G  0 lvm
&#9492;&#9472;raid1vg-tmp_rimage_1           253:19   0    10G  0 lvm
  &#9492;&#9472;raid1vg-tmp                  253:20   0    10G  0 lvm
raid1vg-var_rmeta_1-missing_0_0  253:23   0     4M  0 lvm
&#9492;&#9472;raid1vg-var_rmeta_1            253:24   0     4M  0 lvm
  &#9492;&#9472;raid1vg-var                  253:27   0    10G  0 lvm
raid1vg-var_rimage_1-missing_0_0 253:25   0    10G  0 lvm
&#9492;&#9472;raid1vg-var_rimage_1           253:26   0    10G  0 lvm
  &#9492;&#9472;raid1vg-var                  253:27   0    10G  0 lvm
raid1vg-swap_rmeta_1-missing_0_0 253:30   0     4M  0 lvm
&#9492;&#9472;raid1vg-swap_rmeta_1           253:31   0     4M  0 lvm
  &#9492;&#9472;raid1vg-swap                 253:34   0    16G  0 lvm
raid1vg-swap_rimage_1-missing_0_0
&#9474;                                253:32   0    16G  0 lvm
&#9492;&#9472;raid1vg-swap_rimage_1          253:33   0    16G  0 lvm
  &#9492;&#9472;raid1vg-swap                 253:34   0    16G  0 lvm
raid1vg-www_rmeta_1-missing_0_0  253:37   0     4M  0 lvm
&#9492;&#9472;raid1vg-www_rmeta_1            253:38   0     4M  0 lvm
  &#9492;&#9472;raid1vg-www                  253:41   0    10G  0 lvm
raid1vg-www_rimage_1-missing_0_0 253:39   0    10G  0 lvm
&#9492;&#9472;raid1vg-www_rimage_1           253:40   0    10G  0 lvm
  &#9492;&#9472;raid1vg-www                  253:41   0    10G  0 lvm
raid1vg-home_rmeta_1-missing_0_0 253:44   0     4M  0 lvm
&#9492;&#9472;raid1vg-home_rmeta_1           253:45   0     4M  0 lvm
  &#9492;&#9472;raid1vg-home                 253:48   0   3.6T  0 lvm   /home
raid1vg-home_rimage_1-missing_0_0
&#9474;                                253:46   0   3.6T  0 lvm
&#9492;&#9472;raid1vg-home_rimage_1          253:47   0   3.6T  0 lvm
  &#9492;&#9472;raid1vg-home                 253:48   0   3.6T  0 lvm   /home
```

Running blkid I get this:

```
/dev/sda1: UUID="07950f05-69cb-75e8-1e0e-fbd20d73f6b2" UUID_SUB="f1b89b85-3ddb-14a7-8813-5dfc5045b0f9" LABEL="thelma:126" TYPE="linux_raid_member" PARTUUID="282315a5-01"
/dev/sdb1: UUID="07950f05-69cb-75e8-1e0e-fbd20d73f6b2" UUID_SUB="8be2faea-9852-95f6-5fd6-75897d92f6ee" LABEL="thelma:126" TYPE="linux_raid_member" PARTUUID="fe30e08a-01"
/dev/sdc1: UUID="17BB-A778" TYPE="vfat" PARTLABEL="primary" PARTUUID="51c64cde-77d4-499d-b810-011d709feddc"
/dev/sdc2: UUID="183F-32EF" TYPE="vfat" PARTLABEL="primary" PARTUUID="b5a9973e-1e5d-45a9-86f2-f593ed5b68c2"
/dev/sdc3: UUID="2gSWoZ-FlTK-AYY3-SRhx-rUNT-sFU1-3GwyXH" TYPE="LVM2_member" PARTLABEL="primary" PARTUUID="1b2bffc3-3b02-4a2a-8465-c47802e82bd8"
/dev/sdd1: UUID="dd9fb1f9-fcfd-482e-9c92-eb18a665c686" TYPE="ext4" PARTUUID="bfdc701d-6b1e-4d18-9016-b3b5b3698aa0"
/dev/md126: UUID="TAFsTI-tnBp-lcYZ-ABeQ-l51Y-30jL-CN1Phr" TYPE="LVM2_member"
/dev/mapper/system-tmp: UUID="29867bcd-b08b-429b-af7b-9ba0a02d82dd" TYPE="ext4"
/dev/mapper/system-var: UUID="4730d2da-eb0e-47c2-bedd-3d18d3353895" TYPE="ext4"
/dev/mapper/system-www: UUID="441b1552-4f70-4785-85fc-619bef359543" TYPE="ext4"
/dev/mapper/system-home: UUID="4baa4062-f4ad-4d27-97ad-a6c2e328d434" TYPE="ext4"
/dev/mapper/system-xtra: UUID="3d2ff784-8463-4a11-b328-c347a6b12e97" TYPE="ext4"
/dev/mapper/raid1vg-root_rimage_0: UUID="baf499b7-0b5a-4ac1-8436-f0d25593f581" TYPE="ext4"
/dev/mapper/raid1vg-root: UUID="baf499b7-0b5a-4ac1-8436-f0d25593f581" TYPE="ext4"
/dev/mapper/raid1vg-tmp_rimage_0: UUID="61ce988c-b525-4553-b159-f4cfc15efc90" TYPE="ext4"
/dev/mapper/raid1vg-tmp: UUID="61ce988c-b525-4553-b159-f4cfc15efc90" TYPE="ext4"
/dev/mapper/raid1vg-var_rimage_0: UUID="c0349bf8-7c7d-42d4-a722-a0237ed9419e" TYPE="ext4"
/dev/mapper/raid1vg-var: UUID="c0349bf8-7c7d-42d4-a722-a0237ed9419e" TYPE="ext4"
/dev/mapper/raid1vg-www_rimage_0: UUID="790a61a7-d82a-421a-97c5-a5692f311f44" TYPE="ext4"
/dev/mapper/raid1vg-www: UUID="790a61a7-d82a-421a-97c5-a5692f311f44" TYPE="ext4"
/dev/mapper/raid1vg-home_rimage_0: UUID="9e15b793-e60e-4b95-a647-b5c241ba7313" TYPE="ext4"
/dev/mapper/raid1vg-home: UUID="9e15b793-e60e-4b95-a647-b5c241ba7313" TYPE="ext4"

```

---

### Post by #&amp;thj^% on 2022-07-22
Have you tried the tool "vgck", which checks volume group metadata, and can correct it with the "--updatemetadata" option.
I'd try to update the meta with:
"sudo vgck --updatemetadata <your volume group>" and use the actual volume group name from your own specific error.

---

### Post by rsteinmetz70112 on 2022-07-22
Thanks

```
# vgck
  WARNING: Couldn't find device with uuid 3tzceI-HYoK-3YIo-safD-TPAI-S0ow-K9r0L1.
  WARNING: VG raid1vg is missing PV 3tzceI-HYoK-3YIo-safD-TPAI-S0ow-K9r0L1 (last written to /dev/sdg3).
  The volume group is missing 1 physical volumes.
```

As you can see vgck gives pretty much the same warning but adds that there is a missing volume.
I think this may be left over from when I updated the hard drives and at one time had 2 more drives In the computer when I copied the data over to the new drives. 
It looks like one of the two new drives is not working or is disconnected. There should be 2 4TB drives in a Raid 1 array. 

lsblk lists all of the lv, but doesn't show one of the drives, which should be either /dev/sdd or /dev/sde. 
pvs shows the pv without a drive letter.

```
# pvs
  WARNING: Couldn't find device with uuid 3tzceI-HYoK-3YIo-safD-TPAI-S0ow-K9r0L1.
  WARNING: VG raid1vg is missing PV 3tzceI-HYoK-3YIo-safD-TPAI-S0ow-K9r0L1 (last written to /dev/sdg3).
  PV         VG      Fmt  Attr PSize   PFree
  /dev/md126 system  lvm2 a--  931.38g    0
  /dev/sdc3  raid1vg lvm2 a--   <3.64t    0
**  [unknown]  raid1vg lvm2 a-m   <3.64t    0**

```
OK I checked all of the connections and rebooted and now vgck shows nothing and pvs shows this:

```
# pvs
  PV         VG      Fmt  Attr PSize   PFree
  /dev/md126 system  lvm2 a--  931.38g    0
  /dev/sdb3  raid1vg lvm2 a--   <3.64t    0
  /dev/sdd3  raid1vg lvm2 a--   <3.64t    0

```

Since I'm running one PV on an MD device and one array on LVM,  I'm a little surprised to see two PVs for the same VG

---

### Post by #&amp;thj^% on 2022-07-22
How was the return from 'update-grub' command?
have you ran that yet? And I agree left-overs are a strong possibility.

---

### Post by rsteinmetz70112 on 2022-07-22
I never ran the update-grub. I now think there was a bad connection/loose cable on one of the drives. Checking the cables and rebooting seems to have cleared the problem. I'll watch it and see if it recurs.

---

### Post by #&amp;thj^% on 2022-07-22
Yep it sometimes takes that restart to really see the true outcome...:)
Glad to hear things are good for now....a little learning curve is all.:D

---

