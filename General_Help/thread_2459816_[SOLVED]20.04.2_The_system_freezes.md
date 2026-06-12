---
title: "[SOLVED]*20.04.2 The system freezes"
date: 2021-03-26
forum: General Help
---

### Post by thealpman on 2021-03-26
Hello,

My system started to freeze when I installed some modules to control  lighted keyboard: 
- [https://configurelaptop.eu/clevo-keyboard-backlight-control-for-linux/](https://configurelaptop.eu/clevo-keyboard-backlight-control-for-linux/)
- [https://forums.linuxmint.com/viewtopic.php?t=287190](https://forums.linuxmint.com/viewtopic.php?t=287190)

First  when I try to put it to sleep, then while in  use then on the purple connection screen. 
I have no other solution than to turn it off abruptly and then on again.
The only thing that worked : adding "nomodeset" in the grub file or  starting in recovery mode, but it makes the display very slow, not an  acceptable solution in the long run

My system is 
```
jr@jrubuntu:~$ uname -a
Linux jrubuntu 5.8.0-45-generic #51~20.04.1-Ubuntu SMP Tue Feb 23 13:46:31 UTC 2021 x86_64 x86_64 x86_64 GNU/Linux
jr@jrubuntu:~$ 
```

I ran this :
```
jr@jrubuntu:~$  sudo journalctl -p err
-- Reboot --
mars 26 20:22:50 jrubuntu kernel: tpm tpm0: tpm_try_transmit: send(): error -5
mars 26 20:22:50 jrubuntu kernel: tpm tpm0: [Firmware Bug]: TPM interrupt not working, polling instead
mars 26 20:22:50 jrubuntu kernel: i915 0000:00:02.0: [drm] *ERROR* Port C/TC#1: live status 00000004 mismatches the legacy port flag, fix flag
mars 26 20:22:50 jrubuntu systemd-modules-load[856]: Failed to find module 'clevo-xsm-wmi'
mars 26 20:22:50 jrubuntu systemd-udevd[874]: /etc/udev/rules.d/60-brother-brscan4-libsane-type1.rules:9 Invalid key 'SYSFS'
mars 26 20:22:50 jrubuntu systemd-udevd[874]: /etc/udev/rules.d/60-brother-libsane-type1-inst.rules:14 Invalid key 'SYSFS'
-- Reboot --
jr@jrubuntu:~$
```

So I tried to desinstall this  clevo-xsm-wmi by running (inspired by : [https://forums.linuxmint.com/viewtopic.php?t=287190](https://forums.linuxmint.com/viewtopic.php?t=287190))
```
sudo rmmod clevo-xsm-wmi.ko
```

Which made the problem worse : the system still doesn't run normally but, in recovery mode, now my fan is running at full speed all the time !

I ran boot-repair ([https://webtechmonk.com/boot-repair-in-ubuntu-20-04/](https://webtechmonk.com/boot-repair-in-ubuntu-20-04/)) : [https://paste.ubuntu.com/p/42Vsc56c79/](https://paste.ubuntu.com/p/42Vsc56c79/). It didn't solve the problem.

```
jr@jrubuntu:~$  sudo journalctl -p err
-- Reboot --
mars 27 05:11:10 jrubuntu kernel: tpm tpm0: tpm_try_transmit: send(): error -5
mars 27 05:11:10 jrubuntu kernel: tpm tpm0: [Firmware Bug]: TPM interrupt not working, polling instead
mars 27 05:11:10 jrubuntu kernel: platform idma64.0: failed to claim resource 0: [mem 0x00000800-0x00000fff]
mars 27 05:11:10 jrubuntu kernel: platform i2c_designware.0: failed to claim resource 0: [mem 0x00000000-0x000001ff]
mars 27 05:11:10 jrubuntu kernel: platform idma64.0: failed to claim resource 0: [mem 0x00000800-0x00000fff]
mars 27 05:11:10 jrubuntu kernel: platform i2c_designware.0: failed to claim resource 0: [mem 0x00000000-0x000001ff]
mars 27 05:11:10 jrubuntu kernel: i915 0000:00:02.0: [drm] *ERROR* Port C/TC#1: live status 00000004 mismatches the legacy port flag, fix flag
mars 27 05:11:10 jrubuntu systemd-udevd[873]: /etc/udev/rules.d/60-brother-brscan4-libsane-type1.rules:9 Invalid key 'SYSFS'
mars 27 05:11:10 jrubuntu systemd-udevd[873]: /etc/udev/rules.d/60-brother-libsane-type1-inst.rules:14 Invalid key 'SYSFS'
-- Reboot --

```

Do you have any ideas?

Thanks!


----
My computer : Initia Series (~Clevo)
Processeur i5 Quad Core Intel® Core™ i5-1035G1 (1,0 GHz, 3,6 GHz Turbo)
RAM : 16 Go Corsair 2133 MHz SODIMM DDR4 (2 x 8 Go)
Integrated Intel® HD Graphics

---

### Post by thealpman on 2021-03-26
In case it might be useful
```
 jr@jrubuntu:~$ lspci -nnk | egrep -iA3 "VGA"
 00:02.0 VGA compatible controller [0300]: Intel Corporation Device [8086:8a56] (rev 07)
 	Subsystem: CLEVO/KAPOK Computer Device [1558:40d1]
 	Kernel modules: i915
 00:04.0 Signal processing controller [1180]: Intel Corporation Device [8086:8a03] (rev 03)
 jr@jrubuntu:~$
  
```

---

### Post by thealpman on 2021-03-29
I ran the fixing programs offered during the recovery mode start. It fixed the fan problem, but not the freezing one.
So I used a live USB session and I get a couple error messages when I launch Ubuntu.

[[IMG]https://i.postimg.cc/nMnmBM4T/2021-03-29-18-47.png[/IMG]]("https://postimg.cc/nMnmBM4T")

Could it be related ?

Thank you for your help

---

### Post by thealpman on 2021-04-04
I ran a boot-repair, but it did not solve the problem.
Does someone have an idea ? Thank you !

```
boot-repair-4ppa128                                              [20210401_0952]

============================= Boot Repair Summary ==============================

User choice:

Is there RAID on this computer? no

================================ LVM activation ================================

modprobe dm-mod  
vgscan --mknodes
  Found volume group "vgubuntu" using metadata type lvm2
vgchange -ay
  2 logical volume(s) in volume group "vgubuntu" now active
lvscan
  ACTIVE            '/dev/vgubuntu/root' [929.32 GiB] inherit
  ACTIVE            '/dev/vgubuntu/swap_1' [976.00 MiB] inherit
blkid -g


Error: /dev/mapper/sda3_crypt: unrecognised disk label
Set sda as corresponding disk of mapper/vgubuntu-root
Set sda as corresponding disk of mapper/vgubuntu-root
Set sda as corresponding disk of mapper/vgubuntu-root
/usr/share/boot-sav/bs-cmd_terminal.sh: ligne 177: avertissement : substitution de commande: octet nul ignoré en entrée

Advices: _______________________________________________________________________
Vous souhaiterez peut-être re-essayer après avoir monté vos partitions cryptées afin que l'outil puisse vérifier leur contenu. (http://doc.ubuntu-fr.org/ecryptfs)
Êtes-vous sûr de vouloir continuer quand même ? yes

Recommended repair: ____________________________________________________________

The default repair of the Boot-Repair utility will purge (in order to sign-grub) and reinstall the grub-efi-amd64-signed of
mapper/vgubuntu-root,
using the following options:        sda2/boot, sda1/boot/efi,
Additional repair will be performed: unhide-bootmenu-10s  use-standard-efi-file  restore-efi-backups


/boot/efi added in mapper/vgubuntu-root/fstab
rm /boot/efi/efi/Boot/bootx64.efi
mv /boot/efi/efi/Boot/bkpbootx64.efi /boot/efi/efi/Boot/bootx64.efi
mapper/vgubuntu-root/boot/efi not empty
apt-get -y update
E: Le dépôt https://repo.skype.com/deb stable Release ne contient plus de fichier Release.
E: Le dépôt http://ppa.launchpad.net/webupd8team/indicator-kdeconnect/ubuntu focal Release n'a pas de fichier Release.
E: Le dépôt https://repo.nordvpn.com/deb/nordvpn/debian stable Release ne contient plus de fichier Release.
Purge the GRUB of mapper/vgubuntu-root
grub-efi-amd64-signed available
Lecture des listes de paquets…
Construction de l'arbre des dépendances…SET@_progressbar1.pulse()

Lecture des informations d'état…
Les paquets suivants ont été installés automatiquement et ne sont plus nécessaires :
linux-headers-5.8.0-44-generic linux-hwe-5.8-headers-5.8.0-44
linux-image-5.8.0-44-generic linux-modules-5.8.0-44-generic
linux-modules-extra-5.8.0-44-generic
Veuillez utiliser « sudo apt autoremove » pour les supprimer.
0 mis à jour, 0 nouvellement installés, 1 réinstallés, 0 à enlever et 3 non mis à jour.
Il est nécessaire de prendre 470 ko dans les archives.
Après cette opération, 0 o d'espace disque supplémentaires seront utilisés.
Réception de :1 http://fr.archive.ubuntu.com/ubuntu focal-updates/main amd64 grub-efi-amd64-signed amd64 1.142.11+2.04-1ubuntu26.9 [470 kB]
470 ko réceptionnés en 1s (807 ko/s)
Téléchargement achevé et dans le mode téléchargement uniquement
DEBCHECK debOK, grub-efi-amd64-signed
DEBCHECK debOK
shim-signed available
Please type: sudo dpkg --configure -ansudo apt-get install -fynsudo apt-get install -y lvm2nsudo apt-get purge -y grub*-common shim-signed
shim-signed available
linux-headers-generic available
linux-signed-generic NOT available (apt-cache policy  problem)
Then type: sudo apt-get install -y grub-efi-amd64-signed os-prober shim-signed linux-headers-generic

Unhide GRUB boot menu in mapper/vgubuntu-root/etc/default/grub

============ Reinstall the grub-efi-amd64-signed os-prober shim-signed linux-headers-generic of mapper/vgubuntu-root =============

grub-install --version
grub-install (GRUB) 2.04-1ubuntu26.9

efibootmgr -v from chroot before grub install
BootCurrent: 0004
Timeout: 2 seconds
BootOrder: 0004,2003,0002,2001,2002
Boot0000* EFI PXE 0 for IPv4 (80-FA-5B-8D-67-F6)     PciRoot(0x0)/Pci(0x1d,0x0)/Pci(0x0,0x1)/MAC(80fa5b8d67f6,0)/IPv4(0.0.0.00.0.0.0,0,0)RC
Boot0001* EFI PXE 0 for IPv6 (80-FA-5B-8D-67-F6)     PciRoot(0x0)/Pci(0x1d,0x0)/Pci(0x0,0x1)/MAC(80fa5b8d67f6,0)/IPv6([::]:<->[::]:,0,0)RC
Boot0002* Linpus lite    HD(1,GPT,69d77ddf-009e-4302-87a5-ea1cbd5fec79,0x800,0x100000)/File(EFIBootgrubx64.efi)RC
Boot0004* ubuntu    HD(1,GPT,69d77ddf-009e-4302-87a5-ea1cbd5fec79,0x800,0x100000)/File(EFIubuntushimx64.efi)
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC

uname -r
5.8.0-48-generic

grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot
Installing for x86_64-efi platform.
Installation finished. No error reported.
df /dev/sda1
mv /boot/efi/EFI/Boot/bootx64.efi /boot/efi/EFI/Boot/bkpbootx64.efi
cp /boot/efi/EFI/ubuntu/shimx64.efi /boot/efi/EFI/Boot/bootx64.efi

grub-install --efi-directory=/boot/efi --target=x86_64-efi --uefi-secure-boot
Installing for x86_64-efi platform.
Installation finished. No error reported.

efibootmgr -v from chroot after grub install
BootCurrent: 0004
Timeout: 2 seconds
BootOrder: 0004,2003,0002,2001,2002
Boot0000* EFI PXE 0 for IPv4 (80-FA-5B-8D-67-F6)     PciRoot(0x0)/Pci(0x1d,0x0)/Pci(0x0,0x1)/MAC(80fa5b8d67f6,0)/IPv4(0.0.0.00.0.0.0,0,0)RC
Boot0001* EFI PXE 0 for IPv6 (80-FA-5B-8D-67-F6)     PciRoot(0x0)/Pci(0x1d,0x0)/Pci(0x0,0x1)/MAC(80fa5b8d67f6,0)/IPv6([::]:<->[::]:,0,0)RC
Boot0002* Linpus lite    HD(1,GPT,69d77ddf-009e-4302-87a5-ea1cbd5fec79,0x800,0x100000)/File(EFIBootgrubx64.efi)RC
Boot0004* ubuntu    HD(1,GPT,69d77ddf-009e-4302-87a5-ea1cbd5fec79,0x800,0x100000)/File(EFIubuntushimx64.efi)
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC
Warning: NVram was not modified.

update-grub
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
File descriptor 63 (pipe:[139674]) leaked on vgs invocation. Parent PID 35845: /usr/sbin/grub-probe
File descriptor 63 (pipe:[139674]) leaked on vgs invocation. Parent PID 35845: /usr/sbin/grub-probe
File descriptor 63 (pipe:[139674]) leaked on vgs invocation. Parent PID 35849: /usr/sbin/grub-probe
File descriptor 63 (pipe:[139674]) leaked on vgs invocation. Parent PID 35849: /usr/sbin/grub-probe
File descriptor 63 (pipe:[139674]) leaked on vgs invocation. Parent PID 35853: /usr/sbin/grub-probe
File descriptor 63 (pipe:[139674]) leaked on vgs invocation. Parent PID 35853: /usr/sbin/grub-probe
File descriptor 63 (pipe:[139674]) leaked on vgs invocation. Parent PID 35857: /usr/sbin/grub-probe
File descriptor 63 (pipe:[139674]) leaked on vgs invocation. Parent PID 35857: /usr/sbin/grub-probe
File descriptor 63 (pipe:[139674]) leaked on vgs invocation. Parent PID 35894: /usr/sbin/grub-probe
File descriptor 63 (pipe:[139674]) leaked on vgs invocation. Parent PID 35894: /usr/sbin/grub-probe
Found linux image: /boot/vmlinuz-5.8.0-48-generic
Found initrd image: /boot/initrd.img-5.8.0-48-generic
Found linux image: /boot/vmlinuz-5.8.0-45-generic
Found initrd image: /boot/initrd.img-5.8.0-45-generic
Found linux image: /boot/vmlinuz-5.8.0-44-generic
Found initrd image: /boot/initrd.img-5.8.0-44-generic
File descriptor 63 (pipe:[139674]) leaked on vgs invocation. Parent PID 36380: /usr/sbin/grub-probe
File descriptor 63 (pipe:[139674]) leaked on vgs invocation. Parent PID 36380: /usr/sbin/grub-probe
File descriptor 63 (pipe:[139674]) leaked on lvs invocation. Parent PID 36541: /bin/sh
Adding boot menu entry for UEFI Firmware Settings

Unhide GRUB boot menu in mapper/vgubuntu-root/boot/grub/grub.cfg

Le démarrage de l'ordinateur a été correctement réparé.

Vous pouvez maintenant redémarrer votre ordinateur.

Please do not forget to make your UEFI firmware boot on the L'OS actuellement utilisé - Ubuntu 20.04.2 LTS CurrentSession entry (sda1/EFI/ubuntu/shimx64.efi file) !

============================ Boot Info After Repair ============================
```

---

### Post by thealpman on 2021-12-23
Hello,

The problem is finally solved by a change of RAM!
Apparently Corsair RAM (I had 2x 8GB DDR4) sometimes causes problems with Linux (when everything works fine with Windows).
It was changed by a company specialized in Linux which uses Crucial or Kingston.

I had found a workaround to launch a video in loop in VLC, strangely, it avoided the freezing.

---

