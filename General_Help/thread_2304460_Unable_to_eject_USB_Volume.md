---
title: "Unable to eject USB Volume"
date: 2015-11-26
forum: General Help
---

### Post by Daneel.Olivaw on 2015-11-26
Hi!
I'm using Xubuntu 15.04 and seem to have a problem dealing with USB drives. When I plug any thumstick it automounts and behaves well, but I cannot unmout it. Clicking "eject" or the unmount icon in Nautilus or Thunar gives me this error:

> Failed to eject "7,9 GB Volume".
Error unmounting /dev/sdb1: Command-line `umount  "/media/elio/853E-94BC"' exited with non-zero exit status 32: umount: /media/elio/853E-94BC: not mounted



The only way I can unmout the drive is by using "sudo unmount /dev/sdb1" in the terminal or using gparted.

As an aside, and probably related, when trying to make a bootable USB, neither UNebooting nor MultSystem seem to recognize that there's an USB Drive inserted and mounted. Gparted and Disks do, though. 

I've search arround and found no one with this exact problem and no solution. Please, help.

Thanks a lot in advance.

---

### Post by sudodus on 2015-11-27
The problem can depend on a few different things.

- How the drive is recognized by the system, and reported in /dev/disk/by-id. It can be seen by

```
ls -l /dev/disk/by-id
```

or with an overview with this command line (as used in [mkusb](https://help.ubuntu.com/community/mkusb))

```
ls -l /dev/disk/by-id| grep [a-z]$|tr -s ' ' ' '  |cut -d ' ' -f 9,11|sort -k2|grep -e \^a -e \^u
```

This commands gives the following output for me

```
ata-SAMSUNG_HD322HJ_S17AJ90QB00683 ../../sda                    # SATA HDD
ata-OCZ-AGILITY3_OCZ-LG1P09233GJ67M09 ../../sdb                 # SATA SSD
ata-WDC_WD1003FBYZ-010FB0_WD-WCAW36973968 ../../sdc             # SATA HDD
[COLOR="#0000FF"]**usb**[/COLOR]-SanDisk_Cruzer_Blade_4C532000071019104285-0:0 ../../sdd     # USB pendrive
[COLOR="#FF0000"]**ata**[/COLOR]-DT_Workspace_32GB_30E118B10F9182FC0028 ../../sde            # USB pendrive
```

As you can see, some USB drives, even some pendrives, are recognized as ATA drives. This can confuse the tools to create USB boot drives. mkusb lets you 'toggle USB-only' so that also drives, that are recognized as ATA drives, will be available as targets.

- The permissions of the directory tree, where the drive is automounted. This can differ between versions and flavours of Ubuntu.

- The quality of the cooperation between the pendrive and the USB hardware and firmware in the computer.

---

