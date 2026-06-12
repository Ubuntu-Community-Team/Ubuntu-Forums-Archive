---
title: "dual boot - xubuntu not starting after install near windows 7"
date: 2014-10-22
forum: General Help
---

### Post by gubtan on 2014-10-22
Hello all,

I have a problem.

I use a PC with Windows 7 for a long time ago. BUT I decided I install xubuntu 14 near Windows 7. I made a bootable USB pendrive with xubuntu live. I boot from the pendrive and start xubuntu live. Xubuntu live started correctly. Then I started the install from xubuntu live. When the installator ask me, I chossed "Install Xubuntu alongside Windows 7". On the next I give some free space to xubuntu on the graphical partitioning interface. The installation ran correctly.

Then I restarted the PC, the OS choosing menu released on the screen, I choosed Xubuntu, then I press ENTER. The screen go to black and clear, and after 10-15 sec received this message on the attachement pic.

[ATTACH=CONFIG]257441[/ATTACH]

[IMG]http://kepfeltoltes.hu/141022/dual_boot_fail_www.kepfeltoltes.hu_.jpg[/IMG]

Please write to me what must I have to do that I can enjoy Xubuntu.

Thank You for Your answers.

Regards,

gubtan

---

### Post by Bashing-om on 2014-10-22
gubtan; Hi !

Looks like grub is not finding it's boot files. We can (RE-)install grub.
We need to know where to install, and also check the UUID that grub expects to find.
Boot the liveUSB to "try ubuntu" mode; key combo ctl+alt+t to get a terminal:
Post back - Between code tags, please - the outputs of terminal commands:
```

sudo fdisk -lu
sudo parted -l
sudo blkid

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

With that info we can advise better.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by gubtan on 2014-10-22
Dear Bashing-om,

I will to take what you wrote, but just day after tomorrow, because tomorrow will a celebration day in my country.

Friday morning when I will arrive my office I will run the commands and post the results between CODE tags.

I hope my problem will be good simply with your help.

Regards, 

gubtan

---

### Post by Bashing-om on 2014-10-22
gubtan; Good.

At your convenience we will proceed.

I do not anticipate this to be of any difficulty, once we know what we are working with.

[INDENT][INDENT]knowledge is power
[/INDENT][/INDENT]

---

### Post by gubtan on 2014-10-24
Dear Bashing-om,

The results are following:

```
xubuntu@xubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2fa92fa9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    20482874    10241406    7  HPFS/NTFS/exFAT
/dev/sda2        20482875   976751999   478134562+   f  W95 Ext'd (LBA)
/dev/sda5        20482938   360450404   169983733+   7  HPFS/NTFS/exFAT
/dev/sda6       360450468   688128209   163838871    7  HPFS/NTFS/exFAT
/dev/sda7       688128273   976751999   144311863+   7  HPFS/NTFS/exFAT

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc7b28950

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   488392064   244196001   42  SFS

Disk /dev/sdc: 7747 MB, 7747397632 bytes
32 heads, 63 sectors/track, 7505 cylinders, total 15131636 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x70b2284d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    15130079     7565008+   b  W95 FAT32

Disk /dev/sdd: 82.0 GB, 81963220480 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160084415 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x17431742

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048   101472555    50735254    7  HPFS/NTFS/exFAT
/dev/sdd2       101474302   160083967    29304833    5  Extended
/dev/sdd5       155893760   160083967     2095104   82  Linux swap / Solaris
/dev/sdd6   *   101474304   155893759    27209728   83  Linux

Partition table entries are not in disk order
xubuntu@xubuntu:~$ parted -l
xubuntu@xubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: LABEL="WXPEE_SYS" UUID="5E680E81680E5863" TYPE="ntfs" 
/dev/sda5: LABEL="MM-CM-3ni" UUID="3624094024090499" TYPE="ntfs" 
/dev/sda6: LABEL="Gabi" UUID="708C16828C1642D0" TYPE="ntfs" 
/dev/sda7: LABEL="JM-CM-3ska-A" UUID="CADC1D3ADC1D226D" TYPE="ntfs" 
/dev/sdb1: UUID="D2F49AC1F49AA76F" TYPE="ntfs" 
/dev/sdc1: LABEL="MULTIBOOT" UUID="F89B-6F02" TYPE="vfat" 
/dev/sdd1: UUID="BE6C68326C67E39D" TYPE="ntfs" 
/dev/sdd5: UUID="722e42f1-d636-4772-9c95-ba51a075af7b" TYPE="swap" 
/dev/sdd6: UUID="31639a40-269a-4d7e-b4c4-8ebbbcb08ab5" TYPE="ext4" 
xubuntu@xubuntu:~$ 


