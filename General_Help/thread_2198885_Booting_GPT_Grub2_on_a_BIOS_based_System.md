---
title: "Booting GPT Grub2 on a BIOS based System"
date: 2014-01-11
forum: General Help
---

### Post by sydney2 on 2014-01-11
I have an Intel D945GCCR Board with a 2GB Ram having discontinued support.Similarly I have an 500GB HDD with triple boot Windows XP, Windows 8 & Ubuntu 12.04. Well the other day I came across the advantages of a gpt disk & its awesome capabilities of setting it up on a BIOS based system, so i decided to go with it. Moreover since it would allow 128 partitions on a disk & that would put away the mbr' s drawbacks of 3 primary partitions or maximum 4 & rest of the space unallocated. 
Well I decided the setup on a USB stick for testing purpose since I had no spare HDD with me. The steps I followed were as follows:

   ```
 S1 # dd if=/dev/zero of=/dev/sdb bs=512 count=1
    S2 # parted /dev/sdb
    S3 # mktable gpt 
    S4 # mkpart non-fs 0 1007KB
    S4 # set 1 bios_grub on  (bios boot partition) 
    S5 # mkpartfs ext2 1024KB 500MB

```
Since some machines had fussy bioses of refusing to boot so I decided to set the protective mbr bootable using fdisk.

  ```
  S6 # fdisk /dev/sdb
    S7 # fdisk> a
    S7 # fdisk> w 
     
         writing changes to disk         (there was no warning) 
    
    S 7# mount /dev/sdb2 /mnt/xcv 

```
 
I then installed grub 2.00 to disk as follows:
 

   ```
 S8 # grub-install --target=i386pc --force --no-floppy --boot-directory=/mnt/xcv/boot /dev/sdb
```

This gave an error of no such option --target=i386-pc so I avoided the parameter.
The installation of grub2 then completed successfully.
But to my surprise when I rebooted the machine & selected the USB from my BIOS it just skipped it booting normally. Well since I could not figure out the problem at all I decided to ask for help.

The output of bootscriptinfo

