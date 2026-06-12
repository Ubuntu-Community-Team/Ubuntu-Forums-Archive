---
title: "Ubuntu/FreeBSD"
date: 2021-02-18
forum: General Help
---

### Post by Freiklite on 2021-02-18
Hi,
I am not able to write a 40_custom file despite much reading.
( for example [https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)).
The FreeBSD kernel isn't loaded by /etc/grub.d/40_custom.

Some information:
> $ uname -a
Linux zety-SATELLITE-C70D-B 5.4.0-65-generic #73-Ubuntu SMP Mon Jan 18 17:25:17 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux



FreeBSD release: [FreeBSD-12.2-RELEASE-amd64-dvd1.iso]("https://download.freebsd.org/ftp/releases/amd64/amd64/ISO-IMAGES/12.2/FreeBSD-12.2-RELEASE-amd64-dvd1.iso")
>  $ sudo fdisk -l /dev/sda
 Disque /dev/sda : 931,53 GiB, 1000204886016 octets, 1953525168 secteurs
 Disk model: TOSHIBA MQ01ABD1
 Unités : secteur de 1 × 512 = 512 octets
 Taille de secteur (logique / physique) : 512 octets / 512 octets
 taille d'E/S (minimale / optimale) : 512 octets / 512 octets

 Type d'étiquette de disque : gpt
 Identifiant de disque : EF15C24E-9779-49A5-863F-E111923F2391
 
 
 Périphérique      Début        Fin   Secteurs Taille Type
 /dev/sda1          2048    1050623    1048576                                           512M Système EFI
 /dev/sda2       1050624 1543503871 1542453248                       735,5G Système de fichiers Linux

 /dev/sda3    1543503872 1543913471     409600                         200M Système EFI
 /dev/sda4    1543913472 1946157055  402243584                   191,8G UFS FreeBSD
 /dev/sda5    1946157056 1953525134    7368079                       3,5G Partition d'échange FreeBSD
  

> $ sudo blkid
[sudo] Mot de passe de zety : 
/dev/sda2: UUID="78a9f048-e88d-4c2e-9c83-e0f8efb74c17" TYPE="ext4" PARTUUID="a75f3628-3530-4eb0-a70b-d5382d6b9e00"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/loop7: TYPE="squashfs"
/dev/sda1: UUID="4D9D-7FE8" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="b344a956-bc2a-46e9-b2ef-4fe10bf85e01"
/dev/sda3: SEC_TYPE="msdos" LABEL_FATBOOT="EFISYS" LABEL="EFISYS" UUID="BD41-11EE" TYPE="vfat" PARTUUID="20dc2407-715d-11eb-9846-008cfa86905a"
/dev/sda4: UUID="602d7a3d46fa2dc1" TYPE="ufs" PARTUUID="2107172a-715d-11eb-9846-008cfa86905a"
/dev/sda5: PARTUUID="210c0f68-715d-11eb-9846-008cfa86905a"



FreeBSD installation information:
Auto UFS 
/ada0p4                192GB   freebsd-ufs             /
/ada0p5                3,5GB        freebsd-swap                    none

In advance thank you very much for your attention.
Ciao

---

### Post by TheFu on 2021-02-18
Use **sudoedit** when editing system files.

Is this a trick question?

Don't know much about BSD.  I usually just login as root on those systems via ssh. My BSD systems don't run any GUI.

---

### Post by schragge on 2021-02-18
1) You don't show what _is_ in  **/etc/grub.d/40_custom**
2) I just put my customizations to **/boot/grub/custom.cfg** which is then read by **/etc/grub.d/41_custom**

---

### Post by TheFu on 2021-02-18
> **schragge said:**
> 1) You don't show what _is_ in  **/etc/grub.d/40_custom**
2) I just put my customizations to **/boot/grub/custom.cfg** which is then read by **/etc/grub.d/41_custom**

I backup everything in /etc/.
I never backup /boot/ - ever.
Whenever modifying things, always consider the impacts to your backups.

---

### Post by grahammechanical on 2021-02-18
I will ask the obvious question. Did you run

```
sudo update-grub
```

You say this

> The FreeBSD kernel isn't loaded by /etc/grub.d/40_custom.

Does FreeBSD appear in the Grub menu? Are you pointing Grub to the right partition? FreeBSD is on sda4. Grub wants that to be hd0,4. set root=(hd0,4)