```

What is the next step?

Regard,

gubtan

---

### Post by yancek on 2014-10-24
Not sure what you did here but your last post shows that you have a Linux partition on sdd6 which is the 82GB hard drive.  It shows the same UUID number as shown in the error message in your original post so I'm not sure why it isn't found if you have the 83GB drive attached.  You may need to download and run bootrepair and post the output.

---

### Post by Bashing-om on 2014-10-24
gubtan; Good day !

See yancek's last. Good advise.
However, a caveat, I have seen that in such a complex system that it is easy to not use "boot-repair" properly and this misuse can and does complicate the situation.
I do much prefer to find the problem and fix it manually.

To this end, as the booting system is ubuntu, installed to " Disk /dev/sdd: 82.0 GB, 81963220480 bytes " - maybe an external drive ? -
Make double sure that this drive is set as 1st boot priority in bios and try and boot the system.

If it fails to boot with this hard disk as 1st boot priority, then yes, I would think the next order of business is to (RE-)install grub to the MBR of the drive seen as 'sdd', Then, considering what you want for a multi-boot operating system, we might make it so ubuntu does not see the other Windows operating systems on the machine - such that if/when you want to boot ubuntu, you must select that hard drive in bios, and can not boot Windows from ubuntu's grub.

Let's see the result for now when the 'sdd' drive is set as 1st boot priority, and take the matter up from there.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by yancek on 2014-10-24
> the next order of business is to (RE-)install grub to the MBR of the drive seen as 'sdd',

Good suggestion, I should have mentioned that in my earlier post.  I've never used boot-repair myself although it seems to be the bootinfoscript with a few add-ons but I think for new users it is better to just get the output of bootinfoscript or the option in boot repair.  Never having used boot repair, I don't know how difficult it is to find that option.

---

### Post by gubtan on 2014-10-25
I ran the Boot-Repair, the results are:

```
[COLOR=#666666]=============================[/COLOR][COLOR=#000000] Boot Info Summary: [/COLOR][COLOR=#666666]===============================[/COLOR]
 [COLOR=#666666]=[/COLOR]> Grub2 [COLOR=#666666]([/COLOR]v1.99[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive [COLOR=#AA22FF]**for **[/COLOR]core.img. core.img is at this location and looks 
    in partition 112 [COLOR=#AA22FF]**for**[/COLOR] .
 [COLOR=#666666]=[/COLOR]> Windows 2000/XP/2003 is installed in the MBR of /dev/sdb.
 [COLOR=#666666]=[/COLOR]> Syslinux MBR [COLOR=#666666]([/COLOR]3.61-4.03[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sdc.
 [COLOR=#666666]=[/COLOR]> Grub2 [COLOR=#666666]([/COLOR]v1.99[COLOR=#666666])[/COLOR] is installed in the MBR of /dev/sdd and looks at sector 1 of 
    the same hard drive [COLOR=#AA22FF]**for **[/COLOR]core.img. core.img is at this location and looks 
    in partition 112 [COLOR=#AA22FF]**for**[/COLOR] .

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ntfs
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Windows 2000/XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Windows 2000/XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Windows 2000/XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 63.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Windows 2000/XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       vfat
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  SYSLINUX 4.03 2010-10-22 ........>..sr>..........9...0...~.....~...f...M.f.f....f..0~....>E[COLOR=#666666]}[/COLOR].u......
    Boot sector info:  Syslinux looks at sector 1991836 of /dev/sdc1 [COLOR=#AA22FF]**for **[/COLOR]its 
                       second stage. SYSLINUX is installed in the  directory. 
                       No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /syslinux.cfg /ldlinux.sys

sdd1: __________________________________________________________________________

    File system:       ntfs
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdd2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 

sdd5: __________________________________________________________________________

    File system:       swap
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  -
    Boot sector info: 

sdd6: __________________________________________________________________________

    File system:       ext4
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Grub2 [COLOR=#666666]([/COLOR]v1.99-2.00[COLOR=#666666])[/COLOR]
    Boot sector info:  Grub2 [COLOR=#666666]([/COLOR]v1.99[COLOR=#666666])[/COLOR] is installed in the boot sector of sdd6 
                       and looks at sector 148438408 of the same hard drive 
                       [COLOR=#AA22FF]**for **[/COLOR]core.img. core.img is at this location and looks 
                       in partition 112 [COLOR=#AA22FF]**for**[/COLOR] .
    Operating System:  Ubuntu 14.04.1 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

[COLOR=#666666]============================[/COLOR] Drive/Partition Info: [COLOR=#666666]=============================[/COLOR]

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  [COLOR=#008800]*# of Sectors  Id System*[/COLOR]

/dev/sda1    *             63    20,482,874    20,482,812   7 NTFS / exFAT / HPFS
/dev/sda2          20,482,875   976,751,999   956,269,125   f W95 Extended [COLOR=#666666]([/COLOR]LBA[COLOR=#666666])[/COLOR]
/dev/sda5          20,482,938   360,450,404   339,967,467   7 NTFS / exFAT / HPFS
/dev/sda6         360,450,468   688,128,209   327,677,742   7 NTFS / exFAT / HPFS
/dev/sda7         688,128,273   976,751,999   288,623,727   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  [COLOR=#008800]*# of Sectors  Id System*[/COLOR]

/dev/sdb1                  63   488,392,064   488,392,002  42 SFS


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 7747 MB, 7747397632 bytes
32 heads, 63 sectors/track, 7505 cylinders, total 15131636 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  [COLOR=#008800]*# of Sectors  Id System*[/COLOR]

/dev/sdc1    *             63    15,130,079    15,130,017   b W95 FAT32


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 82.0 GB, 81963220480 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160084415 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  [COLOR=#008800]*# of Sectors  Id System*[/COLOR]

/dev/sdd1               2,048   101,472,555   101,470,508   7 NTFS / exFAT / HPFS
/dev/sdd2         101,474,302   160,083,967    58,609,666   5 Extended
/dev/sdd5         155,893,760   160,083,967     4,190,208  82 Linux swap / Solaris
/dev/sdd6    *    101,474,304   155,893,759    54,419,456  83 Linux


[COLOR=#BB4444]"blkid"[/COLOR] output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        5E680E81680E5863                       ntfs       WXPEE_SYS
/dev/sda5        3624094024090499                       ntfs       Móni
/dev/sda6        708C16828C1642D0                       ntfs       Gabi
/dev/sda7        CADC1D3ADC1D226D                       ntfs       Jóska-A
/dev/sdb1        D2F49AC1F49AA76F                       ntfs       
/dev/sdc1        F89B-6F02                              vfat       MULTIBOOT
/dev/sdd1        BE6C68326C67E39D                       ntfs       
/dev/sdd5        722e42f1-d636-4772-9c95-ba51a075af7b   swap       
/dev/sdd6        31639a40-269a-4d7e-b4c4-8ebbbcb08ab5   [COLOR=#B8860B]ext4[/COLOR]       

[COLOR=#666666]================================[/COLOR] Mount points: [COLOR=#666666]=================================[/COLOR]

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   [COLOR=#666666]([/COLOR]ro,noatime[COLOR=#666666])[/COLOR]
/dev/sdc1        /cdrom                   vfat       [COLOR=#666666]([/COLOR]ro,noatime,fmask[COLOR=#666666]=[/COLOR]0022,dmask[COLOR=#666666]=[/COLOR]0022,codepage[COLOR=#666666]=[/COLOR]437,iocharset[COLOR=#666666]=[/COLOR]iso8859-1,shortname[COLOR=#666666]=[/COLOR]mixed,errors[COLOR=#666666]=[/COLOR]remount-ro[COLOR=#666666])[/COLOR]


[COLOR=#666666]================================[/COLOR] sda1/boot.ini: [COLOR=#666666]================================[/COLOR]

--------------------------------------------------------------------------------
;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[COLOR=#666666][[/COLOR]boot loader[COLOR=#666666]][/COLOR]
[COLOR=#B8860B]timeout[/COLOR][COLOR=#666666]=[/COLOR]3
[COLOR=#B8860B]default[/COLOR][COLOR=#666666]=[/COLOR]multi[COLOR=#666666]([/COLOR]0[COLOR=#666666])[/COLOR]disk[COLOR=#666666]([/COLOR]0[COLOR=#666666])[/COLOR]rdisk[COLOR=#666666]([/COLOR]2[COLOR=#666666])[/COLOR]partition[COLOR=#666666]([/COLOR]1[COLOR=#666666])[/COLOR][COLOR=#BB6622]**\W**[/COLOR]INDOWS
[COLOR=#666666][[/COLOR]operating systems[COLOR=#666666]][/COLOR]
multi[COLOR=#666666]([/COLOR]0[COLOR=#666666])[/COLOR]disk[COLOR=#666666]([/COLOR]0[COLOR=#666666])[/COLOR]rdisk[COLOR=#666666]([/COLOR]2[COLOR=#666666])[/COLOR]partition[COLOR=#666666]([/COLOR]1[COLOR=#666666])[/COLOR][COLOR=#BB6622]**\W**[/COLOR]INDOWS[COLOR=#666666]=[/COLOR][COLOR=#BB4444]"Microsoft Windows XP Professional - magyar"[/COLOR] /NOEXECUTE[COLOR=#666666]=[/COLOR]OPTIN /FASTDETECT
multi[COLOR=#666666]([/COLOR]0[COLOR=#666666])[/COLOR]disk[COLOR=#666666]([/COLOR]0[COLOR=#666666])[/COLOR]rdisk[COLOR=#666666]([/COLOR]1[COLOR=#666666])[/COLOR]partition[COLOR=#666666]([/COLOR]1[COLOR=#666666])[/COLOR][COLOR=#BB6622]**\W**[/COLOR]INDOWS[COLOR=#666666]=[/COLOR][COLOR=#BB4444]"Microsoft Windows XP Professional - magyar"[/COLOR] /NOEXECUTE[COLOR=#666666]=[/COLOR]OPTIN /FASTDETECT
--------------------------------------------------------------------------------

[COLOR=#666666]==============================[/COLOR] sdc1/syslinux.cfg: [COLOR=#666666]==============================[/COLOR]

--------------------------------------------------------------------------------
default menu.c32
prompt 0
menu title UNetbootin
timeout 100

label unetbootindefault
menu label Default
kernel /ubnkern
append [COLOR=#B8860B]initrd[/COLOR][COLOR=#666666]=[/COLOR]/ubninit [COLOR=#B8860B]file[/COLOR][COLOR=#666666]=[/COLOR]/cdrom/preseed/xubuntu.seed [COLOR=#B8860B]boot[/COLOR][COLOR=#666666]=[/COLOR]casper quiet splash --

label ubnentry0
menu label ^Help
kernel /ubnkern
append [COLOR=#B8860B]initrd[/COLOR][COLOR=#666666]=[/COLOR]/ubninit 

label ubnentry1
menu label ^Try Xubuntu without installing
kernel /casper/vmlinuz
append [COLOR=#B8860B]initrd[/COLOR][COLOR=#666666]=[/COLOR]/casper/initrd.lz [COLOR=#B8860B]file[/COLOR][COLOR=#666666]=[/COLOR]/cdrom/preseed/xubuntu.seed [COLOR=#B8860B]boot[/COLOR][COLOR=#666666]=[/COLOR]casper  quiet splash --

label ubnentry2
menu label ^Install Xubuntu
kernel /casper/vmlinuz
append [COLOR=#B8860B]initrd[/COLOR][COLOR=#666666]=[/COLOR]/casper/initrd.lz [COLOR=#B8860B]file[/COLOR][COLOR=#666666]=[/COLOR]/cdrom/preseed/xubuntu.seed [COLOR=#B8860B]boot[/COLOR][COLOR=#666666]=[/COLOR]casper only-ubiquity  quiet splash --

label ubnentry3
menu label ^Check disc [COLOR=#AA22FF]**for **[/COLOR]defects
kernel /casper/vmlinuz
append [COLOR=#B8860B]initrd[/COLOR][COLOR=#666666]=[/COLOR]/casper/initrd.lz [COLOR=#B8860B]boot[/COLOR][COLOR=#666666]=[/COLOR]casper integrity-check  quiet splash --

label ubnentry4
menu label Test ^memory
kernel /install/mt86plus
append [COLOR=#B8860B]initrd[/COLOR][COLOR=#666666]=[/COLOR]/ubninit 

label ubnentry5
menu label ^Boot from first hard disk
kernel /ubnkern
append [COLOR=#B8860B]initrd[/COLOR][COLOR=#666666]=[/COLOR]/ubninit 

--------------------------------------------------------------------------------

[COLOR=#666666]=================[/COLOR] sdc1: Location of files loaded by Syslinux: [COLOR=#666666]==================[/COLOR]

           GiB - GB             File                                 Fragment[COLOR=#666666]([/COLOR]s[COLOR=#666666])[/COLOR]


[COLOR=#666666]==============[/COLOR] sdc1: Version of COM32[COLOR=#666666]([/COLOR]R[COLOR=#666666])[/COLOR] files used by Syslinux: [COLOR=#666666]===============[/COLOR]

 menu.c32                           :  COM32R module [COLOR=#666666]([/COLOR]v4.xx[COLOR=#666666])[/COLOR]

[COLOR=#666666]===========================[/COLOR] sdd6/boot/grub/grub.cfg: [COLOR=#666666]===========================[/COLOR]

--------------------------------------------------------------------------------
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# DO NOT EDIT THIS FILE*[/COLOR]
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# It is automatically generated by grub-mkconfig using templates*[/COLOR]
[COLOR=#008800]*# from /etc/grub.d and settings from /etc/default/grub*[/COLOR]
[COLOR=#008800]*#*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/00_header ###*[/COLOR]
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] -s [COLOR=#B8860B]$prefix[/COLOR]/grubenv [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**  **[/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]have_grubenv[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#AA22FF]true[/COLOR]
[COLOR=#AA22FF]  [/COLOR]load_env
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"${next_entry}"[/COLOR] [COLOR=#666666]][/COLOR] ; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**   **[/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]default[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"${next_entry}"[/COLOR]
   [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]next_entry[/COLOR][COLOR=#666666]=[/COLOR]
   save_env next_entry
   [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]boot_once[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#AA22FF]true[/COLOR]
[COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]**   **[/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]default[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"0"[/COLOR]
[COLOR=#AA22FF]**fi**[/COLOR]

[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#BB4444]"${feature_menuentry_id}"[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**  **[/COLOR][COLOR=#B8860B]menuentry_id_option[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"--id"[/COLOR]
[COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]**  **[/COLOR][COLOR=#B8860B]menuentry_id_option[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]""[/COLOR]
[COLOR=#AA22FF]**fi**[/COLOR]

[COLOR=#AA22FF]export [/COLOR]menuentry_id_option

[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"${prev_saved_entry}"[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**  **[/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]saved_entry[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"${prev_saved_entry}"[/COLOR]
  save_env saved_entry
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]prev_saved_entry[/COLOR][COLOR=#666666]=[/COLOR]
  save_env prev_saved_entry
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]boot_once[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#AA22FF]true[/COLOR]
[COLOR=#AA22FF]**fi**[/COLOR]

[COLOR=#AA22FF]**function **[/COLOR]savedefault [COLOR=#666666]{[/COLOR]
  [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] -z [COLOR=#BB4444]"${boot_once}"[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**    **[/COLOR][COLOR=#B8860B]saved_entry[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"${chosen}"[/COLOR]
    save_env saved_entry
  [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#666666]}[/COLOR]
[COLOR=#AA22FF]**function **[/COLOR]recordfail [COLOR=#666666]{[/COLOR]
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]recordfail[/COLOR][COLOR=#666666]=[/COLOR]1
  [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] -n [COLOR=#BB4444]"${have_grubenv}"[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then if**[/COLOR] [COLOR=#666666][[/COLOR] -z [COLOR=#BB4444]"${boot_once}"[/COLOR] [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then **[/COLOR]save_env recordfail; [COLOR=#AA22FF]**fi**[/COLOR]; [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#666666]}[/COLOR]
[COLOR=#AA22FF]**function **[/COLOR]load_video [COLOR=#666666]{[/COLOR]
  [COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_all_video_module[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**    **[/COLOR]insmod all_video
  [COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]**    **[/COLOR]insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#666666]}[/COLOR]

[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_default_font_path[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR] ; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**   **[/COLOR][COLOR=#B8860B]font[/COLOR][COLOR=#666666]=[/COLOR]unicode
[COLOR=#AA22FF]**else**[/COLOR]
insmod part_msdos
insmod ext2
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'hd3,msdos6'[/COLOR]
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_platform_search_hint[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**  **[/COLOR]search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root --hint-bios[COLOR=#666666]=[/COLOR]hd3,msdos6 --hint-efi[COLOR=#666666]=[/COLOR]hd3,msdos6 --hint-baremetal[COLOR=#666666]=[/COLOR]ahci3,msdos6  31639a40-269a-4d7e-b4c4-8ebbbcb08ab5
[COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]**  **[/COLOR]search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 31639a40-269a-4d7e-b4c4-8ebbbcb08ab5
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]**    **[/COLOR][COLOR=#B8860B]font[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"/usr/share/grub/unicode.pf2"[/COLOR]
[COLOR=#AA22FF]**fi**[/COLOR]

[COLOR=#AA22FF]**if **[/COLOR]loadfont [COLOR=#B8860B]$font[/COLOR] ; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**  **[/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]gfxmode[/COLOR][COLOR=#666666]=[/COLOR]auto
  load_video
  insmod gfxterm
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]locale_dir[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]$prefix[/COLOR]/locale
  [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]lang[/COLOR][COLOR=#666666]=[/COLOR]en_US
  insmod gettext
[COLOR=#AA22FF]**fi**[/COLOR]
terminal_output gfxterm
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"${recordfail}"[/COLOR] [COLOR=#666666]=[/COLOR] 1 [COLOR=#666666]][/COLOR] ; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**  **[/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]timeout[/COLOR][COLOR=#666666]=[/COLOR]10
[COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]**  if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_timeout_style[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR] ; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**    **[/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]timeout_style[/COLOR][COLOR=#666666]=[/COLOR]menu
    [COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]timeout[/COLOR][COLOR=#666666]=[/COLOR]10
  [COLOR=#008800]*# Fallback normal timeout code in case the timeout_style feature is*[/COLOR]
  [COLOR=#008800]*# unavailable.*[/COLOR]
  [COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]**    **[/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]timeout[/COLOR][COLOR=#666666]=[/COLOR]10
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
[COLOR=#AA22FF]**		**[/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]vt_handoff[/COLOR][COLOR=#666666]=[/COLOR]vt.handoff[COLOR=#666666]=[/COLOR]7
	[COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]**		**[/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]vt_handoff[/COLOR][COLOR=#666666]=[/COLOR]
	[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#666666]}[/COLOR]
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"${recordfail}"[/COLOR] ![COLOR=#666666]=[/COLOR] 1 [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**  if**[/COLOR] [COLOR=#666666][[/COLOR] -e [COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]prefix[/COLOR][COLOR=#AA22FF]**}**[/COLOR]/gfxblacklist.txt [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**    if **[/COLOR]hwmatch [COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]prefix[/COLOR][COLOR=#AA22FF]**}**[/COLOR]/gfxblacklist.txt 3; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**      if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]match[/COLOR][COLOR=#AA22FF]**}**[/COLOR] [COLOR=#666666]=[/COLOR] 0 [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**        **[/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]linux_gfx_mode[/COLOR][COLOR=#666666]=[/COLOR]keep
      [COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]**        **[/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]linux_gfx_mode[/COLOR][COLOR=#666666]=[/COLOR]text
      [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]**    else**[/COLOR]
[COLOR=#AA22FF]**      **[/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]linux_gfx_mode[/COLOR][COLOR=#666666]=[/COLOR]text
    [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]**  else**[/COLOR]
[COLOR=#AA22FF]**    **[/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]linux_gfx_mode[/COLOR][COLOR=#666666]=[/COLOR]keep
  [COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]**  **[/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]linux_gfx_mode[/COLOR][COLOR=#666666]=[/COLOR]text
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]export [/COLOR]linux_gfx_mode
menuentry [COLOR=#BB4444]'Ubuntu'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#B8860B]$menuentry_id_option[/COLOR] [COLOR=#BB4444]'gnulinux-simple-31639a40-269a-4d7e-b4c4-8ebbbcb08ab5'[/COLOR] [COLOR=#666666]{[/COLOR]
	recordfail
	load_video
	gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
	insmod gzio
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'hd3,msdos6'[/COLOR]
	[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_platform_search_hint[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**	  **[/COLOR]search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root --hint-bios[COLOR=#666666]=[/COLOR]hd3,msdos6 --hint-efi[COLOR=#666666]=[/COLOR]hd3,msdos6 --hint-baremetal[COLOR=#666666]=[/COLOR]ahci3,msdos6  31639a40-269a-4d7e-b4c4-8ebbbcb08ab5
	[COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]**	  **[/COLOR]search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 31639a40-269a-4d7e-b4c4-8ebbbcb08ab5
	[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]**	**[/COLOR]linux	/boot/vmlinuz-3.13.0-32-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]31639a40-269a-4d7e-b4c4-8ebbbcb08ab5 ro  quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
	initrd	/boot/initrd.img-3.13.0-32-generic
[COLOR=#666666]}[/COLOR]
submenu [COLOR=#BB4444]'Advanced options for Ubuntu'[/COLOR] [COLOR=#B8860B]$menuentry_id_option[/COLOR] [COLOR=#BB4444]'gnulinux-advanced-31639a40-269a-4d7e-b4c4-8ebbbcb08ab5'[/COLOR] [COLOR=#666666]{[/COLOR]
	menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.13.0-32-generic'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#B8860B]$menuentry_id_option[/COLOR] [COLOR=#BB4444]'gnulinux-3.13.0-32-generic-advanced-31639a40-269a-4d7e-b4c4-8ebbbcb08ab5'[/COLOR] [COLOR=#666666]{[/COLOR]
		recordfail
		load_video
		gfxmode [COLOR=#B8860B]$linux_gfx_mode[/COLOR]
		insmod gzio
		insmod part_msdos
		insmod ext2
		[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'hd3,msdos6'[/COLOR]
		[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_platform_search_hint[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**		  **[/COLOR]search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root --hint-bios[COLOR=#666666]=[/COLOR]hd3,msdos6 --hint-efi[COLOR=#666666]=[/COLOR]hd3,msdos6 --hint-baremetal[COLOR=#666666]=[/COLOR]ahci3,msdos6  31639a40-269a-4d7e-b4c4-8ebbbcb08ab5
		[COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]**		  **[/COLOR]search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 31639a40-269a-4d7e-b4c4-8ebbbcb08ab5
		[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]**		**[/COLOR][COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Loading Linux 3.13.0-32-generic ...'[/COLOR]
		linux	/boot/vmlinuz-3.13.0-32-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]31639a40-269a-4d7e-b4c4-8ebbbcb08ab5 ro  quiet splash [COLOR=#B8860B]$vt_handoff[/COLOR]
		[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
		initrd	/boot/initrd.img-3.13.0-32-generic
	[COLOR=#666666]}[/COLOR]
	menuentry [COLOR=#BB4444]'Ubuntu, with Linux 3.13.0-32-generic (recovery mode)'[/COLOR] --class ubuntu --class gnu-linux --class gnu --class os [COLOR=#B8860B]$menuentry_id_option[/COLOR] [COLOR=#BB4444]'gnulinux-3.13.0-32-generic-recovery-31639a40-269a-4d7e-b4c4-8ebbbcb08ab5'[/COLOR] [COLOR=#666666]{[/COLOR]
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'hd3,msdos6'[/COLOR]
		[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_platform_search_hint[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**		  **[/COLOR]search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root --hint-bios[COLOR=#666666]=[/COLOR]hd3,msdos6 --hint-efi[COLOR=#666666]=[/COLOR]hd3,msdos6 --hint-baremetal[COLOR=#666666]=[/COLOR]ahci3,msdos6  31639a40-269a-4d7e-b4c4-8ebbbcb08ab5
		[COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]**		  **[/COLOR]search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 31639a40-269a-4d7e-b4c4-8ebbbcb08ab5
		[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]**		**[/COLOR][COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Loading Linux 3.13.0-32-generic ...'[/COLOR]
		linux	/boot/vmlinuz-3.13.0-32-generic [COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]31639a40-269a-4d7e-b4c4-8ebbbcb08ab5 ro recovery nomodeset 
		[COLOR=#AA22FF]echo[/COLOR]	[COLOR=#BB4444]'Loading initial ramdisk ...'[/COLOR]
		initrd	/boot/initrd.img-3.13.0-32-generic
	[COLOR=#666666]}[/COLOR]
[COLOR=#666666]}[/COLOR]

[COLOR=#008800]*### END /etc/grub.d/10_linux ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/20_linux_xen ###*[/COLOR]

[COLOR=#008800]*### END /etc/grub.d/20_linux_xen ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/20_memtest86+ ###*[/COLOR]
menuentry [COLOR=#BB4444]'Memory test (memtest86+)'[/COLOR] [COLOR=#666666]{[/COLOR]
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'hd3,msdos6'[/COLOR]
	[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_platform_search_hint[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**	  **[/COLOR]search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root --hint-bios[COLOR=#666666]=[/COLOR]hd3,msdos6 --hint-efi[COLOR=#666666]=[/COLOR]hd3,msdos6 --hint-baremetal[COLOR=#666666]=[/COLOR]ahci3,msdos6  31639a40-269a-4d7e-b4c4-8ebbbcb08ab5
	[COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]**	  **[/COLOR]search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 31639a40-269a-4d7e-b4c4-8ebbbcb08ab5
	[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]**	**[/COLOR]knetbsd	/boot/memtest86+.elf
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Memory test (memtest86+, serial console 115200)'[/COLOR] [COLOR=#666666]{[/COLOR]
	insmod part_msdos
	insmod ext2
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'hd3,msdos6'[/COLOR]
	[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_platform_search_hint[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**	  **[/COLOR]search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root --hint-bios[COLOR=#666666]=[/COLOR]hd3,msdos6 --hint-efi[COLOR=#666666]=[/COLOR]hd3,msdos6 --hint-baremetal[COLOR=#666666]=[/COLOR]ahci3,msdos6  31639a40-269a-4d7e-b4c4-8ebbbcb08ab5
	[COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]**	  **[/COLOR]search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 31639a40-269a-4d7e-b4c4-8ebbbcb08ab5
	[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]**	**[/COLOR]linux16	/boot/memtest86+.bin [COLOR=#B8860B]console[/COLOR][COLOR=#666666]=[/COLOR]ttyS0,115200n8
[COLOR=#666666]}[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/20_memtest86+ ###*[/COLOR]

[COLOR=#008800]*### BEGIN /etc/grub.d/30_os-prober ###*[/COLOR]
menuentry [COLOR=#BB4444]'Windows 7 (loader) (on /dev/sda1)'[/COLOR] --class windows --class os [COLOR=#B8860B]$menuentry_id_option[/COLOR] [COLOR=#BB4444]'osprober-chain-5E680E81680E5863'[/COLOR] [COLOR=#666666]{[/COLOR]
	insmod part_msdos
	insmod ntfs
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'hd0,msdos1'[/COLOR]
	[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_platform_search_hint[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**	  **[/COLOR]search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root --hint-bios[COLOR=#666666]=[/COLOR]hd0,msdos1 --hint-efi[COLOR=#666666]=[/COLOR]hd0,msdos1 --hint-baremetal[COLOR=#666666]=[/COLOR]ahci0,msdos1  5E680E81680E5863
	[COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]**	  **[/COLOR]search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root 5E680E81680E5863
	[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]**	**[/COLOR]parttool [COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#AA22FF]**}**[/COLOR] hidden-
	chainloader +1
[COLOR=#666666]}[/COLOR]
menuentry [COLOR=#BB4444]'Windows 7 (loader) (on /dev/sdd1)'[/COLOR] --class windows --class os [COLOR=#B8860B]$menuentry_id_option[/COLOR] [COLOR=#BB4444]'osprober-chain-BE6C68326C67E39D'[/COLOR] [COLOR=#666666]{[/COLOR]
	insmod part_msdos
	insmod ntfs
	[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]'hd3,msdos1'[/COLOR]
	[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] x[COLOR=#B8860B]$feature_platform_search_hint[/COLOR] [COLOR=#666666]=[/COLOR] xy [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**	  **[/COLOR]search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root --hint-bios[COLOR=#666666]=[/COLOR]hd3,msdos1 --hint-efi[COLOR=#666666]=[/COLOR]hd3,msdos1 --hint-baremetal[COLOR=#666666]=[/COLOR]ahci3,msdos1  BE6C68326C67E39D
	[COLOR=#AA22FF]**else**[/COLOR]
[COLOR=#AA22FF]**	  **[/COLOR]search --no-floppy --fs-uuid --set[COLOR=#666666]=[/COLOR]root BE6C68326C67E39D
	[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#AA22FF]**	**[/COLOR]parttool [COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]root[/COLOR][COLOR=#AA22FF]**}**[/COLOR] hidden-
	chainloader +1
[COLOR=#666666]}[/COLOR]
[COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]timeout_style[/COLOR][COLOR=#666666]=[/COLOR]menu
[COLOR=#AA22FF]**if**[/COLOR] [COLOR=#666666][[/COLOR] [COLOR=#BB4444]"${timeout}"[/COLOR] [COLOR=#666666]=[/COLOR] 0 [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**  **[/COLOR][COLOR=#AA22FF]set [/COLOR][COLOR=#B8860B]timeout[/COLOR][COLOR=#666666]=[/COLOR]10
[COLOR=#AA22FF]**fi**[/COLOR]
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
[COLOR=#AA22FF]**  **[/COLOR][COLOR=#AA22FF]source[/COLOR] [COLOR=#AA22FF]**${**[/COLOR][COLOR=#B8860B]config_directory[/COLOR][COLOR=#AA22FF]**}**[/COLOR]/custom.cfg
[COLOR=#AA22FF]**elif**[/COLOR] [COLOR=#666666][[/COLOR] -z [COLOR=#BB4444]"${config_directory}"[/COLOR] -a -f  [COLOR=#B8860B]$prefix[/COLOR]/custom.cfg [COLOR=#666666]][/COLOR]; [COLOR=#AA22FF]**then**[/COLOR]
[COLOR=#AA22FF]**  **[/COLOR][COLOR=#AA22FF]source[/COLOR] [COLOR=#B8860B]$prefix[/COLOR]/custom.cfg;
[COLOR=#AA22FF]**fi**[/COLOR]
[COLOR=#008800]*### END /etc/grub.d/41_custom ###*[/COLOR]
--------------------------------------------------------------------------------

[COLOR=#666666]===============================[/COLOR] sdd6/etc/fstab: [COLOR=#666666]================================[/COLOR]

--------------------------------------------------------------------------------
[COLOR=#008800]*# /etc/fstab: static file system information.*[/COLOR]
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# Use 'blkid' to print the universally unique identifier for a*[/COLOR]
[COLOR=#008800]*# device; this may be used with UUID= as a more robust way to name devices*[/COLOR]
[COLOR=#008800]*# that works even if disks are added and removed. See fstab(5).*[/COLOR]
[COLOR=#008800]*#*[/COLOR]
[COLOR=#008800]*# <file system> <mount point>   <type>  <options>       <dump>  <pass>*[/COLOR]
[COLOR=#008800]*# / was on /dev/sdd6 during installation*[/COLOR]
[COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]31639a40-269a-4d7e-b4c4-8ebbbcb08ab5 /               ext4    [COLOR=#B8860B]errors[/COLOR][COLOR=#666666]=[/COLOR]remount-ro 0       1
[COLOR=#008800]*# swap was on /dev/sdd5 during installation*[/COLOR]
[COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR]722e42f1-d636-4772-9c95-ba51a075af7b none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
--------------------------------------------------------------------------------

[COLOR=#666666]===================[/COLOR] sdd6: Location of files loaded by Grub: [COLOR=#666666]====================[/COLOR]

           GiB - GB             File                                 Fragment[COLOR=#666666]([/COLOR]s[COLOR=#666666])[/COLOR]


[COLOR=#666666]===============================[/COLOR] StdErr Messages: [COLOR=#666666]===============================[/COLOR]

cat: /tmp/BootInfo-OJ8KfWvz/Tmp_Log: No such file or directory
cat: write error: Broken pipe
cat: /tmp/BootInfo-OJ8KfWvz/Tmp_Log: No such file or directory
File descriptor 9 [COLOR=#666666]([/COLOR]/proc/5430/mounts[COLOR=#666666])[/COLOR] leaked on lvscan invocation. Parent PID 20824: bash
File descriptor 63 [COLOR=#666666]([/COLOR]pipe:[COLOR=#666666][[/COLOR]71756[COLOR=#666666]])[/COLOR] leaked on lvscan invocation. Parent PID 20824: bash
  No volume groups found

ADDITIONAL INFORMATION :
[COLOR=#666666]===================[/COLOR] log of boot-repair 2014-10-22__15h27 [COLOR=#666666]===================[/COLOR]
boot-repair version : 3.199~ppa40~saucy
boot-sav version : 3.199~ppa40~saucy
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 3.199~ppa40~saucy
boot-repair is executed in live-session [COLOR=#666666]([/COLOR]Ubuntu 14.04.1 LTS, trusty, Ubuntu, i686[COLOR=#666666])[/COLOR]
ls: cannot access /home/usr/.config: No such file or directory
CPU op-mode[COLOR=#666666]([/COLOR]s[COLOR=#666666])[/COLOR]:        32-bit, 64-bit
[COLOR=#B8860B]initrd[/COLOR][COLOR=#666666]=[/COLOR]/casper/initrd.lz [COLOR=#B8860B]file[/COLOR][COLOR=#666666]=[/COLOR]/cdrom/preseed/xubuntu.seed [COLOR=#B8860B]boot[/COLOR][COLOR=#666666]=[/COLOR]casper  quiet splash -- [COLOR=#B8860B]BOOT_IMAGE[/COLOR][COLOR=#666666]=[/COLOR]/casper/vmlinuz

[COLOR=#666666]===================[/COLOR] os-prober:
/dev/sda1:Windows 7 [COLOR=#666666]([/COLOR]loader[COLOR=#666666])[/COLOR]:Windows:chain
/dev/sdd1:Windows 7 [COLOR=#666666]([/COLOR]loader[COLOR=#666666])[/COLOR]:Windows1:chain
/dev/sdd6:Ubuntu 14.04.1 LTS [COLOR=#666666]([/COLOR]14.04[COLOR=#666666])[/COLOR]:Ubuntu:linux

[COLOR=#666666]===================[/COLOR] blkid:
/dev/loop0: [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"squashfs"[/COLOR]
/dev/sda1: [COLOR=#B8860B]LABEL[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"WXPEE_SYS"[/COLOR] [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"5E680E81680E5863"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"ntfs"[/COLOR]
/dev/sda5: [COLOR=#B8860B]LABEL[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"MM-CM-3ni"[/COLOR] [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"3624094024090499"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"ntfs"[/COLOR]
/dev/sda6: [COLOR=#B8860B]LABEL[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"Gabi"[/COLOR] [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"708C16828C1642D0"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"ntfs"[/COLOR]
/dev/sda7: [COLOR=#B8860B]LABEL[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"JM-CM-3ska-A"[/COLOR] [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"CADC1D3ADC1D226D"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"ntfs"[/COLOR]
/dev/sdb1: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"D2F49AC1F49AA76F"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"ntfs"[/COLOR]
/dev/sdc1: [COLOR=#B8860B]LABEL[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"MULTIBOOT"[/COLOR] [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"F89B-6F02"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"vfat"[/COLOR]
/dev/sdd1: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"BE6C68326C67E39D"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"ntfs"[/COLOR]
/dev/sdd5: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"722e42f1-d636-4772-9c95-ba51a075af7b"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"swap"[/COLOR]
/dev/sdd6: [COLOR=#B8860B]UUID[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"31639a40-269a-4d7e-b4c4-8ebbbcb08ab5"[/COLOR] [COLOR=#B8860B]TYPE[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"ext4"[/COLOR]


2 disks with OS, 3 OS : 1 Linux, 0 MacOS, 2 Windows, 0 unknown [COLOR=#AA22FF]type [/COLOR]OS.

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

[COLOR=#666666]===================[/COLOR] sdd6/etc/grub.d/ :
drwxr-xr-x  2 root root    4096 Jul 23 18:08 grub.d
total 76
-rwxr-xr-x 1 root root  9424 May 15 19:01 00_header
-rwxr-xr-x 1 root root  6058 May  8 12:08 05_debian_theme
-rwxr-xr-x 1 root root 11608 May 15 19:01 10_linux
-rwxr-xr-x 1 root root 10412 May 15 19:01 20_linux_xen
-rwxr-xr-x 1 root root  1992 Mar 12  2014 20_memtest86+
-rwxr-xr-x 1 root root 11692 May 15 19:01 30_os-prober
-rwxr-xr-x 1 root root  1416 May 15 19:01 30_uefi-firmware
-rwxr-xr-x 1 root root   214 May 15 19:01 40_custom
-rwxr-xr-x 1 root root   216 May 15 19:01 41_custom
-rw-r--r-- 1 root root   483 May 15 19:01 [COLOR=#B8860B]README[/COLOR]




[COLOR=#666666]===================[/COLOR] sdd6/etc/default/grub :

[COLOR=#008800]*# If you change this file, run 'update-grub' afterwards to update*[/COLOR]
[COLOR=#008800]*# /boot/grub/grub.cfg.*[/COLOR]
[COLOR=#008800]*# For full documentation of the options in this file, see:*[/COLOR]
[COLOR=#008800]*#   info -f grub -n 'Simple configuration'*[/COLOR]

[COLOR=#B8860B]GRUB_DEFAULT[/COLOR][COLOR=#666666]=[/COLOR]0
[COLOR=#008800]*#GRUB_HIDDEN_TIMEOUT=0*[/COLOR]
[COLOR=#B8860B]GRUB_HIDDEN_TIMEOUT_QUIET[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#AA22FF]true[/COLOR]
[COLOR=#B8860B]GRUB_TIMEOUT[/COLOR][COLOR=#666666]=[/COLOR]10
[COLOR=#B8860B]GRUB_DISTRIBUTOR[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]`[/COLOR]lsb_release -i -s 2> /dev/null [COLOR=#666666]||[/COLOR] [COLOR=#AA22FF]echo [/COLOR]Debian[COLOR=#BB4444]`[/COLOR]
[COLOR=#B8860B]GRUB_CMDLINE_LINUX_DEFAULT[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#BB4444]"quiet splash"[/COLOR]
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




[COLOR=#666666]===================[/COLOR] [COLOR=#B8860B]sdd6recordfail[/COLOR][COLOR=#666666]=[/COLOR]1/grub/grubenv :
[COLOR=#B8860B]recordfail[/COLOR][COLOR=#666666]=[/COLOR][COLOR=#B8860B]1[/COLOR]



[COLOR=#666666]===================[/COLOR] UEFI/Legacy mode:
This live-session is not EFI-compatible.
SecureBoot maybe enabled.


[COLOR=#666666]===================[/COLOR] PARTITIONS & DISKS:
sda1	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	ntldr,	no-winload,	no-recov-nor-hid,	bootmgr,	is-winboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sda1.
sda5	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda5.
sda6	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda6.
sda7	: sda,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sda7.
sdb1	: sdb,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	no-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	farbios,	/mnt/boot-sav/sdb1.
sdd1	: sdd,	not-sepboot,	no-grubenv	nogrub,	no-docgrub,	no-update-grub,	32,	no-boot,	is-os,	not--efi--part,	part-has-no-fstab,	part-has-no-fstab,	no-nt,	haswinload,	no-recov-nor-hid,	bootmgr,	is-winboot,	nopakmgr,	nogrubinstall,	no---usr,	part-has-no-fstab,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sdd1.
sdd6	: sdd,	not-sepboot,	grubenv-ng	grub2,	grub-pc ,	update-grub,	32,	with-boot,	is-os,	not--efi--part,	fstab-without-boot,	fstab-without-efi,	no-nt,	no-winload,	no-recov-nor-hid,	no-bmgr,	notwinboot,	apt-get,	grub-install,	with--usr,	fstab-without-usr,	not-sep-usr,	standard,	not-far,	/mnt/boot-sav/sdd6.

sda	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	has-os,	63 sectors * 512 bytes
sdb	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	no-os,	63 sectors * 512 bytes
sdd	: not-GPT,	BIOSboot-not-needed,	has-no-EFIpart, 	not-usb,	has-os,	2048 sectors * 512 [COLOR=#B8860B]bytes[/COLOR]


[COLOR=#666666]===================[/COLOR] parted -l:

Model: ATA SAMSUNG HD501LJ [COLOR=#666666]([/COLOR]scsi[COLOR=#666666])[/COLOR]
Disk /dev/sda: 500GB
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
1      32.3kB  10.5GB  10.5GB  primary   ntfs         boot
2      10.5GB  500GB   490GB   extended               lba
5      10.5GB  185GB   174GB   logical   ntfs
6      185GB   352GB   168GB   logical   ntfs
7      352GB   500GB   148GB   logical   ntfs


Model: ATA SAMSUNG HD252KJ [COLOR=#666666]([/COLOR]scsi[COLOR=#666666])[/COLOR]
Disk /dev/sdb: 250GB
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
1      32.3kB  250GB  250GB  primary  ntfs


Model: Kingston DataTraveler 2.0 [COLOR=#666666]([/COLOR]scsi[COLOR=#666666])[/COLOR]
Disk /dev/sdc: 7747MB
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
1      32.3kB  7747MB  7747MB  primary  fat32        boot


Model: ATA Maxtor 6Y080L0 [COLOR=#666666]([/COLOR]scsi[COLOR=#666666])[/COLOR]
Disk /dev/sdd: 82.0GB
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
1      1049kB  52.0GB  52.0GB  primary   ntfs
2      52.0GB  82.0GB  30.0GB  extended
6      52.0GB  79.8GB  27.9GB  logical   ext4            boot
5      79.8GB  82.0GB  2145MB  logical   linux-swap[COLOR=#666666]([/COLOR]v1[COLOR=#666666])[/COLOR]

[COLOR=#666666]===================[/COLOR] parted -lm:

BYT;
/dev/sda:500GB:scsi:512:512:msdos:ATA SAMSUNG HD501LJ;
1:32.3kB:10.5GB:10.5GB:ntfs::boot;
2:10.5GB:500GB:490GB:::lba;
5:10.5GB:185GB:174GB:ntfs::;
6:185GB:352GB:168GB:ntfs::;
7:352GB:500GB:148GB:ntfs::;

BYT;
/dev/sdb:250GB:scsi:512:512:msdos:ATA SAMSUNG HD252KJ;
1:32.3kB:250GB:250GB:ntfs::;

BYT;
/dev/sdc:7747MB:scsi:512:512:msdos:Kingston DataTraveler 2.0;
1:32.3kB:7747MB:7747MB:fat32::boot;

BYT;
/dev/sdd:82.0GB:scsi:512:512:msdos:ATA Maxtor 6Y080L0;
1:1049kB:52.0GB:52.0GB:ntfs::;
2:52.0GB:82.0GB:30.0GB:::;
6:52.0GB:79.8GB:27.9GB:ext4::boot;
5:79.8GB:82.0GB:2145MB:linux-swap[COLOR=#666666]([/COLOR]v1[COLOR=#666666])[/COLOR]::;


[COLOR=#666666]===================[/COLOR] mount:
/cow on / [COLOR=#AA22FF]type [/COLOR]overlayfs [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]
proc on /proc [COLOR=#AA22FF]type [/COLOR]proc [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev[COLOR=#666666])[/COLOR]
sysfs on /sys [COLOR=#AA22FF]type [/COLOR]sysfs [COLOR=#666666]([/COLOR]rw,noexec,nosuid,nodev[COLOR=#666666])[/COLOR]
udev on /dev [COLOR=#AA22FF]type [/COLOR]devtmpfs [COLOR=#666666]([/COLOR]rw,mode[COLOR=#666666]=[/COLOR]0755[COLOR=#666666])[/COLOR]
devpts on /dev/pts [COLOR=#AA22FF]type [/COLOR]devpts [COLOR=#666666]([/COLOR]rw,noexec,nosuid,gid[COLOR=#666666]=[/COLOR]5,mode[COLOR=#666666]=[/COLOR]0620[COLOR=#666666])[/COLOR]
tmpfs on /run [COLOR=#AA22FF]type [/COLOR]tmpfs [COLOR=#666666]([/COLOR]rw,noexec,nosuid,size[COLOR=#666666]=[/COLOR]10%,mode[COLOR=#666666]=[/COLOR]0755[COLOR=#666666])[/COLOR]
/dev/sdc1 on /cdrom [COLOR=#AA22FF]type [/COLOR]vfat [COLOR=#666666]([/COLOR]ro,noatime,fmask[COLOR=#666666]=[/COLOR]0022,dmask[COLOR=#666666]=[/COLOR]0022,codepage[COLOR=#666666]=[/COLOR]437,iocharset[COLOR=#666666]=[/COLOR]iso8859-1,shortname[COLOR=#666666]=[/COLOR]mixed,errors[COLOR=#666666]=[/COLOR]remount-ro[COLOR=#666666])[/COLOR]
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
gvfsd-fuse on /run/user/999/gvfs [COLOR=#AA22FF]type [/COLOR]fuse.gvfsd-fuse [COLOR=#666666]([/COLOR]rw,nosuid,nodev,user[COLOR=#666666]=[/COLOR]xubuntu[COLOR=#666666])[/COLOR]
/dev/sda1 on /mnt/boot-sav/sda1 [COLOR=#AA22FF]type [/COLOR]fuseblk [COLOR=#666666]([/COLOR]rw,nosuid,nodev,allow_other,blksize[COLOR=#666666]=[/COLOR]4096[COLOR=#666666])[/COLOR]
/dev/sda5 on /mnt/boot-sav/sda5 [COLOR=#AA22FF]type [/COLOR]fuseblk [COLOR=#666666]([/COLOR]rw,nosuid,nodev,allow_other,blksize[COLOR=#666666]=[/COLOR]4096[COLOR=#666666])[/COLOR]
/dev/sda6 on /mnt/boot-sav/sda6 [COLOR=#AA22FF]type [/COLOR]fuseblk [COLOR=#666666]([/COLOR]rw,nosuid,nodev,allow_other,blksize[COLOR=#666666]=[/COLOR]4096[COLOR=#666666])[/COLOR]
/dev/sda7 on /mnt/boot-sav/sda7 [COLOR=#AA22FF]type [/COLOR]fuseblk [COLOR=#666666]([/COLOR]rw,nosuid,nodev,allow_other,blksize[COLOR=#666666]=[/COLOR]4096[COLOR=#666666])[/COLOR]
/dev/sdb1 on /mnt/boot-sav/sdb1 [COLOR=#AA22FF]type [/COLOR]fuseblk [COLOR=#666666]([/COLOR]rw,nosuid,nodev,allow_other,blksize[COLOR=#666666]=[/COLOR]4096[COLOR=#666666])[/COLOR]
/dev/sdd1 on /mnt/boot-sav/sdd1 [COLOR=#AA22FF]type [/COLOR]fuseblk [COLOR=#666666]([/COLOR]rw,nosuid,nodev,allow_other,blksize[COLOR=#666666]=[/COLOR]4096[COLOR=#666666])[/COLOR]
/dev/sdd6 on /mnt/boot-sav/sdd6 [COLOR=#AA22FF]type [/COLOR]ext4 [COLOR=#666666]([/COLOR]rw[COLOR=#666666])[/COLOR]


[COLOR=#666666]===================[/COLOR] ls:
/sys/block/fd0 [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro size slaves stat subsystem trace uevent
/sys/block/sda [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda5 sda6 sda7 size slaves stat subsystem trace uevent
/sys/block/sdb [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdb1 size slaves stat subsystem trace uevent
/sys/block/sdc [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdc1 size slaves stat subsystem trace uevent
/sys/block/sdd [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sdd1 sdd2 sdd5 sdd6 size slaves stat subsystem trace uevent
/dev [COLOR=#666666]([/COLOR]filtered[COLOR=#666666])[/COLOR]:  autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency cuse disk dri ecryptfs fb0 fd fd0 full fuse fw0 hidraw0 hpet input kmsg log mapper mcelog mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda5 sda6 sda7 sdb sdb1 sdc sdc1 sdd sdd1 sdd2 sdd5 sdd6 sg0 sg1 sg2 sg3 shm snapshot snd stderr stdin stdout uhid uinput urandom vga_arbiter vhci vhost-net zero
ls /dev/mapper:  [COLOR=#B8860B]control[/COLOR]

[COLOR=#666666]===================[/COLOR] hexdump -n512 -C /dev/sda1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 00 00 00 80 00 80 00  fb 8a 38 01 00 00 00 00  |..........8.....|
00000030  00 00 0c 00 00 00 00 00  af 88 13 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  63 58 0e 68 81 0e 68 5e  |........cX.h..h^|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 [COLOR=#AA22FF]cd [/COLOR]13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f [COLOR=#AA22FF]cd [/COLOR]13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb [COLOR=#AA22FF]cd [/COLOR]1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu[COLOR=#B8860B]$.[/COLOR]...r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 [COLOR=#AA22FF]cd [/COLOR]1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f [COLOR=#AA22FF]fc [/COLOR]f3 aa  e9 5f 01 90 90 66 60 1e  |[COLOR=#666666]([/COLOR]........_...f[COLOR=#BB4444]`[/COLOR].|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 [COLOR=#AA22FF]cd [/COLOR]13 66  59 5b 5a 66 59 66 59 1f  |.......fY[COLOR=#666666][[/COLOR]ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 [COLOR=#AA22FF]cd  [/COLOR]10 eb f2 c3 0d 0a 41 20  |t.............A |
00000190  64 69 73 6b 20 72 65 61  64 20 65 72 72 6f 72 20  |disk [COLOR=#AA22FF]read [/COLOR]error |
000001a0  6f 63 63 75 72 72 65 64  00 0d 0a 4d 53 46 44 50  |occurred...MSFDP|
000001b0  20 20 20 69 73 20 6d 69  73 73 69 6e 67 00 0d 0a  |   is missing...|
000001c0  4d 53 46 44 50 20 20 20  69 73 20 63 6f 6d 70 72  |MSFDP   is compr|
000001d0  65 73 73 65 64 00 0d 0a  50 72 65 73 73 20 43 74  |essed...Press Ct|
000001e0  72 6c 2b 41 6c 74 2b 44  65 6c 20 74 6f 20 72 65  |rl+Alt+Del to re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 be d6 00 00 55 aa  |start.........U.|
[COLOR=#B8860B]00000200[/COLOR]

[COLOR=#666666]===================[/COLOR] hexdump -n512 -C /dev/sda5
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 00 00 00 80 00 80 00  ea 7d 43 14 00 00 00 00  |.........[COLOR=#666666]}[/COLOR]C.....|
00000030  00 00 0c 00 00 00 00 00  de 37 44 01 00 00 00 00  |.........7D.....|
00000040  f6 00 00 00 01 00 00 00  99 04 09 24 40 09 24 36  |...........[COLOR=#B8860B]$@[/COLOR].[COLOR=#B8860B]$6[/COLOR]|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb b8 c0 07  |.....3.....|....|
00000060  8e d8 e8 16 00 b8 00 0d  8e c0 33 db c6 06 0e 00  |..........3.....|
00000070  10 e8 53 00 68 00 0d 68  6a 02 cb 8a 16 24 00 b4  |..S.h..hj....[COLOR=#B8860B]$.[/COLOR].|
00000080  08 [COLOR=#AA22FF]cd [/COLOR]13 73 05 b9 ff ff  8a f1 66 0f b6 c6 40 66  |...s......f...@f|
00000090  0f b6 d1 80 e2 3f f7 e2  86 [COLOR=#AA22FF]cd [/COLOR]c0 ed 06 41 66 0f  |.....?.......Af.|
000000a0  b7 c9 66 f7 e1 66 a3 20  00 c3 b4 41 bb aa 55 8a  |..f..f. ...A..U.|
000000b0  16 24 00 [COLOR=#AA22FF]cd [/COLOR]13 72 0f 81  fb 55 aa 75 09 f6 c1 01  |.[COLOR=#B8860B]$.[/COLOR]..r...U.u....|
000000c0  74 04 fe 06 14 00 c3 66  60 1e 06 66 a1 10 00 66  |t......f[COLOR=#BB4444]`[/COLOR]..f...f|
000000d0  03 06 1c 00 66 3b 06 20  00 0f 82 3a 00 1e 66 6a  |....f;. ...:..fj|
000000e0  00 66 50 06 53 66 68 10  00 01 00 80 3e 14 00 00  |.fP.Sfh.....>...|
000000f0  0f 85 0c 00 e8 b3 ff 80  3e 14 00 00 0f 84 61 00  |........>.....a.|
00000100  b4 42 8a 16 24 00 16 1f  8b f4 [COLOR=#AA22FF]cd [/COLOR]13 66 58 5b 07  |.B..[COLOR=#B8860B]$.[/COLOR]......fX[COLOR=#666666][[/COLOR].|
00000110  66 58 66 58 1f eb 2d 66  33 d2 66 0f b7 0e 18 00  |fXfX..-f3.f.....|
00000120  66 f7 f1 fe c2 8a ca 66  8b d0 66 c1 ea 10 f7 36  |f......f..f....6|
00000130  1a 00 86 d6 8a 16 24 00  8a e8 c0 e4 06 0a cc b8  |......[COLOR=#B8860B]$.[/COLOR]........|
00000140  01 02 [COLOR=#AA22FF]cd [/COLOR]13 0f 82 19 00  8c c0 05 20 00 8e c0 66  |........... ...f|
00000150  ff 06 10 00 ff 0e 0e 00  0f 85 6f ff 07 1f 66 61  |..........o...fa|
00000160  c3 a0 f8 01 e8 09 00 a0  fb 01 e8 03 00 fb eb fe  |................|
00000170  b4 01 8b f0 ac 3c 00 74  09 b4 0e bb 07 00 [COLOR=#AA22FF]cd [/COLOR]10  |.....<.t........|
00000180  eb f2 c3 0d 0a 4c 65 6d  65 7a 6f 6c 76 61 73 a0  |.....Lemezolvas.|
00000190  73 69 20 68 69 62 61 20  74 94 72 74 82 6e 74 00  |si hiba t.rt.nt.|
000001a0  0d 0a 48 69 a0 6e 79 7a  a2 20 4e 54 4c 44 52 00  |..Hi.nyz. NTLDR.|
000001b0  0d 0a 54 94 6d 94 72 a1  74 65 74 74 20 4e 54 4c  |..T.m.r.tett NTL|
000001c0  44 52 00 0d 0a e9 6a 72  61 69 6e 64 a1 74 a0 73  |DR....jraind.t.s|
000001d0  3a 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 0d 0a  |: Ctrl+Alt+Del..|
000001e0  00 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  |.restart........|
000001f0  00 00 00 00 00 00 00 00  83 a0 b0 c3 00 00 55 aa  |..............U.|
[COLOR=#B8860B]00000200[/COLOR]

[COLOR=#666666]===================[/COLOR] hexdump -n512 -C /dev/sda6
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 00 00 00 80 00 80 00  2d f7 87 13 00 00 00 00  |........-.......|
00000030  00 00 0c 00 00 00 00 00  72 7f 38 01 00 00 00 00  |........r.8.....|
00000040  f6 00 00 00 01 00 00 00  d0 42 16 8c 82 16 8c 70  |.........B.....p|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb b8 c0 07  |.....3.....|....|
00000060  8e d8 e8 16 00 b8 00 0d  8e c0 33 db c6 06 0e 00  |..........3.....|
00000070  10 e8 53 00 68 00 0d 68  6a 02 cb 8a 16 24 00 b4  |..S.h..hj....[COLOR=#B8860B]$.[/COLOR].|
00000080  08 [COLOR=#AA22FF]cd [/COLOR]13 73 05 b9 ff ff  8a f1 66 0f b6 c6 40 66  |...s......f...@f|
00000090  0f b6 d1 80 e2 3f f7 e2  86 [COLOR=#AA22FF]cd [/COLOR]c0 ed 06 41 66 0f  |.....?.......Af.|
000000a0  b7 c9 66 f7 e1 66 a3 20  00 c3 b4 41 bb aa 55 8a  |..f..f. ...A..U.|
000000b0  16 24 00 [COLOR=#AA22FF]cd [/COLOR]13 72 0f 81  fb 55 aa 75 09 f6 c1 01  |.[COLOR=#B8860B]$.[/COLOR]..r...U.u....|
000000c0  74 04 fe 06 14 00 c3 66  60 1e 06 66 a1 10 00 66  |t......f[COLOR=#BB4444]`[/COLOR]..f...f|
000000d0  03 06 1c 00 66 3b 06 20  00 0f 82 3a 00 1e 66 6a  |....f;. ...:..fj|
000000e0  00 66 50 06 53 66 68 10  00 01 00 80 3e 14 00 00  |.fP.Sfh.....>...|
000000f0  0f 85 0c 00 e8 b3 ff 80  3e 14 00 00 0f 84 61 00  |........>.....a.|
00000100  b4 42 8a 16 24 00 16 1f  8b f4 [COLOR=#AA22FF]cd [/COLOR]13 66 58 5b 07  |.B..[COLOR=#B8860B]$.[/COLOR]......fX[COLOR=#666666][[/COLOR].|
00000110  66 58 66 58 1f eb 2d 66  33 d2 66 0f b7 0e 18 00  |fXfX..-f3.f.....|
00000120  66 f7 f1 fe c2 8a ca 66  8b d0 66 c1 ea 10 f7 36  |f......f..f....6|
00000130  1a 00 86 d6 8a 16 24 00  8a e8 c0 e4 06 0a cc b8  |......[COLOR=#B8860B]$.[/COLOR]........|
00000140  01 02 [COLOR=#AA22FF]cd [/COLOR]13 0f 82 19 00  8c c0 05 20 00 8e c0 66  |........... ...f|
00000150  ff 06 10 00 ff 0e 0e 00  0f 85 6f ff 07 1f 66 61  |..........o...fa|
00000160  c3 a0 f8 01 e8 09 00 a0  fb 01 e8 03 00 fb eb fe  |................|
00000170  b4 01 8b f0 ac 3c 00 74  09 b4 0e bb 07 00 [COLOR=#AA22FF]cd [/COLOR]10  |.....<.t........|
00000180  eb f2 c3 0d 0a 4c 65 6d  65 7a 6f 6c 76 61 73 a0  |.....Lemezolvas.|
00000190  73 69 20 68 69 62 61 20  74 94 72 74 82 6e 74 00  |si hiba t.rt.nt.|
000001a0  0d 0a 48 69 a0 6e 79 7a  a2 20 4e 54 4c 44 52 00  |..Hi.nyz. NTLDR.|
000001b0  0d 0a 54 94 6d 94 72 a1  74 65 74 74 20 4e 54 4c  |..T.m.r.tett NTL|
000001c0  44 52 00 0d 0a e9 6a 72  61 69 6e 64 a1 74 a0 73  |DR....jraind.t.s|
000001d0  3a 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 0d 0a  |: Ctrl+Alt+Del..|
000001e0  00 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  |.restart........|
000001f0  00 00 00 00 00 00 00 00  83 a0 b0 c3 00 00 55 aa  |..............U.|
[COLOR=#B8860B]00000200[/COLOR]

[COLOR=#666666]===================[/COLOR] hexdump -n512 -C /dev/sda7
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 00 00 00 80 00 80 00  6e 0c 34 11 00 00 00 00  |........n.4.....|
00000030  00 00 0c 00 00 00 00 00  c6 40 13 01 00 00 00 00  |.........@......|
00000040  f6 00 00 00 01 00 00 00  6d 22 1d dc 3a 1d dc ca  |........m"..:...|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb b8 c0 07  |.....3.....|....|
00000060  8e d8 e8 16 00 b8 00 0d  8e c0 33 db c6 06 0e 00  |..........3.....|
00000070  10 e8 53 00 68 00 0d 68  6a 02 cb 8a 16 24 00 b4  |..S.h..hj....[COLOR=#B8860B]$.[/COLOR].|
00000080  08 [COLOR=#AA22FF]cd [/COLOR]13 73 05 b9 ff ff  8a f1 66 0f b6 c6 40 66  |...s......f...@f|
00000090  0f b6 d1 80 e2 3f f7 e2  86 [COLOR=#AA22FF]cd [/COLOR]c0 ed 06 41 66 0f  |.....?.......Af.|
000000a0  b7 c9 66 f7 e1 66 a3 20  00 c3 b4 41 bb aa 55 8a  |..f..f. ...A..U.|
000000b0  16 24 00 [COLOR=#AA22FF]cd [/COLOR]13 72 0f 81  fb 55 aa 75 09 f6 c1 01  |.[COLOR=#B8860B]$.[/COLOR]..r...U.u....|
000000c0  74 04 fe 06 14 00 c3 66  60 1e 06 66 a1 10 00 66  |t......f[COLOR=#BB4444]`[/COLOR]..f...f|
000000d0  03 06 1c 00 66 3b 06 20  00 0f 82 3a 00 1e 66 6a  |....f;. ...:..fj|
000000e0  00 66 50 06 53 66 68 10  00 01 00 80 3e 14 00 00  |.fP.Sfh.....>...|
000000f0  0f 85 0c 00 e8 b3 ff 80  3e 14 00 00 0f 84 61 00  |........>.....a.|
00000100  b4 42 8a 16 24 00 16 1f  8b f4 [COLOR=#AA22FF]cd [/COLOR]13 66 58 5b 07  |.B..[COLOR=#B8860B]$.[/COLOR]......fX[COLOR=#666666][[/COLOR].|
00000110  66 58 66 58 1f eb 2d 66  33 d2 66 0f b7 0e 18 00  |fXfX..-f3.f.....|
00000120  66 f7 f1 fe c2 8a ca 66  8b d0 66 c1 ea 10 f7 36  |f......f..f....6|
00000130  1a 00 86 d6 8a 16 24 00  8a e8 c0 e4 06 0a cc b8  |......[COLOR=#B8860B]$.[/COLOR]........|
00000140  01 02 [COLOR=#AA22FF]cd [/COLOR]13 0f 82 19 00  8c c0 05 20 00 8e c0 66  |........... ...f|
00000150  ff 06 10 00 ff 0e 0e 00  0f 85 6f ff 07 1f 66 61  |..........o...fa|
00000160  c3 a0 f8 01 e8 09 00 a0  fb 01 e8 03 00 fb eb fe  |................|
00000170  b4 01 8b f0 ac 3c 00 74  09 b4 0e bb 07 00 [COLOR=#AA22FF]cd [/COLOR]10  |.....<.t........|
00000180  eb f2 c3 0d 0a 4c 65 6d  65 7a 6f 6c 76 61 73 a0  |.....Lemezolvas.|
00000190  73 69 20 68 69 62 61 20  74 94 72 74 82 6e 74 00  |si hiba t.rt.nt.|
000001a0  0d 0a 48 69 a0 6e 79 7a  a2 20 4e 54 4c 44 52 00  |..Hi.nyz. NTLDR.|
000001b0  0d 0a 54 94 6d 94 72 a1  74 65 74 74 20 4e 54 4c  |..T.m.r.tett NTL|
000001c0  44 52 00 0d 0a e9 6a 72  61 69 6e 64 a1 74 a0 73  |DR....jraind.t.s|
000001d0  3a 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 0d 0a  |: Ctrl+Alt+Del..|
000001e0  00 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  |.restart........|
000001f0  00 00 00 00 00 00 00 00  83 a0 b0 c3 00 00 55 aa  |..............U.|
[COLOR=#B8860B]00000200[/COLOR]

[COLOR=#666666]===================[/COLOR] hexdump -n512 -C /dev/sdb1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 3f 00 00 00  |........?...?...|
00000020  00 00 00 00 80 00 80 00  41 45 1c 1d 00 00 00 00  |........AE......|
00000030  00 00 0c 00 00 00 00 00  54 c4 d1 01 00 00 00 00  |........T.......|
00000040  f6 00 00 00 01 00 00 00  6f a7 9a f4 c1 9a f4 d2  |........o.......|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb b8 c0 07  |.....3.....|....|
00000060  8e d8 e8 16 00 b8 00 0d  8e c0 33 db c6 06 0e 00  |..........3.....|
00000070  10 e8 53 00 68 00 0d 68  6a 02 cb 8a 16 24 00 b4  |..S.h..hj....[COLOR=#B8860B]$.[/COLOR].|
00000080  08 [COLOR=#AA22FF]cd [/COLOR]13 73 05 b9 ff ff  8a f1 66 0f b6 c6 40 66  |...s......f...@f|
00000090  0f b6 d1 80 e2 3f f7 e2  86 [COLOR=#AA22FF]cd [/COLOR]c0 ed 06 41 66 0f  |.....?.......Af.|
000000a0  b7 c9 66 f7 e1 66 a3 20  00 c3 b4 41 bb aa 55 8a  |..f..f. ...A..U.|
000000b0  16 24 00 [COLOR=#AA22FF]cd [/COLOR]13 72 0f 81  fb 55 aa 75 09 f6 c1 01  |.[COLOR=#B8860B]$.[/COLOR]..r...U.u....|
000000c0  74 04 fe 06 14 00 c3 66  60 1e 06 66 a1 10 00 66  |t......f[COLOR=#BB4444]`[/COLOR]..f...f|
000000d0  03 06 1c 00 66 3b 06 20  00 0f 82 3a 00 1e 66 6a  |....f;. ...:..fj|
000000e0  00 66 50 06 53 66 68 10  00 01 00 80 3e 14 00 00  |.fP.Sfh.....>...|
000000f0  0f 85 0c 00 e8 b3 ff 80  3e 14 00 00 0f 84 61 00  |........>.....a.|
00000100  b4 42 8a 16 24 00 16 1f  8b f4 [COLOR=#AA22FF]cd [/COLOR]13 66 58 5b 07  |.B..[COLOR=#B8860B]$.[/COLOR]......fX[COLOR=#666666][[/COLOR].|
00000110  66 58 66 58 1f eb 2d 66  33 d2 66 0f b7 0e 18 00  |fXfX..-f3.f.....|
00000120  66 f7 f1 fe c2 8a ca 66  8b d0 66 c1 ea 10 f7 36  |f......f..f....6|
00000130  1a 00 86 d6 8a 16 24 00  8a e8 c0 e4 06 0a cc b8  |......[COLOR=#B8860B]$.[/COLOR]........|
00000140  01 02 [COLOR=#AA22FF]cd [/COLOR]13 0f 82 19 00  8c c0 05 20 00 8e c0 66  |........... ...f|
00000150  ff 06 10 00 ff 0e 0e 00  0f 85 6f ff 07 1f 66 61  |..........o...fa|
00000160  c3 a0 f8 01 e8 09 00 a0  fb 01 e8 03 00 fb eb fe  |................|
00000170  b4 01 8b f0 ac 3c 00 74  09 b4 0e bb 07 00 [COLOR=#AA22FF]cd [/COLOR]10  |.....<.t........|
00000180  eb f2 c3 0d 0a 4c 65 6d  65 7a 6f 6c 76 61 73 a0  |.....Lemezolvas.|
00000190  73 69 20 68 69 62 61 20  74 94 72 74 82 6e 74 00  |si hiba t.rt.nt.|
000001a0  0d 0a 48 69 a0 6e 79 7a  a2 20 4e 54 4c 44 52 00  |..Hi.nyz. NTLDR.|
000001b0  0d 0a 54 94 6d 94 72 a1  74 65 74 74 20 4e 54 4c  |..T.m.r.tett NTL|
000001c0  44 52 00 0d 0a e9 6a 72  61 69 6e 64 a1 74 a0 73  |DR....jraind.t.s|
000001d0  3a 20 43 74 72 6c 2b 41  6c 74 2b 44 65 6c 0d 0a  |: Ctrl+Alt+Del..|
000001e0  00 72 65 73 74 61 72 74  0d 0a 00 00 00 00 00 00  |.restart........|
000001f0  00 00 00 00 00 00 00 00  83 a0 b0 c3 00 00 55 aa  |..............U.|
[COLOR=#B8860B]00000200[/COLOR]

[COLOR=#666666]===================[/COLOR] hexdump -n512 -C /dev/sdd1
00000000  eb 52 90 4e 54 46 53 20  20 20 20 00 02 08 00 00  |.R.NTFS    .....|
00000010  00 00 00 00 00 f8 00 00  3f 00 ff 00 00 08 00 00  |........?.......|
00000020  00 00 00 00 80 00 80 00  20 51 0c 06 00 00 00 00  |........ Q......|
00000030  00 00 0c 00 00 00 00 00  02 00 00 00 00 00 00 00  |................|
00000040  f6 00 00 00 01 00 00 00  9d e3 67 6c 32 68 6c be  |..........gl2hl.|
00000050  00 00 00 00 fa 33 c0 8e  d0 bc 00 7c fb 68 c0 07  |.....3.....|.h..|
00000060  1f 1e 68 66 00 cb 88 16  0e 00 66 81 3e 03 00 4e  |..hf......f.>..N|
00000070  54 46 53 75 15 b4 41 bb  aa 55 [COLOR=#AA22FF]cd [/COLOR]13 72 0c 81 fb  |TFSu..A..U..r...|
00000080  55 aa 75 06 f7 c1 01 00  75 03 e9 dd 00 1e 83 ec  |U.u.....u.......|
00000090  18 68 1a 00 b4 48 8a 16  0e 00 8b f4 16 1f [COLOR=#AA22FF]cd [/COLOR]13  |.h...H..........|
000000a0  9f 83 c4 18 9e 58 1f 72  e1 3b 06 0b 00 75 db a3  |.....X.r.;...u..|
000000b0  0f 00 c1 2e 0f 00 04 1e  5a 33 db b9 00 20 2b c8  |........Z3... +.|
000000c0  66 ff 06 11 00 03 16 0f  00 8e c2 ff 06 16 00 e8  |f...............|
000000d0  4b 00 2b c8 77 ef b8 00  bb [COLOR=#AA22FF]cd [/COLOR]1a 66 23 c0 75 2d  |K.+.w......f#.u-|
000000e0  66 81 fb 54 43 50 41 75  24 81 f9 02 01 72 1e 16  |f..TCPAu[COLOR=#B8860B]$.[/COLOR]...r..|
000000f0  68 07 bb 16 68 70 0e 16  68 09 00 66 53 66 53 66  |h...hp..h..fSfSf|
00000100  55 16 16 16 68 b8 01 66  61 0e 07 [COLOR=#AA22FF]cd [/COLOR]1a 33 c0 bf  |U...h..fa....3..|
00000110  28 10 b9 d8 0f [COLOR=#AA22FF]fc [/COLOR]f3 aa  e9 5f 01 90 90 66 60 1e  |[COLOR=#666666]([/COLOR]........_...f[COLOR=#BB4444]`[/COLOR].|
00000120  06 66 a1 11 00 66 03 06  1c 00 1e 66 68 00 00 00  |.f...f.....fh...|
00000130  00 66 50 06 53 68 01 00  68 10 00 b4 42 8a 16 0e  |.fP.Sh..h...B...|
00000140  00 16 1f 8b f4 [COLOR=#AA22FF]cd [/COLOR]13 66  59 5b 5a 66 59 66 59 1f  |.......fY[COLOR=#666666][[/COLOR]ZfYfY.|
00000150  0f 82 16 00 66 ff 06 11  00 03 16 0f 00 8e c2 ff  |....f...........|
00000160  0e 16 00 75 bc 07 1f 66  61 c3 a0 f8 01 e8 09 00  |...u...fa.......|
00000170  a0 fb 01 e8 03 00 f4 eb  fd b4 01 8b f0 ac 3c 00  |..............<.|
00000180  74 09 b4 0e bb 07 00 [COLOR=#AA22FF]cd  [/COLOR]10 eb f2 c3 0d 0a 4c 65  |t.............Le|
00000190  6d 65 7a 6f 6c 76 61 73  a0 73 69 20 68 69 62 61  |mezolvas.si hiba|
000001a0  20 74 94 72 74 82 6e 74  00 0d 0a 48 69 a0 6e 79  | t.rt.nt...Hi.ny|
000001b0  7a a2 20 42 4f 4f 54 4d  47 52 00 0d 0a 54 94 6d  |z. BOOTMGR...T.m|
000001c0  94 72 a1 74 65 74 74 20  42 4f 4f 54 4d 47 52 00  |.r.tett BOOTMGR.|
000001d0  0d 0a e9 6a 72 61 69 6e  64 a1 74 a0 73 3a 20 43  |...jraind.t.s: C|
000001e0  74 72 6c 2b 41 6c 74 2b  44 65 6c 0d 0a 00 72 65  |trl+Alt+Del...re|
000001f0  73 74 61 72 74 0d 0a 00  8c a9 bb d0 00 00 55 aa  |start.........U.|
[COLOR=#B8860B]00000200[/COLOR]

[COLOR=#666666]===================[/COLOR] df -Th:

Filesystem     Type       Size  Used Avail Use% Mounted on
/cow           overlayfs 1008M  149M  860M  15% /
udev           devtmpfs   998M   12K  998M   1% /dev
tmpfs          tmpfs      202M  1.3M  201M   1% /run
/dev/sdc1      vfat       7.2G  941M  6.3G  13% /cdrom
/dev/loop0     squashfs   884M  884M     0 100% /rofs
none           tmpfs      4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          tmpfs     1008M   12K 1008M   1% /tmp
none           tmpfs      5.0M     0  5.0M   0% /run/lock
none           tmpfs     1008M   80K 1008M   1% /run/shm
none           tmpfs      100M   24K  100M   1% /run/user
/dev/sda1      fuseblk    9.8G  7.8G  2.0G  80% /mnt/boot-sav/sda1
/dev/sda5      fuseblk    163G  102G   61G  63% /mnt/boot-sav/sda5
/dev/sda6      fuseblk    157G  146G   11G  94% /mnt/boot-sav/sda6
/dev/sda7      fuseblk    138G  106G   32G  77% /mnt/boot-sav/sda7
/dev/sdb1      fuseblk    233G  232G  1.2G 100% /mnt/boot-sav/sdb1
/dev/sdd1      fuseblk     49G   39G  9.5G  81% /mnt/boot-sav/sdd1
/dev/sdd6      ext4        26G  2.6G   22G  11% /mnt/boot-sav/sdd6

[COLOR=#666666]===================[/COLOR] fdisk -l:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
[COLOR=#B8860B]Units[/COLOR] [COLOR=#666666]=[/COLOR] sectors of 1 * [COLOR=#B8860B]512[/COLOR] [COLOR=#666666]=[/COLOR] 512 bytes
Sector size [COLOR=#666666]([/COLOR]logical/physical[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
I/O size [COLOR=#666666]([/COLOR]minimum/optimal[COLOR=#666666])[/COLOR]: 512 bytes / 512 bytes
Disk identifier: 0x2fa92fa9

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    20482874    10241406    7  HPFS/NTFS/exFAT
/dev/sda2        20482875   976751999   478134562+   f  W95 Ext[COLOR=#BB4444]'d (LBA)[/COLOR]
[COLOR=#BB4444]/dev/sda5        20482938   360450404   169983733+   7  HPFS/NTFS/exFAT[/COLOR]
[COLOR=#BB4444]/dev/sda6       360450468   688128209   163838871    7  HPFS/NTFS/exFAT[/COLOR]
[COLOR=#BB4444]/dev/sda7       688128273   976751999   144311863+   7  HPFS/NTFS/exFAT[/COLOR]

[COLOR=#BB4444]Disk /dev/sdb: 250.1 GB, 250059350016 bytes[/COLOR]
[COLOR=#BB4444]255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors[/COLOR]
[COLOR=#BB4444]Units = sectors of 1 * 512 = 512 bytes[/COLOR]
[COLOR=#BB4444]Sector size (logical/physical): 512 bytes / 512 bytes[/COLOR]
[COLOR=#BB4444]I/O size (minimum/optimal): 512 bytes / 512 bytes[/COLOR]
[COLOR=#BB4444]Disk identifier: 0xc7b28950[/COLOR]

[COLOR=#BB4444]Device Boot      Start         End      Blocks   Id  System[/COLOR]
[COLOR=#BB4444]/dev/sdb1              63   488392064   244196001   42  SFS[/COLOR]

[COLOR=#BB4444]Disk /dev/sdc: 7747 MB, 7747397632 bytes[/COLOR]
[COLOR=#BB4444]32 heads, 63 sectors/track, 7505 cylinders, total 15131636 sectors[/COLOR]
[COLOR=#BB4444]Units = sectors of 1 * 512 = 512 bytes[/COLOR]
[COLOR=#BB4444]Sector size (logical/physical): 512 bytes / 512 bytes[/COLOR]
[COLOR=#BB4444]I/O size (minimum/optimal): 512 bytes / 512 bytes[/COLOR]
[COLOR=#BB4444]Disk identifier: 0x70b2284d[/COLOR]

[COLOR=#BB4444]Device Boot      Start         End      Blocks   Id  System[/COLOR]
[COLOR=#BB4444]/dev/sdc1   *          63    15130079     7565008+   b  W95 FAT32[/COLOR]

[COLOR=#BB4444]Disk /dev/sdd: 82.0 GB, 81963220480 bytes[/COLOR]
[COLOR=#BB4444]255 heads, 63 sectors/track, 9964 cylinders, total 160084415 sectors[/COLOR]
[COLOR=#BB4444]Units = sectors of 1 * 512 = 512 bytes[/COLOR]
[COLOR=#BB4444]Sector size (logical/physical): 512 bytes / 512 bytes[/COLOR]
[COLOR=#BB4444]I/O size (minimum/optimal): 512 bytes / 512 bytes[/COLOR]
[COLOR=#BB4444]Disk identifier: 0x17431742[/COLOR]

[COLOR=#BB4444]Device Boot      Start         End      Blocks   Id  System[/COLOR]
[COLOR=#BB4444]/dev/sdd1            2048   101472555    50735254    7  HPFS/NTFS/exFAT[/COLOR]
[COLOR=#BB4444]/dev/sdd2       101474302   160083967    29304833    5  Extended[/COLOR]
[COLOR=#BB4444]/dev/sdd5       155893760   160083967     2095104   82  Linux swap / Solaris[/COLOR]
[COLOR=#BB4444]/dev/sdd6   *   101474304   155893759    27209728   83  Linux[/COLOR]

[COLOR=#BB4444]Partition table entries are not in disk order[/COLOR]


[COLOR=#BB4444]User choice: Is sdd (82.0GB) a removable disk? no[/COLOR]
[COLOR=#BB4444]=================== Advices[/COLOR]
[COLOR=#BB4444]SFS detected. You may want to retry after converting Windows dynamic partitioning (SFS partitions) to a basic disk. This can be performed via tools such as TestDisk or EASEUS-Partition-Master / MiniTool-Partition-Wizard.[/COLOR]
[COLOR=#BB4444]Do you want to continue?[/COLOR]

[COLOR=#BB4444]=================== Default settings[/COLOR]
[COLOR=#BB4444]Recommended-Repair[/COLOR]
[COLOR=#BB4444]This setting would reinstall the grub2 of sdd6 into the MBRs of all disks (except USB without OS).[/COLOR]
[COLOR=#BB4444]The boot flag would be placed on sdd6.[/COLOR]
[COLOR=#BB4444]Additional repair would be performed: unhide-bootmenu-10s[/COLOR]

[COLOR=#BB4444]=================== Settings chosen by the user[/COLOR]
[COLOR=#BB4444]Custom-Repair[/COLOR]
[COLOR=#BB4444]This setting will reinstall the grub2 of sdd6 into the MBR of sdd.[/COLOR]
[COLOR=#BB4444]The boot flag will be placed on sdd6.[/COLOR]
[COLOR=#BB4444]Additional repair will be performed: unhide-bootmenu-10s[/COLOR]



[COLOR=#BB4444]*******lspci -nnk | grep -iA3 vga[/COLOR]
[COLOR=#BB4444]01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G73 [GeForce 7300 GT] [10de:0393] (rev a1)[/COLOR]
[COLOR=#BB4444]Kernel driver in use: nouveau[/COLOR]
[COLOR=#BB4444]02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller [11ab:4364] (rev 12)[/COLOR]
[COLOR=#BB4444]Subsystem: ASUSTeK Computer Inc. Motherboard [1043:81f8][/COLOR]
[COLOR=#BB4444]*******[/COLOR]

[COLOR=#BB4444]grub-install: info: executing modprobe efivars 2>/dev/null.[/COLOR]
[COLOR=#BB4444]grub-install: info: Looking for /sys/firmware/efi ...[/COLOR]
[COLOR=#BB4444]grub-install: info: ... not found. Looking for /proc/device-tree ...[/COLOR]
[COLOR=#BB4444]grub-install: info: ... not found.[/COLOR]
[COLOR=#BB4444]Installing for i386-pc platform.[/COLOR]
[COLOR=#BB4444]grub-install: error: install device isn'[/COLOR]t specified.
,.

Reinstall the GRUB of sdd6 into the MBR of sdd
Installing [COLOR=#AA22FF]**for **[/COLOR]i386-pc platform.
Installation finished. No error reported.
grub-install /dev/sdd: [COLOR=#AA22FF]exit [/COLOR]code of grub-install /dev/sdd:0

chroot /mnt/boot-sav/sdd6 update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 [COLOR=#666666]([/COLOR]loader[COLOR=#666666])[/COLOR] on /dev/sda1
Found Windows 7 [COLOR=#666666]([/COLOR]loader[COLOR=#666666])[/COLOR] on /dev/sdd1
Unhide GRUB boot menu in sdd6/boot/grub/grub.cfg

Boot successfully repaired.

You can now reboot your computer. [COLOR=#000000]Please [/COLOR][COLOR=#AA22FF]**do **[/COLOR][COLOR=#000000]not forget to make your BIOS boot on sdd [/COLOR][COLOR=#666666]([/COLOR][COLOR=#000000]82.0GB[/COLOR][COLOR=#666666])[/COLOR][COLOR=#000000] disk![/COLOR]
```

---

### Post by gubtan on 2014-10-25
I hope this will nearest to the solution.

After I start the PC but the problem is here, I log in the BIOS the first boot device is a 82,0GB disk.

What will the next step?

---

### Post by Bashing-om on 2014-10-25
gubtan; Hello;

I appears that grub is successfully installed ( primary boot device is sdd - the 82.0 GB drive - ).
When booting the machine with the 82.0 GB dvice as 1st boot priority ->
a) Do you boot to the grub boot menu ?

b) Can you boot ubuntu  from the boot menu ?

c) Can you boot Windows that is on the 1st hard drive from the grub boot menu ?

d) Can your boot Windows that is on the 82.0 GB drive's 1st partition from the grub boot menu ?

If any of the above fails, explain what actions you have taken, what you expected to happen, and what actually did happen.
("After I start the PC but the problem is here" does not convey useful information, we need to know specifics)

I presently do not perceive a fault, Anyone else see an error ?

[INDENT][INDENT]in the process, fault isolation
[/INDENT][/INDENT]

---

### Post by gubtan on 2014-10-26
Dear Bashing-om,

a.) When I start the PC I see the grub boot menu.
b.) When I choose "Ubuntu" from the grub the error at that time occurs.
c.) In the grub menu I see twoo Windows 7, one on the sda, one on the sdd. I choose that which is on the sdd.
d.) Yes, I can boot the Windows 7 from the grub which is on the 82,0 GB drive (sdd).

What can I do to enjoy the wanted system?

](*,)](*,)](*,)](*,)](*,)

---

### Post by Bashing-om on 2014-10-26
gubtan; Hi !

Rather then taking the time and effort to find the exact reason for failure, let us take a sledge hammer approach and
just (RE-)install grub.
To that end, boot the liveDVD - the same release as that of the install ! -> "try ubuntu" mode -> terminal.
In the liveDVD execute terminal command:
```

sudo fdisk -lu

```
TO make sure our target remains with the same device identification ( ssd6 ).
If the system still sees ssd6 as the ubuntu install location, then:
```

sudo mount /dev/sdd6 /mnt
sudo grub-install --boot-directory=/mnt /dev/sdd
sudo umount /mnt

```

Reboot to bios and set the boot priority to the sdd drive as the 1st boot priority.
Boot into the install of ubuntu and now issue terminal command:
```

sudo update-grub

```
such that grub picks up the other Windows operating systems and chainloads them onto the boot menu. IF this is not the desired result, we will do something else.

Reboot, sdd still as 1st choice boot priority, and tell me all is good.

[INDENT][INDENT][INDENT]it could happen
[/INDENT][/INDENT][/INDENT]

---

### Post by gubtan on 2014-10-27
Dear Bashing/om,

I did what zou wote but this is the result

```
it@it:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2fa92fa9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    20482874    10241406    7  HPFS/NTFS/exFAT
/dev/sda2        20482875   976751999   478134562+   f  W95 Ext'd (LBA)
/dev/sda5        20482938   360450404   169983733+   7  HPFS/NTFS/exFAT
/dev/sda6       360450468   688128209   163838871    7  HPFS/NTFS/exFAT
/dev/sda7       688128273   976751999   144311863+   7  HPFS/NTFS/exFAT

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc7b28950

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   488392064   244196001   42  SFS

Disk /dev/sdc: 7747 MB, 7747397632 bytes
32 heads, 63 sectors/track, 7505 cylinders, total 15131636 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x70b2284d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63    15130079     7565008+   c  W95 FAT32 (LBA)

Disk /dev/sdd: 82.0 GB, 81963220480 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160084415 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x17431742

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1            2048   101472555    50735254    7  HPFS/NTFS/exFAT
/dev/sdd2       101474302   160083967    29304833    5  Extended
/dev/sdd5       155893760   160083967     2095104   82  Linux swap / Solaris
/dev/sdd6   *   101474304   155893759    27209728   83  Linux

Partition table entries are not in disk order
it@it:~$ sudo mount /dev/sdd6 /mnt
it@it:~$ sudo grub-install --boot-directory=/mnt /dev/sdd
Installing for i386-pc platform.
Installation finished. No error reported.
it@it:~$ sudo umount /mnt
it@it:~$ sudo update-grub
/usr/sbin/grub-probe: error: failed to get canonical path of `/cow'.
it@it:~$ 

```

What can I do?

---

### Post by Elfy on 2014-10-27
```
it@it:~$ sudo grub-install --boot-directory=/mnt /dev/sdd
Installing for i386-pc platform.
Installation finished. No error reported.
```

That worked.

You then unmounted and then tried to update-grub for the live session.

That's not what you were advised to do ;)

You were advised to install grub after mounting - you did that and it worked, then advised to reboot

> Reboot to bios and set the boot priority to the sdd drive as the 1st boot priority.
Boot into the install of ubuntu and now issue terminal command:

and THEN update grub.

Try that now.

---

### Post by gubtan on 2014-10-27
Dear Elfy,

I start PC with USBlive xubuntu, I tiped to the terminal>

```
sudo mount /dev/sdd6 /mnt
sudo grub-install --boot-directory=/mnt /dev/sdd
sudo umount /mnt
```

I restarted the PC, I login to the BIOS, I checked that the 1st boot device is the 82,0GB drive.

After I restart the PC and it was the result:

[IMG]http://kepfeltoltes.hu/141027/CAM00730_www.kepfeltoltes.hu_.jpg[/IMG]

](*,)

---

### Post by Bashing-om on 2014-10-27
gubtan; Humm ...

@ Elfy; Glad you are at my back ! Your confirmation and support is highly appreciated .

@ gubtan:
Still with a control file in an inconsistent state .
Let us go a step deeper>
From the liveDVD: - copy and paste all the below commands for the BEST results -
```

sudo mount /dev/sdd6 /mnt/
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo mount --bind /dev/pts /mnt/dev/pts
sudo mount --bind /run /mnt/run
sudo chroot /mnt/ /bin/bash

grub-install --recheck /dev/sdd

```

All the above just so the operating system can check/re-install the control files.
Now, back out gracefully from that CHange Root that was made:
```

exit
sudo umount /mnt/run
sudo umount /mnt/dev/pts
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt/dev
sudo umount /mnt

```

You are now back in the liveDVD environment, at this time reboot back  into the install.
Remove the liveDVD, reset bios (If required) to boot from the hard drive (sdd).

When you have booted into the install run terminal command:
```

sudo update-grub

```
to pick up and chainload the other operating systems onto grub's boot menu.

[INDENT][INDENT]fingers are crossed
[INDENT][INDENT][INDENT]this procedure could work
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by gubtan on 2014-10-28
Dear Bashing-om!

I plug the pendrive to the PC and I started it.

I boot into xubuntu live.

Then I opened a terminal and tiped your commands:

```

[COLOR=#000000][FONT=Ubuntu Mono]sudo mount /dev/sdd6 /mnt/
[/FONT][/COLOR]sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo mount --bind /dev/pts /mnt/dev/pts
sudo mount --bind /run /mnt/run
sudo chroot /mnt/ /bin/bash
[COLOR=#000000][FONT=Ubuntu Mono]grub-install --recheck /dev/sdd
[/FONT][/COLOR]
```

[ATTACH=CONFIG]257553[/ATTACH]

And the I tiped your following commands:

```

[COLOR=#000000][FONT=Ubuntu Mono]exit
[/FONT][/COLOR]sudo umount /mnt/run
sudo umount /mnt/dev/pts
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt/dev
[COLOR=#000000][FONT=Ubuntu Mono]sudo umount /mnt
[/FONT][/COLOR]
```

[ATTACH=CONFIG]257554[/ATTACH]

Then I close the terminal and I choose the restart from the xubuntu main menu.

When the PC restarted I removed the pendrive and I saw the following:

[ATTACH=CONFIG]257555[/ATTACH]

I choose "Ubuntu" and pressed Enter.

After few moments I saw the following:

[ATTACH=CONFIG]257556[/ATTACH]

GR*******GR!

](*,)](*,)](*,)

What is the problem?

Regadrs, 

gubtan

---

### Post by Bashing-om on 2014-10-28
gubtan; Well !

Grub still not finding the partition it is looking for.

Let's see what we can do to match up the partitions to what grub wants.
Mount the install partition:
From the liveDVD:
```

sudo mkdir /mnt/work
sudo mount /dev/sdd6 /mnt/work

```

and now we see what UUIDs the system has assigned, and see if they match up with what is to be 'mounted' :
```

sudo blkid
sudo cat /mnt/work/etc/fstab

```

All done for the present with looking, and as we mounted 'sdd6' manually we are responsible for UN-mounting that partition:
```

sudo umount /mnt/work

```

Depending on those outputs is what we do next.

[INDENT][INDENT]must be a cause
[INDENT][INDENT][INDENT]we will find the solution
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by gubtan on 2014-10-29
Dear  Bashing-om

I did what you wrote this is the result

[IMG]http://kepfeltoltes.hu/141029/67317468620141029_www.kepfeltoltes.hu_.jpg[/IMG]

[ATTACH=CONFIG]257575[/ATTACH]

What can we to do like the next step?

Regards

gubtan

---

### Post by Bashing-om on 2014-10-29
gubtan; Humm ...

/etc/fstab and 'blkid' agree, we must look elsewhere for the fault.

Let's look and see what the system is set to boot up;
Mount the ubuntu file system from the liveDVD:
```

sudo mkdir /mnt/work
sudo mount /dev/sdd6 /mnt/work

```

Now let's see what is:
```

ls -al /mnt/work
ls -al /mnt/work/boot
cat /mnt/work/boot/grub/grub.cfg

```

Done, so now back out gracefully once more:
```

sudo umount /mnt/work

```

We are just looking to see;
If these are all in order, all I know to do next is try and manually boot the system from grub and see what response grub offers.

[INDENT][INDENT]sometimes I wonder
[INDENT][INDENT][INDENT][INDENT]other times I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by gubtan on 2014-10-30
Dear Bashing-om,

The results are the following:

After:
```
sudo mkdir /mnt/work
sudo mount /dev/sdd6 /mnt/work
ls -al /mnt/work
```

[ATTACH=CONFIG]257601[/ATTACH]

After:

```
ls -al /mnt/work/boot


```

[ATTACH=CONFIG]257602[/ATTACH]

After:

```


cat /mnt/work/boot/grub/grub.cfg


```

Here is what I saw:

```


it@it:~$ cat /mnt/work/boot/grub/grub.cfg
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
if [ "${next_entry}" ] ; then
   set default="${next_entry}"
   set next_entry=
   save_env next_entry
   set boot_once=true
else
   set default="0"
fi

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}
function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}
function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_msdos
insmod ext2
set root='hd3,msdos6'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd3,msdos6 --hint-efi=hd3,msdos6 --hint-baremetal=ahci3,msdos6  31639a40-269a-4d7e-b4c4-8ebbbcb08ab5
else
  search --no-floppy --fs-uuid --set=root 31639a40-269a-4d7e-b4c4-8ebbbcb08ab5
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ] ; then
  set timeout=10
else
  if [ x$feature_timeout_style = xy ] ; then
    set timeout_style=menu
    set timeout=10
  # Fallback normal timeout code in case the timeout_style feature is
  # unavailable.
  else
    set timeout=10
  fi
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-31639a40-269a-4d7e-b4c4-8ebbbcb08ab5' {
	recordfail
	load_video
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_msdos
	insmod ext2
	set root='hd3,msdos6'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd3,msdos6 --hint-efi=hd3,msdos6 --hint-baremetal=ahci3,msdos6  31639a40-269a-4d7e-b4c4-8ebbbcb08ab5
	else
	  search --no-floppy --fs-uuid --set=root 31639a40-269a-4d7e-b4c4-8ebbbcb08ab5
	fi
	linux	/boot/vmlinuz-3.13.0-32-generic root=UUID=31639a40-269a-4d7e-b4c4-8ebbbcb08ab5 ro  quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.13.0-32-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-31639a40-269a-4d7e-b4c4-8ebbbcb08ab5' {
	menuentry 'Ubuntu, with Linux 3.13.0-32-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-advanced-31639a40-269a-4d7e-b4c4-8ebbbcb08ab5' {
		recordfail
		load_video
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd3,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd3,msdos6 --hint-efi=hd3,msdos6 --hint-baremetal=ahci3,msdos6  31639a40-269a-4d7e-b4c4-8ebbbcb08ab5
		else
		  search --no-floppy --fs-uuid --set=root 31639a40-269a-4d7e-b4c4-8ebbbcb08ab5
		fi
		echo	'Loading Linux 3.13.0-32-generic ...'
		linux	/boot/vmlinuz-3.13.0-32-generic root=UUID=31639a40-269a-4d7e-b4c4-8ebbbcb08ab5 ro  quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-32-generic
	}
	menuentry 'Ubuntu, with Linux 3.13.0-32-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.13.0-32-generic-recovery-31639a40-269a-4d7e-b4c4-8ebbbcb08ab5' {
		recordfail
		load_video
		insmod gzio
		insmod part_msdos
		insmod ext2
		set root='hd3,msdos6'
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root --hint-bios=hd3,msdos6 --hint-efi=hd3,msdos6 --hint-baremetal=ahci3,msdos6  31639a40-269a-4d7e-b4c4-8ebbbcb08ab5
		else
		  search --no-floppy --fs-uuid --set=root 31639a40-269a-4d7e-b4c4-8ebbbcb08ab5
		fi
		echo	'Loading Linux 3.13.0-32-generic ...'
		linux	/boot/vmlinuz-3.13.0-32-generic root=UUID=31639a40-269a-4d7e-b4c4-8ebbbcb08ab5 ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.13.0-32-generic
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
	insmod part_msdos
	insmod ext2
	set root='hd3,msdos6'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd3,msdos6 --hint-efi=hd3,msdos6 --hint-baremetal=ahci3,msdos6  31639a40-269a-4d7e-b4c4-8ebbbcb08ab5
	else
	  search --no-floppy --fs-uuid --set=root 31639a40-269a-4d7e-b4c4-8ebbbcb08ab5
	fi
	knetbsd	/boot/memtest86+.elf
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
	insmod part_msdos
	insmod ext2
	set root='hd3,msdos6'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd3,msdos6 --hint-efi=hd3,msdos6 --hint-baremetal=ahci3,msdos6  31639a40-269a-4d7e-b4c4-8ebbbcb08ab5
	else
	  search --no-floppy --fs-uuid --set=root 31639a40-269a-4d7e-b4c4-8ebbbcb08ab5
	fi
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 7 (loader) (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-5E680E81680E5863' {
	insmod part_msdos
	insmod ntfs
	set root='hd0,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  5E680E81680E5863
	else
	  search --no-floppy --fs-uuid --set=root 5E680E81680E5863
	fi
	parttool ${root} hidden-
	chainloader +1
}
menuentry 'Windows 7 (loader) (on /dev/sdd1)' --class windows --class os $menuentry_id_option 'osprober-chain-BE6C68326C67E39D' {
	insmod part_msdos
	insmod ntfs
	set root='hd3,msdos1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd3,msdos1 --hint-efi=hd3,msdos1 --hint-baremetal=ahci3,msdos1  BE6C68326C67E39D
	else
	  search --no-floppy --fs-uuid --set=root BE6C68326C67E39D
	fi
	parttool ${root} hidden-
	chainloader +1
}
set timeout_style=menu
if [ "${timeout}" = 0 ]; then
  set timeout=10
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
it@it:~$ 


```

I am waiting for the next step.

](*,)](*,)](*,)

---

### Post by Bashing-om on 2014-10-30
gubtan; Humm;

I am surprised that there is but one kernel available to boot from, and it is a very old one at that.
Can you explain this circumstance ? Have you never been able to update the system ?

Perhaps what is required at this time is to do a Full CHange Root into the install and update/upgrade the system from there ?

[INDENT]look'n for that way forward
[/INDENT]

---

### Post by gubtan on 2014-10-30
Dear Bashing-om,

I use Windows 7 everyday in my job.

I downloaded ISO of the Xubuntu 14.04.1 LTS from this site:

[http://ubuntu.hu/letoltes/tovabb](http://ubuntu.hu/letoltes/tovabb)

After I downloaded the UNetbootin from this site:

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

And then I pluged a pendrive in my USB port of my PC. 
I started UNetbootin and I made the booting live USB pendrive from the ISO from the downloaded Xubuntu. 
I restarted my PC, pressed F8, at the booting menu I choose the pendrive.
The Xubuntu started from the pendrive.
I choose the first point that "Install Xubuntu...". 
The installing started.
At the partitioning sector I choosed "Install Xubuntu alongside Windows 7", and next I used the slider and setup the partition of the Xubuntu to 30GB.
The installation procedure ran without any fault.
After the installation and the restart of the PC occured the fault what I started this topic.

Please help me somehow because I lost my faith slowly.

While I browse the net I found a guide to this theme. Please check it on this link and write to me your opinion about it:

[http://www.dedoimedo.com/computers/dual-boot-windows-7-xubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-7-xubuntu.html)

Regards, 

gubtan

---

### Post by Bashing-om on 2014-10-30
gubtan; Yes;

A great tutorial, I have but one point of difference with the author, in that I recommend that any work done on a Window's partition be done with Window's tools.
a) From Windows defrag the file system at least twice
b) Using Window's disk utility, shrink the Windows' operating system partition
c) from Windows, run check disk twice to insure the new partition table is correct
d) Now one may install ubuntu ( manual selection) into that "unallocated space -> partitioned as a user preference.


To our situation at hand, ubuntu is installed, but has never been updated. Let's take care of that detail, then see where we stand.
To that end we will do a Full Change Root from the liveDVD.

Boot up the liveDVD -> "try ubuntu" mode -> terminal:
Terminal commands:
```

sudo mount /dev/sdd6 /mnt/
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo mount --bind /dev/pts /mnt/dev/pts
sudo mount --bind /run /mnt/run
sudo chroot /mnt/ /bin/bash

```

You see the terminal prompt has changed - you are now root, be triple cautious and exercise due care.
Presently insure that networking is available:
```

ping -c3 google.com

```
You get a response like this:
```

--- google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 25.086/28.571/31.270/2.592 ms
sysop@1404mini:~$

```
IF you do not - STOP, we can not proceed with out a working internet connection.
If the response is good - no reason for it not to be at this point - proceed to update the system:
```

apt -get update
apt-get upgrade
apt-get dist-upgrade
update-grub

```

OK, system should be in good shape, back out of the CHange Root, gracefully and back into the liveDVD environment, like this:
```

exit
sudo umount /mnt/run 
sudo umount /mnt/dev/pts
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt/dev
sudo umount /mnt

```

Boot back to bios, and make sure that sdd is set as the 1st boot priority. Continue the boot process.

Tell me
[INDENT][INDENT]you now boot up ubuntu !
[/INDENT][/INDENT]

---

### Post by oldfred on 2014-10-30
If you do the full chroot, best to run a full set of updates & uninstall grub & reinstall grub completely. And make sure latest kernel is installed.

I would add these commands if chrooted:
       #Commands once in chroot, everything after the # is just notes, do not copy:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
      
 # uninstall both grub legacy & grub2 reinstall grub2 and to sda in this example, use your drive:
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda

    #dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
# fix Broken packages -f 
apt-get -f install
dpkg --configure -a

Some have been able to boot after the busybox:
[http://ubuntuforums.org/showthread.php?t=1531999&highlight=rootdelay](http://ubuntuforums.org/showthread.php?t=1531999&highlight=rootdelay)
> After the Busy Box error message comes up, wait 15 seconds, then type "exit" (without the quotes.) and hit enter.
You should boot into your Ubuntu OS.  If not, keep typing exit and hit enter until it does. 

---

### Post by Bashing-om on 2014-10-30
+1
@ oldfred; Thanks for having my back, Your knowledge and expertise is so appreciated .

2 heads are better than one, even when this one is a goat head

---

### Post by gubtan on 2014-11-03
Dear Bashing-om & oldfred,

The fail is here.

I wait about 20 sec and I tiped "exit" then Enter and the xubuntu started.

How can I jumpout the "exit" style?

](*,)](*,)](*,)](*,)

---

### Post by oldfred on 2014-11-03
I would still run the commands I posted to refresh system when in chroot, but you do not need the chroot.  Use sudo -i (close terminal as soon as done to cancel the sudo) or put sudo before every command.

If any error messages post those, but no need to post the normal updates as it may be a lot.

---

