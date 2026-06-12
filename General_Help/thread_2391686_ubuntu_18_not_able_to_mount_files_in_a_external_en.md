---
title: "ubuntu 18 not able to mount files in a external enclosure"
date: 2018-05-12
forum: General Help
---

### Post by cubbyboy57 on 2018-05-12
I have a machine that has Ubuntu 15.10.  I have an external enclosure with 4 hard drives in it. NO raid NO zfs they are just 4 drives in the enclosure.
I bought a new hard drive and installed Ubuntu 18.04 and when I go into the file manager it shows 4 volumes.  If i click the volume I get -- unknown file system type 'zfs_member'.
If I put the disks onto the motherboard it sees them fine as ext4 partitions and mounts them.
If I put the hard drive with Ubuntu 15.10 in it sees them fine in either place.  Any ideas why?

---

### Post by dino99 on 2018-05-12
Should be nice to know the output of 'sudo blkid' and also 'journalctl -b > journal.txt' to be sure the external hardware is well reconized/supported by both ubuntu & kernel
But 15.10 is quite old, and possibly not able to support recent hardware.

---

### Post by cubbyboy57 on 2018-05-12
Thanks for getting me started - I think there is a limit to the size of the file I can attach.  I uploaded to google drive and hopefully shared the link correctly.  Let me know if there is a better way of sharing the large text.
most of the files are greek to me - I know enough to enjoy surfing and emailing from Ubuntu, not so much when it goes wrong.
Ubuntu 15
[https://drive.google.com/file/d/1p4ZjnUgB0HQJ149Jlg38Jypnb_7Vl2oZ/view?usp=sharing]("https://drive.google.com/file/d/1p4ZjnUgB0HQJ149Jlg38Jypnb_7Vl2oZ/view?usp=sharing")
Ubuntu 18
[https://drive.google.com/file/d/194rT_Ka1wR96XzvrfRYfiOK2OUsIfD5d/view?usp=sharing]("https://drive.google.com/file/d/194rT_Ka1wR96XzvrfRYfiOK2OUsIfD5d/view?usp=sharing")

output from blkid - Ubuntu15:
root@cubbyboy57-desktop:~# blkid
/dev/sda1: UUID="3f3ba85f-ddad-45b7-a60c-60ba2e566d1a" TYPE="ext2" PARTUUID="00068448-01"
/dev/sda5: UUID="MLBa3q-cYDK-nref-JGPi-oXBc-tHH8-rkPEPw" TYPE="LVM2_member" PARTUUID="00068448-05"
/dev/sda6: UUID="f46b2c58-1c88-4177-bc7b-0da1cba7a213" TYPE="ext4" PARTUUID="00068448-06"
/dev/sdb1: LABEL="DISK01" UUID="5da8c067-7e92-4a5d-8191-b1dbad5faa52" TYPE="ext4" PARTUUID="c0938f90-4f14-4fa6-a51a-cb5fbcfd8844"
/dev/sdc1: LABEL="DISK02" UUID="71b0edd2-2982-4739-aaae-f285b7760a4c" TYPE="ext4" PARTUUID="d7af3f0a-2ef1-4bf6-9dcf-d2f2e5a1a385"
/dev/sdd1: LABEL="DISK03" UUID="196f5d29-87c8-4ba4-bbdb-1c4a35e7c837" TYPE="ext4" PARTUUID="a5d5af07-ca45-4868-a7c8-ec48f9e39d13"
/dev/sde1: LABEL="DISK04" UUID="9c393c76-f0aa-41a6-958d-e36451529b4c" TYPE="ext4" PARTUUID="a7d53721-5208-42f5-af68-8af1ca91def2"
/dev/mapper/ubuntu--vg-root: UUID="b5df0d44-763d-4ea9-8628-737b6b077283" TYPE="ext4"
/dev/mapper/ubuntu--vg-swap_1: UUID="d7606f95-3a65-4a72-9b84-73af6c4fcee4" TYPE="swap"

output of blkid from ubuntu18:
root@cubbyboy57-MS-7996:~# blkid
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/sda1: UUID="1888-9A18" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="44403cf5-87ea-4e05-b731-78b06ba6581a"
/dev/sda2: UUID="31ece8bb-e21a-

Thanks again for taking your time -
james

---

### Post by cubbyboy57 on 2018-05-12
sorry i don't think the blkid for Ubuntu 18 copied correctly:
root@cubbyboy57-MS-7996:~# blkid
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/sda1: UUID="1888-9A18" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="44403cf5-87ea-4e05-b731-78b06ba6581a"
/dev/sda2: UUID="31ece8bb-e21a-4762-a298-2c7a814385a0" TYPE="ext4" PARTUUID="420c780e-7025-43d5-b7f7-79eba425703e"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/loop8: TYPE="squashfs"
/dev/loop9: TYPE="squashfs"
/dev/loop10: TYPE="squashfs"
/dev/loop11: TYPE="squashfs"

---

