---
title: "fstab and the pass field (fsck order): A discussion"
date: 2023-08-25
forum: General Help
---

### Post by Paddy Landau on 2023-08-25
I've found conflicting information on the 'net when looking for the precise meaning of the *pass* field in [FONT=courier new]/etc/fstab[/FONT].

Part of the reason seems to be that the treatment of the *pass* flag [is inconsistent]("https://unix.stackexchange.com/a/547660/41226") across implementations.

From what I can tell…

[LIST]
[*]Zero always means not to check the partition.
[*]On some implementations, non-zero values indicate the order in which to check: first 1, then 2, then 3, and so on. If multiple partitions have the same number, they are checked in parallel if on separate physical drives, otherwise the system decides the order.
[*]On some implementations, numbers greater than 2 are treated as 2.
[*]On some implementations, all non-zero values are treated as 1.
[/LIST]
I'd like to know, purely for interest, which of the implementations applies to Ubuntu — if anyone actually knows! Given that the implementation often changes it might even be different between even recent versions.

The most common advice seems to be to set root to use 1 and other partitions to use 2. You would use 0 for swap, RAM disks, removable media, bind mounts, etc.

Of course, some of the advice is based on "traditional" set-ups, and those set-ups are still in common use.

Given that we now increasingly use two extra important partitions, specifically ESP (the EFI System Partition) and [FONT=courier new]/boot[/FONT] when using encrypted drives on Secure Boot systems, I suggest that we should change the advice to say:

[LIST]
[*]Use 1 for ESP, [FONT=courier new]/boot[/FONT] and root partitions.
[*]Use 2 for the remaining internal partitions.
[/LIST]
What do you think?

---

### Post by #&amp;thj^% on 2023-08-25
> **Paddy Landau said:**
> I've found conflicting information on the 'net when looking for the precise meaning of the *pass* field in [FONT=courier new]/etc/fstab[/FONT].
```
 man fstab | grep pass
   The sixth field (fs_passno).
       specified with a fs_passno of 1. Other filesystems should have a
       fs_passno of 2. Filesystems within a drive will be checked

```
> **Paddy Landau said:**
> 
Part of the reason seems to be that the treatment of the *pass* flag [is inconsistent]("https://unix.stackexchange.com/a/547660/41226") across implementations.

From what I can tell…

[LIST]
[*]Zero always means not to check the partition.
[*]On some implementations, non-zero values indicate the order in which to check: first 1, then 2, then 3, and so on. If multiple partitions have the same number, they are checked in parallel if on separate physical drives, otherwise the system decides the order.
[*]On some implementations, numbers greater than 2 are treated as 2.
[*]On some implementations, all non-zero values are treated as 1.
[/LIST]
I'd like to know, purely for interest, which of the implementations applies to Ubuntu — if anyone actually knows! Given that the implementation often changes it might even be different between even recent versions.

The most common advice seems to be to set root to use 1 and other partitions to use 2. You would use 0 for swap, RAM disks, removable media, bind mounts, etc.

Of course, some of the advice is based on "traditional" set-ups, and those set-ups are still in common use.

Given that we now increasingly use two extra important partitions, specifically ESP (the EFI System Partition) and [FONT=courier new]/boot[/FONT] when using encrypted drives on Secure Boot systems, I suggest that we should change the advice to say:

[LIST]
[*]Use 1 for ESP, [FONT=courier new]/boot[/FONT] and root partitions.
[*]Use 2 for the remaining internal partitions.
[/LIST]
What do you think?
I do like your suggestions though.
The rest can be read at "man fstab"

---

### Post by MAFoElffen on 2023-08-25
> **Paddy Landau said:**
> IThe most common advice seems to be to set root to use 1 and other partitions to use 2. You would use 0 for swap, RAM disks, removable media, bind mounts, etc.

Of course, some of the advice is based on "traditional" set-ups, and those set-ups are still in common use.