```
                      Boot Info Script 0.61      [1 April 2012]
    
    
    ============================= Boot Info Summary: ===============================
    
     => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
        the same hard drive for core.img. core.img is at this location and looks 
        for (,msdos3)/boot/grub on this drive.
     => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 34 
        of the same hard drive for core.img. core.img is at this location and 
        looks for (,gpt2)/boot/grub on this drive.
    
    sda1: __________________________________________________________________________
    
        File system:       ntfs
        Boot sector type:  Windows Vista/7: NTFS
        Boot sector info:  No errors found in the Boot Parameter Block.
        Operating System:  Windows XP
        Boot files:        /boot.ini /bootmgr /Boot/BCD /ntldr /NTDETECT.COM
    
    sda2: __________________________________________________________________________
    
        File system:       ntfs
        Boot sector type:  Windows Vista/7: NTFS
        Boot sector info:  No errors found in the Boot Parameter Block.
        Operating System:  
        Boot files:        /bootmgr /Windows/System32/winload.exe
    
    sda3: __________________________________________________________________________
    
        File system:       ext4
        Boot sector type:  -
        Boot sector info: 
        Operating System:  Ubuntu 12.04.2 LTS
        Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img
    
    sda4: __________________________________________________________________________
    
        File system:       Extended Partition
        Boot sector type:  -
        Boot sector info: 
    
    sda5: __________________________________________________________________________
    
        File system:       swap
        Boot sector type:  -
        Boot sector info: 
    
    sdb1: __________________________________________________________________________
    
        File system:       BIOS Boot partition
        Boot sector type:  Grub2's core.img
        Boot sector info: 
    
    sdb2: __________________________________________________________________________
    
        File system:       ext2
        Boot sector type:  -
        Boot sector info: 
        Operating System:  
        Boot files:        /boot/grub/core.img
    
    ============================ Drive/Partition Info: =============================
    
    Drive: sda _____________________________________________________________________
    GNU Fdisk 1.2.4
    Copyright (C) 1998 - 2006 Free Software Foundation, Inc.
    This program is free software, covered by the GNU General Public License.
    
    This program is distributed in the hope that it will be useful,
    
    Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
    
    /dev/sda1    *             63   135,170,909   135,170,847   7 NTFS / exFAT / HPFS
    /dev/sda2         135,172,096   325,636,095   190,464,000   7 NTFS / exFAT / HPFS
    /dev/sda3         325,636,096   429,152,255   103,516,160  83 Linux
    /dev/sda4         429,154,302   433,057,791     3,903,490   5 Extended
    /dev/sda5         429,154,304   433,057,791     3,903,488  82 Linux swap / Solaris
    
    
    Drive: sdb _____________________________________________________________________
    GNU Fdisk 1.2.4
    Copyright (C) 1998 - 2006 Free Software Foundation, Inc.
    This program is free software, covered by the GNU General Public License.
    
    This program is distributed in the hope that it will be useful,
    
    Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
    
    /dev/sdb1                   1     3,948,543     3,948,543  ee GPT
    
    
    GUID Partition Table detected.
    
    Partition    Start Sector    End Sector  # of Sectors System
    /dev/sdb1              34         1,966         1,933 BIOS Boot partition
    /dev/sdb2           2,000       976,562       974,563 EFI System partition
    
    "blkid" output: ________________________________________________________________
    
    Device           UUID                                   TYPE       LABEL
    
    /dev/sda1        F6BCBA5DBCBA1857                       ntfs       
    /dev/sda2        828AB9A48AB994DF                       ntfs       
    /dev/sda3        e55facfa-1f7c-40ba-ba23-b8984d83b2e6   ext4       
    /dev/sda5        824dc774-d5f4-4c8f-b435-851878cf2b2b   swap       
    /dev/sdb2        67fa2c27-39ab-4fdf-a1b6-7c197717639a   ext2       
    /dev/sr0                                                udf        XXXXXX
    
    ================================ Mount points: =================================
    
    Device           Mount_Point              Type       Options
    
    /dev/sda3        /                        ext4       (rw,errors=remount-ro)
    /dev/sr0         /media/disk              udf        (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,umask=0077,dmode=0500,uhelper=udisks)
    
    
    ================================ sda1/boot.ini: ================================
    
    --------------------------------------------------------------------------------
    ;
    ;Warning: Boot.ini is used on Windows XP and earlier operating systems.
    ;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
    ;
    [boot loader]
    timeout=30
    default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
    [operating systems]
    multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /NOEXECUTE=OPTIN /FASTDETECT
    --------------------------------------------------------------------------------
    
    =========================== sda3/boot/grub/grub.cfg: ===========================
    
    --------------------------------------------------------------------------------
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
    set default="0"
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
      insmod vbe
      insmod vga
      insmod video_bochs
      insmod video_cirrus
    }
    
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos3)'
    search --no-floppy --fs-uuid --set=root e55facfa-1f7c-40ba-ba23-b8984d83b2e6
    if loadfont /usr/share/grub/unicode.pf2 ; then
      set gfxmode=auto
      load_video
      insmod gfxterm
      insmod part_msdos
      insmod ext2
      set root='(hd0,msdos3)'
      search --no-floppy --fs-uuid --set=root e55facfa-1f7c-40ba-ba23-b8984d83b2e6
      set locale_dir=($root)/boot/grub/locale
      set lang=en_IN
      insmod gettext
    fi
    terminal_output gfxterm
    if [ "${recordfail}" = 1 ] ; then
      set timeout=-1
    else
      if [ x$feature_timeout_style = xy ] ; then
        set timeout_style=hidden
        set timeout=0
      # Fallback hidden-timeout code in case the timeout_style feature is
      # unavailable.
      elif sleep --interruptible 0 ; then
        set timeout=0
      fi
    fi
    ### END /etc/grub.d/00_header ###
    
    ### BEGIN /etc/grub.d/05_debian_theme ###
    set menu_color_normal=white/black
    set menu_color_highlight=black/light-gray
    if background_color 44,0,30; then
      clear
    fi
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
    if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
    menuentry 'Ubuntu, with Linux 3.5.0-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos3)'
        search --no-floppy --fs-uuid --set=root e55facfa-1f7c-40ba-ba23-b8984d83b2e6
        linux    /boot/vmlinuz-3.5.0-23-generic root=UUID=e55facfa-1f7c-40ba-ba23-b8984d83b2e6 ro   quiet splash $vt_handoff
        initrd    /boot/initrd.img-3.5.0-23-generic
    }
    menuentry 'Ubuntu, with Linux 3.5.0-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
        recordfail
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos3)'
        search --no-floppy --fs-uuid --set=root e55facfa-1f7c-40ba-ba23-b8984d83b2e6
        echo    'Loading Linux 3.5.0-23-generic ...'
        linux    /boot/vmlinuz-3.5.0-23-generic root=UUID=e55facfa-1f7c-40ba-ba23-b8984d83b2e6 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.5.0-23-generic
    }
    ### END /etc/grub.d/10_linux ###
    
    ### BEGIN /etc/grub.d/20_linux_xen ###
    ### END /etc/grub.d/20_linux_xen ###
    
    ### BEGIN /etc/grub.d/20_memtest86+ ###
    menuentry "Memory test (memtest86+)" {
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos3)'
        search --no-floppy --fs-uuid --set=root e55facfa-1f7c-40ba-ba23-b8984d83b2e6
        linux16    /boot/memtest86+.bin
    }
    menuentry "Memory test (memtest86+, serial console 115200)" {
        insmod part_msdos
        insmod ext2
        set root='(hd0,msdos3)'
        search --no-floppy --fs-uuid --set=root e55facfa-1f7c-40ba-ba23-b8984d83b2e6
        linux16    /boot/memtest86+.bin console=ttyS0,115200n8
    }
    ### END /etc/grub.d/20_memtest86+ ###
    
    ### BEGIN /etc/grub.d/30_os-prober ###
    menuentry "Windows 8 (loader) (on /dev/sda1)" --class windows --class os {
        insmod part_msdos
        insmod ntfs
        set root='(hd0,msdos1)'
        search --no-floppy --fs-uuid --set=root F6BCBA5DBCBA1857
        drivemap -s (hd0) ${root}
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
    if [ -f  $prefix/custom.cfg ]; then
      source $prefix/custom.cfg;
    fi
    ### END /etc/grub.d/41_custom ###
    --------------------------------------------------------------------------------
    
    =============================== sda3/etc/fstab: ================================
    
    --------------------------------------------------------------------------------
    # /etc/fstab: static file system information.
    #
    # Use 'blkid' to print the universally unique identifier for a
    # device; this may be used with UUID= as a more robust way to name devices
    # that works even if disks are added and removed. See fstab(5).
    #
    # <file system> <mount point>   <type>  <options>       <dump>  <pass>
    proc            /proc           proc    nodev,noexec,nosuid 0       0
    # / was on /dev/sda3 during installation
    UUID=e55facfa-1f7c-40ba-ba23-b8984d83b2e6 /               ext4    errors=remount-ro 0       1
    # swap was on /dev/sda5 during installation
    UUID=824dc774-d5f4-4c8f-b435-851878cf2b2b none            swap    sw              0       0
    --------------------------------------------------------------------------------
    
    =================== sda3: Location of files loaded by Grub: ====================
    
               GiB - GB             File                                 Fragment(s)
    
     163.409683228 = 175.459811328  boot/grub/core.img                             1
     160.004222870 = 171.803226112  boot/grub/grub.cfg                             1
     156.344421387 = 167.873544192  boot/initrd.img-3.5.0-23-generic               1
     181.418338776 = 194.796457984  boot/vmlinuz-3.5.0-23-generic                  1
     156.344421387 = 167.873544192  initrd.img                                     1
     181.418338776 = 194.796457984  vmlinuz                                        1
    
    =================== sdb2: Location of files loaded by Grub: ====================
    
               GiB - GB             File                                 Fragment(s)
    
       0.313095093 = 0.336183296    boot/grub/core.img                             2
    
    =============================== StdErr Messages: ===============================
    
    xz: (stdin): Compressed data is corrupt
    xz: (stdin): Compressed data is corrupt  

```
 

