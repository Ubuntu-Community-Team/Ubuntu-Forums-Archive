---
title: "Making Bootable USB from second partition NTFS"
date: 2022-09-20
forum: General Help
---

### Post by inukaze on 2022-09-20
Hi there, the recent days i am trying to make booteable usb on the second partition [16 GB Pendrive]

i make two partitions with NTFS format
The first      11,72 GB 
The second  2,70   GB

[[img]https://i.postimg.cc/ZW1pWCwS/lubuntu-001.png[/img]](https://postimg.cc/ZW1pWCwS)

Reason for make by that way :
1 - Old Windows systems just take the first partition when are FAT32 / exFAT or NTFS

2 - If you put iso file and boot iso file from grub, the live mode does not allow you to mount usb partition because is in using by loopback to read the iso file. But is you had a separated partition you can mount from live mode and edit files, thing i really need.

because in this moment i am using Slackware 64 14.2 after i extract the iso content on the second usb partition i renamed "boot" folder to "boot.lubuntu" and "EFI" to "EFI.lubuntu", and execute the follow commands :

```
USBPART=$(blkid | grep "LUBUNTU" | awk '{print$01}' | sed 's/\/*:$//') ; echo "Particion USB=$USBPART" ; USB=$(echo "$USBPART" | sed 's/[0-9]*//g') ; echo "Dispositivo USB=$USB"

``` -> This for determine partitions based on label "LUBUNTU"

```
ms-sys -b "$USB"
``` -> You can download it from "[http://ms-sys.sourceforge.net/#Download]("http://ms-sys.sourceforge.net/#Download")" , this tool is for write "MBR Sector"

```
mkdir -p  "/run/media/inukaze/LUBUNTU/boot" ; grub-install --recheck --removable --boot-directory="/run/media/inukaze/LUBUNTU/boot" "$USB"
``` --> For make a new boot folder and install grub on the second usb partition

Test with QEmu :
```
reset ; USBPART=$(blkid | grep "LUBUNTU" | awk '{print$01}' | sed 's/\/*:$//') ; echo "Particion USB=$USBPART" ; USB=$(echo "$USBPART" | sed 's/[0-9]*//g') ; echo "Dispositivo USB=$USB" ; PULSE="/opt/pulseaudio-9.0/usr/lib64" ; LD_PRELOAD="$PULSE/libpulse.so.0:$PULSE/pulseaudio/libpulsecommon-9.0.so" /usr/bin/qemu-system-x86_64 -monitor stdio -cpu qemu64 -soundhw ac97 -k es-es -machine accel=kvm -m 768 -drive format=raw,file="$USB" -net nic,macaddr=52:54:00:a2:94:59 -net user,net=10.0.2.0/24,dhcpstart=10.0.2.15,dns=10.0.2.3,hostfwd=tcp::60022-:22 -rtc base=localtime
```

[[img]https://i.postimg.cc/CZH8cDys/qemu-lubuntu2204usb-001.png[/img]](https://postimg.cc/CZH8cDys)[[img]https://i.postimg.cc/zbxgrrGL/qemu-lubuntu2204usb-002.png[/img]](https://postimg.cc/zbxgrrGL)[[img]https://i.postimg.cc/D4mbfMSx/qemu-lubuntu2204usb-003.png[/img]](https://postimg.cc/D4mbfMSx)[[img]https://i.postimg.cc/phWF4TRb/qemu-lubuntu2204usb-004.png[/img]](https://postimg.cc/phWF4TRb)[[img]https://i.postimg.cc/PNqDMPS1/qemu-lubuntu2204usb-005.png[/img]](https://postimg.cc/PNqDMPS1)


I can't make it boot correctly

by now my current grubf.cfg on second usb partition content is the follow :
```
set timeout=30

loadfont ter-u20b
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray

#Inukaze :
insmod part_msdos
set root='(hd0,msdos1)'
#search.fs_uuid 37CB796666F9DB51
##insmod search_fs_uuid search --no-floppy --set=partition --fs-uuid 37CB796666F9DB51

menuentry "Prueba y/o Instala Lubuntu 22.04" {
	insmod part_msdos
	insmod gzio
	insmod ext2
	search --no-floppy --fs-uuid --set=root --set=partition --fs-uuid 37CB796666F9DB51
	set gfxpayload=keep
	linux ($root)/casper/vmlinuz file=/preseed/lubuntu.seed boot=casper ipv6.disable=1 languagechooser/language-name=Spanish countrychooser/shortlist=ES localechooser/supported-locales=es_ES.UTF-8 initrd=/casper/initrd locale=es_ES bootkbd=es console-setup/layoutcode=es toram quiet splash --- 
	initrd ($root)/casper/initrd
}
menuentry "Lubuntu (Graficos Seguros)" {
	insmod part_msdos
	insmod gzio
	insmod ext2
	insmod search_fs_uuid search --no-floppy --set=partition --fs-uuid 37CB796666F9DB51
	set gfxpayload=keep
	linux	/casper/vmlinuz nomodeset file=/preseed/lubuntu.seed quiet splash --- 
	initrd	/casper/initrd
}
grub_platform
if [ "$grub_platform" = "efi" ]; then
menuentry 'Iniciar desde el siguiente volumen' {
	exit 1
}
menuentry 'UEFI - Configurar Firmware' {
	fwsetup
}
else
menuentry 'Probar Memoria RAM' {
	linux16 /boot/memtest86+.bin
}
fi

```



My old method for Lubuntu 16.04 with "syslinux" with 2 Partitions (First NTFS, second FAT32) [8GB Pendrive] , guide on spanish : 
#Pre-Requisitos :
# ms-sys, descargar, compilar e instalar -> [http://ms-sys.sourceforge.net/#Download](http://ms-sys.sourceforge.net/#Download)
# syslinux, descargar desde los repositorios

# en la memoria extraible usb, crear 2 particiones, la primera en ntfs con 6.06 GB (6208 MB) y la segunda con el resto en FAT32
# de etiqueta a la segunda partición colocale "USBDISTRO" y a la primera "casper-rw" (en minúscula, FAT32 no soporta minúsculas, ntfs si, la partición debe ser FAT32 o al intentar iniciarlo veras el error "BOOTMGR is missing")

# Solo coloca casper-rw si quieres persistencia (esto guarda las instalaciones que hagas y configuraciones, por ende también tarda mas en iniciar)


# NOTAS : La ISO que usare sera la de Ubuntu 16.04, si buscas compatibilidad con equipos viejos, usa la de 32 Bits
# Necesitas como mínimo asignarle a la segunda partición 940 MB para únicamente la ISO sin tener espacio adicional para instalar
# Cosas que puedas necesitar.

# Si estas usando un Pendrive por ejemplo de 16 GB, te sugiero dejarle 2GB (2052 MB) a la partición secundaria del pendrive
# Si te preguntas el porque, es para que en en la otra partición, puedas descargar los archivos ".deb" de la arquitectura
# Que te guste usar para instalarlos rápidamente en el sistema.

# Procedimiento sin explicación para automatización :
```
su
```

```
USBPART=$(blkid | grep "LUBUNTU" | awk '{print$01}' | sed 's/\/*:$//') ; echo "Partición USB=$USBPART" ; \
USB=$(echo "$USBPART" | sed 's/[0-9]*//g') ; echo "Dispositivo USB=$USB" ; \
mkdir -p /tmp/usbp2 ; mkdir -p /tmp/lubuntuISO ; \
mount "$USBPART" /tmp/usbp2 ; mount "$HOME/lubuntu-16.04.6-desktop-amd64.iso" /tmp/lubuntuISO -o loop ; chmod 777 -R /tmp/usbp2 ; \
cd "/tmp/lubuntuISO" ; \
cp -rf casper dists install pics pool preseed .disk README.diskdefines /tmp/usbp2/ ; \
cp -rf isolinux /tmp/usbp2/syslinux

```

```
cd /tmp/usbp2/syslinux
mv isolinux.cfg syslinux.cfg
mv isolinux.bin syslinux.bin
syslinux "$USBPART"
ms-sys -s "$USB"
rm -rf "/tmp/usbp2/syslinux/txt.cfg"
rm -rf "/tmp/usbp2/syslinux/exithelp.cfg"
rm -rf "/tmp/usbp2/syslinux/syslinux.cfg"
touch "/tmp/usbp2/syslinux/txt.cfg" 

```

```
echo 'default live
label live
  menu label ^Try lubuntu without installing
  kernel /casper/vmlinuz
  append file=/preseed/lubuntu.seed vga=0x314 boot=casper ipv6.disable=1 languagechooser/language-name=Spanish countrychooser/shortlist=ES localechooser/supported-locales=es_ES.UTF-8 initrd=/casper/initrd locale=es_ES bootkbd=es console-setup/layoutcode=es toram quiet splash ---
label persistent
  menu label ^Try lubuntu without installing
  kernel /casper/vmlinuz
  append file=/preseed/lubuntu.seed vga=0x314 boot=casper persistent ipv6.disable=1 languagechooser/language-name=Spanish countrychooser/shortlist=ES localechooser/supported-locales=es_ES.UTF-8 initrd=/casper/initrd locale=es_ES bootkbd=es console-setup/layoutcode=es toram quiet splash ---
label live-install
  menu label ^Install lubuntu
  kernel /casper/vmlinuz
  append file=/preseed/lubuntu.seed vga=0x314 boot=casper only-ubiquity ipv6.disable=1 languagechooser/language-name=Spanish countrychooser/shortlist=ES localechooser/supported-locales=es_ES.UTF-8 initrd=/casper/initrd locale=es_ES bootkbd=es console-setup/layoutcode=es toram quiet splash ---
label check
  menu label ^Check disc for defects
  kernel /casper/vmlinuz
  append vga=0x314 boot=casper integrity-check initrd=/casper/initrd.lz toram quiet splash ---
label memtest
  menu label Test ^memory
  kernel /install/mt86plus
label hd
  menu label ^Boot from first hard disk
  localboot 0x80' | tee "/tmp/usbp2/syslinux/txt.cfg"
touch "/tmp/usbp2/syslinux/syslinux.cfg"
echo '# D-I config version 2.0
# search path for the c32 support libraries (libcom32, libutil etc.)
MENU HIDDEN
include menu.cfg
default live
prompt 0
timeout 1' | tee "/tmp/usbp2/syslinux/syslinux.cfg"
touch "/tmp/usbp2/syslinux/exithelp.cfg"
echo 'label menu
    kernel vesamenu.c32
    config syslinux.cfg' | tee "/tmp/usbp2/syslinux/exithelp.cfg"

```

```
#En caso de usar la imagen de 32 Bits debes clonar el archivo initrd como initrd.lz#
#cp /tmp/usbp2/casper/initrd /tmp/usbp2/casper/initrd.lz
```

```
cd "$HOME"
```

#Para probar usando QEMU / KVM : 
```
qemu-system-x86_64 \
 -monitor stdio \
 -cpu qemu64 \
 -soundhw ac97 \
 -k es-es \
 -machine accel=kvm \
 -m 768 \
 -drive format=raw,file="$USB" \
 -net nic,macaddr=52:54:00:a2:94:59 \
 -net user,net=10.0.2.0/24,dhcpstart=10.0.2.15,dns=10.0.2.3,hostfwd=tcp::60022-:22 \
 -rtc base=localtime
 -device usb tablet

```
#Para desmontar, borrar temporales y salir
```
umount "$USBPART" ; rm -rf /tmp/usbp2 ; exit
```

END of old method

---

### Post by tea for one on 2022-09-20
> **inukaze said:**
> because in this moment i am using Slackware 64 14.2 
Use Ubuntu 22.04
> i am trying to make booteable usb
**mkusb** is a very good utility [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
There are various options with mkusb including:-
[LIST]
[*]Adding persistence with an ext4 partition
[*]Using the spare space on the usb drive  for a Windows shared partition using ntfs  
[*]Able to boot in Legacy mode and UEFI mode
[/LIST]
What more could you want?

Here is the terminal output of a 16GB Sandisk USB:-
```
user@user-22-04:~$ lsblk -e 7 -o name,size,type,fstype,fsuse%,fsavail,mountpoint 
NAME          SIZE TYPE FSTYPE  FSUSE% FSAVAIL MOUNTPOINT
sdb          14.5G disk                        
&#9500;&#9472;sdb1        5.4G part [COLOR="#0000FF"]ntfs[/COLOR]        1%    5.3G /media/user/usbdata
&#9500;&#9472;sdb2        977K part [COLOR="#0000FF"]to boot in Legacy mode[/COLOR]                      
&#9500;&#9472;sdb3      244.1M part vfat  [COLOR="#0000FF"]to boot in UEFI mode[/COLOR]                 
&#9500;&#9472;sdb4        3.6G part iso9660   100%       0 /media/user/Ubuntu 22.04.1 LTS am
&#9492;&#9472;sdb5        5.4G part [COLOR="#0000FF"]ext4[/COLOR]        3%    4.8G /media/user/writable
```

---

### Post by inukaze on 2022-09-20
> **tea for one said:**
> Use Ubuntu 22.04
You mean just for use the "grub-install" ?

> **tea for one said:**
> **mkusb** is a very good utility [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
There are various options with mkusb including:-
[LIST]
[*]Adding persistence with an ext4 partition
[*]Using the spare space on the usb drive  for a Windows shared partition using ntfs  
[*]Able to boot in Legacy mode and UEFI mode
[/LIST]
What more could you want?

No Replace whole disk, just limit to the partiton i choose. and not use "persistence file" ( just is extremely slow to boot when exist, normally lubuntu from usb take around 15 mins start on my machine, Slackware 15.0 Xfce from usb can boot in 3 mins, lubuntu + persistence file need around 1 hour to boot from usb )

> **tea for one said:**
> Here is the terminal output of a 16GB Sandisk USB:-
```
user@user-22-04:~$ lsblk -e 7 -o name,size,type,fstype,fsuse%,fsavail,mountpoint 
NAME          SIZE TYPE FSTYPE  FSUSE% FSAVAIL MOUNTPOINT
sdb          14.5G disk                        
&#9500;&#9472;sdb1        5.4G part [COLOR="#0000FF"]ntfs[/COLOR]        1%    5.3G /media/user/usbdata
&#9500;&#9472;sdb2        977K part [COLOR="#0000FF"]to boot in Legacy mode[/COLOR]                      
&#9500;&#9472;sdb3      244.1M part vfat  [COLOR="#0000FF"]to boot in UEFI mode[/COLOR]                 
&#9500;&#9472;sdb4        3.6G part iso9660   100%       0 /media/user/Ubuntu 22.04.1 LTS am
&#9492;&#9472;sdb5        5.4G part [COLOR="#0000FF"]ext4[/COLOR]        3%    4.8G /media/user/writable
```

Thanks for you answer, i am looking for a manual method of make i need, i need understand how work it
well i am going to read how works the liveslak scripts looking for info.

---

### Post by tea for one on 2022-09-21
I wrote "Use Ubuntu" because mkusb works perfectly within Ubuntu.
mkusb will install grub to your USB drive.
Persistence is not mandatory, it is a user choice.

Anyway, I hope that you are successful with your preference for a manual method of making a bootable USB device.

---

### Post by guiverc on 2022-09-21
> **inukaze said:**
> You mean just for use the "grub-install" ?


No Replace whole disk, just limit to the partiton i choose. and not use "persistence file" ( just is extremely slow to boot when exist, normally lubuntu from usb take around 15 mins start on my machine, Slackware 15.0 Xfce from usb can boot in 3 mins, lubuntu + persistence file need around 1 hour to boot from usb )



The slow booting, plus time to start (15 mins) reminds me of this issue

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1922342](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1922342)

Ubuntu modified the way systems boot starting with *groovy* (20.10) where some boxes firmware has *issues* with it (ie. *bugs or non-standards-compliant code in the firmware on boxes make it very slow*). This causes boots to be very slow; ~10 mins for Lubuntu (*times vary on boxes & how you measure the boot time*) and longer for other *flavors* or main Ubuntu.

There are ways to *speed* that up, as I recall I added a little on the [Lubuntu *discourse *]("https://discourse.lubuntu.me/t/slow-boot-times-of-lubuntu-22-04-lts-on-some-hardware/3280")but I've not updated that in awhile. Probably the best place to look in the final comment on that bug report, as I've not yet actioned that (*it's on my todo list*), and that is where I hope I'll find *reminders* of the issue (*there are other related bug reports, but links exist if you look*)

I've left this comment mostly due to the *slow boot* comment... I've booted ISOs from partitions quite a lot, alas not for years, but I just used to `dd` the ISO to a partition & manually modified the grub of the booting system to offer that as an option on boot.

---

### Post by yancek on 2022-09-21
>  For make a new boot folder and install grub on the second usb partition 

You have an msdos (legacy) drive according to the information you posted so you would need to install Grub to the MBR pointing to the /boot/grub directory on the second partition. 

>   you can mount from live mode and edit files 

If you have loop mounted or extracted the Lubuntu iso and copied the directories/files to the second partition, your entries for grub.cfg appear correct and you should be able to edit them.

Do you have the i386-pc directory in the grub director on the usb?  Error in your first image.

---

### Post by inukaze on 2022-09-21
Thanks for the information, i am reading about mkusb , mkusb-dus, etc , and well i am going to backup pendrive content first

Just for prevent this :
[https://help.ubuntu.com/community/mkusb#WARNING:_mkusb_will_overwrite_the_entire_target_device](https://help.ubuntu.com/community/mkusb#WARNING:_mkusb_will_overwrite_the_entire_target_device)

For make test with mkusb and their variants.

Two last questions :

1 - which tool you recommend to make a custom iso based on lubuntu for put on usb stick ?

2 - Just for curiosity, ubuntu server still not had a variant without : snap, pulseaudio, avahi, systemd, flatpak ? ( that things are the main reason i migrate from ubuntu to another distros )

---

### Post by tea for one on 2022-09-21
> **inukaze said:**
> which tool you recommend to make a custom iso based on lubuntu for put on usb stick ?
I assume that you have already installed Ubuntu or an Ubuntu family member [https://launchpad.net/cubic](https://launchpad.net/cubic)

---

### Post by inukaze on 2022-09-21
Thanks for the information, i am reading about mkusb , mkusb-dus, etc , and well i am going to backup pendrive content first

Just for prevent this :
[https://help.ubuntu.com/community/mkusb#WARNING:_mkusb_will_overwrite_the_entire_target_device](https://help.ubuntu.com/community/mkusb#WARNING:_mkusb_will_overwrite_the_entire_target_device)

For make test with mkusb and their variants.

Just for curiosity, ubuntu server still not had a variant without : snap, pulseaudio, avahi, systemd ?

---

### Post by inukaze on 2022-09-21
Well trying to use mkusb on Slackware64 14.2 : i open the follow site on web browser to get links -> [https://ppa.launchpadcontent.net/mkusb/ppa/ubuntu/pool/main/m/mkusb/](https://ppa.launchpadcontent.net/mkusb/ppa/ubuntu/pool/main/m/mkusb/)

```
mkdir -p /tmp/deb/txz
cd /tmp/deb/

wget -c 'https://ppa.launchpadcontent.net/mkusb/ppa/ubuntu/pool/main/m/mkusb/mkusb-common_22.1.1-1ubuntu1_all.deb'
wget -c 'https://ppa.launchpadcontent.net/mkusb/ppa/ubuntu/pool/main/m/mkusb/mkusb_22.1.1-1ubuntu1_all.deb'
wget -c 'https://ppa.launchpadcontent.net/mkusb/ppa/ubuntu/pool/main/m/mkusb/usb-pack-efi_22.1.1-1ubuntu1_all.deb'
wget -c 'https://ppa.launchpadcontent.net/mkusb/ppa/ubuntu/pool/main/m/mkusb/mkusb-plug_22.1.1-1ubuntu1_all.deb'
wget -c 'https://ppa.launchpadcontent.net/mkusb/ppa/ubuntu/pool/main/m/mkusb/mkusb-nox_22.1.1-1ubuntu1_all.deb'
wget -c 'https://ppa.launchpadcontent.net/mkusb/ppa/ubuntu/pool/main/m/mkusb/dus_22.1.1-1ubuntu1_all.deb'
wget -c 'https://ppa.launchpadcontent.net/mkusb/ppa/ubuntu/pool/main/m/mkusb/guidus_22.1.1-1ubuntu1_all.deb'

for i in *.deb ; do "deb2tgz" "${i%.*}.deb" ; done
mv *.txz ./txz/
cd txz
su
for i in *.txz ; do "installpkg" "${i%.*}.txz" ; ldconfig ; done
```

installpkg output :

> Verifying package dus_22.1.1-1ubuntu1_all.txz.
Installing package dus_22.1.1-1ubuntu1_all.txz:
PACKAGE DESCRIPTION:
WARNING:  Package has not been created with 'makepkg'
Package dus_22.1.1-1ubuntu1_all.txz installed.

Verifying package guidus_22.1.1-1ubuntu1_all.txz.
Installing package guidus_22.1.1-1ubuntu1_all.txz:
PACKAGE DESCRIPTION:
WARNING:  Package has not been created with 'makepkg'
Package guidus_22.1.1-1ubuntu1_all.txz installed.

Verifying package mkusb_22.1.1-1ubuntu1_all.txz.
Installing package mkusb_22.1.1-1ubuntu1_all.txz:
PACKAGE DESCRIPTION:
WARNING:  Package has not been created with 'makepkg'
Package mkusb_22.1.1-1ubuntu1_all.txz installed.

Verifying package mkusb-common_22.1.1-1ubuntu1_all.txz.
Installing package mkusb-common_22.1.1-1ubuntu1_all.txz:
PACKAGE DESCRIPTION:
WARNING:  Package has not been created with 'makepkg'
Package mkusb-common_22.1.1-1ubuntu1_all.txz installed.

Verifying package mkusb-nox_22.1.1-1ubuntu1_all.txz.
Installing package mkusb-nox_22.1.1-1ubuntu1_all.txz:
PACKAGE DESCRIPTION:
WARNING:  Package has not been created with 'makepkg'
Package mkusb-nox_22.1.1-1ubuntu1_all.txz installed.

Verifying package mkusb-plug_22.1.1-1ubuntu1_all.txz.
Installing package mkusb-plug_22.1.1-1ubuntu1_all.txz:
PACKAGE DESCRIPTION:
WARNING:  Package has not been created with 'makepkg'
Package mkusb-plug_22.1.1-1ubuntu1_all.txz installed.

Verifying package usb-pack-efi_22.1.1-1ubuntu1_all.txz.
Installing package usb-pack-efi_22.1.1-1ubuntu1_all.txz:
PACKAGE DESCRIPTION:
WARNING:  Package has not been created with 'makepkg'
Package usb-pack-efi_22.1.1-1ubuntu1_all.txz installed.

mkusb - dus mode :
```
mkusb
---------------------------------------------------------------------
Usage: mkusb [input-file]      # optional parameter
---------------------------------------------------------------------
d:  dus , guidus, mkusb-dus    - Classic, easy to use
p: Plug,   mkusb-plug          - New, easy to use
n: NoX,    sudo mkusb-nox      - original text mode
b: Bas,    sudo mkusb-bas      - basic text mode for old/basic linux
e: Eleven, sudo -H mkusb-11    - Old user interface
q: Quit
---------------------------------------------------------------------
Select version of mkusb (d/p/n/b/e/q) d
 dus 22.1.1 
 p_toolsel starts here ...
Drive that contains source file: /dev/sda
Live drive, that is booted from: /dev/sda
mktemp: invalid option -- '-'
Usage: mktemp [-V] | [-dqtu] [-p prefix] [template]
mktemp: invalid option -- '-'
Usage: mktemp [-V] | [-dqtu] [-p prefix] [template]
mktemp: invalid option -- '-'
Usage: mktemp [-V] | [-dqtu] [-p prefix] [template]
mktemp: invalid option -- '-'
Usage: mktemp [-V] | [-dqtu] [-p prefix] [template]
mktemp: invalid option -- '-'
Usage: mktemp [-V] | [-dqtu] [-p prefix] [template]
mktemp: invalid option -- '-'
Usage: mktemp [-V] | [-dqtu] [-p prefix] [template]
/usr/bin/dus: line 1854: : No such file or directory
/usr/bin/dus: line 1848: : No such file or directory
/usr/bin/dus: line 1848: : No such file or directory
/usr/bin/dus: line 1927: : No such file or directory
/usr/bin/dus: line 1928: : No such file or directory
/usr/bin/dus: line 1929: : No such file or directory
rm: cannot remove '': No such file or directory
rm: cannot remove '': No such file or directory
/usr/bin/dus: línea 2006: : No existe el fichero o el directorio
/usr/bin/dus: línea 2019: : No existe el fichero o el directorio
cat: '': No existe el fichero o el directorio
 No suitable target device found 
p_target: target=/dev/
No target device or bad target device
mktemp: invalid option -- '-'
Usage: mktemp [-V] | [-dqtu] [-p prefix] [template]
Drive that contains source file: /dev/sda
Live drive, that is booted from: /dev/sda
mktemp: invalid option -- '-'
Usage: mktemp [-V] | [-dqtu] [-p prefix] [template]
mktemp: invalid option -- '-'
Usage: mktemp [-V] | [-dqtu] [-p prefix] [template]
mktemp: invalid option -- '-'
Usage: mktemp [-V] | [-dqtu] [-p prefix] [template]
mktemp: invalid option -- '-'
Usage: mktemp [-V] | [-dqtu] [-p prefix] [template]
mktemp: invalid option -- '-'
Usage: mktemp [-V] | [-dqtu] [-p prefix] [template]
mktemp: invalid option -- '-'
Usage: mktemp [-V] | [-dqtu] [-p prefix] [template]
/usr/bin/dus: line 1854: : No such file or directory
/usr/bin/dus: line 1848: : No such file or directory
/usr/bin/dus: line 1848: : No such file or directory
/usr/bin/dus: line 1927: : No such file or directory
/usr/bin/dus: line 1928: : No such file or directory
/usr/bin/dus: line 1929: : No such file or directory
rm: cannot remove '': No such file or directory
rm: cannot remove '': No such file or directory
/usr/bin/dus: línea 2006: : No existe el fichero o el directorio
/usr/bin/dus: línea 2019: : No existe el fichero o el directorio
cat: '': No existe el fichero o el directorio
 No suitable target device found 
p_target: target=/dev/
No target device or bad target device
p_clean:
clean if necessary and return
 p_toolsel starts here ...
Drive that contains source file: /dev/sda
Live drive, that is booted from: /dev/sda
mktemp: invalid option -- '-'
Usage: mktemp [-V] | [-dqtu] [-p prefix] [template]
mktemp: invalid option -- '-'
Usage: mktemp [-V] | [-dqtu] [-p prefix] [template]
mktemp: invalid option -- '-'
Usage: mktemp [-V] | [-dqtu] [-p prefix] [template]
mktemp: invalid option -- '-'
Usage: mktemp [-V] | [-dqtu] [-p prefix] [template]
mktemp: invalid option -- '-'
Usage: mktemp [-V] | [-dqtu] [-p prefix] [template]
mktemp: invalid option -- '-'
Usage: mktemp [-V] | [-dqtu] [-p prefix] [template]
/usr/bin/dus: line 1854: : No such file or directory
/usr/bin/dus: line 1848: : No such file or directory
/usr/bin/dus: line 1848: : No such file or directory
/usr/bin/dus: line 1927: : No such file or directory
/usr/bin/dus: line 1928: : No such file or directory
/usr/bin/dus: line 1929: : No such file or directory
rm: cannot remove '': No such file or directory
rm: cannot remove '': No such file or directory
/usr/bin/dus: línea 2006: : No existe el fichero o el directorio
/usr/bin/dus: línea 2019: : No existe el fichero o el directorio
cat: '': No existe el fichero o el directorio
 No suitable target device found 
p_target: target=/dev/
No target device or bad target device
clean if necessary and return
clean if necessary and return
clean if necessary and quit
```

mkusb - Plug :
```
---------------------------------------------------------------------
Usage: mkusb [input-file]      # optional parameter
---------------------------------------------------------------------
d:  dus , guidus, mkusb-dus    - Classic, easy to use
p: Plug,   mkusb-plug          - New, easy to use
n: NoX,    sudo mkusb-nox      - original text mode
b: Bas,    sudo mkusb-bas      - basic text mode for old/basic linux
e: Eleven, sudo -H mkusb-11    - Old user interface
q: Quit
---------------------------------------------------------------------
Select version of mkusb (d/p/n/b/e/q) p
which: no mkfs.exfat in (/media/Compartido/Videojuegos/Gestor/Linux/Steam/Slackware64/home/bin/:/usr/local/sbin:/usr/local/bin:/sbin:/usr/sbin:/bin:/usr/bin)
 'mkfs.exfat' not in PATH 
Please consider installing it and/or copy it into '/usr/local/sbin'
maybe easiest to use the 'installer' that comes with the tarball.
Optional tool - Press Enter to continue 
----------------------------------------------------------------
source file: '/media/Slack32/lubuntu-22.04-desktop-amd64.iso'
--{vfat|exfat|ntfs}
*** usbfs ***
spawn bash -c xorriso-dd-target -plug_test -trust_lsblk_udev  | tee /tmp/tmp.VAq34G

Caused by option -plug_test: Attempt to find the desired device
by watching it appear after being plugged in.

Step 1:
Please make sure that the desired target device is plugged _out_ now.
If it is currently plugged in, make sure to unmount all its fileystems
and then unplug it.
Press the Enter key when ready.
 
Found and noted as _not_ desired:  sda sdb sdc  

Step 2:
Please plug in the desired target device and then press the Enter key.
 
Waiting up to 10 seconds for a new device to be listed ... found: sdh
Now waiting 5 seconds to let it settle .........
Found and noted as desired device:  sdh

sdh : NO  : usb+ has_ntfs- : Verbatim STORE N GO 
Repeating test of target device with elevated permissions:
target device: /dev/sdh
 sdh : NO  : usb+ has_ntfs- : Verbatim STORE N GO  
         task: '--ntfs'
  source file: '/media/Slack32/lubuntu-22.04-desktop-amd64.iso'
target device:  /dev/sdh

MODEL            NAME FSTYPE LABEL    SIZE
STORE N GO       sdh                 14,4G
                 sdh1 ntfs   Inukaze 11,7G
                 sdh2 ntfs   LUBUNTU  2,7G
          ***** datp: live with ntfs data partition ***** 
Trying to unmount partitions if mounted on the target device
umount: /dev/sdh: no montado
umount: /dev/sdh1: no montado
umount: /dev/sdh2: no montado
gpt_zap: done
--------------------------------------------------------------------------------
 Please wait until the process has finished and 'Done' is written 
..... Flash modified iso file to target ........................................
2606266368=file size
2605711360 bytes (2,6 GB, 2,4 GiB) copied, 775,937 s, 3,4 MB/s 
2485+1 registros leídos
2485+1 registros escritos
2606266368 bytes (2,6 GB, 2,4 GiB) copied, 776,171 s, 3,4 MB/s
----- cleanup after dd ------------------------------------------
 3450 pts/1    00:00:00 mkusb-sedd
/usr/sbin/mkusb-sedd: línea 678:  3450 Terminado               ( while true; do
    sleep 2; tmpline=$(tr '\015' '\n' < "$tmpfile" | tail -n1); tmpstr=${tmpline%% *}; tproc=$(((100*tmpstr+50)/size)); echo "$tproc
# $tmpline" >> "$tailfile";
done )
Warning: Not all of the space available to /dev/sdh appears to be used, you can fix the GPT to use all of the space (an extra 25162692 blocks) or continue with the current setting? 
/dev/sdh3 after flashing
Warning: Not all of the space available to /dev/sdh appears to be used, you can fix the GPT to use all of the space (an extra 25162692 blocks) or continue with the current setting? 
gpt_fix ...
gpt_fix: done :-)
..... Create partition .........................................................

Bienvenido a fdisk (util-linux 2.27.1).
Los cambios solo permanecerán en la memoria, hasta que decida escribirlos.
Tenga cuidado antes de utilizar la orden de escritura.


Orden (m para obtener ayuda): Número de partición (4-248, valor predeterminado 4): El valor está fuera del rango.
Número de partición (4-248, valor predeterminado 4): Primer sector (5090300-30252992, valor predeterminado 5091328): Último sector, +sectores o +tamaño{K,M,G,T,P} (5091328-30252992, valor predeterminado 30252992): 
Crea una nueva partición 4 de tipo 'Linux filesystem' y de tamaño 12 GiB.

Orden (m para obtener ayuda): Se ha modificado la tabla de particiones.
Llamando a ioctl() para volver a leer la tabla de particiones.
Fallo al leer de nuevo la tabla de particiones.: Dispositivo o recurso ocupado

El núcleo todavía usa la tabla antigua. La nueva tabla se usará en el próximo reinicio o después de que usted ejecute partprobe(8) o kpartx(8).

prober: /dev/sdh4 for persistence
..... Overwrite first mibibyte of partition ....................................
umount: /dev/sdh: no montado
umount: /dev/sdh1: no montado
umount: /dev/sdh2: no montado
umount: /dev/sdh3: no montado
umount: /dev/sdh4: no montado
1024+0 registros leídos
1024+0 registros escritos
1048576 bytes (1,0 MB, 1,0 MiB) copied, 0,133409 s, 7,9 MB/s
..... Create file system in usbdata partition  .................................
Cluster size has been automatically set to 4096 bytes.
Creating NTFS volume structures.
mkntfs completed successfully. Have a nice day.
Finally, please wait for a few more seconds ...
--------------------------------------------------------------------------------
NAME MODEL            FSTYPE  LABEL                   MOUNTPOINT  SIZE NAME
sdh  STORE N GO       iso9660 Lubuntu 22.04 LTS amd64            14,4G sdh
sdh1                  iso9660 Lubuntu 22.04 LTS amd64             2,4G sdh1
sdh2                  vfat    ESP                                 4,2M sdh2
sdh3                  iso9660 Lubuntu 22.04 LTS amd64             300K sdh3
sdh4                  ntfs    usbdata                              12G sdh4
```

[[img]https://i.postimg.cc/bZfh4LCt/lubuntu-002-mkusb.png[/img]](https://postimg.cc/bZfh4LCt)

QEmu Test :
```
USBPART=$(blkid | grep "Lubuntu 22.04 LTS amd64" | awk '{print$01}' | sed 's/\/*:$//') ; echo "Particion USB=$USBPART" ; USB=$(echo "$USBPART" | sed 's/[0-9]*//g') ; echo "Dispositivo USB=$USB" ; PULSE="/opt/pulseaudio-9.0/usr/lib64" ; LD_PRELOAD="$PULSE/libpulse.so.0:$PULSE/pulseaudio/libpulsecommon-9.0.so" /usr/bin/qemu-system-x86_64 -monitor stdio -cpu qemu64 -soundhw ac97 -k es-es -machine accel=kvm -m 768 -drive format=raw,file="$USB" -net nic,macaddr=52:54:00:a2:94:59 -net user,net=10.0.2.0/24,dhcpstart=10.0.2.15,dns=10.0.2.3,hostfwd=tcp::60022-:22 -rtc base=localtime
```

> Particion USB=/dev/sdh1
Dispositivo USB=/dev/sdh
QEMU 4.1.0 monitor - type 'help' for more information
(qemu) 


Well its exactly the same result :
[[img]https://i.postimg.cc/QVTDxRWz/lubuntu-003-mkusb.png[/img]](https://postimg.cc/QVTDxRWz)[[img]https://i.postimg.cc/LgDFFMnQ/lubuntu-004-mkusb.png[/img]](https://postimg.cc/LgDFFMnQ)[[img]https://i.postimg.cc/0KP14N2J/lubuntu-005-mkusb.png[/img]](https://postimg.cc/0KP14N2J)[[img]https://i.postimg.cc/7bn5ZGzd/lubuntu-006-mkusb.png[/img]](https://postimg.cc/7bn5ZGzd)

---

### Post by inukaze on 2022-09-22
i had create three partitons :

Inukaze 	=> 11.72 GB (	12003 MB	)	NTFS
USB-Inicio	=> 100 MB				EXT2 -> Set boot
Lubuntu	=> 2.43 GB   (	2688	MB	)	FAT32

[[img]https://i.postimg.cc/qzDFxLch/lubuntu-usb-001.png[/img]](https://postimg.cc/qzDFxLch)

#Access like root
```
su
```

#Determinate device and partitions : Boot (Inicio) & Distro (Lubuntu)
```
USBPARTDISTRO=$(blkid | grep "LUBUNTU" | awk '{print$01}' | sed 's/\/*:$//') ; echo "Particion USB-Distro=$USBPARTDISTRO" ; USB=$(echo "$USBPARTDISTRO" | sed 's/[0-9]*//g') ; USBPARTBOOT=$(blkid | grep "USB-Inicio" | awk '{print$01}' | sed 's/\/*:$//') ; echo "Particion USB-Inicio=$USBPARTBOOT" ; USB=$(echo "$USBPARTBOOT" | sed 's/[0-9]*//g') ; echo "Dispositivo USB=$USB"
```

#Create folders in case does not exist :
```
mkdir -p /run/media/inukaze/{USB-Inicio,LUBUNTU}
```

#Mount Partitions
```
mount "$USBPARTBOOT" "/run/media/inukaze/USB-Inicio"
mount "$USBPARTDISTRO" "/run/media/inukaze/LUBUNTU"
```

#Set 2 Values with the paths i need
```
BOOT="/run/media/inukaze/USB-Inicio"
LUBUNTU="/run/media/inukaze/LUBUNTU"
```

#Write permissions on the mount points i need :
```
chmod 777 -R "$BOOT" ; chmod 777 -R "$LUBUNTU"
```

#ms-sys : Write Master Boot Record (MBR) with GRUB2 Format on USB Device :
```
ms-sys -b "$USB"
```

#Install GRUB2 on USB Partition
```
grub-install --recheck --removable --boot-directory="$BOOT" "$USB"
```

[[img]https://i.postimg.cc/Bj8VYKNh/lubuntu-usb-002.png[/img]](https://postimg.cc/Bj8VYKNh)

#Mount Lubuntu 22.04 ISO & Copy all need content to usb partition
```
ISO="/media/Slack32/lubuntu-22.04-desktop-amd64.iso"
mkdir -p /tmp/ISO
mount "$ISO" "/tmp/ISO" -o loop 
cd "/tmp/ISO"
cp -rf ".disk" "boot" "casper" "dists" "EFI" "install" "pool" "preseed"  "boot.catalog" "md5sum.txt" "$LUBUNTU/"
```

[[img]https://i.postimg.cc/YvJyJCst/lubuntu-usb-003.png[/img]](https://postimg.cc/YvJyJCst)

#You must Generate the "grub.cfg" for right boot from menu entry om GRUB2 : 
```
echo 'set timeout=30

loadfont ter-u20b
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
insmod ext2
set root='"'(hd0,msdos3)'"'

menuentry "'"Prueba o Instala Lubuntu 22.04"'" {
	insmod part_msdos
	insmod gzio
	search.fs_uuid '$(blkid $USBPARTDISTRO | awk '{print $3}' | sed -n 's/.*UUID=\"\([^\"]*\)\".*/\1/p')'
	set gfxpayload=keep
	''linux     /casper/vmlinuz file=/preseed/lubuntu.seed boot=casper ipv6.disable=1 languagechooser/language-name=Spanish countrychooser/shortlist=ES localechooser/supported-locales=es_ES.UTF-8 initrd=/casper/initrd locale=es_ES bootkbd=es console-setup/layoutcode=es toram quiet splash --- ''
	''initrd    /casper/initrd''
}
menuentry "'"Lubuntu (Graficos Seguros)"'" {
	insmod part_msdos
	insmod gzio
	insmod search_fs_uuid search --no-floppy --set=partition --fs-uuid '$(blkid $USBPARTDISTRO | awk '{print $3}' | sed -n 's/.*UUID=\"\([^\"]*\)\".*/\1/p')'
	set gfxpayload=keep
	''linux	    /casper/vmlinuz nomodeset file=/preseed/lubuntu.seed quiet splash --- ''
	''initrd    /casper/initrd''
}
grub_platform
if [ "$grub_platform" = "efi" ]; then
menuentry '"'Iniciar desde el siguiente volumen'"' {
	exit 1
}
menuentry '"'UEFI - Configurar Firmware'"' {
	fwsetup
}
else
menuentry '"'Probar Memoria RAM'"' {
	linux16 /boot/memtest86+.bin
}
fi
' | tee "$BOOT/grub/grub.cfg"
```

[[img]https://i.postimg.cc/Ff3nmXM3/lubuntu-usb-004.png[/img]](https://postimg.cc/Ff3nmXM3)

#Notice the UUID is now set on the output of echo
[[img]https://i.postimg.cc/8JbKJBPC/lubuntu-usb-005.png[/img]](https://postimg.cc/8JbKJBPC)

#Test with QEmu : You need minimal set 2 GB RAM (-m 2048)
```
USBPART=$(blkid | grep "LUBUNTU" | awk '{print$01}' | sed 's/\/*:$//') ; echo "Particion USB=$USBPART" ; USB=$(echo "$USBPART" | sed 's/[0-9]*//g') ; echo "Dispositivo USB=$USB" ; PULSE="/opt/pulseaudio-9.0/usr/lib64" ; LD_PRELOAD="$PULSE/libpulse.so.0:$PULSE/pulseaudio/libpulsecommon-9.0.so" /usr/bin/qemu-system-x86_64 -monitor stdio -cpu qemu64 -soundhw ac97 -k es-es -machine accel=kvm -m 2048 -drive format=raw,file="$USB" -net nic,macaddr=52:54:00:a2:94:59 -net user,net=10.0.2.0/24,dhcpstart=10.0.2.15,dns=10.0.2.3,hostfwd=tcp::60022-:22 -rtc base=localtime
```

[[img]https://i.postimg.cc/1V5Wpnfr/lubuntu-usb-006.png[/img]](https://postimg.cc/1V5Wpnfr)
"This forum force me to not include the another 2 links"
[[img]https://i.postimg.cc/Mnj9b8KN/lubuntu-usb-009.png[/img]](https://postimg.cc/Mnj9b8KN)[[img]https://i.postimg.cc/gLJDxCTM/lubuntu-usb-010.png[/img]](https://postimg.cc/gLJDxCTM)

Now is solved.

Note : i had try to make the sane but just with two ntfs partitions but when you do that grub just says "no such device" & "you must load a kernel first"

 i will going trying to put directly my Slackware 15.0 on the usb distro partition just for test is possible to use by that way on live mode without liveslak scripts XD

---