Regards

---

### Post by HermanAB on 2021-02-19
BTW, I have always found OpenBSD easier to install than FreeBSD, and once they are working, there is not much of a difference.

---

### Post by Freiklite on 2021-02-21
Hi,
1-
the command:
```
sudo update-grub
```
displays FreeBSD in the Grub menu but that runs a error message.

2-
Gparted information says:
> /dev/sda3
/dev/sda4 
/dev/sda5
unmounted
> Périphérique      Début        Fin   Secteurs Taille Type
/dev/sda1          2048    1050623    1048576   512M Système EFI
/dev/sda2       1050624 1543503871 1542453248 735,5G Système de fichiers Linux
/dev/sda3    1543503872 1543913471     409600   200M Système EFI
/dev/sda4    1543913472 1946157055  402243584 191,8G UFS FreeBSD
/dev/sda5    1946157056 1953525134    7368079   3,5G Partition d'échange FreeBSD

3-
I tried several commands:[HTML]# /dev/sda4: UUID="602d7a3d46fa2dc1" TYPE="ufs" PARTUUID="2107172a-715d-11eb-9846-008cfa86905a"
sudo mount -t ufs -o rw -U 602d7a3d46fa2dc1 /boot
~$ sudo mount -t ufs -o rw -U 602d7a3d46fa2dc1 /boot
mount: /boot: wrong fs type, bad option, bad superblock on /dev/sda4, missing codepage or helper program, or other error.

$ sudo fdisk -l /dev/sda4
[sudo] Mot de passe de zety : 
Disque /dev/sda4 : 191,82 GiB, 205948715008 octets, 402243584 secteurs
Unités : secteur de 1 × 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 512 octets
taille d'E/S (minimale / optimale) : 512 octets / 512 octets

$ dmesg | tail
               
               >>>WARNING<<< Wrong ufstype may corrupt your filesystem, default is ufstype=old
[  422.785064] ufs: ufs_fill_super(): bad magic number
[ 2755.388657] ufs: ufs was compiled with read-only support, can't be mounted as read-write
[ 2755.388766] ufs: You didn't specify the type of your ufs filesystem
               
               mount -t ufs -o ufstype=sun|sunx86|44bsd|ufs2|5xbsd|old|hp|nextstep|nextstep-cd|openstep ...
               
               >>>WARNING<<< Wrong ufstype may corrupt your filesystem, default is ufstype=old
[ 2755.409913] ufs: ufs_fill_super(): bad magic number

sudo mount -t ufs2 -o ro -U 602d7a3d46fa2dc1 /boot
$ sudo mount -t ufs2 -o ro -U 602d7a3d46fa2dc1 /boot
mount: /boot: type de système de fichiers « ufs2 » inconnu.

sudo mount -t 44bsd -o ro -U 602d7a3d46fa2dc1 /boot
$ sudo mount -t 44bsd -o ro -U 602d7a3d46fa2dc1 /boot
mount: /boot: type de système de fichiers « 44bsd » inconnu.

sudo mount -U 602d7a3d46fa2dc1 -t ufs /boot -o ro
$ sudo mount -U 602d7a3d46fa2dc1 -t ufs /boot -o ro
mount: /boot: wrong fs type, bad option, bad superblock on /dev/sda4, missing codepage or helper program, or other error.



sudo mount /dev/sda4 /boot
$ sudo mount /dev/sda4 /boot
mount: /boot: wrong fs type, bad option, bad superblock on /dev/sda4, missing codepage or helper program, or other error.


sudo mount /dev/sda4 /media
$ sudo mount /dev/sda4 /media
mount: /media: wrong fs type, bad option, bad superblock on /dev/sda4, missing codepage or helper program, or other error.






sudo mount -t ufstype=ufs -o ro -U 602d7a3d46fa2dc1 /boot
$ sudo mount -t ufstype=ufs -o ro -U 602d7a3d46fa2dc1 /boot
mount: /boot: type de système de fichiers « ufstype=ufs » inconnu.


sudo mount -t ufstype=old -o ro -U 602d7a3d46fa2dc1 /boot
sudo mount -t ufstype=old -o ro -U 602d7a3d46fa2dc1 /boot
mount: /boot: type de système de fichiers « ufstype=old » inconnu.
zety@zety-SATELLITE-C70D-B:/boot$ sudo mount -t old -o ro -U 602d7a3d46fa2dc1 /boot
mount: /boot: type de système de fichiers « old » inconnu.


