---
title: "Need help recreated IEMI entry"
date: 2016-08-24
forum: General Help
---

### Post by bvargo on 2016-08-24
Background info:
Ubuntu 16.04 LTS, 64 bit.

```
root@:~# blkid
/dev/sda1: UUID="178B-8074" TYPE="vfat" PARTUUID="72d37707-6cac-4631-bb48-7fc8a2719469"
/dev/sda2: UUID="2f6beedb-b275-4c4e-a71f-2f37557e5c12" TYPE="ext4" PARTUUID="2ea39837-82c8-4ca2-a10d-ef5b8610d907"
/dev/sda4: UUID="06fe7f10-6d4e-42b1-b495-548021a1b89b" TYPE="ext4" PARTUUID="810969e9-4c40-4b1f-a2bd-cf398fc7f951"
/dev/sda5: UUID="3a696036-ee16-4be4-9524-d908ded95a11" TYPE="swap" PARTUUID="edcfaa3c-826c-4574-af69-4935c8ffe9f7"
/dev/sda6: UUID="dfdbbfcf-aa70-4ab4-ba0b-fad17feae26a" TYPE="ext4" PARTUUID="ddf09229-66b3-49fa-90f2-c314ac530630"

```

```
root@:~# cat /etc/fstab
# <file system>                         <mount point>    <type>  <options>       <dump>  <pass>
# / was on /dev/sda4 during installation
UUID=06fe7f10-6d4e-42b1-b495-548021a1b89b /              ext4    noatime,errors=remount-ro 0       1
# /boot was on /dev/sda2 during installation
UUID=2f6beedb-b275-4c4e-a71f-2f37557e5c12    /boot       ext4    noatime,defaults      0       2
# /boot/efi was on /dev/sda1 during installation
UUID=178B-8074  /boot/efi      vfat    umask=0077      0       1
# swap was on /dev/sda5 during installation
UUID=3a696036-ee16-4be4-9524-d908ded95a11 none           swap    sw            0       0
# new /home, /dev/sda6
UUID=dfdbbfcf-aa70-4ab4-ba0b-fad17feae26a /home         ext4 noatime,defaults      0       2

```

fdisk -l
```

Disk /dev/sda: 111.8 GiB, 120034123776 bytes, 234441648 sectorsUnits: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 11D0B980-B9E4-4B02-AF95-4F1E9EA9967C


Device         Start       End   Sectors  Size Type
/dev/sda1       2048   1046527   1044480  510M EFI System
/dev/sda2    1046528   3000319   1953792  954M Linux filesystem
/dev/sda4    3000320  64636927  61636608 29.4G Linux filesystem
/dev/sda5  229558272 234440703   4882432  2.3G Linux swap
/dev/sda6   64636928 229558271 164921344 78.7G Linux filesystem


Partition table entries are not in disk order.

```

I would appreciate some help to figure out how to recreate the IEMI entry for my SSD. I resized and moved my /root partition and gparted said that it may cause a problem which it did. I was able to boot via USB and go in and [update GRUB]("http://gparted.org/display-doc.php?name=help-manual&lang=C#gparted-fix-grub-boot-problem") such that I was able to get the drive to boot without a problem but the IEMI entry is gone.  I'm really not sure how to use e.g. efibootmgr to restore the IEMI and there are so many different and disparate pieces of information about this that I don't feel comfortable just guessing.  I followed the info on the gparted faq with the addition of step 5b which was to mount /dev/sda1 at /tmp/mydir/boot/efi.

FWIW, my motherboard is a Gigabyte Z77X-UD3H with v.F17 BIOS.  There is no way through BIOS (that I can find) to designate a drive as an IEMI drive.

The relevant info is above but the partitions are as follows:
/dev/sda1 EFI partition
/dev/sda2 /boot partition
/dev/sda4 /root partition
/dev/sda6 /home partition

What I'm confused about is what is my boot partition, sda1 or sda2?  How to I go about reestablishing the IEMI entry?  Is which efi file should I specify from /dev/sda1, mounted at /boot/efi/, EFI/fwupx64.efi  EFI/grubx64.efi  EFI/MokManager.efi  EFI/shimx64.efi?

Info from efibootmgr:

```

root@:~# mount | grep efivars
efivarfs on /sys/firmware/efi/efivars type efivarfs (rw,nosuid,nodev,noexec,relatime)
root@:~# efibootmgr -v
BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0000,0005
Boot0000* ubuntu	HD(1,GPT,72d37707-6cac-4631-bb48-7fc8a2719469,0x800,0xff000)/File(\EFI\ubuntu\shimx64.efi)
Boot0005* Hard Drive 	BBS(HD,,0x0)AMGOAMNO........o.K.I.N.G.S.T.O.N. .S.H.1.0.3.S.3.1.2.0.G....................A...........................>..Gd-.;.A..MQ..L.0.5.2.0.B.6.3.7.C.2.1.0.0.B.D.3. . . . ......AMBO

```

---

### Post by bvargo on 2016-09-06
Help appreciated...bump.

---