Given that we now increasingly use two extra important partitions, specifically ESP (the EFI System Partition) and [FONT=courier new]/boot[/FONT] when using encrypted drives on Secure Boot systems, I suggest that we should change the advice to say:

[LIST]
[*]Use 1 for ESP, [FONT=courier new]/boot[/FONT] and root partitions. 
[*]Use 2 for the remaining internal partitions. 
[/LIST]
What do you think?
That is the rule of thumb I follow.

With how you word that, I treat ZFS and BTRFS as not traditional. 

ZFS has it's own mounts into a filesystem. BTRFS is mounted through fstab. Both have their own type of file check utility, which is not fsck, and they are both not compatible with fsck. So if in the fstab, I warn Users to use "0" in the pass field, so that fsck is not used on them at boot. That *would* cause a problem.

---

### Post by Paddy Landau on 2023-08-26
> **1fallen said:**
> man fstab…
From what I've read on the net, not all of them say exactly the same thing. But also, it seems as though that advice might be a tad out of date?
> **MAFoElffen said:**
> ZFS … BTRFS … I warn Users to use "0" in the pass field, so that fsck is not used on them at boot. That *would* cause a problem.
Now, that's strange that this isn't catered for! I've never used ZFS or BTRFS, but I might do so someday, so I'll add this to my documentation. Shouldn't this be reported as a bug, i.e. fsck should pass such a request to the correct utility? What other file systems would be similarly affected?

---

### Post by MAFoElffen on 2023-08-26
Dang I was wrong... Sort of... LOL 

