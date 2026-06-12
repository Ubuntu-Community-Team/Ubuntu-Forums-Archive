---
title: "restore secboot and remove partitions, nvidia 25 install faileded"
date: 2023-03-03
forum: General Help
---

### Post by slicken on 2023-03-03
I installed "Nvidia 25" divers and it wanted me to enter a password so it could install with BIOS setting ""secure boot" enabled.
After I realized I dont have Nvidia card on my laptop i didnt go trou the installation.
I could not boot properly so I reinstalled "Ubuntu 22.04 5./ 15.0-43-generic".


Now I can only boot with BIOS setting "secure boot" disabled.


```
--start--
slk@slk-pc:~$ sudo fdisk -l
[sudo] password for slk:
Disk /dev/loop0: 61,96 MiB, 64970752 bytes, 126896 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/nvme0n1: 476,94 GiB, 512110190592 bytes, 1000215216 sectors
Disk model: Micron MTFDKBA512TFH
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 1575072B-4D16-491F-B3CA-5037E5D94345


Device Start End Sectors Size Type
/dev/nvme0n1p1 2048 1050623 1048576 512M EFI System
/dev/nvme0n1p2 1050624 5244927 4194304 2G Linux swap
/dev/nvme0n1p3 5244928 9439231 4194304 2G Solaris boot
/dev/nvme0n1p4 9439232 1000215182 990775951 472,4G Solaris root


--end--
```


Please help me restore boot section so it dont try to boot the Nvidia ting it installed
and delete the partitions it created, so I can boot properly with BIOS "secure boot" enabled.

---

### Post by oldfred on 2023-03-04
Please use Code Tags when posting terminal output.

