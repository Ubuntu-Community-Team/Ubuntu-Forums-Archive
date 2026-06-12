---
title: "Windows not recognized in Grub"
date: 2021-10-27
forum: General Help
---

### Post by waffen on 2021-10-27
Hello!!

I have 2 HD in my PC:

HD1 -> Ubuntu 21.10
HD2-> Ubuntu 20.04 & Windows 10

When I did:
 ```
sudo update-grub
```

the result is: 

```

mario@lacunza:~$ sudo update-grub
Obteniendo el archivo «/etc/default/grub»
Obteniendo el archivo «/etc/default/grub.d/init-select.cfg»
Generando un fichero de configuración de grub...
Encontrada imagen de linux: /boot/vmlinuz-5.13.0-20-generic
Encontrada imagen de memoria inicial: /boot/initrd.img-5.13.0-20-generic
Encontrada imagen de linux: /boot/vmlinuz-5.13.0-19-generic
Encontrada imagen de memoria inicial: /boot/initrd.img-5.13.0-19-generic
Encontrado Ubuntu 20.04.2 LTS (20.04) en /dev/sdb6
Adding boot menu entry for UEFI Firmware Settings
hecho

```

So only the Windows is not recognized, any idea how to fix it?

Result of: sudo fdisk -l
```

Disco /dev/sda: 1,82 TiB, 2000398934016 bytes, 3907029168 sectores
Disk model: ST2000VX015-2XG1
Unidades: sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico/físico): 512 bytes / 4096 bytes
Tamaño de E/S (mínimo/óptimo): 4096 bytes / 4096 bytes
Tipo de etiqueta de disco: gpt
Identificador del disco: 99E99A90-1651-4F57-B265-16996D239F1A

Dispositivo Comienzo      Final   Sectores Tamaño Tipo
/dev/sda1       2048       4095       2048     1M Arranque de BIOS
/dev/sda2       4096    1054719    1050624   513M Sistema EFI
/dev/sda3    1054720 3907028991 3905974272   1,8T Sistema de ficheros de Linux


Disco /dev/sdb: 931,51 GiB, 1000204886016 bytes, 1953525168 sectores
Disk model: ST1000DM003-1ER1
Unidades: sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico/físico): 512 bytes / 4096 bytes
Tamaño de E/S (mínimo/óptimo): 4096 bytes / 4096 bytes
Tipo de etiqueta de disco: dos
Identificador del disco: 0x5080fa9e

Dispositivo Inicio  Comienzo      Final   Sectores Tamaño Id Tipo
/dev/sdb1   *           2048    1126399    1124352   549M  7 HPFS/NTFS/exFAT
/dev/sdb2            1126400  551381426  550255027 262,4G  7 HPFS/NTFS/exFAT
/dev/sdb3          551383040  552466431    1083392   529M 27 NTFS de WinRE ocult
/dev/sdb4          552468478 1953523693 1401055216 668,1G  5 Extendida
/dev/sdb5          552468480  571998207   19529728   9,3G 82 Linux swap / Solari
/dev/sdb6          572000256 1953523693 1381523438 658,8G 83 Linux

La partición 4 no empieza en el límite del sector físico.

```

---

### Post by oldfred on 2021-10-27
You have Windows in the old BIOS/MBR configuration. Your Ubuntu gpt partitioned drive shows both a bios_grub partition for BIOS boot and an ESP for UEFI boot. You can have both partitions, but grub normally is installed in one mode or the other.
Windows only boots from MBR drives with BIOS and only from gpt drives with UEFI.
Ubuntu will install in UEFI or BIOS mode from either gpt or MBR(msdos). 

If system is UEFI, better to have Windows in UEFI boot mode. Microsoft has required vendors to install in UEFI boot mode to gpt partitioned drives since Windows 8 released in 2012. Even Windows 7 could be installed in UEFI mode, just not with UEFI Secure Boot on.

UEFI & BIOS are not compatible, once you start booting from UEFI boot menu, you cannot switch boot modes. Or grub can only boot other installs in same boot mode. 

If you do not want to reinstall Windows in UEFI mode, and do not want to only dual boot from UEFI boot menu, you have to reinstall grub in BIOS mode for both Ubuntu installs. Best then to keep a Windows boot loader on Windows drive, and have grub installed to protective MBR & bios_grub on Ubuntu drive that is gpt. 

With two Ubuntu installs, you have to manage which grub install is in charge and change some settings to avoid having to always update both installs to have updated grub menu to boot newest kernel after every kernel update. I can post links on that if desired.

With UEFI hardware you have to always be consistent on how you boot, always UEFI or always BIOS. To boot install media or repair ISO, you have to choose correct mode UEFI or BIOS in UEFI boot menu for both Windows & Ubuntu. And then have to have UEFI set to boot installed systems in that mode either UEFI or BIOS/CSM/Legacy.

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by waffen on 2021-10-27
Thanks for the GREAT explanation! 

Actually I do this when I try to run Windows: at the PC startup  F12 for boot menu, choose the second HD and there I can see my old grub menu and launch Windows with no issues. 

I'm out of my home right now, when I get back I'll post the results.

---

### Post by tea for one on 2021-10-28
Here is a bit more information about boot modes:-
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Your disks also have different partition tables
sda has gpt - [COLOR="#0000FF"]Tipo de etiqueta de disco: gpt[/COLOR]
sdb has dos [COLOR="#0000FF"]Tipo de etiqueta de disco: dos[/COLOR]

You can see that [COLOR="#0000FF"]sdb[/COLOR] contains an extended partition [COLOR="#0000FF"]/dev/sdb4          552468478 1953523693 1401055216 668,1G  5 Extendida[/COLOR],
which is required because msdos partition table only allows 4 primary partitions.

If you decide to re-install Windows 10 and Ubuntu 20.04 on your sdb drive, then gpt should be automatically used and the need for extended partitions is not required.
Management of partitions is a bit easier with GPT.
Also, I reckon Grub will then recognise your Windows installation.

UEFI boot mode and GPT for both disks is the better choice for the future.

If re-installing, it is a good idea to only have the target drive accessible.
Lastly, do not forget backups.

---

### Post by waffen on 2021-10-29
Ok, thanks to all for the explanation! I'll need to reinstall Windows next week, now I'm full with a job I can't do it.

---