sudo mount -t ufs -o  ufstype=ufs -o ro -U 602d7a3d46fa2dc1 /boot
[sudo] Mot de passe de zety : 
mount: /boot: wrong fs type, bad option, bad superblock on /dev/sda4, missing codepage or helper program, or other error.

[/HTML]

4-
As you can see I lacks a firm grasp of the subject,

Ciao

---

### Post by TheFu on 2021-02-21
Code tags, please: [https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code)   Outputs with columns are difficult to read, especially when not in a language we know.

---

### Post by oldfred on 2021-02-21
I see two ESP - efi system partitions. You have sda1 & sda3 as ESP.
Most systems will only work with one ESP. Some have used a second FAT32 partition to hold boot files. 
UEFI will not directly boot from a FAT32 partition, but grub may find & use the files in it to boot.

Best to only have one ESP. Normally all installed systems share that one ESP with different folders for their boot.
And then UEFI refers to that one ESP to find boot files.

You may need to reinstall boot loader. Do not know BSD's and how they do UEFI.
You can also post this from Ubuntu to see what partition by GUID/partUUID & files it uses to boot.
sudo efibootmgr -v
lsblk -o name,mountpoint,label,size,fstype,uuid,partuuid | egrep -v "^loop"

---

### Post by Freiklite on 2021-02-22
Hi,
Here are the requested information:
```
$ sudo efibootmgr -v
[sudo] Mot de passe de zety : 
BootCurrent: 0000
Timeout: 0 seconds
BootOrder: 0000,0001,2003,2001,2002
Boot0000* ubuntu    HD(1,GPT,b344a956-bc2a-46e9-b2ef-4fe10bf85e01,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)
Boot0001* EFI HDD Device (TOSHIBA MQ01ABD100)    PciRoot(0x0)/Pci(0x11,0x0)/Ata(0,0,0)/HD(3,GPT,20dc2407-715d-11eb-9846-008cfa86905a,0x5c000000,0x64000)RC
Boot0002* Realtek PXE    PciRoot(0x0)/Pci(0x2,0x2)/Pci(0x0,0x0)/MAC(008cfa86905a,0)/IPv4(0.0.0.00.0.0.0,0,0)RC
Boot0003* Realtek PXE    PciRoot(0x0)/Pci(0x2,0x2)/Pci(0x0,0x0)/MAC(008cfa86905a,0)/IPv6([::]:<->[::]:,0,0)RC
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC


```
```
$ lsblk -o name,mountpoint,label,size,fstype,uuid,partuuid | egrep -v "^loop" 
NAME   MOUNTPOINT                   LABEL    SIZE FSTYPE   UUID                                 PARTUUID
sda                                        931,5G                                               
&#9500;&#9472;sda1 /boot/efi                             512M vfat     4D9D-7FE8                            b344a956-bc2a-46e9-b2ef-4fe10bf85e01
&#9500;&#9472;sda2 /                                   735,5G ext4     78a9f048-e88d-4c2e-9c83-e0f8efb74c17 a75f3628-3530-4eb0-a70b-d5382d6b9e00
&#9500;&#9472;sda3                              EFISYS   200M vfat     BD41-11EE                            20dc2407-715d-11eb-9846-008cfa86905a
&#9500;&#9472;sda4                                     191,8G ufs      602d7a3d46fa2dc1                     2107172a-715d-11eb-9846-008cfa86905a
&#9492;&#9472;sda5                                       3,5G                                               210c0f68-715d-11eb-9846-008cfa86905a
sr0                                         1024M                  

```
The report is available at:
[http://paste.ubuntu.com/p/PWCnF2Njgz/](http://paste.ubuntu.com/p/PWCnF2Njgz/)

Boot-Repair suggests:
> Suggested repair: ______________________________________________________________

The default repair of the Boot-Repair utility would reinstall the grub-efi-amd64-signed of
sda2,
using the following options:        sda1/boot/efi,
Additional repair would be performed: unhide-bootmenu-10s  use-standard-efi-file    

Final advice in case of suggested repair: ______________________________________


Please do not forget to make your UEFI firmware boot on the Ubuntu 20.04.2 LTS entry (sda1/efi/****/shim****.efi (**** will be updated in the final message) file) !


I need some advice.
The repair option of Boot Repair **(Recommended repair**) is it effective?
Ciao :

---

### Post by TheFu on 2021-02-22
> **Freiklite said:**
> 
sudo mount -t ufs -o  ufstype=ufs -o ro -U 602d7a3d46fa2dc1 /boot


I haven't any clue but .... 

mount only allows 1 -o in the command line. When multiple option are needed, they must be grouped together, comma separated, NO SPACES!!!  Assuming that is the only problem with the command (I didn't check other options that I've never used), 
```
sudo mount -t ufs -o  ufstype=ufs,ro -U 602d7a3d46fa2dc1 /boot
```
would be the correct line assuming you have ufs support libraries loaded. I don't see a mount.ufs on my systems, so I think they are not included in Ubuntu by default.  In 
Linux, /boot/ can't be UFS.  On my Linux systems, /boot/ is ext2 or ext4.

I don't believe ufstype=ufs is valid either.  You'll need to check that on a system with ufs-tools.  In theory, the -t ufs should be sufficient, unless there are sub-types of UFS.

On my freeBSD systems, I don't have a separate /boot/ partition, just a virtual mount from a ufs file system.  Inside freeBSD, the mount manpage doesn't mention UUIDs at all, so I doubt that is supported.

---

### Post by Freiklite on 2021-02-28
Hi, 
After a boot-repair there is a final message:
```
Do not forget to make your UEFI firmware boot on the Ubuntu 20.04.2 LTS entry (sda1/UEFI/ubuntu/shimx64.efi file).
```

Where is the Ubuntu 20.04.2 LTS entry?
Then what must I do exactly?

Thank very much for your suggestion and your patience,
Ciao

---

### Post by CelticWarrior on 2021-02-28
Open UEFI ("BIOS") settings > Boot and select accordingly.

---

### Post by Freiklite on 2021-03-01
Hi,
A new paste: [https://paste.ubuntu.com/p/5H2tWnGbnN/](https://paste.ubuntu.com/p/5H2tWnGbnN/)
I did in Advanced options > Grub location > separate /boot/efi partition: sda1 (ubuntu20.04.2LTS)  > apply
I rebooted. 
the grub menu doesn't change.
Ciao

P.S.: > $ locate shimx64.efi
/usr/lib/shim/shimx64.efi
/usr/lib/shim/shimx64.efi.signed


Must I edit the grub file and add "sda1/EFI/ubuntu/shimx64.efi"after or before vmlinuz, etc?

---

### Post by oldfred on 2021-03-01
Look at line 93 in report, it is the same as sudo efibootmgr -v.
And it shows your UEFI entry.

```
BootOrder: 0000,2002,0001,2003,2001
Boot0000* ubuntu    HD(1,GPT,b344a956-bc2a-46e9-b2ef-4fe10bf85e01,0x800,0x100000)/File(EFIubuntu[COLOR=#ff0000]shimx64.efi[/COLOR])
Boot0001* freebsd    HD(1,GPT,b344a956-bc2a-46e9-b2ef-4fe10bf85e01,0x800,0x100000)/File(EFIfreebsdshimx64.efi)

```


You still show two ESP, both sda1 & sda3. Most systems only want one per drive. With gparted removed esp flag form sda3.

The errors on FreeBSD's swap should just be considered as normal. Script does not like unformatted partitions and I do not think it is set up to correctly see any typical BSDs. It also show similar errors on Windows reserved and bios_grub as they are unformatted but required partitions if using a configuration that needs them.
Since script not familiar with ufs, you should manually mount it before running script. 

[https://unix.stackexchange.com/questions/320292/unable-to-dual-boot-freebsd-alongside-arch-linux-with-grub2](https://unix.stackexchange.com/questions/320292/unable-to-dual-boot-freebsd-alongside-arch-linux-with-grub2)
User added the ufs2 driver for grub & chained to the loader.efi file. I would think, you could configfile to /EFI/freebsd/shimx64.efi also, see grub's configfile in ESP for loading full grub in your install at /EFI/ubuntu/grub.cfg as typical configfile type entry.
```
insmod ufs2  
set root=(hd0,gpt4)  
chainloader /boot/loader.efi
```

---

### Post by Freiklite on 2021-03-02
Hi, 
Thank you very much for your attention and thank you all for being so patient.
I stop the thread.
Bye.

---