So how do I go about it now. Are they any grievous mistakes?

Well any help would be greatly appreciated & honored....

Regards 

Sydney

---

### Post by sydney2 on 2014-01-11
No response. Could anyone help me please..........................

Sydney....

---

### Post by grahammechanical on 2014-01-11
Grub is indeed installed into the MBR of sdb (usb stick, I presume) but is there an operating system on that USB stick? I see two partitions on sdb - sdb1 = BIOS Boot partition and sdb2 = EFI system partition. Is the OS in sdb2?

The Grub configuration file has Ubuntu 12.04 in the 10_Linux section as being on msdos3 (sda3) and the Windows 8 (loader) in the 30_os-prober section but nothing for any operating system on sdb. It is Grub os-prober that finds other operating systems on the same disk and on other disks. 

Load into Ubuntu 12.04 and run

```
sudo update-grub
```

And then see if an option to load an OS on sdb (usb stick) is in the Grub menu. If not run

```
sudo grub-install /dev/sda
```

I have found that updating the Grub configuration file (update-grub) is enough sometimes. Other times it works if I install grub again (grub-install). You may also find that you have the same copy of the Grub configuration file in the MBR of sdb and that has not been updated. There will be no change if you boot on sdb from the BIOS. So, you might want to load into Ubuntu on sdb and run the commands again but this time make this change to the second command

