---
title: "grub can't boot my windows 7 PLEASE HELP ME"
date: 2013-09-10
forum: General Help
---

### Post by simo2 on 2013-09-10
hi
guys i did a big mistake i formate or delete a partition for booting for windows 7 dev/sda1 now it doesn't exist any more ! and now by the grub menu i can't boot to windows 7 ! 
i did the sudo update-grub  it dosn't found the windows 7 any more !
please help me im in a **** please guys

---

### Post by VMC on 2013-09-10
what the output of ```
sudo fdisk -l
```.

---

### Post by varunendra on 2013-09-11
> **simo2 said:**
> hi
guys i did a big mistake i formate or delete a partition for booting for windows 7 dev/sda1 now it doesn't exist any more !

Which means you deleted the 'Boot' folder which contains win7 boot program and configuration (BCD).

The popular "[Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")" program does have an option to "Fix Windows boot files", but I don't think it can restore BCD because as far as I know, BCD is a restricted proprietary thing.

Please post what VMC asked for, and maybe try Boot-Repair anyway after re-creating an NTFS partition for restoration of BCD and other boot files. But I think you are going to need the Windows installation disc or a windows 7 system repair disc after all.

---

### Post by simo2 on 2013-09-11
root@bt:~# sudo fdisk -l


Disque /dev/sda: 500.1 Go, 500107862016 octets
255 têtes, 63 secteurs/piste, 60801 cylindres
Unités = cylindres de 16065 * 512 = 8225280 octets
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Identifiant de disque : 0xba4906e2


Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sda2              13       30405   244121600    7  HPFS/NTFS
/dev/sda3           30405       48641   146483610    7  HPFS/NTFS
/dev/sda4           48642       60802    97677313    5  Etendue
/dev/sda5           48642       60302    93659136   83  Linux
/dev/sda6           60302       60802     4017152   82  Linux swap / Solaris

---

### Post by simo2 on 2013-09-11
when i try to install the boot-Repair by sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
he wan't find one file ! W: Impossible de récupérer [http://ppa.launchpad.net/venerix/blug/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/venerix/blug/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

---

### Post by varunendra on 2013-09-11
> **simo2 said:**
> when i try to install the boot-Repair by sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update
he wan't find one file ! W: Impossible de récupérer [http://ppa.launchpad.net/venerix/blug/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/venerix/blug/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Because you have added wrong repository for Boot Repair. Disable or delete the current ppa (Alt+F2 > software-properties-gtk > "Other Software" tab > remove the ppa) and add the one given on the wiki page that I linked to in my previous post ([Install Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu") section).

---

