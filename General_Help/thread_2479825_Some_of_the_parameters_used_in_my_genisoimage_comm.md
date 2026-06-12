---
title: "Some of the parameters used in my genisoimage command don’t produce a bootable ISO"
date: 2022-10-09
forum: General Help
---

### Post by marietto2008 on 2022-10-09
Hello.

I'm on Ubuntu 22.04 and I'm trying to extract all the files from a (bootable) Debian ISO and then re-generate a bootable ISO image. Below you can see the commands that I've issued. For some unknown reason,the generated ISO image does not boot. Can someone help me to understand why ? thanks.

```
apt update && apt -y install xorriso genisoimage

wget https://cdimage.debian.org/debian-cd/current/amd64/iso-cd/debian-11.5.0-amd64-netinst.iso

xorriso -osirrox on -indev debian-11.5.0-amd64-netinst.iso -extract / isofiles/

genisoimage -r -J -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -o debian-11-unattended.iso isofiles
```

as you can see I haven't done any modification to the files inside the ISO image,so the error should be most likely on the latest command.

---

### Post by scdbackup on 2022-10-09
Hi,

your genisoimage run does not produce boot lures for EFI which would lead
to GRUB, but only boot lures for legacy BIOS which would lead to ISOLINUX.
So the fact that you see in
  [https://ibb.co/GstvTvR](https://ibb.co/GstvTvR)
a GRUB prompt indicates that this GRUB stems from some other storage medium.
(Shown on [https://askubuntu.com/questions/1434549](https://askubuntu.com/questions/1434549) which is cumbersome for
me to participate.)

Is your QEMU/KVM running with EFI as firmware (OVMF) ? If so, try to get
it started with legacy BIOS (SeaBIOS) and with the ISO as virtual CD-ROM.

For a still valid proposal to repack a Debian amd64 bootable ISO for EFI
and BIOS from CD and USB stick see:
[https://wiki.debian.org/RepackBootableISO#Determine_those_options_which_need_to_be_adapted_on_amd64_or_i386](https://wiki.debian.org/RepackBootableISO#Determine_those_options_which_need_to_be_adapted_on_amd64_or_i386)

Have a nice day :)

Thomas

---

### Post by marietto2008 on 2022-10-09
```
root@Z390-AORUS-PRO-DEST:/home/ziomario/Scrivania/PassT-Cubic/ISO# xorriso -osirrox on -indev debian-live-11.5.0-amd64-xfce.iso -extract / isofiles/

(on the experiment n.2 I have extracted the files with Ark,but the error is still there)

xorriso 1.5.4 : RockRidge filesystem manipulator, libburnia project.

Copying of file objects from ISO image to disk filesystem is: Enabled
xorriso : NOTE : Loading ISO image tree from LBA 0
xorriso : UPDATE :    1386 nodes read in 1 seconds
xorriso : NOTE : Detected El-Torito boot information which currently is set to be discarded
Drive current: -indev 'debian-live-11.5.0-amd64-xfce.iso'
Media current: stdio file, overwriteable
Media status : is written , is appendable
Boot record  : El Torito , MBR isohybrid cyl-align-off GPT
Media summary: 1 session, 1310720 data blocks, 2560m data, 42.2g free
Volume id    : 'd-live 11.5.0 xf amd64'
xorriso : UPDATE :     310 files restored ( 357.9m) in 1 seconds , 270.9xD
xorriso : UPDATE :     310 files restored ( 716.7m) in 2 seconds , 271.6xD
xorriso : UPDATE :     310 files restored (1043.2m) in 3 seconds , 247.1xD
xorriso : UPDATE :     310 files restored (1400.4m) in 4 seconds , 270.5xD
xorriso : UPDATE :     310 files restored (1642.5m) in 5 seconds , 183.2xD
xorriso : UPDATE :     310 files restored (1834.0m) in 6 seconds , 144.6xD
xorriso : UPDATE :     310 files restored (2030.0m) in 7 seconds , 147.9xD
xorriso : UPDATE :     310 files restored (2133.7m) in 8 seconds , 78.4xD
xorriso : UPDATE :     310 files restored (2141.9m) in 9 seconds , 6.2xD
xorriso : UPDATE :     310 files restored (2149.9m) in 10 seconds , 6.0xD
xorriso : UPDATE :     310 files restored (2156.5m) in 11 seconds , 4.9xD
xorriso : UPDATE :     830 files restored (2400.3m) in 12 seconds , 184.5xD
xorriso : UPDATE :    1386 files restored (2556.1m) in 12 seconds = 155.2xD
Extracted from ISO image: file '/'='/home/ziomario/Scrivania/PassT-Cubic/ISO/isofiles'

script.sh

orig_iso=debian-live-11.5.0-amd64-xfce.iso
new_files=isofiles
new_iso=debian-live-11.5.0-amd64-modified-xfce.iso
mbr_template=isohdpfx.bin

# Extract MBR template file to disk
dd if="$orig_iso" bs=1 count=432 of="$mbr_template"

# Create the new ISO image
xorriso -as mkisofs \
   -r -J --joliet-long \
   -V 'Debian' \
   -o "$new_iso" \
   -isohybrid-mbr "$mbr_template" \
   -partition_offset 16 \
   -c isolinux/boot.cat \
   -b isolinux/isolinux.bin \
   -no-emul-boot -boot-load-size 4 -boot-info-table \
   "$new_files"

root@Z390-AORUS-PRO-DEST:/home/ziomario/Scrivania/PassT-Cubic/ISO# ./script.sh

432+0 record dentro
432+0 record fuori
432 bytes copied, 0.000551842 s, 783 kB/s
xorriso 1.5.4 : RockRidge filesystem manipulator, libburnia project.

Drive current: -outdev 'stdio:debian-live-11.5.0-amd64-modified-xfce.iso'
Media current: stdio file, overwriteable
Media status : is blank
Media summary: 0 sessions, 0 data blocks, 0 data, 39.7g free
xorriso : WARNING : -volid text does not comply to ISO 9660 / ECMA 119 rules
Added to ISO image: directory '/'='/home/ziomario/Scrivania/PassT-Cubic/ISO/isofiles'
xorriso : UPDATE :    1386 files added in 1 seconds
xorriso : UPDATE :    1386 files added in 1 seconds
xorriso : NOTE : Copying to System Area: 432 bytes from file '/home/ziomario/Scrivania/PassT-Cubic/ISO/isohdpfx.bin'
libisofs: NOTE : Automatically adjusted MBR geometry to 1018/161/32
libisofs: NOTE : Aligned image size to cylinder size by 246 blocks
xorriso : UPDATE :  7.27% done
xorriso : UPDATE :  81.07% done
xorriso : UPDATE :  95.06% done
ISO image produced: 1311184 sectors
Written to medium : 1311184 sectors at LBA 0
Writing to 'stdio:debian-live-11.5.0-amd64-modified-xfce.iso' completed successfully.

```

the ISO produced is not bootable. Used : UEFI x86_64: /usr/share/OVMF/OVMF_CODE_4M.fd

attached some screenshot...

---

### Post by scdbackup on 2022-10-10
Hi,

your ISO still has no EFI equipment while your firmware is "UEFI x86_64".
It would boot with legacy BIOS as firmware from (virtual) USB stick and
from (virtual) CD-ROM.

To enable booting via UEFI insert before the last line
```
 
"$new_files"

```  
these lines
```
  
-eltorito-alt-boot \
-e boot/grub/efi.img \
-no-emul-boot -isohybrid-gpt-basdat -isohybrid-apm-hfsplus \

```  

I just ran:
```

xorriso -as mkisofs \
    -r -J --joliet-long \
    -V 'Debian' \
    -o "$new_iso" \
    -isohybrid-mbr "$mbr_template" \
    -partition_offset 16 \
    -c isolinux/boot.cat \
    -b isolinux/isolinux.bin \
    -no-emul-boot -boot-load-size 4 -boot-info-table \
    -eltorito-alt-boot \
    -e boot/grub/efi.img \
    -no-emul-boot -isohybrid-gpt-basdat -isohybrid-apm-hfsplus \
    $new_files

```

Inspection by
```

xorriso -indev "$new_iso" -report_system_area plain -report_el_torito plain

```
yields
```

...
MBR partition table:   N Status  Type        Start       Blocks
MBR partition      :   1   0x80  0x00           64       890816
MBR partition      :   2   0x00  0xef         8092         5184
MBR partition path :   2  /boot/grub/efi.img
...
El Torito images   :   N  Pltf  B   Emul  Ld_seg  Hdpt  Ldsiz         LBA
El Torito boot img :   1  BIOS  y   none  0x0000  0x00      4        3319
El Torito boot img :   2  UEFI  y   none  0x0000  0x00   5184        2023
El Torito img path :   1  /isolinux/isolinux.bin
El Torito img opts :   1  boot-info-table isohybrid-suitable
El Torito img path :   2  /boot/grub/efi.img

```
MBR partition 2 is the EFI System Partition for booting from USB stick.
El Torito boot image 2 is the same storage area advertised as boot
opportunity for EFI from CD-ROM.

Have a nice day :)

Thomas

---

### Post by marietto2008 on 2022-10-10
Still does not work :

```
orig_iso=debian-live-11.5.0-amd64-xfce.iso
new_files=debian-live-11.5.0-amd64-xfce
new_iso=debian-live-11.5.0-amd64-modified-xfce.iso
mbr_template=isohdpfx.bin

# Extract MBR template file to disk
dd if="$orig_iso" bs=1 count=432 of="$mbr_template"

xorriso -as mkisofs \
   -r -J --joliet-long \
   -V 'd-live 11.5.0 xf amd64' \
   -o "$new_iso" \
   -isohybrid-mbr "$mbr_template" \
   -partition_offset 16 \
   -c isolinux/boot.cat \
   -b isolinux/isolinux.bin \
   -eltorito-alt-boot \
   -e boot/grub/efi.img \
   -no-emul-boot -isohybrid-gpt-basdat -isohybrid-apm-hfsplus \
   "$new_files"

./script.sh

432+0 record dentro
432+0 record fuori
432 bytes copied, 0.00075784 s, 570 kB/s
xorriso 1.5.4 : RockRidge filesystem manipulator, libburnia project.

Drive current: -outdev 'stdio:debian-live-11.5.0-amd64-modified-xfce.iso'
Media current: stdio file, overwriteable
Media status : is blank
Media summary: 0 sessions, 0 data blocks, 0 data, 40.2g free
xorriso : WARNING : -volid text problematic as automatic mount point name
xorriso : WARNING : -volid text is too long for Joliet (22 > 16)
xorriso : WARNING : -volid text does not comply to ISO 9660 / ECMA 119 rules
Added to ISO image: directory '/'='/home/ziomario/Scrivania/PassT-Cubic/ISO/debian-live-11.5.0-amd64-xfce'
xorriso : UPDATE :    1386 files added in 1 seconds
libisofs: FAILURE : Invalid image size 38 Kb. Must be one of 1.2, 1.44or 2.88 Mb
libisofs: FAILURE : Trying to use an invalid file as boot image
xorriso : FAILURE : Could not attach El-Torito boot image to ISO 9660 image
xorriso : UPDATE :    1386 files added in 1 seconds
xorriso : aborting : -abort_on 'FAILURE' encountered 'FAILURE'
```

---

### Post by scdbackup on 2022-10-10
Hi,

you omitted the modifying options for the -b boot image:
```

-no-emul-boot -boot-load-size 4 -boot-info-table \

```
By the lack of -no-emul-boot, you asked for marking the BIOS boot image
as floppy emulation image. Such an image has to bear the size of an
antique floppy diskette: 1.2 MB (5 1/4 inch), 1.44 MB (3 1/2 inch),
2.88 MB (3 1/2 inch ED).
The ISOLINUX boot image is not a floppy image but rather a 16-bit x86
program, which needs to be announced by -no-emul-boot. Its load size is
only 4 * 512 bytes, because some old BIOS implementations refuse to load
more into memory. Therefore the ISOLINUX boot image has a boot info table
which tells it where to find the rest of its code. This table gets filled
with the correct block address by xorriso (or mkisofs, or genisoimage) if
option -boot-info-table is present.

The missing options have to given before option
```

-eltorito-alt-boot \

```
because that option marks the end of the modifying options of -b and
the begin of a new boot image definition, this time with main option -e.

Have a nice day :)

