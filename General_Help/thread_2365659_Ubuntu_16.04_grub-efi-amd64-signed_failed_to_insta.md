---
title: "Ubuntu 16.04: grub-efi-amd64-signed failed to install into /target/ error"
date: 2017-07-09
forum: General Help
---

### Post by benedictflorance on 2017-07-09
I have Dell Inspiron 5567 laptop (i-7, 8GB) with Windows-10 OS installed on it. I am trying to install ubuntu 16.04 as a dual boot OS on Windows10. I have disabled fast boot and secure boot options also. I am facing following error while installing ubuntu 16.04:


grub-efi-amd64-signed failed to install into /target/. Without GRUB boot loader,
the installed system will not boot


I have created three partitions:


    [HTML]
    20GB-ext4- Root mounted
    18.9GB-ext4- /home
    4GB Swap area
[/HTML]

_**Launchpad link for the log files**_: [https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/1703167](https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/1703167)


_**Pastebin link for boot-repair:**_ [https://pastebin.com/raw/u4LSP0V4](https://pastebin.com/raw/u4LSP0V4)


[U][B]Output of sudo fdisk -l: 
[/B][/U]

    [HTML]Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
    Units: sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 4096 bytes
    I/O size (minimum/optimal): 4096 bytes / 4096 bytes
    Disklabel type: gpt
    Disk identifier: F87D48DF-F3FF-429E-8F0B-558F81712A60
    
    Device          Start        End    Sectors   Size Type
    /dev/sda1        2048    1026047    1024000   500M EFI System
    /dev/sda2     1026048    1288191     262144   128M Microsoft reserved
    /dev/sda3     1288192 1843265535 1841977344 878.3G Microsoft basic data
    /dev/sda4  1927151616 1928073215     921600   450M Windows recovery environment
    /dev/sda5  1928073216 1951281151   23207936  11.1G Windows recovery environment
    /dev/sda6  1951281152 1953523711    2242560   1.1G Windows recovery environment
    /dev/sda7  1843265536 1851078655    7813120   3.7G Linux swap
    /dev/sda8  1851078656 1890140159   39061504  18.6G Linux filesystem
    /dev/sda9  1890140160 1927151615   37011456  17.7G Linux filesystem
    
    Partition table entries are not in disk order.
[/HTML]

[U][B]Output of sudo parted -l:
[/B][/U]

    [HTML]Model: ATA TOSHIBA MQ01ABD1 (scsi)
    Disk /dev/sda: 1000GB
    Sector size (logical/physical): 512B/4096B
    Partition Table: gpt
    Disk Flags: 
    
    Number  Start   End     Size    File system     Name                          Flags
     1      1049kB  525MB   524MB   fat32           EFI system partition          boot, esp
     2      525MB   660MB   134MB                   Microsoft reserved partition  msftres
     3      660MB   944GB   943GB   ntfs            Basic data partition          msftdata
     7      944GB   948GB   4000MB  linux-swap(v1)
     8      948GB   968GB   20.0GB  ext4
     9      968GB   987GB   18.9GB  ext4
     4      987GB   987GB   472MB   ntfs                                          hidden, diag
     5      987GB   999GB   11.9GB  ntfs                                          hidden, diag
     6      999GB   1000GB  1148MB  ntfs                                          hidden, diag
    
    
    Model: SRT USB (scsi)
    Disk /dev/sdb: 32.5GB
    Sector size (logical/physical): 512B/512B
    Partition Table: msdos
    Disk Flags: 
    
    Number  Start   End     Size    Type     File system  Flags
    1      1049kB  32.5GB  32.5GB  primary  fat32        boot, lba[/HTML]

Please guide me how to resolve this problem.

---

### Post by Kris_M on 2017-07-09
I thought I saw somewhere that you couldn't use fastboot with uefi but I could be wrong.

---

### Post by westie457 on 2017-07-09
Looking through the report the /efi partition is mounted read only and has some corruption.

Give this a try.

Boot using install media to try mode > open a terminal > type in and run ```
sudo fsck /dev/sda1
```You should get info on screen saying something like 'dirty bit is set', follow the prompts to fix

Run Boot Repair again > go to advanced > select the option to (re)install Grub making sure that the target partition is /dev/sda1 (boot/efi).

If this does not work there are other options to try.

---

### Post by benedictflorance on 2017-07-09
It asks several prompts. Don't know what to select for each prompt. Kindly guide me.

---

### Post by yancek on 2017-07-09
Did you turn off fastboot from within windows also:

Menu, Settings, System, Power & Sleep, Additional Power settings,  Here on the left are options to Choose what the power button does and Choose what closing the lid does.  There is an option under each to Change Settings that are currently unavailable.  Select this and then select the options you want at least for power button for both battery and plugged in.  If you've already done this, open a terminal and run:  sudo efibootmgr to show your EFI entry information and post it here.

---

### Post by westie457 on 2017-07-09
> **benedictflorance said:**
> It asks several prompts. Don't know what to select for each prompt. Kindly guide me.
Can you post the complete output from the fsck command please.

---

### Post by oldfred on 2017-07-09
If you press f12 when starting to boot, you may need a full shutdown or cold boot, does it not now show the ubuntu entry in UEFI boot order.

It did not add it several times, but last time  you show this as UEFI boot menu. And Ubuntu should be default or first boot.

```
BootOrder: 0002,0000,0001
Boot0000* Windows Boot Manager	HD(1,GPT,e61f16d9-dfa1-470d-ad0b-34358db52315,0x800,0xfa000)/File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....f...............
Boot0001* UEFI: SRT USB 1100, Partition 1	PciRoot(0x0)/Pci(0x14,0x0)/USB(1,0)/HD(1,MBR,0x4294967246,0x800,0x3c77800)..BO
Boot0002* ubuntu	HD(1,GPT,e61f16d9-dfa1-470d-ad0b-34358db52315,0x800,0xfa000)/File(EFIubuntushimx64.efi)

```

---

