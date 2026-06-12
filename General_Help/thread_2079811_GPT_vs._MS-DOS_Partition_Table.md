---
title: "GPT vs. MS-DOS Partition Table"
date: 2012-11-02
forum: General Help
---

### Post by Slug71 on 2012-11-02
I know this is an old thread but im having issues relating to this. I've tried installing both 12.04 and 12.10 with BTRFS(both / and /home) on my test rig as well as my Netbook and both fail to install Grub2. When I access the install via the LiveCD and try to install Grub2 manually, I get "core.img is unually large" and it doesn't install.

My partitions are showing as ms-dos so I know they are not GPT. Any reason why this is happening and will a BIOS-boot partition help like id does with a GPT partition table?

---

### Post by oldfred on 2012-11-02
Moved you from 2 year old thread. While on gpt vs. MBR it was more to do with burg.

You have to have space after the MBR for core.img. When using gparted to create partitions the first sector should be 2048 which then is lots of room for core.img after MBR. Perhaps the extra add in modules for your BTRFS needs extra room?

You are not trying to install grub to PBR - partition boot sector are you. That always give that error as core.img does not fit.

You have to use gpt if you want a bios_grub partition. But you cannot use gpt with Windows unless booting with UEFI.

I have gpt on my 160GB drive and even a 16GB flash drive with bios_grub partitions. I only use ext3 or ext4 but I do not think formatting makes a difference.

Post this:

sudo parted /dev/sda unit s print

---

### Post by Slug71 on 2012-11-03
> **oldfred said:**
> Moved you from 2 year old thread. While on gpt vs. MBR it was more to do with burg.

You have to have space after the MBR for core.img. When using gparted to create partitions the first sector should be 2048 which then is lots of room for core.img after MBR. Perhaps the extra add in modules for your BTRFS needs extra room?

You are not trying to install grub to PBR - partition boot sector are you. That always give that error as core.img does not fit.

You have to use gpt if you want a bios_grub partition. But you cannot use gpt with Windows unless booting with UEFI.

I have gpt on my 160GB drive and even a 16GB flash drive with bios_grub partitions. I only use ext3 or ext4 but I do not think formatting makes a difference.

Post this:

sudo parted /dev/sda unit s print

Thanks oldfred. This is all new to me regarding HDD's partition formats.

The output of the above gives me


> Model: ATA WDC WD3200AAKS-0 (scsi)
Disk /dev/sda: 625142448s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start       End         Size        Type      File system     Flags
 1      63s         39070079s   39070017s   primary   fat32           boot, lba
 2      39070080s   78140159s   39070080s   primary   freebsd-ufs
 3      78140160s   117210239s  39070080s   primary   ext4
 4      117210301s  625137344s  507927044s  extended
 5      117210303s  125402302s  8192000s    logical   linux-swap(v1)
 6      125402304s  156122302s  30719999s   logical   ext4
 7      156122304s  176602302s  20479999s   logical   ext4
 8      176602608s  200041379s  23438772s   logical   ext4
 9      200041443s  217616489s  17575047s   logical   ext4
10      217616553s  246919049s  29302497s   logical   ext4
11      246919113s  266454089s  19534977s   logical   ext4
12      266454153s  295756649s  29302497s   logical   btrfs
13      295756713s  315291689s  19534977s   logical   btrfs
14      315291753s  344594249s  29302497s   logical   ext3
15      344594313s  364129289s  19534977s   logical   ext3
16      364129353s  393431849s  29302497s   logical   ext4
17      393431913s  412966889s  19534977s   logical   ext4
18      412966953s  442269449s  29302497s   logical   ext4
19      442269513s  461804489s  19534977s   logical   ext4
20      461804553s  491107049s  29302497s   logical   ext4
21      491107113s  510642089s  19534977s   logical   ext4
22      510642153s  539944649s  29302497s   logical   ext4
23      539944713s  559479689s  19534977s   logical   ext4
24      559479753s  588782249s  29302497s   logical   ext4
25      588782313s  625137344s  36355032s   logical   ext4

1 = ReactOS
2 = PC-BSD
3 = Open Solaris

The rest is Ubuntu, Kubuntu, Xubuntu, OpenSUSE, Fedora, Mandrake, Foresight, Mint and Crunchbang. Not in that order.

---

### Post by oldfred on 2012-11-03
Your first partition is at sector 63 which is the old standard. So maybe with your unusually large core.img it is a problem. What is in FAT32 sda1. I do not like moving partitions start, but you may have to, if it is not full. You would have to shrink it then move it right so start is 2048 or more. Sometimes gparted may round.

---

### Post by Slug71 on 2012-11-03
> **oldfred said:**
> Your first partition is at sector 63 which is the old standard. So maybe with your unusually large core.img it is a problem. What is in FAT32 sda1. I do not like moving partitions start, but you may have to, if it is not full. You would have to shrink it then move it right so start is 2048 or more. Sometimes gparted may round.

Thanks oldfred. Its ReactOS. I can move it since I need to do a reinstall anyway.

---

