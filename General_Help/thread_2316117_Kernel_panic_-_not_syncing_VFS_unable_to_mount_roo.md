---
title: "Kernel panic - not syncing: VFS: unable to mount root fs on unknown-block(0,0)"
date: 2016-03-05
forum: General Help
---

### Post by strux2 on 2016-03-05
Hi I was trying to create some VMs with KVM, and noticed system getting quite slow, so I rebooted it. After that I saw '[FONT=arial]Kernel panic - not syncing: VFS: unable to mount root fs on unknown-block(0,0)[/FONT]'. I tried to fix it with boot-repair as advised on some forums but it didn't really help. Here is the output from boot-repair [http://paste.ubuntu.com/15286567/](http://paste.ubuntu.com/15286567/)

System is Ubuntu Server 15.10. I have 2 3TB drives in Raid1 and 3 partitions boot, data, and swap. I'm managed to mount md0 and I'm in the process of copping data now, but it will take take me ageeeees, to restore everything. Is there any way I can fix this?

I really appreciate any help you can give me!

Here is output from boot-repair again, for ones who are too lazy to open the link :D

```

Boot Info Script e7fc706 + Boot-Repair extra info      [COLOR=#666666][[/COLOR]Boot-Info 23Nov2014[COLOR=#666666]][/COLOR]


[COLOR=#666666]=============================[/COLOR] Boot Info Summary: [COLOR=#666666]===============================[/COLOR]

 [COLOR=#666666]=[/COLOR]> Grub2 [COLOR=#666666]([/COLOR]v2.00[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sda and looks at sector 2048 
    of the same hard drive [COLOR=#AA22FF]**for **[/COLOR]core.img. core.img is at this location and 
    looks [COLOR=#AA22FF]**for**[/COLOR] [COLOR=#666666]([/COLOR]mduuid/820cb4ed94c23134540ee824eef0b2ce[COLOR=#666666])[/COLOR]/boot/grub.
 [COLOR=#666666]=[/COLOR]> Grub2 [COLOR=#666666]([/COLOR]v2.00[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sdb and looks at sector 2048 
    of the same hard drive [COLOR=#AA22FF]**for **[/COLOR]core.img. core.img is at this location and 
    looks [COLOR=#AA22FF]**for**[/COLOR] [COLOR=#666666]([/COLOR]mduuid/820cb4ed94c23134540ee824eef0b2ce[COLOR=#666666])[/COLOR]/boot/grub.
 [COLOR=#666666]=[/COLOR]> Syslinux MBR [COLOR=#666666]([/COLOR]3.61-4.03[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sdc.

sda1: __________________________________________________________________________

    File system:       BIOS Boot partition
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Grub2[COLOR=#BB4444]'s core.img[/COLOR]
[COLOR=#BB4444]    Boot sector info: [/COLOR]

[COLOR=#BB4444]sda2: __________________________________________________________________________[/COLOR]

[COLOR=#BB4444]    File system:       swap[/COLOR]
[COLOR=#BB4444]    Boot sector type:  -[/COLOR]
[COLOR=#BB4444]    Boot sector info: [/COLOR]

[COLOR=#BB4444]sda3: __________________________________________________________________________[/COLOR]

[COLOR=#BB4444]    File system:       linux_raid_member[/COLOR]
[COLOR=#BB4444]    Boot sector type:  -[/COLOR]
[COLOR=#BB4444]    Boot sector info: [/COLOR]

[COLOR=#BB4444]sdb1: __________________________________________________________________________[/COLOR]

[COLOR=#BB4444]    File system:       BIOS Boot partition[/COLOR]
[COLOR=#BB4444]    Boot sector type:  Grub2'[/COLOR]s core.img
    Boot sector info: 

sdb2: __________________________________________________________________________

    File system:       swap
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 

sdb3: __________________________________________________________________________

    File system:       linux_raid_member
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Unknown
    Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 40.
    Operating System:  
    Boot files:        

sdc2: __________________________________________________________________________

    File system:       vfat
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  SYSLINUX 4.03 0x4d8ae235
    Boot sector info:  Syslinux looks at sector 1360016 of /dev/sdc2 [COLOR=#AA22FF]**for **[/COLOR]its 
                       second stage. SYSLINUX is installed in the / 
                       directory. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux.cfg /casper/vmlinuz.efi 
                       /EFI/BOOT/grubx64.efi /ldlinux.sys

md/0: __________________________________________________________________________

    File system:       ext4
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 
    Operating System:  Ubuntu 15.10 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

[COLOR=#666666]============================[/COLOR] Drive/Partition Info: [COLOR=#666666]=============================[/COLOR]

Drive: sda _____________________________________________________________________

Disk /dev/sda: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  [COLOR=#008800]*# of Sectors  Id System*[/COLOR]

/dev/sda1                   1 4,294,967,295 4,294,967,295  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  [COLOR=#008800]*# of Sectors System*[/COLOR]
/dev/sda1           2,048         4,095         2,048 BIOS Boot partition
/dev/sda2   2,623,682,560 2,639,306,751    15,624,192 Swap partition [COLOR=#666666]([/COLOR]Linux[COLOR=#666666])[/COLOR]
/dev/sda3           4,096 2,623,682,559 2,623,678,464 RAID partition [COLOR=#666666]([/COLOR]Linux[COLOR=#666666])[/COLOR]

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  [COLOR=#008800]*# of Sectors  Id System*[/COLOR]

/dev/sdb1                   1 4,294,967,295 4,294,967,295  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  [COLOR=#008800]*# of Sectors System*[/COLOR]
/dev/sdb1           2,048         4,095         2,048 BIOS Boot partition
/dev/sdb2   2,623,682,560 2,639,306,751    15,624,192 Swap partition [COLOR=#666666]([/COLOR]Linux[COLOR=#666666])[/COLOR]
/dev/sdb3           4,096 2,623,682,559 2,623,678,464 RAID partition [COLOR=#666666]([/COLOR]Linux[COLOR=#666666])[/COLOR]

Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 16.0 GB, 16022241280 bytes
255 heads, 63 sectors/track, 1947 cylinders, total 31293440 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  [COLOR=#008800]*# of Sectors  Id System*[/COLOR]

/dev/sdc1                   1       409,639       409,639  ee GPT
/dev/sdc2    *        411,648    31,291,391    30,879,744   b W95 FAT32


GUID Partition Table detected.

Partition    Start Sector    End Sector  [COLOR=#008800]*# of Sectors System*[/COLOR]
/dev/sdc1              40       409,639       409,600 EFI System partition
/dev/sdc2         411,648    31,291,391    30,879,744 Data partition [COLOR=#666666]([/COLOR]Windows/Linux[COLOR=#666666])[/COLOR]

[COLOR=#BB4444]"blkid"[/COLOR] output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/loop1       24165057-c5aa-45bf-b759-7c5f1cd9e8e7   ext2       
/dev/md/0        85895180-74f7-4686-85a0-4871022f72b6   ext4       
/dev/md0         85895180-74f7-4686-85a0-4871022f72b6   ext4       
/dev/sda2        a0a5c2f0-02fd-4efe-9771-ee0075ef32e1   swap       
/dev/sda3        820cb4ed-94c2-3134-540e-e824eef0b2ce   linux_raid_member sizif:0
/dev/sdb2        f2b7dc5e-d013-449b-a641-279394a7d604   swap       
/dev/sdb3        820cb4ed-94c2-3134-540e-e824eef0b2ce   linux_raid_member sizif:0
/dev/sdc1        67E3-17ED                              vfat       EFI
/dev/sdc2        FAD7-1E11                              vfat       UNTITLED
/dev/zram0       1e86f862-aff2-415d-ab35-819cdba86b2e   swap       
/dev/zram1       05cbe675-70bc-4669-ad1d-2390480a01d8   [COLOR=#B8860B]swap[/COLOR]       

[COLOR=#666666]=========================[/COLOR] [COLOR=#BB4444]"ls -l /dev/disk/by-id"[/COLOR] output: [COLOR=#666666]======================[/COLOR]

total 0
lrwxrwxrwx 1 root root  9 Mar  4 23:14 ata-WDC_WD30EFRX-68EUZN0_WD-WCC4N3CYK485 -> ../../sdb
lrwxrwxrwx 1 root root 10 Mar  4 23:04 ata-WDC_WD30EFRX-68EUZN0_WD-WCC4N3CYK485-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Mar  4 23:04 ata-WDC_WD30EFRX-68EUZN0_WD-WCC4N3CYK485-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 Mar  4 23:04 ata-WDC_WD30EFRX-68EUZN0_WD-WCC4N3CYK485-part3 -> ../../sdb3
lrwxrwxrwx 1 root root  9 Mar  4 23:15 ata-WDC_WD30EFRX-68EUZN0_WD-WMC4N0K9F8EZ -> ../../sda
lrwxrwxrwx 1 root root 10 Mar  4 23:04 ata-WDC_WD30EFRX-68EUZN0_WD-WMC4N0K9F8EZ-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Mar  4 23:04 ata-WDC_WD30EFRX-68EUZN0_WD-WMC4N0K9F8EZ-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Mar  4 23:04 ata-WDC_WD30EFRX-68EUZN0_WD-WMC4N0K9F8EZ-part3 -> ../../sda3
lrwxrwxrwx 1 root root  9 Mar  4 23:09 md-name-sizif:0 -> ../../md0
lrwxrwxrwx 1 root root  9 Mar  4 23:09 md-uuid-820cb4ed:94c23134:540ee824:eef0b2ce -> ../../md0
lrwxrwxrwx 1 root root  9 Mar  4 23:09 usb-_Patriot_Memory_079B1C003C485264-0:0 -> ../../sdc
lrwxrwxrwx 1 root root 10 Mar  4 23:04 usb-_Patriot_Memory_079B1C003C485264-0:0-part1 -> ../../sdc1
lrwxrwxrwx 1 root root 10 Mar  4 23:04 usb-_Patriot_Memory_079B1C003C485264-0:0-part2 -> ../../sdc2
lrwxrwxrwx 1 root root  9 Mar  4 23:14 wwn-0x50014ee26185e547 -> ../../sdb
lrwxrwxrwx 1 root root 10 Mar  4 23:04 wwn-0x50014ee26185e547-part1 -> ../../sdb1
lrwxrwxrwx 1 root root 10 Mar  4 23:04 wwn-0x50014ee26185e547-part2 -> ../../sdb2
lrwxrwxrwx 1 root root 10 Mar  4 23:04 wwn-0x50014ee26185e547-part3 -> ../../sdb3
lrwxrwxrwx 1 root root  9 Mar  4 23:15 wwn-0x50014ee6b04b99e7 -> ../../sda
lrwxrwxrwx 1 root root 10 Mar  4 23:04 wwn-0x50014ee6b04b99e7-part1 -> ../../sda1
lrwxrwxrwx 1 root root 10 Mar  4 23:04 wwn-0x50014ee6b04b99e7-part2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Mar  4 23:04 wwn-0x50014ee6b04b99e7-part3 -> ../../sda3

[COLOR=#666666]================================[/COLOR] Mount points: [COLOR=#666666]=================================[/COLOR]

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   [COLOR=#666666]([/COLOR]ro,noatime[COLOR=#666666])[/COLOR]
/dev/sdc2        /cdrom                   vfat       [COLOR=#666666]([/COLOR]rw,relatime,fmask[COLOR=#666666]=[/COLOR]0022,dmask[COLOR=#666666]=[/COLOR]0022,codepage[COLOR=#666666]=[/COLOR]437,iocharset[COLOR=#666666]=[/COLOR]iso8859-1,shortname[COLOR=#666666]=[/COLOR]mixed,errors[COLOR=#666666]=[/COLOR]remount-ro[COLOR=#666666])[/COLOR]


[COLOR=#666666]===========================[/COLOR] sdc2/boot/grub/grub.cfg: [COLOR=#666666]===========================[/COLOR]

--------------------------------------------------------------------------------

[COLOR=#AA22FF]**if **[/COLOR]loadfont /boot/grub/font.pf2 ; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF][/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]gfxmode[/COLOR][COLOR=#666666]=[/COLOR]auto
    insmod efi_gop
    insmod efi_uga
    insmod gfxterm
    terminal_output gfxterm
[COLOR=#AA22FF]**fi**[/COLOR]

[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]menu_color_normal[/COLOR][COLOR=#666666]=[/COLOR]white/black
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]menu_color_highlight[/COLOR][COLOR=#666666]=[/COLOR]black/light-gray

menuentry [COLOR=#BB4444]"Boot-Repair-Disk session"[/COLOR] [COLOR=#666666]{[/COLOR]
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]gfxpayload[/COLOR][COLOR=#666666]=[/COLOR]keep
    linux    /casper/vmlinuz.efi  [COLOR=#B8860B]file[/COLOR][COLOR=#666666]=[/COLOR]/cdrom/preseed/lubuntu.seed [COLOR=#B8860B]boot[/COLOR][COLOR=#666666]=[/COLOR]casper quiet splash --
    initrd    /casper/initrd.lz
[COLOR=#666666]}[/COLOR]
--------------------------------------------------------------------------------

[COLOR=#666666]==============================[/COLOR] sdc2/syslinux.cfg: [COLOR=#666666]==============================[/COLOR]

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append [COLOR=#B8860B]initrd[/COLOR][COLOR=#666666]=[/COLOR]/ubninit [COLOR=#B8860B]file[/COLOR][COLOR=#666666]=[/COLOR]/cdrom/preseed/lubuntu.seed [COLOR=#B8860B]boot[/COLOR][COLOR=#666666]=[/COLOR]casper quiet splash -- persistent

label ubnentry0
menu label ^Help
kernel /ubnkern
append [COLOR=#B8860B]initrd[/COLOR][COLOR=#666666]=[/COLOR]/ubninit  persistent

label ubnentry1
menu label ^64bit session
kernel /casper/vmlinuz.efi
append [COLOR=#B8860B]initrd[/COLOR][COLOR=#666666]=[/COLOR]/casper/initrd.lz [COLOR=#B8860B]file[/COLOR][COLOR=#666666]=[/COLOR]/cdrom/preseed/lubuntu.seed [COLOR=#B8860B]boot[/COLOR][COLOR=#666666]=[/COLOR]casper  quiet splash -- persistent

label ubnentry2
menu label ^64bit session [COLOR=#666666]([/COLOR]failsafe[COLOR=#666666])[/COLOR]
kernel /casper/vmlinuz.efi
append [COLOR=#B8860B]initrd[/COLOR][COLOR=#666666]=[/COLOR]/casper/initrd.lz [COLOR=#B8860B]file[/COLOR][COLOR=#666666]=[/COLOR]/cdrom/preseed/lubuntu.seed [COLOR=#B8860B]boot[/COLOR][COLOR=#666666]=[/COLOR]casper  noapic noapm nodma nomce nolapic nomodeset nosmp [COLOR=#B8860B]vga[/COLOR][COLOR=#666666]=[/COLOR]normal -- persistent

label ubnentry3
menu label Boot-Repair-Disk session
kernel /casper/vmlinuz.efi
append [COLOR=#B8860B]initrd[/COLOR][COLOR=#666666]=[/COLOR]/casper/initrd.lz [COLOR=#B8860B]file[/COLOR][COLOR=#666666]=[/COLOR]/cdrom/preseed/lubuntu.seed [COLOR=#B8860B]boot[/COLOR][COLOR=#666666]=[/COLOR]casper quiet splash -- persistent

--------------------------------------------------------------------------------

[COLOR=#666666]==============[/COLOR] sdc2: Version of COM32[COLOR=#666666]([/COLOR]R[COLOR=#666666])[/COLOR] files used by Syslinux: [COLOR=#666666]===============[/COLOR]

 menu.c32                           :  COM32R module [COLOR=#666666]([/COLOR]v4.xx[COLOR=#666666])[/COLOR]

[COLOR=#666666]===========================[/COLOR] md/0/boot/grub/grub.cfg: [COLOR=#666666]===========================[/COLOR]

--------------------------------------------------------------------------------
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# DO NOT EDIT THIS FILE*[/COLOR]
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# It is automatically generated by grub-mkconfig using templates*[/COLOR]
[COLOR=#008800]*# from /etc/grub.d and settings from /etc/default/grub*[/COLOR]
[COLOR=#008800]*#*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/00_header ###*[/COLOR]
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] -s [COLOR=#B8860B]$prefix[/COLOR]/grubenv [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]have_grubenv[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#AA22FF]true[/COLOR]
load_env
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"${next_entry}"[/COLOR] [COLOR=#666666]][/COLOR] ; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]default[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"${next_entry}"[/COLOR]
   [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]next_entry[/COLOR][COLOR=#666666]=[/COLOR]
   save_env next_entry
   [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]boot_once[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#AA22FF]true[/COLOR]
[COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]default[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"0"[/COLOR]
[COLOR=#AA22FF]**fi**[/COLOR]

[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#BB4444]"${feature_menuentry_id}"[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#B8860B]menuentry_id_option[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"--id"[/COLOR]
[COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#B8860B]menuentry_id_option[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]""[/COLOR]
[COLOR=#AA22FF]**fi**[/COLOR]

[COLOR=#AA22FF]export [/COLOR]menuentry_id_option

[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"${prev_saved_entry}"[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]saved_entry[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"${prev_saved_entry}"[/COLOR]
  save_env saved_entry
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]prev_saved_entry[/COLOR][COLOR=#666666]=[/COLOR]
  save_env prev_saved_entry
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]boot_once[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#AA22FF]true[/COLOR]
[COLOR=#AA22FF]**fi**[/COLOR]

[COLOR=#AA22FF]**function **[/COLOR]savedefault [COLOR=#666666]{[/COLOR]
  [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] -z [COLOR=#BB4444]"${boot_once}"[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#B8860B]saved_entry[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"${chosen}"[/COLOR]
    save_env saved_entry
  [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#666666]}[/COLOR]
[COLOR=#AA22FF]**function **[/COLOR]recordfail [COLOR=#666666]{[/COLOR]
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]recordfail[/COLOR][COLOR=#666666]=[/COLOR]1
  [COLOR=#008800]*# GRUB lacks write support for diskfilter, so recordfail support is disabled.*[/COLOR]
[COLOR=#666666]}[/COLOR]
[COLOR=#AA22FF]**function **[/COLOR]load_video [COLOR=#666666]{[/COLOR]
  [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_all_video_module[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
insmod all_video
  [COLOR=#AA22FF]**else**[/COLOR]
insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#666666]}[/COLOR]

[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_default_font_path[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR] ; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#B8860B]font[/COLOR][COLOR=#666666]=[/COLOR]unicode
[COLOR=#AA22FF]**else**[/COLOR]
insmod part_gpt
insmod part_gpt
insmod diskfilter
insmod mdraid1x
insmod ext2
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'mduuid/820cb4ed94c23134540ee824eef0b2ce'[/COLOR]
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_platform_search_hint[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root --hint[COLOR=#666666]=[/COLOR][COLOR=#BB4444]'mduuid/820cb4ed94c23134540ee824eef0b2ce'[/COLOR]  85895180-74f7-4686-85a0-4871022f72b6
[COLOR=#AA22FF]**else**[/COLOR]
search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 85895180-74f7-4686-85a0-4871022f72b6
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#B8860B]font[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"/usr/share/grub/unicode.pf2"[/COLOR]
[COLOR=#AA22FF]**fi**[/COLOR]

[COLOR=#AA22FF]**if **[/COLOR]loadfont [COLOR=#B8860B]$font[/COLOR] ; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]gfxmode[/COLOR][COLOR=#666666]=[/COLOR]auto
  load_video
  insmod gfxterm
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]locale_dir[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]$prefix[/COLOR]/locale
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]lang[/COLOR][COLOR=#666666]=[/COLOR]en_US
  insmod gettext
[COLOR=#AA22FF]**fi**[/COLOR]
terminal_output gfxterm
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"${recordfail}"[/COLOR] [COLOR=#666666]=[/COLOR] 1 [COLOR=#666666]][/COLOR] ; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]timeout[/COLOR][COLOR=#666666]=[/COLOR]10
[COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]**  if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_timeout_style[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR] ; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]timeout_style[/COLOR][COLOR=#666666]=[/COLOR]menu
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]timeout[/COLOR][COLOR=#666666]=[/COLOR]10
  [COLOR=#008800]*# Fallback normal timeout code in case the timeout_style feature is*[/COLOR]
  [COLOR=#008800]*# unavailable.*[/COLOR]
  [COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]timeout[/COLOR][COLOR=#666666]=[/COLOR]10
  [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/00_header ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/05_debian_theme ###*[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]menu_color_normal[/COLOR][COLOR=#666666]=[/COLOR]white/black
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]menu_color_highlight[/COLOR][COLOR=#666666]=[/COLOR]black/light-gray
[COLOR=#008800]*### END /etc/grub.d/05_debian_theme ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/10_linux ###*[/COLOR]
[COLOR=#AA22FF]**function **[/COLOR]gfxmode [COLOR=#666666]{[/COLOR]
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]gfxpayload[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"${1}"[/COLOR]
    [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"${1}"[/COLOR] [COLOR=#666666]=[/COLOR] [COLOR=#BB4444]"keep"[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF][/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]vt_handoff[/COLOR][COLOR=#666666]=[/COLOR]vt.handoff[COLOR=#666666]=[/COLOR]7
    [COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF][/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]vt_handoff[/COLOR][COLOR=#666666]=[/COLOR]
    [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#666666]}[/COLOR]
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"${recordfail}"[/COLOR] ![COLOR=#666666]=[/COLOR] 1 [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**  if**[/COLOR] [COLOR=#666666][[/COLOR] -e [COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]prefix[/COLOR][COLOR=#AA22FF]**}**[/COLOR]/gfxblacklist.txt [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**    if **[/COLOR]hwmatch [COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]prefix[/COLOR][COLOR=#AA22FF]**}**[/COLOR]/gfxblacklist.txt 3; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**      if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]match[/COLOR][COLOR=#AA22FF]**}**[/COLOR] [COLOR=#666666]=[/COLOR] 0 [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]linux_gfx_mode[/COLOR][COLOR=#666666]=[/COLOR]keep
      [COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]linux_gfx_mode[/COLOR][COLOR=#666666]=[/COLOR]text
      [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]**    else**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]linux_gfx_mode[/COLOR][COLOR=#666666]=[/COLOR]text
    [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]**  else**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]linux_gfx_mode[/COLOR][COLOR=#666666]=[/COLOR]keep
  [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]linux_gfx_mode[/COLOR][COLOR=#666666]=[/COLOR]text
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]export [/COLOR]linux_gfx_mode
menuentry [COLOR=#BB4444]'Ubuntu'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#B8860B]$menuentry_id_option[/COLOR] [COLOR=#BB4444]'gnulinux-simple-85895180-74f7-4686-85a0-4871022f72b6'[/COLOR] [COLOR=#666666]{[/COLOR]
    recordfail
    load_video
    gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
    insmod gzio
    [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$grub_platform[/COLOR] [COLOR=#666666]=[/COLOR] xxen [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then **[/COLOR]insmod xzio; insmod lzopio; [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF][/COLOR]insmod part_gpt
    insmod part_gpt
    insmod diskfilter
    insmod mdraid1x
    insmod ext2
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'mduuid/820cb4ed94c23134540ee824eef0b2ce'[/COLOR]
    [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_platform_search_hint[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF][/COLOR]search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root --hint[COLOR=#666666]=[/COLOR][COLOR=#BB4444]'mduuid/820cb4ed94c23134540ee824eef0b2ce'[/COLOR]  85895180-74f7-4686-85a0-4871022f72b6
    [COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF][/COLOR]search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 85895180-74f7-4686-85a0-4871022f72b6
    [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF][/COLOR]linux    /boot/vmlinuz-4.2.0-30-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]85895180-74f7-4686-85a0-4871022f72b6 ro  nomdmonddf nomdmonisw
    initrd    /boot/initrd.img-4.2.0-30-generic
[COLOR=#666666]}[/COLOR]
submenu [COLOR=#BB4444]'Advanced options for Ubuntu'[/COLOR] [COLOR=#B8860B]$menuentry_id_option[/COLOR] [COLOR=#BB4444]'gnulinux-advanced-85895180-74f7-4686-85a0-4871022f72b6'[/COLOR] [COLOR=#666666]{[/COLOR]
    menuentry [COLOR=#BB4444]'Ubuntu, with Linux 4.2.0-30-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#B8860B]$menuentry_id_option[/COLOR] [COLOR=#BB4444]'gnulinux-4.2.0-30-generic-advanced-85895180-74f7-4686-85a0-4871022f72b6'[/COLOR] [COLOR=#666666]{[/COLOR]
        recordfail
        load_video
        gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
        insmod gzio
        [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$grub_platform[/COLOR] [COLOR=#666666]=[/COLOR] xxen [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then **[/COLOR]insmod xzio; insmod lzopio; [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF][/COLOR]insmod part_gpt
        insmod part_gpt
        insmod diskfilter
        insmod mdraid1x
        insmod ext2
        [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'mduuid/820cb4ed94c23134540ee824eef0b2ce'[/COLOR]
        [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_platform_search_hint[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF][/COLOR]search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root --hint[COLOR=#666666]=[/COLOR][COLOR=#BB4444]'mduuid/820cb4ed94c23134540ee824eef0b2ce'[/COLOR]  85895180-74f7-4686-85a0-4871022f72b6
        [COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF][/COLOR]search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 85895180-74f7-4686-85a0-4871022f72b6
        [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF][/COLOR][COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 4.2.0-30-generic ...'[/COLOR]
        linux    /boot/vmlinuz-4.2.0-30-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]85895180-74f7-4686-85a0-4871022f72b6 ro  nomdmonddf nomdmonisw
        [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
        initrd    /boot/initrd.img-4.2.0-30-generic
    [COLOR=#666666]}[/COLOR]
    menuentry [COLOR=#BB4444]'Ubuntu, with Linux 4.2.0-30-generic (upstart)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#B8860B]$menuentry_id_option[/COLOR] [COLOR=#BB4444]'gnulinux-4.2.0-30-generic-init-upstart-85895180-74f7-4686-85a0-4871022f72b6'[/COLOR] [COLOR=#666666]{[/COLOR]
        recordfail
        load_video
        gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
        insmod gzio
        [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$grub_platform[/COLOR] [COLOR=#666666]=[/COLOR] xxen [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then **[/COLOR]insmod xzio; insmod lzopio; [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF][/COLOR]insmod part_gpt
        insmod part_gpt
        insmod diskfilter
        insmod mdraid1x
        insmod ext2
        [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'mduuid/820cb4ed94c23134540ee824eef0b2ce'[/COLOR]
        [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_platform_search_hint[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF][/COLOR]search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root --hint[COLOR=#666666]=[/COLOR][COLOR=#BB4444]'mduuid/820cb4ed94c23134540ee824eef0b2ce'[/COLOR]  85895180-74f7-4686-85a0-4871022f72b6
        [COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF][/COLOR]search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 85895180-74f7-4686-85a0-4871022f72b6
        [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF][/COLOR][COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 4.2.0-30-generic ...'[/COLOR]
        linux    /boot/vmlinuz-4.2.0-30-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]85895180-74f7-4686-85a0-4871022f72b6 ro  nomdmonddf nomdmonisw [COLOR=#B8860B]init[/COLOR][COLOR=#666666]=[/COLOR]/sbin/upstart
        [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
        initrd    /boot/initrd.img-4.2.0-30-generic
    [COLOR=#666666]}[/COLOR]
    menuentry [COLOR=#BB4444]'Ubuntu, with Linux 4.2.0-30-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#B8860B]$menuentry_id_option[/COLOR] [COLOR=#BB4444]'gnulinux-4.2.0-30-generic-recovery-85895180-74f7-4686-85a0-4871022f72b6'[/COLOR] [COLOR=#666666]{[/COLOR]
        recordfail
        load_video
        insmod gzio
        [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$grub_platform[/COLOR] [COLOR=#666666]=[/COLOR] xxen [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then **[/COLOR]insmod xzio; insmod lzopio; [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF][/COLOR]insmod part_gpt
        insmod part_gpt
        insmod diskfilter
        insmod mdraid1x
        insmod ext2
        [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'mduuid/820cb4ed94c23134540ee824eef0b2ce'[/COLOR]
        [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_platform_search_hint[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF][/COLOR]search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root --hint[COLOR=#666666]=[/COLOR][COLOR=#BB4444]'mduuid/820cb4ed94c23134540ee824eef0b2ce'[/COLOR]  85895180-74f7-4686-85a0-4871022f72b6
        [COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF][/COLOR]search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 85895180-74f7-4686-85a0-4871022f72b6
        [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF][/COLOR][COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading Linux 4.2.0-30-generic ...'[/COLOR]
        linux    /boot/vmlinuz-4.2.0-30-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]85895180-74f7-4686-85a0-4871022f72b6 ro recovery nomodeset 
        [COLOR=#AA22FF]echo[/COLOR]    [COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
        initrd    /boot/initrd.img-4.2.0-30-generic
    [COLOR=#666666]}[/COLOR]
[COLOR=#666666]}[/COLOR]

[COLOR=#008800]*### END /etc/grub.d/10_linux ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/20_linux_xen ###*[/COLOR]

[COLOR=#008800]*### END /etc/grub.d/20_linux_xen ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/30_os-prober ###*[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/30_os-prober ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/30_uefi-firmware ###*[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/30_uefi-firmware ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/40_custom ###*[/COLOR]
[COLOR=#008800]*# This file provides an easy way to add custom menu entries.  Simply type the*[/COLOR]
[COLOR=#008800]*# menu entries you want to add after this comment.  Be careful not to change*[/COLOR]
[COLOR=#008800]*# the 'exec tail' line above.*[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/40_custom ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/41_custom ###*[/COLOR]
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] -f  [COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]config_directory[/COLOR][COLOR=#AA22FF]**}**[/COLOR]/custom.cfg [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]source[/COLOR] [COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]config_directory[/COLOR][COLOR=#AA22FF]**}**[/COLOR]/custom.cfg
[COLOR=#AA22FF]**elif**[/COLOR] [COLOR=#666666][[/COLOR] -z [COLOR=#BB4444]"${config_directory}"[/COLOR] -a -f  [COLOR=#B8860B]$prefix[/COLOR]/custom.cfg [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]source[/COLOR] [COLOR=#B8860B]$prefix[/COLOR]/custom.cfg;
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/41_custom ###*[/COLOR]
--------------------------------------------------------------------------------

[COLOR=#666666]===============================[/COLOR] md/0/etc/fstab: [COLOR=#666666]================================[/COLOR]

--------------------------------------------------------------------------------
[COLOR=#008800]*# /etc/fstab: static file system information.*[/COLOR]
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# Use 'blkid' to print the universally unique identifier for a*[/COLOR]
[COLOR=#008800]*# device; this may be used with UUID= as a more robust way to name devices*[/COLOR]
[COLOR=#008800]*# that works even if disks are added and removed. See fstab(5).*[/COLOR]
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# <file system> <mount point>   <type>  <options>       <dump>  <pass>*[/COLOR]
[COLOR=#008800]*# / was on /dev/md0 during installation*[/COLOR]
[COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]85895180-74f7-4686-85a0-4871022f72b6 /               ext4    [COLOR=#B8860B]errors[/COLOR][COLOR=#666666]=[/COLOR]remount-ro 0       1
[COLOR=#008800]*# swap was on /dev/sda2 during installation*[/COLOR]
[COLOR=#008800]*#UUID=a0a5c2f0-02fd-4efe-9771-ee0075ef32e1 none            swap    sw              0       0*[/COLOR]
[COLOR=#008800]*# swap was on /dev/sdb2 during installation*[/COLOR]
[COLOR=#008800]*#UUID=f2b7dc5e-d013-449b-a641-279394a7d604 none            swap    sw              0       0*[/COLOR]
/dev/mapper/cryptswap1 none swap sw 0 0
/dev/mapper/cryptswap2 none swap sw 0 0
--------------------------------------------------------------------------------

[COLOR=#666666]========================[/COLOR] Unknown MBRs/Boot Sectors/etc: [COLOR=#666666]========================[/COLOR]

Unknown BootLoader on sdc1

00000000  eb 58 90 42 53 44 20 20  34 2e 34 00 02 01 20 00  |.X.BSD  4.4... .|
00000010  02 00 00 00 00 f0 00 00  20 00 10 00 00 00 00 00  |........ .......|
00000020  00 40 06 00 4f 0c 00 00  00 00 00 00 02 00 00 00  |.@..O...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 00 29 ed 17 e3 67 45  46 49 20 20 20 20 20 20  |..[COLOR=#666666])[/COLOR]...gEFI      |
00000050  20 20 46 41 54 33 32 20  20 20 fa 31 c0 8e d0 bc  |  FAT32   .1....|
00000060  00 7c fb 8e d8 e8 00 00  5e 83 c6 19 bb 07 00 [COLOR=#AA22FF]fc[/COLOR]  |.|......^.......|
00000070  ac 84 c0 74 06 b4 0e [COLOR=#AA22FF]cd  [/COLOR]10 eb f5 30 e4 [COLOR=#AA22FF]cd [/COLOR]16 [COLOR=#AA22FF]cd[/COLOR]  |...t.......0....|
00000080  19 0d 0a 4e 6f 6e 2d 73  79 73 74 65 6d 20 64 69  |...Non-system di|
00000090  73 6b 0d 0a 50 72 65 73  73 20 61 6e 79 20 6b 65  |sk..Press any ke|
000000a0  79 20 74 6f 20 72 65 62  6f 6f 74 0d 0a 00 00 00  |y to reboot.....|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
[COLOR=#B8860B]00000200[/COLOR]


[COLOR=#666666]===============================[/COLOR] StdErr Messages: [COLOR=#666666]===============================[/COLOR]

cat: write error: Broken pipe
cat: write error: Broken pipe
File descriptor 9 [COLOR=#666666]([/COLOR]/proc/32867/mounts[COLOR=#666666])[/COLOR] leaked on lvs invocation. Parent PID 53263: bash
File descriptor 63 [COLOR=#666666]([/COLOR]pipe:[COLOR=#666666][[/COLOR]50999[COLOR=#666666]])[/COLOR] leaked on lvs invocation. Parent PID 53263: bash
  No volume groups found

ADDITIONAL INFORMATION :
[COLOR=#666666]===================[/COLOR] log of boot-repair 2016-03-04__23h08 [COLOR=#666666]===================[/COLOR]
boot-repair version : 4ppa14
boot-sav version : 4ppa14
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 4ppa14

BLKID BEFORE RAID ACTIVATION:
/dev/loop0: [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"squashfs"[/COLOR]
/dev/loop1: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"24165057-c5aa-45bf-b759-7c5f1cd9e8e7"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"ext2"[/COLOR]
/dev/sda2: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"a0a5c2f0-02fd-4efe-9771-ee0075ef32e1"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"swap"[/COLOR]
/dev/sda3: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"820cb4ed-94c2-3134-540e-e824eef0b2ce"[/COLOR] [COLOR=#B8860B]UUID_SUB[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"180eced3-bbe8-008f-0647-564f705bf124"[/COLOR] [COLOR=#B8860B]LABEL[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"sizif:0"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"linux_raid_member"[/COLOR]
/dev/sdb2: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"f2b7dc5e-d013-449b-a641-279394a7d604"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"swap"[/COLOR]
/dev/sdb3: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"820cb4ed-94c2-3134-540e-e824eef0b2ce"[/COLOR] [COLOR=#B8860B]UUID_SUB[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"b5e3dcd5-8726-2dc8-fc71-936090e1e063"[/COLOR] [COLOR=#B8860B]LABEL[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"sizif:0"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"linux_raid_member"[/COLOR]
/dev/sdc1: [COLOR=#B8860B]LABEL[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"EFI"[/COLOR] [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"67E3-17ED"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"vfat"[/COLOR]
/dev/sdc2: [COLOR=#B8860B]LABEL[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"UNTITLED"[/COLOR] [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"FAD7-1E11"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"vfat"[/COLOR]
/dev/md0: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"85895180-74f7-4686-85a0-4871022f72b6"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"ext4"[/COLOR]
/dev/zram0: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"1e86f862-aff2-415d-ab35-819cdba86b2e"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"swap"[/COLOR]
/dev/zram1: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"05cbe675-70bc-4669-ad1d-2390480a01d8"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"swap"[/COLOR]
Scanning MDraid Partitions
mdadm --detail --scan: ARRAY /dev/md/0 [COLOR=#B8860B]metadata[/COLOR][COLOR=#666666]=[/COLOR]1.2 [COLOR=#B8860B]name[/COLOR][COLOR=#666666]=[/COLOR]sizif:0 [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]820cb4ed:94c23134:540ee824:eef0b2ce
dmraid packages needed
W: Failed to fetch cdrom://Lubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 [COLOR=#666666]([/COLOR]20140722.2[COLOR=#666666])[/COLOR]/dists/trusty/main/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Lubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 [COLOR=#666666]([/COLOR]20140722.2[COLOR=#666666])[/COLOR]/dists/trusty/multiverse/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Lubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 [COLOR=#666666]([/COLOR]20140722.2[COLOR=#666666])[/COLOR]/dists/trusty/restricted/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Lubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 [COLOR=#666666]([/COLOR]20140722.2[COLOR=#666666])[/COLOR]/dists/trusty/universe/binary-amd64/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.
E: Could not get lock /var/lib/dpkg/lock - open [COLOR=#666666]([/COLOR]11: Resource temporarily unavailable[COLOR=#666666])[/COLOR]
E: Unable to lock the administration directory [COLOR=#666666]([/COLOR]/var/lib/dpkg/[COLOR=#666666])[/COLOR], is another process using it?
E: Could not get lock /var/lib/dpkg/lock - open [COLOR=#666666]([/COLOR]11: Resource temporarily unavailable[COLOR=#666666])[/COLOR]
E: Unable to lock the administration directory [COLOR=#666666]([/COLOR]/var/lib/dpkg/[COLOR=#666666])[/COLOR], is another process using it?
E: Could not get lock /var/lib/dpkg/lock - open [COLOR=#666666]([/COLOR]11: Resource temporarily unavailable[COLOR=#666666])[/COLOR]
E: Unable to lock the administration directory [COLOR=#666666]([/COLOR]/var/lib/dpkg/[COLOR=#666666])[/COLOR], is another process using it?
E: Could not get lock /var/lib/dpkg/lock - open [COLOR=#666666]([/COLOR]11: Resource temporarily unavailable[COLOR=#666666])[/COLOR]
E: Unable to lock the administration directory [COLOR=#666666]([/COLOR]/var/lib/dpkg/[COLOR=#666666])[/COLOR], is another process using it?
Could not install dmraid
Please close all your package managers [COLOR=#666666]([/COLOR]Software Center, Update Manager, Synaptic, ...[COLOR=#666666])[/COLOR]. Then try again.
File descriptor 9 [COLOR=#666666]([/COLOR]/proc/32867/mounts[COLOR=#666666])[/COLOR] leaked on lvs invocation. Parent PID 36330: /bin/sh
No volume groups found
boot-repair is executed in live-session [COLOR=#666666]([/COLOR]Boot-Repair-Disk 64bit 29nov2014, trusty, Ubuntu, x86_64[COLOR=#666666])[/COLOR]
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode[COLOR=#666666]([/COLOR]s[COLOR=#666666])[/COLOR]:        32-bit, 64-bit
[COLOR=#B8860B]initrd[/COLOR][COLOR=#666666]=[/COLOR]/casper/initrd.lz [COLOR=#B8860B]file[/COLOR][COLOR=#666666]=[/COLOR]/cdrom/preseed/lubuntu.seed [COLOR=#B8860B]boot[/COLOR][COLOR=#666666]=[/COLOR]casper quiet splash -- persistent [COLOR=#B8860B]BOOT_IMAGE[/COLOR][COLOR=#666666]=[/COLOR]/casper/vmlinuz.efi
Set sda as corresponding disk of md0

WARNING: GPT [COLOR=#666666]([/COLOR]GUID Partition Table[COLOR=#666666])[/COLOR] detected on [COLOR=#BB4444]'/dev/sda'[/COLOR]! The util fdisk doesn[COLOR=#BB4444]'t support GPT. Use GNU Parted.[/COLOR]


[COLOR=#BB4444]WARNING: GPT (GUID Partition Table) detected on '[/COLOR]/dev/sdb[COLOR=#BB4444]'! The util fdisk doesn'[/COLOR]t support GPT. Use GNU Parted.


WARNING: GPT [COLOR=#666666]([/COLOR]GUID Partition Table[COLOR=#666666])[/COLOR] detected on [COLOR=#BB4444]'/dev/sdc'[/COLOR]! The util fdisk doesn[COLOR=#BB4444]'t support GPT. Use GNU Parted.[/COLOR]

[COLOR=#BB4444]Disk /dev/md0 doesn'[/COLOR]t contain a valid partition [COLOR=#B8860B]table[/COLOR]

[COLOR=#666666]===================[/COLOR] os-prober:


[COLOR=#666666]===================[/COLOR] blkid:
/dev/loop0: [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"squashfs"[/COLOR]
/dev/loop1: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"24165057-c5aa-45bf-b759-7c5f1cd9e8e7"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"ext2"[/COLOR]
/dev/sda2: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"a0a5c2f0-02fd-4efe-9771-ee0075ef32e1"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"swap"[/COLOR]
/dev/sda3: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"820cb4ed-94c2-3134-540e-e824eef0b2ce"[/COLOR] [COLOR=#B8860B]UUID_SUB[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"180eced3-bbe8-008f-0647-564f705bf124"[/COLOR] [COLOR=#B8860B]LABEL[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"sizif:0"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"linux_raid_member"[/COLOR]
/dev/sdb2: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"f2b7dc5e-d013-449b-a641-279394a7d604"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"swap"[/COLOR]
/dev/sdb3: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"820cb4ed-94c2-3134-540e-e824eef0b2ce"[/COLOR] [COLOR=#B8860B]UUID_SUB[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"b5e3dcd5-8726-2dc8-fc71-936090e1e063"[/COLOR] [COLOR=#B8860B]LABEL[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"sizif:0"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"linux_raid_member"[/COLOR]
/dev/sdc1: [COLOR=#B8860B]LABEL[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"EFI"[/COLOR] [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"67E3-17ED"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"vfat"[/COLOR]
/dev/sdc2: [COLOR=#B8860B]LABEL[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"UNTITLED"[/COLOR] [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"FAD7-1E11"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"vfat"[/COLOR]
/dev/md0: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"85895180-74f7-4686-85a0-4871022f72b6"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"ext4"[/COLOR]
/dev/zram0: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"1e86f862-aff2-415d-ab35-819cdba86b2e"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"swap"[/COLOR]
/dev/zram1: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"05cbe675-70bc-4669-ad1d-2390480a01d8"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"swap"[/COLOR]

Linux not detected by os-prober on md0. Please report this message to [EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL]

WARNING: GPT [COLOR=#666666]([/COLOR]GUID Partition Table[COLOR=#666666])[/COLOR] detected on [COLOR=#BB4444]'/dev/sda'[/COLOR]! The util sfdisk doesn[COLOR=#BB4444]'t support GPT. Use GNU Parted.[/COLOR]


[COLOR=#BB4444]WARNING: GPT (GUID Partition Table) detected on '[/COLOR]/dev/sdb[COLOR=#BB4444]'! The util sfdisk doesn'[/COLOR]t support GPT. Use GNU Parted.


WARNING: GPT [COLOR=#666666]([/COLOR]GUID Partition Table[COLOR=#666666])[/COLOR] detected on [COLOR=#BB4444]'/dev/sdc'[/COLOR]! The util sfdisk doesn[COLOR=#BB4444]'t support GPT. Use GNU Parted.[/COLOR]


[COLOR=#BB4444]WARNING: GPT (GUID Partition Table) detected on '[/COLOR]/dev/sda[COLOR=#BB4444]'! The util fdisk doesn'[/COLOR]t support GPT. Use GNU Parted.


WARNING: GPT [COLOR=#666666]([/COLOR]GUID Partition Table[COLOR=#666666])[/COLOR] detected on [COLOR=#BB4444]'/dev/sdb'[/COLOR]! The util fdisk doesn[COLOR=#BB4444]'t support GPT. Use GNU Parted.[/COLOR]


[COLOR=#BB4444]WARNING: GPT (GUID Partition Table) detected on '[/COLOR]/dev/sdc[COLOR=#BB4444]'! The util fdisk doesn'[/COLOR]t support GPT. Use GNU Parted.


[COLOR=#666666]===================[/COLOR] md0/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Mar  4 22:54 grub.d
drwxr-xr-x  2 root root    4096 Mar  4 22:53 grub.d.bak
total 72
-rwxr-xr-x 1 root root  9791 Dec 17 21:46 00_header
-rwxr-xr-x 1 root root  6058 Sep  4 11:13 05_debian_theme
-rwxr-xr-x 1 root root 12261 Dec 17 21:46 10_linux
-rwxr-xr-x 1 root root 11082 Dec 17 21:46 20_linux_xen
-rwxr-xr-x 1 root root 11692 Dec 17 21:46 30_os-prober
-rwxr-xr-x 1 root root  1418 Dec 17 21:46 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Dec 17 21:46 40_custom
-rwxr-xr-x 1 root root   216 Dec 17 21:46 41_custom
-rw-r--r-- 1 root root   483 Dec 17 21:46 [COLOR=#B8860B]README[/COLOR]




[COLOR=#666666]===================[/COLOR] md0/etc/default/grub :

[COLOR=#008800]*# If you change this file, run 'update-grub' afterwards to update*[/COLOR]
[COLOR=#008800]*# /boot/grub/grub.cfg.*[/COLOR]
[COLOR=#008800]*# For full documentation of the options in this file, see:*[/COLOR]
[COLOR=#008800]*#   info -f grub -n 'Simple configuration'*[/COLOR]

[COLOR=#B8860B]GRUB_DEFAULT[/COLOR][COLOR=#666666]=[/COLOR]0
[COLOR=#008800]*#GRUB_HIDDEN_TIMEOUT=0*[/COLOR]
[COLOR=#B8860B]GRUB_HIDDEN_TIMEOUT_QUIET[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#AA22FF]true[/COLOR]
[COLOR=#B8860B]GRUB_TIMEOUT[/COLOR][COLOR=#666666]=[/COLOR]10
[COLOR=#B8860B]GRUB_DISTRIBUTOR[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]`[/COLOR]lsb_release -i -s 2> /dev/null [COLOR=#666666]||[/COLOR] [COLOR=#AA22FF]echo [/COLOR]Debian[COLOR=#BB4444]`[/COLOR]
[COLOR=#B8860B]GRUB_CMDLINE_LINUX_DEFAULT[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"nomdmonddf nomdmonisw"[/COLOR]
[COLOR=#B8860B]GRUB_CMDLINE_LINUX[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]""[/COLOR]

[COLOR=#008800]*# Uncomment to enable BadRAM filtering, modify to suit your needs*[/COLOR]
[COLOR=#008800]*# This works with Linux (no patch required) and with any kernel that obtains*[/COLOR]
[COLOR=#008800]*# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)*[/COLOR]
[COLOR=#008800]*#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"*[/COLOR]

[COLOR=#008800]*# Uncomment to disable graphical terminal (grub-pc only)*[/COLOR]
[COLOR=#008800]*#GRUB_TERMINAL=console*[/COLOR]

[COLOR=#008800]*# The resolution used on graphical terminal*[/COLOR]
[COLOR=#008800]*# note that you can use only modes which your graphic card supports via VBE*[/COLOR]
[COLOR=#008800]*# you can see them in real GRUB with the command `vbeinfo'*[/COLOR]
[COLOR=#008800]*#GRUB_GFXMODE=640x480*[/COLOR]

[COLOR=#008800]*# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux*[/COLOR]
[COLOR=#008800]*#GRUB_DISABLE_LINUX_UUID=true*[/COLOR]

[COLOR=#008800]*# Uncomment to disable generation of recovery mode menu entries*[/COLOR]
[COLOR=#008800]*#GRUB_DISABLE_RECOVERY="true"*[/COLOR]

[COLOR=#008800]*# Uncomment to get a beep at grub start*[/COLOR]
[COLOR=#008800]*#GRUB_INIT_TUNE="480 440 1"*[/COLOR]




[COLOR=#666666]===================[/COLOR] md0/etc/mdadm/mdadm.conf :
[COLOR=#008800]*# mdadm.conf*[/COLOR]
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# Please refer to mdadm.conf(5) for information about this file.*[/COLOR]
[COLOR=#008800]*#*[/COLOR]

[COLOR=#008800]*# by default (built-in), scan all partitions (/proc/partitions) and all*[/COLOR]
[COLOR=#008800]*# containers for MD superblocks. alternatively, specify devices to scan, using*[/COLOR]
[COLOR=#008800]*# wildcards if desired.*[/COLOR]
[COLOR=#008800]*#DEVICE partitions containers*[/COLOR]

[COLOR=#008800]*# auto-create devices with Debian standard permissions*[/COLOR]
CREATE [COLOR=#B8860B]owner[/COLOR][COLOR=#666666]=[/COLOR]root [COLOR=#B8860B]group[/COLOR][COLOR=#666666]=[/COLOR]disk [COLOR=#B8860B]mode[/COLOR][COLOR=#666666]=[/COLOR]0660 [COLOR=#B8860B]auto[/COLOR][COLOR=#666666]=[/COLOR]yes

[COLOR=#008800]*# automatically tag new arrays as belonging to the local system*[/COLOR]
HOMEHOST <system>

[COLOR=#008800]*# instruct the monitoring daemon where to send mail alerts*[/COLOR]
MAILADDR root

[COLOR=#008800]*# definitions of existing MD arrays*[/COLOR]
ARRAY /dev/md/0  [COLOR=#B8860B]metadata[/COLOR][COLOR=#666666]=[/COLOR]1.2 [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]820cb4ed:94c23134:540ee824:eef0b2ce [COLOR=#B8860B]name[/COLOR][COLOR=#666666]=[/COLOR]sizif:0

[COLOR=#008800]*# This file was auto-generated on Fri, 09 Oct 2015 19:46:13 +0200*[/COLOR]
[COLOR=#008800]*# by mkconf $Id$*[/COLOR]



[COLOR=#666666]===================[/COLOR] UEFI/Legacy mode:
This live-session is not in EFI-mode.
SecureBoot maybe enabled.


[COLOR=#666666]===================[/COLOR] PARTITIONS & DISKS:
sdc1    : sdc,    not-sepboot,    no-grubenv    nogrub,    no-docgrub,    no-update-grub,    32,    no-boot,    no-os,    not--efi--part,    part-has-no-fstab,    part-has-no-fstab,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    nopakmgr,    nogrubinstall,    no---usr,    part-has-no-fstab,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/sdc1.
md0    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    not-far,    /mnt/boot-sav/md0.

sda    : GPT,    BIOS_boot,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes
sdb    : GPT,    BIOS_boot,    has-no-EFIpart,     not-usb,    no-os,    2048 sectors * 512 bytes
sdc    : GPT,    no-BIOS_boot,    has-no-EFIpart,     usb-disk,    no-os,    40 sectors * 512 [COLOR=#B8860B]bytes[/COLOR]


[COLOR=#666666]===================[/COLOR] parted -l:

Model: ATA WDC WD30EFRX-68E [COLOR=#666666]([/COLOR]scsi[COLOR=#666666])[/COLOR]
Disk /dev/sda: 3001GB
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
1      1049kB  2097kB  1049kB                        bios_grub
3      2097kB  2993GB  2993GB                        raid
2      2993GB  3001GB  8000MB  linux-swap[COLOR=#666666]([/COLOR]v1[COLOR=#666666])[/COLOR]


Model: ATA WDC WD30EFRX-68E [COLOR=#666666]([/COLOR]scsi[COLOR=#666666])[/COLOR]
Disk /dev/sdb: 3001GB
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
1      1049kB  2097kB  1049kB                        bios_grub
3      2097kB  2993GB  2993GB                        raid
2      2993GB  3001GB  8000MB  linux-swap[COLOR=#666666]([/COLOR]v1[COLOR=#666666])[/COLOR]


Model:  Patriot Memory [COLOR=#666666]([/COLOR]scsi[COLOR=#666666])[/COLOR]
Disk /dev/sdc: 16.0GB
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                  Flags
1      20.5kB  210MB   210MB   fat32        EFI System Partition  boot
2      211MB   16.0GB  15.8GB  fat32        UNTITLED              msftdata


Model: Linux Software RAID Array [COLOR=#666666]([/COLOR]md[COLOR=#666666])[/COLOR]
Disk /dev/md0: 2992GB
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512B/4096B
Partition Table: loop

Number  Start  End     Size    File system  Flags
1      0.00B  2992GB  2992GB  ext4



                                                                          
Error: /dev/zram0: unrecognised disk label


                                                                          
Error: /dev/zram1: unrecognised disk [COLOR=#B8860B]label[/COLOR]

[COLOR=#666666]===================[/COLOR] parted -lm:

BYT;
/dev/sda:3001GB:scsi:512:4096:gpt:ATA WDC WD30EFRX-68E;
1:1049kB:2097kB:1049kB:::bios_grub;
3:2097kB:2993GB:2993GB:::raid;
2:2993GB:3001GB:8000MB:linux-swap[COLOR=#666666]([/COLOR]v1[COLOR=#666666])[/COLOR]::;

BYT;
/dev/sdb:3001GB:scsi:512:4096:gpt:ATA WDC WD30EFRX-68E;
1:1049kB:2097kB:1049kB:::bios_grub;
3:2097kB:2993GB:2993GB:::raid;
2:2993GB:3001GB:8000MB:linux-swap[COLOR=#666666]([/COLOR]v1[COLOR=#666666])[/COLOR]::;

BYT;
/dev/sdc:16.0GB:scsi:512:512:gpt: Patriot Memory;
1:20.5kB:210MB:210MB:fat32:EFI System Partition:boot;
2:211MB:16.0GB:15.8GB:fat32:UNTITLED:msftdata;

BYT;
/dev/md0:2992GB:md:512:4096:loop:Linux Software RAID Array;
1:0.00B:2992GB:2992GB:ext4::;


                                                                          
Error: /dev/zram0: unrecognised disk label


                                                                          
Error: /dev/zram1: unrecognised disk [COLOR=#B8860B]label[/COLOR]


[COLOR=#666666]===================[/COLOR] mount:
/cow on / [COLOR=#AA22FF]type [/COLOR]overlayfs [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
proc on /proc [COLOR=#AA22FF]type [/COLOR]proc [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev[COLOR=#666666])[/COLOR]
sysfs on /sys [COLOR=#AA22FF]type [/COLOR]sysfs [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev[COLOR=#666666])[/COLOR]
udev on /dev [COLOR=#AA22FF]type [/COLOR]devtmpfs [COLOR=#666666]([/COLOR]rw,mode[COLOR=#666666]=[/COLOR]0755[COLOR=#666666])[/COLOR]
devpts on /dev/pts [COLOR=#AA22FF]type [/COLOR]devpts [COLOR=#666666]([/COLOR]rw,noexec,nosuid,gid[COLOR=#666666]=[/COLOR]5,mode[COLOR=#666666]=[/COLOR]0620[COLOR=#666666])[/COLOR]
tmpfs on /run [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,noexec,nosuid,size[COLOR=#666666]=[/COLOR]10%,mode[COLOR=#666666]=[/COLOR]0755[COLOR=#666666])[/COLOR]
/dev/sdc2 on /cdrom [COLOR=#AA22FF]type [/COLOR]vfat [COLOR=#666666]([/COLOR]rw,relatime,fmask[COLOR=#666666]=[/COLOR]0022,dmask[COLOR=#666666]=[/COLOR]0022,codepage[COLOR=#666666]=[/COLOR]437,iocharset[COLOR=#666666]=[/COLOR]iso8859-1,shortname[COLOR=#666666]=[/COLOR]mixed,errors[COLOR=#666666]=[/COLOR]remount-ro[COLOR=#666666])[/COLOR]
/dev/loop0 on /rofs [COLOR=#AA22FF]type [/COLOR]squashfs [COLOR=#666666]([/COLOR]ro,noatime[COLOR=#666666])[/COLOR]
none on /sys/fs/cgroup [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
none on /sys/fs/fuse/connections [COLOR=#AA22FF]type [/COLOR]fusectl [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
none on /sys/kernel/debug [COLOR=#AA22FF]type [/COLOR]debugfs [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
none on /sys/kernel/security [COLOR=#AA22FF]type [/COLOR]securityfs [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
tmpfs on /tmp [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,nosuid,nodev[COLOR=#666666])[/COLOR]
none on /run/lock [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev,size[COLOR=#666666]=[/COLOR]5242880[COLOR=#666666])[/COLOR]
none on /run/shm [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,nosuid,nodev[COLOR=#666666])[/COLOR]
none on /run/user [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev,size[COLOR=#666666]=[/COLOR]104857600,mode[COLOR=#666666]=[/COLOR]0755[COLOR=#666666])[/COLOR]
none on /sys/fs/pstore [COLOR=#AA22FF]type [/COLOR]pstore [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
systemd on /sys/fs/cgroup/systemd [COLOR=#AA22FF]type [/COLOR]cgroup [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev,none,name[COLOR=#666666]=[/COLOR]systemd[COLOR=#666666])[/COLOR]
gvfsd-fuse on /run/user/999/gvfs [COLOR=#AA22FF]type [/COLOR]fuse.gvfsd-fuse [COLOR=#666666]([/COLOR]rw,nosuid,nodev,user[COLOR=#666666]=[/COLOR]lubuntu[COLOR=#666666])[/COLOR]
/dev/sdc1 on /mnt/boot-sav/sdc1 [COLOR=#AA22FF]type [/COLOR]vfat [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
/dev/md0 on /mnt/boot-sav/md0 [COLOR=#AA22FF]type [/COLOR]ext4 [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]


[COLOR=#666666]===================[/COLOR] ls:
/sys/block/md0 [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev discard_alignment ext_range holders inflight md power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sda [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda3 size slaves stat subsystem trace uevent
/sys/block/sdb [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 sdb2 sdb3 size slaves stat subsystem trace uevent
/sys/block/sdc [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdc1 sdc2 size slaves stat subsystem trace uevent
/dev [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency cuse disk ecryptfs fd full fuse hidraw0 hidraw1 hidraw2 hpet hpilo input kmsg kvm log mapper mcelog md md0 mem net network_latency network_throughput null port ppp psaux ptmx ptp0 ptp1 pts random rfkill rtc rtc0 sda sda1 sda2 sda3 sdb sdb1 sdb2 sdb3 sdc sdc1 sdc2 serial sg0 sg1 sg2 shm snapshot snd stderr stdin stdout uhid uinput urandom usb vga_arbiter vhci vhost-net watchdog zero
ls /dev/md:  0
ls /dev/mapper:  [COLOR=#B8860B]control[/COLOR]

[COLOR=#666666]===================[/COLOR] hexdump -n512 -C /dev/sdc1
00000000  eb 58 90 42 53 44 20 20  34 2e 34 00 02 01 20 00  |.X.BSD  4.4... .|
00000010  02 00 00 00 00 f0 00 00  20 00 10 00 00 00 00 00  |........ .......|
00000020  00 40 06 00 4f 0c 00 00  00 00 00 00 02 00 00 00  |.@..O...........|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  00 01 29 ed 17 e3 67 45  46 49 20 20 20 20 20 20  |..[COLOR=#666666])[/COLOR]...gEFI      |
00000050  20 20 46 41 54 33 32 20  20 20 fa 31 c0 8e d0 bc  |  FAT32   .1....|
00000060  00 7c fb 8e d8 e8 00 00  5e 83 c6 19 bb 07 00 [COLOR=#AA22FF]fc[/COLOR]  |.|......^.......|
00000070  ac 84 c0 74 06 b4 0e [COLOR=#AA22FF]cd  [/COLOR]10 eb f5 30 e4 [COLOR=#AA22FF]cd [/COLOR]16 [COLOR=#AA22FF]cd[/COLOR]  |...t.......0....|
00000080  19 0d 0a 4e 6f 6e 2d 73  79 73 74 65 6d 20 64 69  |...Non-system di|
00000090  73 6b 0d 0a 50 72 65 73  73 20 61 6e 79 20 6b 65  |sk..Press any ke|
000000a0  79 20 74 6f 20 72 65 62  6f 6f 74 0d 0a 00 00 00  |y to reboot.....|
000000b0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

WARNING: GPT [COLOR=#666666]([/COLOR]GUID Partition Table[COLOR=#666666])[/COLOR] detected on [COLOR=#BB4444]'/dev/sda'[/COLOR]! The util fdisk doesn[COLOR=#BB4444]'t support GPT. Use GNU Parted.[/COLOR]


[COLOR=#BB4444]WARNING: GPT (GUID Partition Table) detected on '[/COLOR]/dev/sdb[COLOR=#BB4444]'! The util fdisk doesn'[/COLOR]t support GPT. Use GNU Parted.


WARNING: GPT [COLOR=#666666]([/COLOR]GUID Partition Table[COLOR=#666666])[/COLOR] detected on [COLOR=#BB4444]'/dev/sdc'[/COLOR]! The util fdisk doesn[COLOR=#BB4444]'t support GPT. Use GNU Parted.[/COLOR]

[COLOR=#BB4444]Disk /dev/md0 doesn'[/COLOR]t contain a valid partition [COLOR=#B8860B]table[/COLOR]

[COLOR=#666666]===================[/COLOR] df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs 1008M   59M  899M   7% /
udev           devtmpfs   7.9G   12K  7.9G   1% /dev
tmpfs          tmpfs      1.6G 1004K  1.6G   1% /run
/dev/sdc2      vfat        15G  1.7G   14G  12% /cdrom
/dev/loop0     squashfs   549M  549M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs      7.9G   12K  7.9G   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs      7.9G     0  7.9G   0% /run/shm
none           tmpfs      100M   16K  100M   1% /run/user
/dev/sdc1      vfat       197M   512  197M   1% /mnt/boot-sav/sdc1
/dev/md0       ext4       2.7T  581G  2.0T  23% /mnt/boot-sav/md0

[COLOR=#666666]===================[/COLOR] fdisk -l:

Disk /dev/sda: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 4096 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdb: 3000.6 GB, 3000592982016 bytes
255 heads, 63 sectors/track, 364801 cylinders, total 5860533168 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 4096 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

Disk /dev/sdc: 16.0 GB, 16022241280 bytes
255 heads, 63 sectors/track, 1947 cylinders, total 31293440 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
Disk identifier: 0x00000000

Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      409639      204819+  ee  GPT
/dev/sdc2   *      411648    31291391    15439872    b  W95 FAT32

Disk /dev/md0: 2992.5 GB, 2992456597504 bytes
2 heads, 4 sectors/track, 730580224 cylinders, total 5844641792 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 4096 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 4096 bytes / 4096 bytes
Disk identifier: [COLOR=#B8860B]0x00000000[/COLOR]



[COLOR=#666666]===================[/COLOR] Recommended repair
The default repair of the Boot-Repair utility will purge [COLOR=#666666]([/COLOR]in order to [COLOR=#AA22FF]enable[/COLOR]-raid[COLOR=#666666])[/COLOR] and reinstall the grub2 of md0 into the MBRs of all disks [COLOR=#666666]([/COLOR]except USB without OS[COLOR=#666666])[/COLOR].
Additional repair will be performed: unhide-bootmenu-10s


chroot /mnt/boot-sav/md0 apt-get -y --force-yes update
Purge the GRUB of md0
grub-pc available

0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
DEBCHECK debOK, grub-pc
DEBCHECK debOK
shim-signed available
linux-signed-generic available
Please [COLOR=#AA22FF]type[/COLOR]: sudo chroot [COLOR=#BB4444]"/mnt/boot-sav/md0"[/COLOR] dpkg --configure -ansudo chroot [COLOR=#BB4444]"/mnt/boot-sav/md0"[/COLOR] apt-get install -fynsudo chroot [COLOR=#BB4444]"/mnt/boot-sav/md0"[/COLOR] apt-get install -y --force-yes mdadmnsudo chroot [COLOR=#BB4444]"/mnt/boot-sav/md0"[/COLOR] mdadm --assemble --scannsudo chroot [COLOR=#BB4444]"/mnt/boot-sav/md0"[/COLOR] apt-get purge -y --force-yes grub*-common shim-signed linux-signed*

[COLOR=#666666]===================[/COLOR] md0/etc/mdadm/mdadm.conf :
[COLOR=#008800]*# mdadm.conf*[/COLOR]
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# Please refer to mdadm.conf(5) for information about this file.*[/COLOR]
[COLOR=#008800]*#*[/COLOR]

[COLOR=#008800]*# by default (built-in), scan all partitions (/proc/partitions) and all*[/COLOR]
[COLOR=#008800]*# containers for MD superblocks. alternatively, specify devices to scan, using*[/COLOR]
[COLOR=#008800]*# wildcards if desired.*[/COLOR]
[COLOR=#008800]*#DEVICE partitions containers*[/COLOR]

[COLOR=#008800]*# auto-create devices with Debian standard permissions*[/COLOR]
CREATE [COLOR=#B8860B]owner[/COLOR][COLOR=#666666]=[/COLOR]root [COLOR=#B8860B]group[/COLOR][COLOR=#666666]=[/COLOR]disk [COLOR=#B8860B]mode[/COLOR][COLOR=#666666]=[/COLOR]0660 [COLOR=#B8860B]auto[/COLOR][COLOR=#666666]=[/COLOR]yes

[COLOR=#008800]*# automatically tag new arrays as belonging to the local system*[/COLOR]
HOMEHOST <system>

[COLOR=#008800]*# instruct the monitoring daemon where to send mail alerts*[/COLOR]
MAILADDR root

[COLOR=#008800]*# definitions of existing MD arrays*[/COLOR]
ARRAY /dev/md/0  [COLOR=#B8860B]metadata[/COLOR][COLOR=#666666]=[/COLOR]1.2 [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]820cb4ed:94c23134:540ee824:eef0b2ce [COLOR=#B8860B]name[/COLOR][COLOR=#666666]=[/COLOR]sizif:0

[COLOR=#008800]*# This file was auto-generated on Fri, 09 Oct 2015 19:46:13 +0200*[/COLOR]
[COLOR=#008800]*# by mkconf $Id$*[/COLOR]




[COLOR=#666666]===================[/COLOR] md0/proc/mdstat :
Personalities : [COLOR=#666666][[/COLOR]raid1[COLOR=#666666]][/COLOR] [COLOR=#666666][[/COLOR]linear[COLOR=#666666]][/COLOR] [COLOR=#666666][[/COLOR]multipath[COLOR=#666666]][/COLOR] [COLOR=#666666][[/COLOR]raid0[COLOR=#666666]][/COLOR] [COLOR=#666666][[/COLOR]raid6[COLOR=#666666]][/COLOR] [COLOR=#666666][[/COLOR]raid5[COLOR=#666666]][/COLOR] [COLOR=#666666][[/COLOR]raid4[COLOR=#666666]][/COLOR] [COLOR=#666666][[/COLOR]raid10[COLOR=#666666]][/COLOR]
md0 : active raid1 sdb3[COLOR=#666666][[/COLOR]1[COLOR=#666666]][/COLOR] sda3[COLOR=#666666][[/COLOR]0[COLOR=#666666]][/COLOR]
2922320896 blocks super 1.2 [COLOR=#666666][[/COLOR]2/2[COLOR=#666666]][/COLOR] [COLOR=#666666][[/COLOR]UU[COLOR=#666666]][/COLOR]
bitmap: 9/22 pages [COLOR=#666666][[/COLOR]36KB[COLOR=#666666]][/COLOR], 65536KB chunk

unused devices: <none>



Then [COLOR=#AA22FF]type[/COLOR]: sudo chroot [COLOR=#BB4444]"/mnt/boot-sav/md0"[/COLOR] apt-get install -y --force-yes grub-pc linux-generic

[COLOR=#666666]===================[/COLOR] md0/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Mar  4 23:11 grub.d
drwxr-xr-x  2 root root    4096 Mar  4 22:53 grub.d.bak
total 72
-rwxr-xr-x 1 root root  9791 Dec 17 21:46 00_header
-rwxr-xr-x 1 root root  6058 Sep  4 11:13 05_debian_theme
-rwxr-xr-x 1 root root 12261 Dec 17 21:46 10_linux
-rwxr-xr-x 1 root root 11082 Dec 17 21:46 20_linux_xen
-rwxr-xr-x 1 root root 11692 Dec 17 21:46 30_os-prober
-rwxr-xr-x 1 root root  1418 Dec 17 21:46 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Dec 17 21:46 40_custom
-rwxr-xr-x 1 root root   216 Dec 17 21:46 41_custom
-rw-r--r-- 1 root root   483 Dec 17 21:46 [COLOR=#B8860B]README[/COLOR]




[COLOR=#666666]===================[/COLOR] md0/etc/default/grub :

[COLOR=#008800]*# If you change this file, run 'update-grub' afterwards to update*[/COLOR]
[COLOR=#008800]*# /boot/grub/grub.cfg.*[/COLOR]
[COLOR=#008800]*# For full documentation of the options in this file, see:*[/COLOR]
[COLOR=#008800]*#   info -f grub -n 'Simple configuration'*[/COLOR]

[COLOR=#B8860B]GRUB_DEFAULT[/COLOR][COLOR=#666666]=[/COLOR]0
[COLOR=#B8860B]GRUB_HIDDEN_TIMEOUT[/COLOR][COLOR=#666666]=[/COLOR]0
[COLOR=#B8860B]GRUB_HIDDEN_TIMEOUT_QUIET[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#AA22FF]true[/COLOR]
[COLOR=#B8860B]GRUB_TIMEOUT[/COLOR][COLOR=#666666]=[/COLOR]10
[COLOR=#B8860B]GRUB_DISTRIBUTOR[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]`[/COLOR]lsb_release -i -s 2> /dev/null [COLOR=#666666]||[/COLOR] [COLOR=#AA22FF]echo [/COLOR]Debian[COLOR=#BB4444]`[/COLOR]
[COLOR=#B8860B]GRUB_CMDLINE_LINUX_DEFAULT[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"nomdmonddf nomdmonisw"[/COLOR]
[COLOR=#B8860B]GRUB_CMDLINE_LINUX[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]""[/COLOR]

[COLOR=#008800]*# Uncomment to enable BadRAM filtering, modify to suit your needs*[/COLOR]
[COLOR=#008800]*# This works with Linux (no patch required) and with any kernel that obtains*[/COLOR]
[COLOR=#008800]*# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)*[/COLOR]
[COLOR=#008800]*#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"*[/COLOR]

[COLOR=#008800]*# Uncomment to disable graphical terminal (grub-pc only)*[/COLOR]
[COLOR=#008800]*#GRUB_TERMINAL=console*[/COLOR]

[COLOR=#008800]*# The resolution used on graphical terminal*[/COLOR]
[COLOR=#008800]*# note that you can use only modes which your graphic card supports via VBE*[/COLOR]
[COLOR=#008800]*# you can see them in real GRUB with the command `vbeinfo'*[/COLOR]
[COLOR=#008800]*#GRUB_GFXMODE=640x480*[/COLOR]

[COLOR=#008800]*# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux*[/COLOR]
[COLOR=#008800]*#GRUB_DISABLE_LINUX_UUID=true*[/COLOR]

[COLOR=#008800]*# Uncomment to disable generation of recovery mode menu entries*[/COLOR]
[COLOR=#008800]*#GRUB_DISABLE_RECOVERY="true"*[/COLOR]

[COLOR=#008800]*# Uncomment to get a beep at grub start*[/COLOR]
[COLOR=#008800]*#GRUB_INIT_TUNE="480 440 1"*[/COLOR]




[COLOR=#666666]===================[/COLOR] md0/etc/mdadm/mdadm.conf :
[COLOR=#008800]*# mdadm.conf*[/COLOR]
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# Please refer to mdadm.conf(5) for information about this file.*[/COLOR]
[COLOR=#008800]*#*[/COLOR]

[COLOR=#008800]*# by default (built-in), scan all partitions (/proc/partitions) and all*[/COLOR]
[COLOR=#008800]*# containers for MD superblocks. alternatively, specify devices to scan, using*[/COLOR]
[COLOR=#008800]*# wildcards if desired.*[/COLOR]
[COLOR=#008800]*#DEVICE partitions containers*[/COLOR]

[COLOR=#008800]*# auto-create devices with Debian standard permissions*[/COLOR]
CREATE [COLOR=#B8860B]owner[/COLOR][COLOR=#666666]=[/COLOR]root [COLOR=#B8860B]group[/COLOR][COLOR=#666666]=[/COLOR]disk [COLOR=#B8860B]mode[/COLOR][COLOR=#666666]=[/COLOR]0660 [COLOR=#B8860B]auto[/COLOR][COLOR=#666666]=[/COLOR]yes

[COLOR=#008800]*# automatically tag new arrays as belonging to the local system*[/COLOR]
HOMEHOST <system>

[COLOR=#008800]*# instruct the monitoring daemon where to send mail alerts*[/COLOR]
MAILADDR root

[COLOR=#008800]*# definitions of existing MD arrays*[/COLOR]
ARRAY /dev/md/0  [COLOR=#B8860B]metadata[/COLOR][COLOR=#666666]=[/COLOR]1.2 [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]820cb4ed:94c23134:540ee824:eef0b2ce [COLOR=#B8860B]name[/COLOR][COLOR=#666666]=[/COLOR]sizif:0

[COLOR=#008800]*# This file was auto-generated on Fri, 09 Oct 2015 19:46:13 +0200*[/COLOR]
[COLOR=#008800]*# by mkconf $Id$*[/COLOR]




[COLOR=#666666]===================[/COLOR] md0/proc/mdstat :
Personalities : [COLOR=#666666][[/COLOR]raid1[COLOR=#666666]][/COLOR] [COLOR=#666666][[/COLOR]linear[COLOR=#666666]][/COLOR] [COLOR=#666666][[/COLOR]multipath[COLOR=#666666]][/COLOR] [COLOR=#666666][[/COLOR]raid0[COLOR=#666666]][/COLOR] [COLOR=#666666][[/COLOR]raid6[COLOR=#666666]][/COLOR] [COLOR=#666666][[/COLOR]raid5[COLOR=#666666]][/COLOR] [COLOR=#666666][[/COLOR]raid4[COLOR=#666666]][/COLOR] [COLOR=#666666][[/COLOR]raid10[COLOR=#666666]][/COLOR]
md0 : active raid1 sdb3[COLOR=#666666][[/COLOR]1[COLOR=#666666]][/COLOR] sda3[COLOR=#666666][[/COLOR]0[COLOR=#666666]][/COLOR]
2922320896 blocks super 1.2 [COLOR=#666666][[/COLOR]2/2[COLOR=#666666]][/COLOR] [COLOR=#666666][[/COLOR]UU[COLOR=#666666]][/COLOR]
bitmap: 7/22 pages [COLOR=#666666][[/COLOR]28KB[COLOR=#666666]][/COLOR], 65536KB chunk

unused devices: <none>



Unhide GRUB boot menu in md0/etc/default/grub

[COLOR=#666666]===================[/COLOR] md0/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Mar  4 23:11 grub.d
drwxr-xr-x  2 root root    4096 Mar  4 22:53 grub.d.bak
total 72
-rwxr-xr-x 1 root root  9791 Dec 17 21:46 00_header
-rwxr-xr-x 1 root root  6058 Sep  4 11:13 05_debian_theme
-rwxr-xr-x 1 root root 12261 Dec 17 21:46 10_linux
-rwxr-xr-x 1 root root 11082 Dec 17 21:46 20_linux_xen
-rwxr-xr-x 1 root root 11692 Dec 17 21:46 30_os-prober
-rwxr-xr-x 1 root root  1418 Dec 17 21:46 30_uefi-firmware
-rwxr-xr-x 1 root root   214 Dec 17 21:46 40_custom
-rwxr-xr-x 1 root root   216 Dec 17 21:46 41_custom
-rw-r--r-- 1 root root   483 Dec 17 21:46 [COLOR=#B8860B]README[/COLOR]




[COLOR=#666666]===================[/COLOR] md0/etc/default/grub :

[COLOR=#008800]*# If you change this file, run 'update-grub' afterwards to update*[/COLOR]
[COLOR=#008800]*# /boot/grub/grub.cfg.*[/COLOR]
[COLOR=#008800]*# For full documentation of the options in this file, see:*[/COLOR]
[COLOR=#008800]*#   info -f grub -n 'Simple configuration'*[/COLOR]

[COLOR=#B8860B]GRUB_DEFAULT[/COLOR][COLOR=#666666]=[/COLOR]0
[COLOR=#008800]*#GRUB_HIDDEN_TIMEOUT=0*[/COLOR]
[COLOR=#B8860B]GRUB_HIDDEN_TIMEOUT_QUIET[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#AA22FF]true[/COLOR]
[COLOR=#B8860B]GRUB_TIMEOUT[/COLOR][COLOR=#666666]=[/COLOR]10
[COLOR=#B8860B]GRUB_DISTRIBUTOR[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]`[/COLOR]lsb_release -i -s 2> /dev/null [COLOR=#666666]||[/COLOR] [COLOR=#AA22FF]echo [/COLOR]Debian[COLOR=#BB4444]`[/COLOR]
[COLOR=#B8860B]GRUB_CMDLINE_LINUX_DEFAULT[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"nomdmonddf nomdmonisw"[/COLOR]
[COLOR=#B8860B]GRUB_CMDLINE_LINUX[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]""[/COLOR]

[COLOR=#008800]*# Uncomment to enable BadRAM filtering, modify to suit your needs*[/COLOR]
[COLOR=#008800]*# This works with Linux (no patch required) and with any kernel that obtains*[/COLOR]
[COLOR=#008800]*# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)*[/COLOR]
[COLOR=#008800]*#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"*[/COLOR]

[COLOR=#008800]*# Uncomment to disable graphical terminal (grub-pc only)*[/COLOR]
[COLOR=#008800]*#GRUB_TERMINAL=console*[/COLOR]

[COLOR=#008800]*# The resolution used on graphical terminal*[/COLOR]
[COLOR=#008800]*# note that you can use only modes which your graphic card supports via VBE*[/COLOR]
[COLOR=#008800]*# you can see them in real GRUB with the command `vbeinfo'*[/COLOR]
[COLOR=#008800]*#GRUB_GFXMODE=640x480*[/COLOR]

[COLOR=#008800]*# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux*[/COLOR]
[COLOR=#008800]*#GRUB_DISABLE_LINUX_UUID=true*[/COLOR]

[COLOR=#008800]*# Uncomment to disable generation of recovery mode menu entries*[/COLOR]
[COLOR=#008800]*#GRUB_DISABLE_RECOVERY="true"*[/COLOR]

[COLOR=#008800]*# Uncomment to get a beep at grub start*[/COLOR]
[COLOR=#008800]*#GRUB_INIT_TUNE="480 440 1"*[/COLOR]




[COLOR=#666666]===================[/COLOR] md0/etc/mdadm/mdadm.conf :
[COLOR=#008800]*# mdadm.conf*[/COLOR]
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# Please refer to mdadm.conf(5) for information about this file.*[/COLOR]
[COLOR=#008800]*#*[/COLOR]

[COLOR=#008800]*# by default (built-in), scan all partitions (/proc/partitions) and all*[/COLOR]
[COLOR=#008800]*# containers for MD superblocks. alternatively, specify devices to scan, using*[/COLOR]
[COLOR=#008800]*# wildcards if desired.*[/COLOR]
[COLOR=#008800]*#DEVICE partitions containers*[/COLOR]

[COLOR=#008800]*# auto-create devices with Debian standard permissions*[/COLOR]
CREATE [COLOR=#B8860B]owner[/COLOR][COLOR=#666666]=[/COLOR]root [COLOR=#B8860B]group[/COLOR][COLOR=#666666]=[/COLOR]disk [COLOR=#B8860B]mode[/COLOR][COLOR=#666666]=[/COLOR]0660 [COLOR=#B8860B]auto[/COLOR][COLOR=#666666]=[/COLOR]yes

[COLOR=#008800]*# automatically tag new arrays as belonging to the local system*[/COLOR]
HOMEHOST <system>

[COLOR=#008800]*# instruct the monitoring daemon where to send mail alerts*[/COLOR]
MAILADDR root

[COLOR=#008800]*# definitions of existing MD arrays*[/COLOR]
ARRAY /dev/md/0  [COLOR=#B8860B]metadata[/COLOR][COLOR=#666666]=[/COLOR]1.2 [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]820cb4ed:94c23134:540ee824:eef0b2ce [COLOR=#B8860B]name[/COLOR][COLOR=#666666]=[/COLOR]sizif:0

[COLOR=#008800]*# This file was auto-generated on Fri, 09 Oct 2015 19:46:13 +0200*[/COLOR]
[COLOR=#008800]*# by mkconf $Id$*[/COLOR]




[COLOR=#666666]===================[/COLOR] md0/proc/mdstat :
Personalities : [COLOR=#666666][[/COLOR]raid1[COLOR=#666666]][/COLOR] [COLOR=#666666][[/COLOR]linear[COLOR=#666666]][/COLOR] [COLOR=#666666][[/COLOR]multipath[COLOR=#666666]][/COLOR] [COLOR=#666666][[/COLOR]raid0[COLOR=#666666]][/COLOR] [COLOR=#666666][[/COLOR]raid6[COLOR=#666666]][/COLOR] [COLOR=#666666][[/COLOR]raid5[COLOR=#666666]][/COLOR] [COLOR=#666666][[/COLOR]raid4[COLOR=#666666]][/COLOR] [COLOR=#666666][[/COLOR]raid10[COLOR=#666666]][/COLOR]
md0 : active raid1 sdb3[COLOR=#666666][[/COLOR]1[COLOR=#666666]][/COLOR] sda3[COLOR=#666666][[/COLOR]0[COLOR=#666666]][/COLOR]
2922320896 blocks super 1.2 [COLOR=#666666][[/COLOR]2/2[COLOR=#666666]][/COLOR] [COLOR=#666666][[/COLOR]UU[COLOR=#666666]][/COLOR]
bitmap: 1/22 pages [COLOR=#666666][[/COLOR]4KB[COLOR=#666666]][/COLOR], 65536KB chunk

unused devices: <none>




Reinstall the GRUB of md0 into all MBRs of disks with OS or not-USB

*******lspci -nnk | grep -iA3 vga
01:00.1 VGA compatible controller [COLOR=#666666][[/COLOR]0300[COLOR=#666666]][/COLOR]: Matrox Electronics Systems Ltd. MGA G200EH [COLOR=#666666][[/COLOR]102b:0533[COLOR=#666666]][/COLOR]
Subsystem: Hewlett-Packard Company iLO4 [COLOR=#666666][[/COLOR]103c:3381[COLOR=#666666]][/COLOR]
01:00.2 System peripheral [COLOR=#666666][[/COLOR]0880[COLOR=#666666]][/COLOR]: Hewlett-Packard Company Integrated Lights-Out Standard Management Processor Support and Messaging [COLOR=#666666][[/COLOR]103c:3307[COLOR=#666666]][/COLOR] [COLOR=#666666]([/COLOR]rev 05[COLOR=#666666])[/COLOR]
Subsystem: Hewlett-Packard Company iLO4 [COLOR=#666666][[/COLOR]103c:3381[COLOR=#666666]][/COLOR]
*******

grub-install --version
grub-install [COLOR=#666666]([/COLOR]GRUB[COLOR=#666666])[/COLOR] 2.02~beta2-29ubuntu0.3,grub-install [COLOR=#666666]([/COLOR]GRUB[COLOR=#666666])[/COLOR] 2.

Reinstall the GRUB of md0 into the MBR of sdb
Installing [COLOR=#AA22FF]**for **[/COLOR]i386-pc platform.
Installation finished. No error reported.
grub-install /dev/sdb: [COLOR=#AA22FF]exit [/COLOR]code of grub-install /dev/sdb:0

*******lspci -nnk | grep -iA3 vga
01:00.1 VGA compatible controller [COLOR=#666666][[/COLOR]0300[COLOR=#666666]][/COLOR]: Matrox Electronics Systems Ltd. MGA G200EH [COLOR=#666666][[/COLOR]102b:0533[COLOR=#666666]][/COLOR]
Subsystem: Hewlett-Packard Company iLO4 [COLOR=#666666][[/COLOR]103c:3381[COLOR=#666666]][/COLOR]
01:00.2 System peripheral [COLOR=#666666][[/COLOR]0880[COLOR=#666666]][/COLOR]: Hewlett-Packard Company Integrated Lights-Out Standard Management Processor Support and Messaging [COLOR=#666666][[/COLOR]103c:3307[COLOR=#666666]][/COLOR] [COLOR=#666666]([/COLOR]rev 05[COLOR=#666666])[/COLOR]
Subsystem: Hewlett-Packard Company iLO4 [COLOR=#666666][[/COLOR]103c:3381[COLOR=#666666]][/COLOR]
*******

grub-install --version
grub-install [COLOR=#666666]([/COLOR]GRUB[COLOR=#666666])[/COLOR] 2.02~beta2-29ubuntu0.3,grub-install [COLOR=#666666]([/COLOR]GRUB[COLOR=#666666])[/COLOR] 2.

Reinstall the GRUB of md0 into the MBR of sdc
Installing [COLOR=#AA22FF]**for **[/COLOR]i386-pc platform.
grub-install: warning: this GPT partition label contains no BIOS Boot Partition; embedding won't be possible.
grub-install: error: embedding is not possible, but this is required [COLOR=#AA22FF]**for **[/COLOR]RAID and LVM install.
grub-install /dev/sdc: [COLOR=#AA22FF]exit [/COLOR]code of grub-install /dev/sdc:1

*******lspci -nnk | grep -iA3 vga
01:00.1 VGA compatible controller [COLOR=#666666][[/COLOR]0300[COLOR=#666666]][/COLOR]: Matrox Electronics Systems Ltd. MGA G200EH [COLOR=#666666][[/COLOR]102b:0533[COLOR=#666666]][/COLOR]
Subsystem: Hewlett-Packard Company iLO4 [COLOR=#666666][[/COLOR]103c:3381[COLOR=#666666]][/COLOR]
01:00.2 System peripheral [COLOR=#666666][[/COLOR]0880[COLOR=#666666]][/COLOR]: Hewlett-Packard Company Integrated Lights-Out Standard Management Processor Support and Messaging [COLOR=#666666][[/COLOR]103c:3307[COLOR=#666666]][/COLOR] [COLOR=#666666]([/COLOR]rev 05[COLOR=#666666])[/COLOR]
Subsystem: Hewlett-Packard Company iLO4 [COLOR=#666666][[/COLOR]103c:3381[COLOR=#666666]][/COLOR]
*******

grub-install --version
grub-install [COLOR=#666666]([/COLOR]GRUB[COLOR=#666666])[/COLOR] 2.02~beta2-29ubuntu0.3,grub-install [COLOR=#666666]([/COLOR]GRUB[COLOR=#666666])[/COLOR] 2.

Reinstall the GRUB of md0 into the MBR of sda
Installing [COLOR=#AA22FF]**for **[/COLOR]i386-pc platform.
Installation finished. No error reported.
grub-install /dev/sda: [COLOR=#AA22FF]exit [/COLOR]code of grub-install /dev/sda:0

chroot /mnt/boot-sav/md0 update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.2.0-30-generic
Found initrd image: /boot/initrd.img-4.2.0-30-generic
Unhide GRUB boot menu in md0/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer.
Please [COLOR=#AA22FF]**do **[/COLOR]not forget to make your BIOS boot on sda [COLOR=#666666]([/COLOR]3001GB[COLOR=#666666])[/COLOR] disk!
```

---

### Post by strux2 on 2016-03-05
So I fixed this myself at the end. Just in case someone has this issue, I did following:
- booted with live cd
- mounted my raid md0 and other needed folders, and did a chroot
- installed older version of linux-kernel
- installed grub in 1MB partitions I had (sda1 and sdab). Not at sda and sdab
everything boots normally.

I'm not sure but I'm assuming that boot-repair wasn't been able to fix it as it was trying to install grub on sda and sdb instead of sda1 and sdb1 (disks over 2TB)

I hope this will help someone out!
Cheers

---

