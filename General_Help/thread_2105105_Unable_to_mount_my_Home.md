---
title: "Unable to mount my Home"
date: 2013-01-15
forum: General Help
---

### Post by freerage on 2013-01-15
Hello,

I can't start the graphical session from my account with an Home encrpted (ecryptfs). After trying to log in, I'm sent to a black screen witch quickly disappear and I'm back to the login screen.

I thought the problem was coming from Unity, but if I mount the Home with another account (not crypted) I can start the session. 

Just before the this problem, I was installing samba... Maybe it's related ?

I'm under 12.04 on an Asus UX31A-R4003P.

For Information :
> 
**sudo fdisk -l **  Attention : identifiant de table de partitions GPT (GUID) détecté sur « /dev/sda » ! L'utilitaire sfdisk ne prend pas GPT en charge. Utilisez GNU Parted.   Disk /dev/sda: 252.0 GB, 252000000000 bytes 255 têtes, 63 secteurs/piste, 30637 cylindres, total 492187500 secteurs Unités = secteurs de 1 * 512 = 512 octets Taille de secteur (logique / physique) : 512 octets / 512 octets taille d'E/S (minimale / optimale) : 512 octets / 512 octets Identifiant de disque : 0x2790deaf  Périphérique Amorce  Début        Fin      Blocs     Id  Système /dev/sda1               1   492187499   246093749+  ee  GPT  Disk /dev/mapper/cryptswap1: 10.0 GB, 10000269312 bytes 255 têtes, 63 secteurs/piste, 1215 cylindres, total 19531776 secteurs Unités = secteurs de 1 * 512 = 512 octets Taille de secteur (logique / physique) : 512 octets / 512 octets taille d'E/S (minimale / optimale) : 512 octets / 512 octets Identifiant de disque : 0xbe60a626  Le disque /dev/mapper/cryptswap1 ne contient pas une table de partitions valable> **cat /etc/fstab** # /etc/fstab: static file system information. # # Use 'blkid' to print the universally unique identifier for a # device; this may be used with UUID= as a more robust way to name devices # that works even if disks are added and removed. See fstab(5). # # <file system> <mount point>   <type>  <options>       <dump>  <pass> proc            /proc           proc    nodev,noexec,nosuid 0       0 # / was on /dev/sda3 during installation UUID=b58d6bf8-bc7b-4c42-8601-f74e95167153 /               ext4        discard,noatime,nodiratime,errors=remount-ro 0       1 # /boot/efi was on /dev/sda1 during installation UUID=86D4-BD05  /boot/efi       vfat    defaults        0       1 # swap was on /dev/sda2 during installation #UUID=eb915754-df71-489e-a57a-0fb2efd4a558 none            swap    sw              0       0 /dev/mapper/cryptswap1 none swap sw 0 0 tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0Thanks for your help,
free.rage.

---

### Post by freerage on 2013-01-16
HI,

Problem solved, I simply had changed my password with root (*sudo passwd $user*) so the change was not effective on the user account !! 

I changed back with *passwd $user* and it's now ok.

Regards,
freerage.

---

