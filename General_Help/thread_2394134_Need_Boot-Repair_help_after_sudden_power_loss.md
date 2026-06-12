---
title: "Need Boot-Repair help after sudden power loss"
date: 2018-06-12
forum: General Help
---

### Post by wildfirecats on 2018-06-12
Hi guys,

 Boot repair summary: [http://paste.ubuntu.com/p/5PVr43YGRT/](http://paste.ubuntu.com/p/5PVr43YGRT/)

 I have a single Ubuntu 16.04 LTS installation on the only harddrive in my system. I have only one harddrive and one OS. 

 Everything was working fine until a sudden power outage. The power loss lead to the loss of all BIOS settings (dead battery). After re-configuring everything in BIOS, I can only boot into the GRUB2 CLI prompt. 

 I booted by Ubuntu 16.04  USB into a live CD system and installed [Boot Repair]("https://sourceforge.net/p/boot-repair/home/Home/") and tried the  "Recommended Repair", but after it successfully completes and  reboots, I still get booted into the same GRUB2 CLI prompt. I tried the "Recommended Repair" twice and nothing has changed as far as I can tell. 

 Thank you in advance for all your help.

---

### Post by Cavsfan on 2018-06-13
Boot into a live session of Ubuntu LiveCD 

Open terminal and run **sudo fdisk -l**  or **sudo blkid** to see where Linux is installed on

Run **sudo mount /dev/sdxY /mnt** where x is letter and Y a number you have found in the previous step

Run **sudo grub-install --root-directory=/mnt/dev/sdx** to install grub

Run **sudo update-grub** to update grub

Reboot

---

### Post by Cavsfan on 2018-06-13
If you've got one hard drive and 2-3 partitions. This should be fairly easy to figure out.

**sudo mount /dev/sda1 /mnt** or **sudo mount /dev/sda2 /mnt **etc.

Then [B]sudo grub-install --root-directory=/mnt/dev/sda

[/B][Reinstalling GRUB 2 from a Working System]("https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2_from_a_Working_System")

---

### Post by wildfirecats on 2018-06-14
Thanks, guys. 

```
Device             Start       End   Sectors   Size Type
/dev/nvme0n1p1      2048    110591    108544    53M EFI System
/dev/nvme0n1p2    110592  40060927  39950336  19.1G Linux filesystem
/dev/nvme0n1p3  40060928 498089983 458029056 218.4G Linux filesystem
/dev/nvme0n1p4 498089984 500117503   2027520   990M Linux swap
```

My OS partition is /dev/nvme0n1p2 so I ran the following on the liveCD:

```
ubuntu@ubuntu:~$ sudo mount /dev/nvme0n1p2 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/dev/nvme0n1p2
Installing for i386-pc platform.
grub-install: error: install device isn't specified.
```

Seems like the mount failed because **/mnt/dev/nvme0n1p2** doesn't exist after mount.

Please advise.

---

### Post by Cavsfan on 2018-06-16
> **wildfirecats said:**
> Thanks, guys. 

```
Device             Start       End   Sectors   Size Type
/dev/nvme0n1p1      2048    110591    108544    53M EFI System
/dev/nvme0n1p2    110592  40060927  39950336  19.1G Linux filesystem
/dev/nvme0n1p3  40060928 498089983 458029056 218.4G Linux filesystem
/dev/nvme0n1p4 498089984 500117503   2027520   990M Linux swap
```

My OS partition is /dev/nvme0n1p2 so I ran the following on the liveCD:

```
ubuntu@ubuntu:~$ sudo mount /dev/nvme0n1p2 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/dev/nvme0n1p2
Installing for i386-pc platform.
grub-install: error: install device isn't specified.
```

Seems like the mount failed because **/mnt/dev/nvme0n1p2** doesn't exist after mount.

Please advise.

How did you get that list? It doesn't specify. But, I've got the same EFI partitioning.
As you can see I have Arch Linux, Xenial Xerus 16.04 LTS, Bionic Beaver 18.04 LTS, Cosmic Cuttlefish 18.10 and Debian Sid installed in EFI mode.
I've had grub installed on each one at one time.
I am currently on Debian Sid:

```
cavsfan@Debian:~$ sudo blkid | grep sdc
/dev/sdc1: UUID="688D-126B" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="3c1b6d6f-8a24-43da-b595-8c304ceee48d"
/dev/sdc3: UUID="C4968A52968A44C0" TYPE="ntfs" PARTLABEL="Windows_10" PARTUUID="345c85f4-bce7-4bc7-bbe0-db03eb319cad"
/dev/sdc4: UUID="701AE4631AE427B4" TYPE="ntfs" PARTUUID="1e337754-b45d-45a5-a971-b8cdcae8a002"
/dev/sdc5: UUID="287deb24-5e5d-481e-b5d4-fa9d4b796987" TYPE="swap" PARTLABEL="Basic data partition" PARTUUID="3a259867-656d-41ed-9931-cf15a3bd0148"
/dev/sdc6: LABEL="ArchLinux" UUID="bbca28b2-503e-4dc8-9850-c54bd0492da8" TYPE="ext4" PARTLABEL="Arch_Linux" PARTUUID="5312b771-0835-4957-80a6-9a8a7107f24a"
/dev/sdc7: LABEL="Xenial" UUID="904400cd-3311-4504-b422-ad01c0701253" TYPE="ext4" PARTLABEL="Xenial_Xerus" PARTUUID="57075798-adb7-4590-ae23-6a75d976c3c1"
/dev/sdc8: LABEL="Bionic" UUID="21cf477b-a314-4691-85f6-256e6209d5d9" TYPE="ext4" PARTLABEL="Bionic_Beaver" PARTUUID="c4e0fdc9-7eac-4661-a7c6-c5a00c9a46fc"
/dev/sdc9: LABEL="Cosmic" UUID="cb979c41-6dc8-4ca3-ac8a-a13b5c98fee0" TYPE="ext4" PARTLABEL="Cosmic" PARTUUID="5ee7c2ec-94f5-4864-bf22-9c9aec1c09e4"
/dev/sdc10: LABEL="Media" UUID="840ac879-510a-4b8d-be01-9d3a5f37dbb2" TYPE="ext4" PARTLABEL="Media" PARTUUID="61e2e7f9-1a98-44f7-881e-ae85fceaf994"
/dev/sdc11: LABEL="Debian" UUID="e2be3614-25b0-4549-8271-d3a867993282" TYPE="ext4" PARTUUID="bb68b062-1297-4f3c-a3c1-801fc27324d0"
/dev/sdc2: PARTLABEL="Microsoft reserved partition" PARTUUID="49992d5b-79cd-4934-a12f-11782bb345bd"

```

So it should be like a **/dev/sda** and not **/dev/nvme0n1p2 **one would think.

What is the output of **sudo blkid**&#8203;?

---

### Post by oldfred on 2018-06-16
This is missing a space between /mnt & /dev/nvme0n1p2
sudo grub-install --root-directory=/mnt/dev/nvme0n1p2

You also may need fsck on all your Linux partitions.

 To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

In your case, the /dev/sdb1 example will be more like the /dev/nvme0n1p2  and then do again with partition  p3 as NVMe drives use different naming.

---