fsck.brtfs does work with BTRFS. But the man page and doc's still recommend setting the pass field to 0.
RE man fsck.btrfs: [https://manpages.ubuntu.com/manpages/jammy/en/man8/fsck.btrfs.8.html](https://manpages.ubuntu.com/manpages/jammy/en/man8/fsck.btrfs.8.html)
> 
fsck.btrfs is a type of utility that should exist for any filesystem and is called during system setup when the corresponding /etc/fstab entries contain non-zero value for fs_passno , see fstab(5) for more.

Traditional filesystems need to run their respective fsck utility in case the filesystem was not unmounted cleanly and the log needs to be replayed before mount. This is not needed for BTRFS. [COLOR=#ff0000]You should set fs_passno to 0.[/COLOR]

If you wish to check the consistency of a BTRFS filesystem or repair a damaged filesystem, see btrfs-check(8). By default the filesystem consistency is checked, the repair mode is enabled via --repair option (use with care!).

Most of the time, we recommend people to use brtfs check
RE: man page btrfs-check -- [https://manpages.ubuntu.com/manpages/jammy/en/man8/btrfs-check.8.html](https://manpages.ubuntu.com/manpages/jammy/en/man8/btrfs-check.8.html)

With ZFS, you use 
```

sudo zpool scrub <pool_name>

```
ZFS uses it's "own" mounts for pools, and a combination of what is mounted in the pool mounts and what is in the fstab. If you only look at the fstab, you are going to get lost. 

For example, this is the output from lsblk (showing mountpints) and the active lines in the fstab in my laptop:
```

mafoelffen@Mikes-ThinkPad-T520:~$ lsblk -e7 -o name,label,size,fstype,mountpoint,model
NAME     LABEL       SIZE FSTYPE     MOUNTPOINT MODEL
sda                  1.8T                       Samsung SSD 870 QVO 2TB
&#9500;&#9472;sda1   {SYSTEM}    550M vfat       /boot/efi  
&#9500;&#9472;sda2               128M                       
&#9500;&#9472;sda3   {Windows}   900G ntfs                  
&#9500;&#9472;sda4               983M                       
&#9500;&#9472;sda5                30G                       
&#9500;&#9472;sda6                32G                       
&#9474; &#9492;&#9472;swap swap         32G swap       [SWAP]     
&#9500;&#9472;sda7   bpool         2G zfs_member            
&#9500;&#9472;sda8   rpool       500G zfs_member            
&#9492;&#9472;sda9   hpool     397.4G zfs_member            
sdb                  1.8T                       Samsung SSD 870 QVO 2TB
&#9500;&#9472;sdb1   kpool      1000G zfs_member            
&#9492;&#9472;sdb2   dpool       863G zfs_member            
sdc                  1.8T                       Dogfish SSD 2TB
&#9492;&#9472;sdc1   backups     1.5T zfs_member            
mafoelffen@Mikes-ThinkPad-T520:~$ grep -v '#' /etc/fstab
/dev/disk/by-uuid/281F-B438 /boot/efi vfat defaults,umask=0077 0 1
/boot/efi/grub /boot/grub none defaults,bind 0 0
/dev/mapper/swap none swap defaults 0 0

```
Doesn't look like much is there and just shows 3 of the many mounts. Whereas this output reveals a different story:
```

mafoelffen@Mikes-ThinkPad-T520:~$ sudo zfs list
[sudo] password for mafoelffen: 
NAME                                               USED  AVAIL     REFER  MOUNTPOINT
backups                                            224G  1.20T       96K  /zfs-backups
backups/BACKUPS                                    224G  1.20T       96K  none
backups/BACKUPS/ubuntu_2204                        224G  1.20T       96K  /zfs-backups
backups/BACKUPS/ubuntu_2204/images-vm              224G  1.20T       96K  /zfs-backups/images-vm
backups/BACKUPS/ubuntu_2204/images-vm/2023-07-25   224G  1.20T      224G  /zfs-backups/images-vm/2023-07-25
bpool                                              437M  1.32G       96K  /boot
bpool/BOOT                                         437M  1.32G       96K  none
bpool/BOOT/ubuntu_2204                             437M  1.32G      437M  /boot
dpool                                             1.68M   829G       96K  /dpool
dpool/DATA                                         192K   829G       96K  none
dpool/DATA/ubuntu_2204                              96K   829G       96K  /dpool
hpool                                             50.2G   333G       96K  /home
hpool/USERDATA                                    50.2G   333G       96K  none
hpool/USERDATA/root_2204                          2.86G   333G     2.86G  /root
hpool/USERDATA/ubuntu_2204                        47.3G   333G     47.3G  /home
kpool                                              409G   552G       96K  /kpool
kpool/QEMU-KVM                                     409G   552G       96K  none
kpool/QEMU-KVM/ubuntu_2204                         409G   552G       96K  /kpool
kpool/QEMU-KVM/ubuntu_2204/ISO                     185G   552G      185G  /home/mafoelffen/Downloads/ISO
kpool/QEMU-KVM/ubuntu_2204/images                  224G   552G      224G  /var/lib/libvirt/images
kpool/QEMU-KVM/ubuntu_2204/libvirt                 528K   552G      528K  /etc/libvirt/
rpool                                             23.4G   457G       96K  /
rpool/ROOT                                        23.4G   457G       96K  none
rpool/ROOT/ubuntu_2204                            23.4G   457G     8.03G  /
rpool/ROOT/ubuntu_2204/srv                          96K   457G       96K  /srv
rpool/ROOT/ubuntu_2204/tmp                         332K   457G      332K  /tmp
rpool/ROOT/ubuntu_2204/usr                        3.18G   457G       96K  /usr
rpool/ROOT/ubuntu_2204/usr/local                  3.18G   457G     3.18G  /usr/local
rpool/ROOT/ubuntu_2204/var                        12.2G   457G       96K  /var
rpool/ROOT/ubuntu_2204/var/cache                   611M   457G      611M  /var/cache
rpool/ROOT/ubuntu_2204/var/games                    96K   457G       96K  /var/games
rpool/ROOT/ubuntu_2204/var/lib                    6.93G   457G     6.78G  /var/lib
rpool/ROOT/ubuntu_2204/var/lib/AccountsService     112K   457G      112K  /var/lib/AccountsService
rpool/ROOT/ubuntu_2204/var/lib/NetworkManager      460K   457G      460K  /var/lib/NetworkManager
rpool/ROOT/ubuntu_2204/var/lib/apt                 100M   457G      100M  /var/lib/apt
rpool/ROOT/ubuntu_2204/var/lib/docker               96K   457G       96K  /var/lib/docker
rpool/ROOT/ubuntu_2204/var/lib/dpkg               59.3M   457G     59.3M  /var/lib/dpkg
rpool/ROOT/ubuntu_2204/var/lib/nfs                 104K   457G      104K  /var/lib/nfs
rpool/ROOT/ubuntu_2204/var/log                     625M   457G      625M  /var/log
rpool/ROOT/ubuntu_2204/var/mail                     96K   457G       96K  /var/mail
rpool/ROOT/ubuntu_2204/var/snap                   3.59G   457G     3.59G  /var/snap
rpool/ROOT/ubuntu_2204/var/spool                   328K   457G      328K  /var/spool
rpool/ROOT/ubuntu_2204/var/tmp                     452M   457G      452M  /var/tmp
rpool/ROOT/ubuntu_2204/var/www                      96K   457G       96K  /var/www

```
All mine have two cron jobs that run once a month for scrub and trim. I acually run scrubs on my pools once a week for my own maintenance on my machines. 3 out of my 4 machines here are ZFS-On-Root. The one that isn't, is a Raspberry Pi4 that I have booting from an NVMe drive. When I get some time, I have plans to migrate that one to ZFS.

The big difference and plus to scrub over fsck types of file system checkers/repair tools, is that a scrub job runs on a mounted, live filesystem...

---

### Post by Paddy Landau on 2023-08-26
OK, that is interesting! I didn't realise how complex ZFS would be.

---

### Post by MAFoElffen on 2023-08-26
> **Paddy Landau said:**
> OK, that is interesting! I didn't realize how complex ZFS would be.
Well, lets say: adaptable and flexible.

My configs are a bit more complex than the basic configuration. That is an understatement. I tend to push things to the limits, exploiting what is possible. My configs are not "basic". The Ubuntu default install template config has 2 pools: rpool and bpool. Where everything "/" is lumped into rpool, and /boot split out to /bpool. That makes things for Grub2 easier in the boot process. The datasets under that are split out, so during snapshots, important pieces are snapshoted so that the system can be restored to a certain point of time, without backing up trivial things.

The datasets in the pools could just be one... But If you do split them out further, it gives you more options to do things. Of course, I do like to separate further, so that I isolate my /home, /data, KVM virtual machines & backups. That way, when I do a migration, I can reiinstall a new release and just migrate the other pieces.

That machine install is actually less complex than my server, and my workstation, that both involve many more drives, and RAIDz... They follow the same basic framework pattern.

With ZFS- There is a learning curve. Once understood, lots of things can be changed to adapt to to different things... Usually on a live filesystem. 

My server:
```

mafoelffen@Mikes-B460M:~$ lsblk -e7 -o name,label,size,fstype,mountpoint,model
NAME        LABEL      SIZE FSTYPE     MOUNTPOINT MODEL
sda                    1.8T                       Samsung SSD 870 EVO 2TB
&#9492;&#9472;sda1      datapool   1.8T zfs_member            
sdb                    1.8T                       Samsung SSD 870 EVO 2TB
&#9492;&#9472;sdb1      datapool   1.8T zfs_member            
sdc                    1.8T                       Samsung SSD 870 EVO 2TB
&#9492;&#9472;sdc1      datapool   1.8T zfs_member            
sdd                  476.9G                       Crucial_CT512MX100SSD1
&#9500;&#9472;sdd1                  16M ext4                  
&#9500;&#9472;sdd2               476.3G ntfs                  
&#9492;&#9472;sdd3                 607M ntfs                  
sde                    1.8T                       Samsung SSD 870 EVO 2TB
&#9492;&#9472;sde1      datapool   1.8T zfs_member            
sdf                    1.8T                       Samsung SSD 870 EVO 2TB
&#9492;&#9472;sdf1      datapool   1.8T zfs_member            
nvme0n1                1.8T                       Samsung SSD 970 EVO Plus 2TB
&#9492;&#9472;nvme0n1p1 kpool      1.8T zfs_member            
nvme3n1                1.8T                       Samsung SSD 970 EVO Plus 2TB
&#9492;&#9472;nvme3n1p1 kpool      1.8T zfs_member            
nvme1n1                1.8T                       Samsung SSD 970 EVO Plus 2TB
&#9492;&#9472;nvme1n1p1 kpool      1.8T zfs_member            
nvme2n1                1.8T                       Samsung SSD 970 EVO Plus 2TB
&#9492;&#9472;nvme2n1p1 kpool      1.8T zfs_member            
nvme5n1              931.5G                       WD Blue SN570 1TB
&#9500;&#9472;nvme5n1p1            512M vfat       /boot/efi  
&#9500;&#9472;nvme5n1p2              2G swap       [SWAP]     
&#9500;&#9472;nvme5n1p3 bpool        2G zfs_member            
&#9492;&#9472;nvme5n1p4 rpool      927G zfs_member            
nvme6n1                1.8T                       Samsung SSD 970 EVO Plus 2TB
&#9492;&#9472;nvme6n1p1 datapool  1000G zfs_member            
nvme4n1     datapool   1.8T zfs_member            Samsung SSD 970 EVO 2TB
&#9500;&#9472;nvme4n1p1            1.3T zfs_member            
&#9492;&#9472;nvme4n1p2 datapool    10G zfs_member            
mafoelffen@Mikes-B460M:~$ 
mafoelffen@Mikes-B460M:~$ sudo zpool status -v datapool kpool
  pool: datapool
 state: ONLINE
  scan: scrub repaired 0B in 00:16:02 with 0 errors on Sun Aug 13 00:40:03 2023
config:

    NAME                                                   STATE     READ WRITE CKSUM
    datapool                                               ONLINE       0     0     0
      raidz2-0                                             ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA09560A-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA11601H-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TA47393M-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNS0W330507J-part1  ONLINE       0     0     0
        ata-Samsung_SSD_870_EVO_2TB_S6PNNM0TB08933B-part1  ONLINE       0     0     0
    logs    
      nvme-Samsung_SSD_970_EVO_2TB_S464NB0KB10521K-part2   ONLINE       0     0     0
    cache
      nvme-Samsung_SSD_970_EVO_2TB_S464NB0KB10521K-part1   ONLINE       0     0     0

errors: No known data errors

  pool: kpool
 state: ONLINE
  scan: scrub repaired 0B in 00:07:43 with 0 errors on Sun Aug 13 00:31:45 2023
config:

    NAME                                 STATE     READ WRITE CKSUM
    kpool                                ONLINE       0     0     0
      raidz2-0                           ONLINE       0     0     0
        nvme-eui.0025385a2140bd61-part1  ONLINE       0     0     0
        nvme-eui.0025385a21418769-part1  ONLINE       0     0     0
        nvme-eui.0025385a2141f4fc-part1  ONLINE       0     0     0
        nvme-eui.0025385b21407ef0-part1  ONLINE       0     0     0

errors: No known data errors
mafoelffen@Mikes-B460M:~$ zfs list
NAME                                               USED  AVAIL     REFER  MOUNTPOINT
bpool                                              302M  1.46G       96K  /boot
bpool/BOOT                                         301M  1.46G       96K  none
bpool/BOOT/ubuntu_2cwpns                           301M  1.46G      301M  /boot
datapool                                           939G  3.81T      307K  /data
datapool/DATA                                      938G  3.81T      307K  none
datapool/DATA/ubuntu_2cwpns                        938G  3.81T     10.0G  /data
datapool/DATA/ubuntu_2cwpns/ISO                    405G  3.81T      405G  /data/ISO
datapool/DATA/ubuntu_2cwpns/KVM-VM                 523G  3.81T      523G  /data/KVM-VM
kpool                                             1.56T  1.85T      279K  /KVM_Pool
kpool/KVM                                         1.56T  1.85T      279K  none
kpool/KVM/ubuntu_2cwpns                           1.56T  1.85T     1.56T  /KVM_Pool
rpool                                             16.3G   875G       96K  /
rpool/ROOT                                        14.3G   875G       96K  none
rpool/ROOT/ubuntu_2cwpns                          14.3G   875G     6.58G  /
rpool/ROOT/ubuntu_2cwpns/srv                        96K   875G       96K  /srv
rpool/ROOT/ubuntu_2cwpns/usr                       224K   875G       96K  /usr
rpool/ROOT/ubuntu_2cwpns/usr/local                 128K   875G      128K  /usr/local
rpool/ROOT/ubuntu_2cwpns/var                      7.73G   875G       96K  /var
rpool/ROOT/ubuntu_2cwpns/var/games                  96K   875G       96K  /var/games
rpool/ROOT/ubuntu_2cwpns/var/lib                  7.47G   875G     7.01G  /var/lib
rpool/ROOT/ubuntu_2cwpns/var/lib/AccountsService   108K   875G      108K  /var/lib/AccountsService
rpool/ROOT/ubuntu_2cwpns/var/lib/NetworkManager    188K   875G      188K  /var/lib/NetworkManager
rpool/ROOT/ubuntu_2cwpns/var/lib/apt               421M   875G      421M  /var/lib/apt
rpool/ROOT/ubuntu_2cwpns/var/lib/dpkg             47.6M   875G     47.6M  /var/lib/dpkg
rpool/ROOT/ubuntu_2cwpns/var/log                   261M   875G      261M  /var/log
rpool/ROOT/ubuntu_2cwpns/var/mail                   96K   875G       96K  /var/mail
rpool/ROOT/ubuntu_2cwpns/var/snap                 1.86M   875G     1.86M  /var/snap
rpool/ROOT/ubuntu_2cwpns/var/spool                 120K   875G      120K  /var/spool
rpool/ROOT/ubuntu_2cwpns/var/www                    96K   875G       96K  /var/www
rpool/USERDATA                                    1.93G   875G       96K  /
rpool/USERDATA/mafoelffen_gtg9x1                  1.92G   875G     1.92G  /home/mafoelffen
rpool/USERDATA/root_gtg9x1                        2.67M   875G     2.67M  /root

```
My suggests, install a vm with it. Play and learn how to use it. I think that once you learn how to use it, and what you can do with it, that you will fall in love with it.

Ask 1fallen or me if you have any questions on what to do on it or with it.

---

### Post by #&amp;thj^% on 2023-08-26
> **MAFoElffen said:**
> Well, lets say: adaptable and flexible.
+1 Well Said

> **MAFoElffen said:**
> 
My suggests, install a vm with it. Play and learn how to use it. I think that once you learn how to use it, and what you can do with it, that you will fall in love with it.

Ask 1fallen or me if you have any questions on what to do on it or with it.

I can't remember when I first looked at ZFS I think on 18.04 and 20.04 and it just wasn't ready for me....:lolflag:
(it really turns out i wasn't ready for ZFS)
MAFoElffen challenged me in thread a few years back And i tried it again and haven't left it since...go figure.

---

### Post by Paddy Landau on 2023-08-27
ZFS sounds fascinating. Unfortunately, I don't have the time to do learn that sort of thing any more. I wish that I did!

---