Thomas

---

### Post by marietto2008 on 2022-10-10
even this version works great,thanks. I'm happy to have fixed that. I've asked in a lot of places for some help and nothing that really worked I found until now. A week has gone only by asking,but now I'm satisfied. Your competence is glaring.

```
orig_iso=debian-live-11.5.0-amd64-xfce.iso
new_files=debian-live-11.5.0-amd64-xfce
new_iso=debian-live-11.5.0-amd64-mod-xfce.iso
mbr_template=isohdpfx.bin

# Extract MBR template file to disk
dd if="$orig_iso" bs=1 count=432 of="$mbr_template"

xorriso -as mkisofs \
   -r -J --joliet-long \
   -V 'd-live 11.5.0 xf amd64' \
   -o "$new_iso" \
   -isohybrid-mbr "$mbr_template" \
   -partition_offset 16 \
   -c isolinux/boot.cat \
   -b isolinux/isolinux.bin \
   -no-emul-boot -boot-load-size 4 -boot-info-table \
   -eltorito-alt-boot \
   -e boot/grub/efi.img \
   -no-emul-boot -isohybrid-gpt-basdat -isohybrid-apm-hfsplus \
   "$new_files"
```

---

### Post by scdbackup on 2022-10-10
Hi,

> Your competence is glaring.

I'm the developer of xorriso. So i am also to blame for the complications,
for which the only excuse is the complicated world of firmwares for which
the various distro ISOs have to be prepared.

If you ever plan to repack ISOs of Ubuntu, Arch, or Fedora, then prepare
for new adventures with different xorriso commands or mkisofs options.

Have a nice day :)

Thomas

---

### Post by scdbackup on 2022-10-10
Hi,

i forgot to ask you to post a final comment to
[https://askubuntu.com/questions/1434549](https://askubuntu.com/questions/1434549) which states that the problem
was in the lack of EFI boot lures: EFI System Partition for USB stick,
EFI El Torito boot image for CD-ROM.

It might help others who come to your post there and would get sent on
the same odyssee as you experienced.

Have a nice day :)

Thomas

---

### Post by marietto2008 on 2022-10-11
I don't like Fedora or arch and derivates. I have always used Debian and derivates. I have evaluated to customize and re-distribute Ubuntu,but in the end I haven't chosen it because behind of it there is a private company,Canonical,that does not let me freely use the Ubuntu logos and pictures because it is a trademark and I should pay to have their certification. I Instead I can use the Debian logo much easier. So I go for Debian.

---