```
sudo grub-install /dev/sdb
```

That way each disk will have its own Grub configuration file in its own MBR. I have two hard disks and I like each to have its own version of Grub in its own MBR then I can boot each disk from the BIOS or load into any OS on any disk from whatever Grub boot menu appears.

Regards.

---

### Post by sydney2 on 2014-01-11
Thanks for the reply. Well I tried the solutions u suggested but no effect. To make things completely focused on the USB I disabled the 500 HDD in the BIOS but no still no effect. 
I had earlier heard that ubuntu while installing to a gpt disk would prepare a BIOS BOOT PARTITION automatically but I dont kow if that would be successfull on my machine or atleast on other machines. So is it the problem with my Motherboard' s BIOS or can things be still rectified? 

Thanks

Sydney

---

### Post by oldfred on 2014-01-11
I have used gpt on two of my now 4 drives and on a couple of flash drives with BIOS. I started using gpt on my 160GB drive and XP on a MBR drive with 10.10.. XP will not read data nor work with gpt partitioned drives. Later versions of Windows will read data on gpt drives if booted on a different drive with BIOS/MBR, but Windows only boots from gpt drives with UEFI.

With BIOS booting you have to have a 1 or 2MB unformatted partition with the bios_grub flag for grub to install correctly.

       I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning. But I also install gdisk for review and other tasks on gpt drives.
sudo apt-get install gdisk
      
 You can set bios_grub flag in gparted (right click flags) & no format
In GPT fdisk (gdisk), give bios_grub a type code of EF02. 
Or with terminal - see man parted:
sudo parted /dev/sdb set <partition_number> boot on
      
 [http://www.rodsbooks.com/gdisk/walkthrough.html](http://www.rodsbooks.com/gdisk/walkthrough.html)
[http://www.rodsbooks.com/gdisk/advice.html](http://www.rodsbooks.com/gdisk/advice.html)

Old installs did not add bios_grub partition, but new installs seem to. I always partition in advance so have not tried it lately.

I assumed my flash drive may be used for UEFI boot later when I get a new system so I put a efi partition first, a bios_grub second and then a system partition. On my large flash drive I then have a data partition but not swap as I have enough RAM as I rarely use swap. Or I still have the swap on my hard drive on my laptop that I could mount as laptop has little RAM.

```
Disk /dev/sdb: 31.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name        Flags
 1      20.5kB  500MB   500MB   fat32        EFI System  boot
 2      500MB   501MB   1049kB                           bios_grub
 3      501MB   15.2GB  14.7GB  ext4         sys
 4      15.2GB  31.0GB  15.8GB  ext4         sys
```

The boot flag is only on efi partitions which really are only required if UEFI booting. All others should be data partitions.

---

### Post by sydney2 on 2014-01-13
Hey I got it solved. It worked just awesome & successfully booted to Ubuntu 12.04. I performed this using my 500GB HDD itself. My usb siick must have been incompatible & just stupid to make things successful. Well the GPT just required to mark the protective mbr active & it was done. By the way could someone share me knowledge on Ubuntu' s gdisk partition type codes? 

Thanks.......................

Sydney..

---

### Post by oldfred on 2014-01-13
This shows the official GUID, but they are very long numbers.
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

If using gdisk the l command shows types as shown here:
[http://www.rodsbooks.com/gdisk/walkthrough.html](http://www.rodsbooks.com/gdisk/walkthrough.html)

---