How to use Code tags, # in Forum's advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
[http://ubuntuforums.org/showthread.php?p=12776168#post12776168](http://ubuntuforums.org/showthread.php?p=12776168#post12776168)

Also removed loops which are your snaps, not partitions.

What version of Ubuntu?
Its showing Solaris boot & root?

You normally have to install with Secure boot on, to get signed versions of kernel, drivers & grub installed.

---

### Post by slicken on 2023-03-04
I have linux ubuntu 22.04

```

uname -a
inux slk-pc 5.15.0-43-generic #46-Ubuntu SMP Tue Jul 12 10:30:17 UTC 2022 x86_64 x86_64 x86_64 GNU/Linux

```

I always had secure boot enabled, but now I cant. If I do, it boots to a bluescreen menu wich I think this Nvidia 25 installed. If I disable secure boot it boots properly.
But I want to remove this blue boot page, that Nvidia 25 driver installed so I can boot properly with secure boot enabled.


Any idie what I should do?

---

### Post by oldfred on 2023-03-04
You can install the nVidia driver for Secure Boot.
It just Canonical cannot verify it is secure as it is a binary blob. If you trust nVidia, as user you can sign the nVidia driver with a MOK.
MOK - machine owner key 

[https://wiki.ubuntu.com/UEFI/SecureBoot](https://wiki.ubuntu.com/UEFI/SecureBoot)

Boot live installer with Secure Boot on.
Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version over somewhat older ISO with your USB installer  or any working install.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

You may need to reinstall kernel, drivers & grub or maybe just remove a boot entry in grub or UEFI.

---

### Post by slicken on 2023-03-04
> You can install the nVidia driver for Secure Boot.
It just Canonical cannot verify it is secure as it is a binary blob. If you trust nVidia, as user you can sign the nVidia driver with a MOK.
MOK - machine owner key[URL="https://wiki.ubuntu.com/UEFI/SecureBoot"]
[/URL]Yes, it boots with this Shim MOK thingy, witch I cant sign.
[URL="https://wiki.ubuntu.com/UEFI/SecureBoot"]
[/URL]> Boot live installer with Secure Boot on.

Even if I set USB to first boot option in BIOS, it boots this Shim MOK signer anyways, so I can only boot with secure boot disabled.

> You may need to reinstall kernel, drivers & grub or maybe just remove a boot entry in grub or UEFI.

Yes probobly, but I am noob, so I need help if you can locate the problem.

here is boot-info:  [https://paste.ubuntu.com/p/5jfYXFcqcJ/](https://paste.ubuntu.com/p/5jfYXFcqcJ/)

---

### Post by tea for one on 2023-03-04
A couple of questions:-

Why do you want to enable secure boot?
You mentioned in post 5 that you are a new user, therefore I'm very surprised to see you have zfs?

Secure boot disabled and the ext4 file system is fine for a home (non enterprise) user.

---

### Post by oldfred on 2023-03-04
I do not know zfs, so cannot tell if settings are correct or not.

[https://www.phoronix.com/scan.php?page=news_item&px=Linus-Says-No-To-ZFS-Linux](https://www.phoronix.com/scan.php?page=news_item&px=Linus-Says-No-To-ZFS-Linux)

---

### Post by slicken on 2023-03-06
> [COLOR=#000000]Why do you want to enable secure boot?[/COLOR][COLOR=#000000]
My laptop is brand new, bought in in January.
I installed Ubuntu 22.04 on it directly , since I dont like Windows.
Secure boot, was always enabled, event when I installed Ubuntu on it.

[/COLOR]> [COLOR=#000000]You mentioned in post 5 that you are a new user, therefore I'm very surprised to see you have zfs?[/COLOR][COLOR=#000000]
[/COLOR]I am not new to Ubuntu, but I am no pro, or know anything about how to restore/delete shim boot, that the Nvidia driver installed.
So I am noob here.

I choose zfk, when I installed ubuntu. I wanted to remove all windows partitions, so I though why not, lets try zfk.
It anoyys me that I screwed up secure boot. And I want to learn, how to restore this.

---

### Post by slicken on 2023-03-07
> **oldfred said:**
> I do not know zfs, so cannot tell if settings are correct or not.

[https://www.phoronix.com/scan.php?page=news_item&px=Linus-Says-No-To-ZFS-Linux](https://www.phoronix.com/scan.php?page=news_item&px=Linus-Says-No-To-ZFS-Linux)

nice read.
if I re.install untuntu 22.04 and use ext4 instead.
would you be able to help me then?

i will do it, if someone in here can confidintly say they can help me remove this shim screen witch comes first, even if I have USB or anything else with highest boot prio.


regards,

---

### Post by oldfred on 2023-03-07
You typically use shimx64.efi to boot with grub.
The shim file is for use with UEFI Secure Boot, but seems to be the default with all UEFI boots. I do not have Secure boot on and default boot is with shimx64.efi.

Please see link in my signature below for more UEFI info.
Brand/model & video card/chip make a difference. 

I prefer to have UEFI Secure boot off on my desktop systems. But may need to turn it back on in future.
Was surprised my Dell with Intel 11th Gen chip (no nVidia) booted with UEFI Secure boot on and I did not change to AHCI for drives. It used a VMD driver for NVMe drive. Have not actually dealt with MOK keys for binary drivers & Secure Boot.

Many new systems are now UEFI only. 
Make sure UEFI & if NVMe drive(s) have latest updates to firmware.
Some very new systems may need newest version of Ubuntu. 22.04.2 has updated kernel & drivers.

---

### Post by MAFoElffen on 2023-03-08
> **oldfred said:**
> You typically use shimx64.efi to boot with grub.
The shim file is for use with UEFI Secure Boot, but seems to be the default with all UEFI boots. I do not have Secure boot on and default boot is with shimx64.efi.

+1, shown here on mine with Ubuntu 22/04.2 and Windows 11
```

mafoelffen@Mikes-B460M:~$ sudo mokutil --sb-state
SecureBoot disabled
Platform is in Setup Mode
mafoelffen@Mikes-B460M:~$ efibootmgr -v
BootCurrent: 0002
Timeout: 1 seconds
BootOrder: 0002,0000
Boot0000* Windows Boot Manager    HD(1,GPT,e72b3745-510c-481f-95f6-f721bc03e49e,0x800,0x100000)/File(\EFI\MICROSOFT\BOOT\BOOTMGFW.EFI)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...d................
Boot0002* ubuntu    HD(1,GPT,e72b3745-510c-481f-95f6-f721bc03e49e,0x800,0x100000)/File(\EFI\UBUNTU\SHIMX64.EFI)..BO

```
And no, in your boot-info report, I didn't see anything wrong there with your ZFS settings... One of mine
```

mafoelffen@Mikes-B460M:~$ sudo zfs list
NAME                                               USED  AVAIL     REFER  MOUNTPOINT
bpool                                              290M  1.47G       96K  /boot
bpool/BOOT                                         289M  1.47G       96K  none
bpool/BOOT/ubuntu_2cwpns                           289M  1.47G      289M  /boot
datapool                                           654G  2.87T       96K  none
datapool/DATA                                      654G  2.87T      654G  /data
rpool                                             11.9G   880G       96K  /
rpool/ROOT                                        7.27G   880G       96K  none
rpool/ROOT/ubuntu_2cwpns                          7.27G   880G     4.42G  /
rpool/ROOT/ubuntu_2cwpns/srv                        96K   880G       96K  /srv
rpool/ROOT/ubuntu_2cwpns/usr                       224K   880G       96K  /usr
rpool/ROOT/ubuntu_2cwpns/usr/local                 128K   880G      128K  /usr/local
rpool/ROOT/ubuntu_2cwpns/var                      2.85G   880G       96K  /var
rpool/ROOT/ubuntu_2cwpns/var/games                  96K   880G       96K  /var/games
rpool/ROOT/ubuntu_2cwpns/var/lib                  2.75G   880G     2.61G  /var/lib
rpool/ROOT/ubuntu_2cwpns/var/lib/AccountsService   108K   880G      108K  /var/lib/AccountsService
rpool/ROOT/ubuntu_2cwpns/var/lib/NetworkManager    152K   880G      152K  /var/lib/NetworkManager
rpool/ROOT/ubuntu_2cwpns/var/lib/apt              98.2M   880G     98.2M  /var/lib/apt
rpool/ROOT/ubuntu_2cwpns/var/lib/dpkg             41.1M   880G     41.1M  /var/lib/dpkg
rpool/ROOT/ubuntu_2cwpns/var/log                   101M   880G      101M  /var/log
rpool/ROOT/ubuntu_2cwpns/var/mail                   96K   880G       96K  /var/mail
rpool/ROOT/ubuntu_2cwpns/var/snap                 1.45M   880G     1.45M  /var/snap
rpool/ROOT/ubuntu_2cwpns/var/spool                 120K   880G      120K  /var/spool
rpool/ROOT/ubuntu_2cwpns/var/www                    96K   880G       96K  /var/www
rpool/USERDATA                                    4.62G   880G       96K  /
rpool/USERDATA/mafoelffen_gtg9x1                  4.62G   880G     4.62G  /home/mafoelffen
rpool/USERDATA/root_gtg9x1                        1.75M   880G     1.75M  /root

```
That is 10th i9-10700

---

