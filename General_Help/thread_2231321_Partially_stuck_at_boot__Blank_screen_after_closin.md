---
title: "Partially stuck at boot : Blank screen after closing lid / suspending + other issues"
date: 2014-06-24
forum: General Help
---

### Post by AntonKjaerHansen on 2014-06-24
Good evening,

As I have recently recovered from a corrupted Win7-system om my HP Envy 15 1099eo, by installing GRUB2 and Ubuntu 13.10 on it, I have experienced multiple issues regarding booting the computer, which I'm partly able to bypass. I lack the technical expertise to establish a diagnosis. As the machine suffers from an array of issues, this post will be be split into sections surrounding each major issue indicated by a bold heading. It is my theory that the issues are an effect of the hardware, and I therefore thought debating these issues in the community first. might indicate wether or not a formal bug should be submitted.

1: Box and system
- lshw dump
- dmidecode dump

2. #1 - Issue :** Blank grub screen, Stuck at boot, smboot.**
- Boot-repair
- fwts non-interactive dump
- dmesg (error): vpd r/w failed.  This is likely a firmware bug on this device.
- possibly related bug-reference

3. #2 - Issue : [B]Black screen after closing lid and suspension.
 [/B]- fwts interactive dump

**Box and system**
HP Envy 15 1099eo ([http://h10025.www1.hp.com/ewfrf/wc/product?product=4119989&lc=en&cc=us&dlc=en](http://h10025.www1.hp.com/ewfrf/wc/product?product=4119989&lc=en&cc=us&dlc=en)). 

```

kush@NIXONKUSH:~$ sudo lshw -short
H/W path        Device     Class       Description
==================================================
                           system      HP Envy 15 Notebook PC (VJ288EA#UUW)
/0                         bus         7009
/0/0                       memory      1MiB BIOS
/0/13                      memory      8GiB System Memory
/0/13/0                    memory      4GiB SODIMM DDR3 Synchronous 1333 MHz (0,8 ns)
/0/13/1                    memory      4GiB SODIMM DDR3 Synchronous 1333 MHz (0,8 ns)
/0/13/2                    memory      SODIMM DDR3 Synchronous 1333 MHz (0,8 ns) [empty]
/0/1a                      processor   Intel(R) Core(TM) i7 CPU       Q 740  @ 1.73GHz
/0/1a/1b                   memory      6MiB L3 cache
/0/1a/1d                   memory      256KiB L2 cache
/0/1a/1e                   memory      32KiB L1 cache
/0/1c                      memory      32KiB L1 cache
/0/100                     bridge      Core Processor DMI
/0/100/3                   bridge      Core Processor PCI Express Root Port 1
/0/100/3/0                 display     RV740/M97 [Mobility Radeon HD 4830]
/0/100/3/0.1               multimedia  RV710/730 HDMI Audio [Radeon HD 4000 series]
/0/100/8                   generic     Core Processor System Management Registers
/0/100/8.1                 generic     Core Processor Semaphore and Scratchpad Registers
/0/100/8.2                 generic     Core Processor System Control and Status Registers
/0/100/8.3                 generic     Core Processor Miscellaneous Registers
/0/100/10                  generic     Core Processor QPI Link
/0/100/10.1                generic     Core Processor QPI Routing and Protocol Registers
/0/100/1b                  multimedia  5 Series/3400 Series Chipset High Definition Audio
/0/100/1c                  bridge      5 Series/3400 Series Chipset PCI Express Root Port 1
/0/100/1c/0     wlan0      network     PRO/Wireless 5100 AGN [Shiloh] Network Connection
/0/100/1c.1                bridge      5 Series/3400 Series Chipset PCI Express Root Port 2
/0/100/1c.1/0   eth0       network     AR8131 Gigabit Ethernet
/0/100/1d                  bus         5 Series/3400 Series Chipset USB2 Enhanced Host Controller
/0/100/1e                  bridge      82801 Mobile PCI Bridge
/0/100/1f                  bridge      Mobile 5 Series Chipset LPC Interface Controller
/0/100/1f.2                storage     82801 Mobile SATA Controller [RAID mode]
/0/100/1f.3                bus         5 Series/3400 Series Chipset SMBus Controller
/0/100/1f.6                generic     5 Series/3400 Series Chipset Thermal Subsystem
/0/101                     bridge      Core Processor QuickPath Architecture Generic Non-Core Registers
/0/102                     bridge      Core Processor QuickPath Architecture System Address Decoder
/0/103                     bridge      Core Processor QPI Link 0
/0/104                     bridge      Core Processor QPI Physical 0
/0/105                     bridge      Core Processor Integrated Memory Controller
/0/106                     bridge      Core Processor Integrated Memory Controller Target Address Decoder
/0/107                     bridge      Core Processor Integrated Memory Controller Test Registers
/0/108                     bridge      Core Processor Integrated Memory Controller Channel 0 Control Registers
/0/109                     bridge      Core Processor Integrated Memory Controller Channel 0 Address Registers
/0/10a                     bridge      Core Processor Integrated Memory Controller Channel 0 Rank Registers
/0/10b                     bridge      Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers
/0/10c                     bridge      Core Processor Integrated Memory Controller Channel 1 Control Registers
/0/10d                     bridge      Core Processor Integrated Memory Controller Channel 1 Address Registers
/0/10e                     bridge      Core Processor Integrated Memory Controller Channel 1 Rank Registers
/0/10f                     bridge      Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers
/0/1            scsi0      storage     
/0/1/0.0.0      /dev/sda   disk        320GB ST9320423AS
/0/1/0.0.0/1    /dev/sda1  volume      282GiB EXT4 volume
/0/1/0.0.0/2    /dev/sda2  volume      15GiB Extended partition
/0/1/0.0.0/2/5  /dev/sda5  volume      15GiB Linux swap / Solaris partition


```

```

BIOS Information
    Vendor: Hewlett-Packard
    Version: F.2C
    Release Date: 18/02/2011
    ROM Size: 1536 kB
    Characteristics:
        PCI is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        EDD is supported
        Japanese floppy for NEC 9800 1.2 MB is supported (int 13h)
        Japanese floppy for Toshiba 1.2 MB is supported (int 13h)
        5.25"/360 kB floppy services are supported (int 13h)
        5.25"/1.2 MB floppy services are supported (int 13h)
        3.5"/720 kB floppy services are supported (int 13h)
        3.5"/2.88 MB floppy services are supported (int 13h)
        8042 keyboard services are supported (int 9h)
        CGA/mono video services are supported (int 10h)
        ACPI is supported
        USB legacy is supported
        BIOS boot specification is supported
        Targeted content distribution is supported
    BIOS Revision: 15.44
    Firmware Revision: 54.53

System Information
    Manufacturer: Hewlett-Packard
    Product Name: HP Envy 15 Notebook PC
    Version: 0394100000241910001420000
    Serial Number: CNF94390SS
    UUID: 39464E43-3334-3039-5353-C80AA97A2C78
    Wake-up Type: Power Switch
    SKU Number: VJ288EA#UUW
    Family: 103C_5335KV

Base Board Information
    Manufacturer: Quanta
    Product Name: 7009
    Version: 36.35
    Serial Number: CNF94390SS
    Asset Tag: Base Board Asset Tag
    Features:
        Board is a hosting board
        Board is replaceable
    Location In Chassis: Base Board Chassis Location
    Type: Motherboard

Chassis Information
    Manufacturer: Quanta
    Type: Notebook
    Lock: Not Present
    Version: N/A
    Serial Number: None
    Asset Tag: Not Specified
    Boot-up State: Safe
    Power Supply State: Safe
    Thermal State: Safe
    Security Status: None
    OEM Information: 0x00000119
    Height: Unspecified
    Number Of Power Cords: 1
    Contained Elements: 0
    SKU Number: Not Specified

System Slot Information
    Designation: J5C1
    Type: x16 PCI Express x16
    Current Usage: Available
    Length: Other
    ID: 0
    Characteristics:
        PME signal is supported
        Hot-plug devices are supported
    Bus Address: 0000:00:1f.7

System Slot Information
    Designation: J6C1
    Type: x1 PCI Express x1
    Current Usage: Available
    Length: Other
    ID: 0
    Characteristics:
        PME signal is supported
        Hot-plug devices are supported
    Bus Address: 0000:00:1f.7

System Slot Information
    Designation: J6C2
    Type: x1 PCI Express x1
    Current Usage: Available
    Length: Other
    ID: 1
    Characteristics:
        PME signal is supported
        Hot-plug devices are supported
    Bus Address: 0000:00:1f.7

System Slot Information
    Designation: J6D2
    Type: x1 PCI Express x1
    Current Usage: Available
    Length: Other
    ID: 2
    Characteristics:
        PME signal is supported
        Hot-plug devices are supported
    Bus Address: 0000:00:1f.7

System Slot Information
    Designation: J7C1
    Type: x1 PCI Express x1
    Current Usage: Available
    Length: Other
    ID: 3
    Characteristics:
        PME signal is supported
        Hot-plug devices are supported
    Bus Address: 0000:00:1f.7

System Slot Information
    Designation: J7D2
    Type: x1 PCI Express x1
    Current Usage: Available
    Length: Other
    ID: 4
    Characteristics:
        PME signal is supported
        Hot-plug devices are supported
    Bus Address: 0000:00:1f.7

System Slot Information
    Designation: J8C2
    Type: x16 PCI Express x16
    Current Usage: Available
    Length: Other
    ID: 1
    Characteristics:
        PME signal is supported
        Hot-plug devices are supported
    Bus Address: 0000:00:1f.7

System Slot Information
    Designation: J8C1
    Type: x1 PCI Express x1
    Current Usage: Available
    Length: Other
    ID: 5
    Characteristics:
        PME signal is supported
        Hot-plug devices are supported
    Bus Address: 0000:00:1f.7

On Board Device Information
    Type: Video
    Status: Enabled
    Description: Video Graphics Controller

On Board Device Information
    Type: Ethernet
    Status: Enabled
    Description: Realtek Lan Controller

OEM Strings
    String 1: $HP$
    String 2: LOC#UUW
    String 3: ABS 70/71 79 7A 7B 7C
    String 4: CNB1 0394100000241910001420000

System Configuration Options
    Option 1: String1 for Type12 Equipment Manufacturer
    Option 2: String2 for Type12 Equipment Manufacturer
    Option 3: String3 for Type12 Equipment Manufacturer
    Option 4: String4 for Type12 Equipment Manufacturer

System Event Log
    Area Length: 0 bytes
    Header Start Offset: 0x0000
    Data Start Offset: 0x0000
    Access Method: General-purpose non-volatile data functions
    Access Address: 0x0000
    Status: Valid, Not Full
    Change Token: 0x12345678
    Header Format: OEM-specific
    Supported Log Type Descriptors: 3
    Descriptor 1: POST memory resize
    Data Format 1: None
    Descriptor 2: POST error
    Data Format 2: POST results bitmap
    Descriptor 3: Log area reset/cleared
    Data Format 3: None

Built-in Pointing Device
    Type: Touch Pad
    Interface: PS/2
    Buttons: 4

System Boot Information
    Status: No errors detected

Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 16 GB
    Number Of Devices: 4

Memory Device
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 4096 MB
    Form Factor: SODIMM
    Set: None
    Locator: Bottom
    Bank Locator: BANK 0
    Type: DDR3
    Type Detail: Synchronous
    Speed: 1333 MHz
    Manufacturer: Hynix
    Serial Number: 4370BD05
    Asset Tag: Unknown
    Part Number: HMT351S6BFR8C-H9  
    Rank: Unknown

Memory Device Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x000FFFFFFFF
    Range Size: 4 GB
    Partition Row Position: 2
    Interleave Position: 1
    Interleaved Data Depth: 1

Memory Device
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 4096 MB
    Form Factor: SODIMM
    Set: None
    Locator: Bottom
    Bank Locator: BANK 1
    Type: DDR3
    Type Detail: Synchronous
    Speed: 1333 MHz
    Manufacturer: Hynix
    Serial Number: 4330BCC6
    Asset Tag: Unknown
    Part Number: HMT351S6BFR8C-H9  
    Rank: Unknown

Memory Device Mapped Address
    Starting Address: 0x00100000000
    Ending Address: 0x001FFFFFFFF
    Range Size: 4 GB
    Partition Row Position: 2
    Interleave Position: 1
    Interleaved Data Depth: 1

Memory Device
    Total Width: 64 bits
    Data Width: 64 bits
    Size: No Module Installed
    Form Factor: SODIMM
    Set: None
    Locator: On Board
    Bank Locator: BANK 3
    Type: DDR3
    Type Detail: Synchronous
    Speed: 1333 MHz
    Manufacturer: Hynix
    Serial Number: 4350BCC7
    Asset Tag: Unknown
    Part Number: HMT351S6BFR8C-H9  
    Rank: Unknown

Memory Array Mapped Address
    Starting Address: 0x00000000000
    Ending Address: 0x001FFFFFFFF
    Range Size: 8 GB
    Partition Width: 4

Processor Information
    Socket Designation: CPU
    Type: Central Processor
    Family: Core 2 Duo
    Manufacturer: Intel(R) Corporation
    ID: E5 06 01 00 FF FB EB BF
    Signature: Type 0, Family 6, Model 30, Stepping 5
    Flags:
        FPU (Floating-point unit on-chip)
        VME (Virtual mode extension)
        DE (Debugging extension)
        PSE (Page size extension)
        TSC (Time stamp counter)
        MSR (Model specific registers)
        PAE (Physical address extension)
        MCE (Machine check exception)
        CX8 (CMPXCHG8 instruction supported)
        APIC (On-chip APIC hardware supported)
        SEP (Fast system call)
        MTRR (Memory type range registers)
        PGE (Page global enable)
        MCA (Machine check architecture)
        CMOV (Conditional move instruction supported)
        PAT (Page attribute table)
        PSE-36 (36-bit page size extension)
        CLFSH (CLFLUSH instruction supported)
        DS (Debug store)
        ACPI (ACPI supported)
        MMX (MMX technology supported)
        FXSR (FXSAVE and FXSTOR instructions supported)
        SSE (Streaming SIMD extensions)
        SSE2 (Streaming SIMD extensions 2)
        SS (Self-snoop)
        HTT (Multi-threading)
        TM (Thermal monitor supported)
        PBE (Pending break enabled)
    Version: Intel(R) Core(TM) i7 CPU       Q 740  @ 1.73GHz
    Voltage: 1.2 V
    External Clock: 1066 MHz
    Max Speed: 1733 MHz
    Current Speed: 1733 MHz
    Status: Populated, Enabled
    Upgrade: ZIF Socket
    Serial Number: Not Specified
    Asset Tag: FFFF
    Part Number: Not Specified
    Core Count: 4
    Core Enabled: 4
    Thread Count: 8
    Characteristics:
        64-bit capable

Cache Information
    Socket Designation: L3 Cache
    Configuration: Enabled, Not Socketed, Level 3
    Operational Mode: Write Through
    Location: Internal
    Installed Size: 6144 kB
    Maximum Size: 6144 kB
    Supported SRAM Types:
        Synchronous
    Installed SRAM Type: Synchronous
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Unified
    Associativity: Other

Cache Information
    Socket Designation: L1 Cache
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Write Through
    Location: Internal
    Installed Size: 32 kB
    Maximum Size: 32 kB
    Supported SRAM Types:
        Synchronous
    Installed SRAM Type: Synchronous
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Data
    Associativity: 8-way Set-associative

Cache Information
    Socket Designation: L2 Cache
    Configuration: Enabled, Not Socketed, Level 2
    Operational Mode: Write Through
    Location: Internal
    Installed Size: 256 kB
    Maximum Size: 256 kB
    Supported SRAM Types:
        Synchronous
    Installed SRAM Type: Synchronous
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Unified
    Associativity: 8-way Set-associative

Cache Information
    Socket Designation: L1 Cache
    Configuration: Enabled, Not Socketed, Level 1
    Operational Mode: Write Through
    Location: Internal
    Installed Size: 32 kB
    Maximum Size: 32 kB
    Supported SRAM Types:
        Synchronous
    Installed SRAM Type: Synchronous
    Speed: Unknown
    Error Correction Type: Single-bit ECC
    System Type: Instruction
    Associativity: 4-way Set-associative



```



**#1 - Blank grub screen, Stuck at boot, smboot.**

When booting from scratch, immediately after HP BIOS screen I'm presented with a dark-orange blank grub screen, and I'm forced to reboot. 2nd boot shows the regular grub screen with the "Ubuntu", "Advanced options for Ubuntu" and Mem Tests. When choosing "Ubuntu" the system stucks, and I'm forced to reboot. 3rd boot I choose the "Advanced options for Ubuntu" in the grub menu. I usually go with the "3.11.0-24-generic". Sometimes the system successfully boots into Ubuntu the first time (though usually its first in the 4th to 5th boot) and I'm met with a ton of prompts to send error reports.

After running Boot-Repair ([http://paste.ubuntu.com/7696837/plain/](http://paste.ubuntu.com/7696837/plain/))

```

 Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 23Dec2013]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    in partition 94 for .

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 13.10 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   591,605,759   591,603,712  83 Linux
/dev/sda2         591,607,806   625,141,759    33,533,954   5 Extended
/dev/sda5         591,607,808   625,141,759    33,533,952  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        52423430-ed6f-46b2-b259-60ddc64c17d0   ext4       
/dev/sda5        da42303a-14a3-41c1-b402-da2dd6717e7c   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro)


=========================== sda1/boot/grub/grub.cfg: ===========================

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
set root='hd0,msdos1'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  52423430-ed6f-46b2-b259-60ddc64c17d0
else
  search --no-floppy --fs-uuid --set=root 52423430-ed6f-46b2-b259-60ddc64c17d0
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=da_DK
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=10
else
  set timeout=10
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
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-52423430-ed6f-46b2-b259-60ddc64c17d0' {
recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  52423430-ed6f-46b2-b259-60ddc64c17d0
    else
      search --no-floppy --fs-uuid --set=root 52423430-ed6f-46b2-b259-60ddc64c17d0
    fi
    linux    /boot/vmlinuz-3.11.0-24-generic root=UUID=52423430-ed6f-46b2-b259-60ddc64c17d0 ro   
    initrd    /boot/initrd.img-3.11.0-24-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-52423430-ed6f-46b2-b259-60ddc64c17d0' {
    menuentry 'Ubuntu, with Linux 3.11.0-24-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-24-generic-advanced-52423430-ed6f-46b2-b259-60ddc64c17d0' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  52423430-ed6f-46b2-b259-60ddc64c17d0
        else
          search --no-floppy --fs-uuid --set=root 52423430-ed6f-46b2-b259-60ddc64c17d0
        fi
        echo    'Loading Linux 3.11.0-24-generic ...'
        linux    /boot/vmlinuz-3.11.0-24-generic root=UUID=52423430-ed6f-46b2-b259-60ddc64c17d0 ro   
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.11.0-24-generic
    }
    menuentry 'Ubuntu, with Linux 3.11.0-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-24-generic-recovery-52423430-ed6f-46b2-b259-60ddc64c17d0' {
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  52423430-ed6f-46b2-b259-60ddc64c17d0
        else
          search --no-floppy --fs-uuid --set=root 52423430-ed6f-46b2-b259-60ddc64c17d0
        fi
        echo    'Loading Linux 3.11.0-24-generic ...'
        linux    /boot/vmlinuz-3.11.0-24-generic root=UUID=52423430-ed6f-46b2-b259-60ddc64c17d0 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.11.0-24-generic
    }
    menuentry 'Ubuntu, with Linux 3.11.0-19-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-19-generic-advanced-52423430-ed6f-46b2-b259-60ddc64c17d0' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  52423430-ed6f-46b2-b259-60ddc64c17d0
        else
          search --no-floppy --fs-uuid --set=root 52423430-ed6f-46b2-b259-60ddc64c17d0
        fi
        echo    'Loading Linux 3.11.0-19-generic ...'
        linux    /boot/vmlinuz-3.11.0-19-generic root=UUID=52423430-ed6f-46b2-b259-60ddc64c17d0 ro   
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.11.0-19-generic
    }
    menuentry 'Ubuntu, with Linux 3.11.0-19-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-19-generic-recovery-52423430-ed6f-46b2-b259-60ddc64c17d0' {
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  52423430-ed6f-46b2-b259-60ddc64c17d0
        else
          search --no-floppy --fs-uuid --set=root 52423430-ed6f-46b2-b259-60ddc64c17d0
        fi
        echo    'Loading Linux 3.11.0-19-generic ...'
        linux    /boot/vmlinuz-3.11.0-19-generic root=UUID=52423430-ed6f-46b2-b259-60ddc64c17d0 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.11.0-19-generic
    }
    menuentry 'Ubuntu, with Linux 3.11.0-18-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-18-generic-advanced-52423430-ed6f-46b2-b259-60ddc64c17d0' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  52423430-ed6f-46b2-b259-60ddc64c17d0
        else
          search --no-floppy --fs-uuid --set=root 52423430-ed6f-46b2-b259-60ddc64c17d0
        fi
        echo    'Loading Linux 3.11.0-18-generic ...'
        linux    /boot/vmlinuz-3.11.0-18-generic root=UUID=52423430-ed6f-46b2-b259-60ddc64c17d0 ro   
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.11.0-18-generic
    }
    menuentry 'Ubuntu, with Linux 3.11.0-18-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-18-generic-recovery-52423430-ed6f-46b2-b259-60ddc64c17d0' {
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  52423430-ed6f-46b2-b259-60ddc64c17d0
        else
          search --no-floppy --fs-uuid --set=root 52423430-ed6f-46b2-b259-60ddc64c17d0
        fi
        echo    'Loading Linux 3.11.0-18-generic ...'
        linux    /boot/vmlinuz-3.11.0-18-generic root=UUID=52423430-ed6f-46b2-b259-60ddc64c17d0 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.11.0-18-generic
    }
    menuentry 'Ubuntu, with Linux 3.11.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-12-generic-advanced-52423430-ed6f-46b2-b259-60ddc64c17d0' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  52423430-ed6f-46b2-b259-60ddc64c17d0
        else
          search --no-floppy --fs-uuid --set=root 52423430-ed6f-46b2-b259-60ddc64c17d0
        fi
        echo    'Loading Linux 3.11.0-12-generic ...'
        linux    /boot/vmlinuz-3.11.0-12-generic root=UUID=52423430-ed6f-46b2-b259-60ddc64c17d0 ro   
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.11.0-12-generic
    }
    menuentry 'Ubuntu, with Linux 3.11.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.11.0-12-generic-recovery-52423430-ed6f-46b2-b259-60ddc64c17d0' {
    recordfail
        load_video
        insmod gzio
        insmod part_msdos
        insmod ext2
        set root='hd0,msdos1'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  52423430-ed6f-46b2-b259-60ddc64c17d0
        else
          search --no-floppy --fs-uuid --set=root 52423430-ed6f-46b2-b259-60ddc64c17d0
        fi
        echo    'Loading Linux 3.11.0-12-generic ...'
        linux    /boot/vmlinuz-3.11.0-12-generic root=UUID=52423430-ed6f-46b2-b259-60ddc64c17d0 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /boot/initrd.img-3.11.0-12-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry 'Memory test (memtest86+)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  52423430-ed6f-46b2-b259-60ddc64c17d0
    else
      search --no-floppy --fs-uuid --set=root 52423430-ed6f-46b2-b259-60ddc64c17d0
    fi
    linux16    /boot/memtest86+.bin
}
menuentry 'Memory test (memtest86+, serial console 115200)' {
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  52423430-ed6f-46b2-b259-60ddc64c17d0
    else
      search --no-floppy --fs-uuid --set=root 52423430-ed6f-46b2-b259-60ddc64c17d0
    fi
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
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
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=52423430-ed6f-46b2-b259-60ddc64c17d0 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=da42303a-14a3-41c1-b402-da2dd6717e7c none            swap    sw              0       0
tmpfs /dev/shm tmpfs defaults 0 0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  4d ef 19 41 8b 9a 85 6e  20 2d 80 40 d2 8f 16 f7  |M..A...n -.@....|
00000010  be 1c 46 11 6f 2c 06 1c  c2 a8 7b 79 b8 c1 54 47  |..F.o,....{y..TG|
00000020  34 9d c9 cc e6 a6 5e 07  fe 8f 2f d4 55 d4 c5 8e  |4.....^.../.U...|
00000030  57 ed 3e 65 08 72 43 00  ce d1 5f 6e 2e 6e 97 19  |W.>e.rC..._n.n..|
00000040  92 00 4f 6a ea e7 03 de  0c 34 a5 05 b0 ad f9 91  |..Oj.....4......|
00000050  c4 73 55 d3 d8 2c 79 61  d8 ce af 1a fd a6 fa 36  |.sU..,ya.......6|
00000060  01 6f 16 8f ef 74 7c 4e  8b d0 aa 92 ea b6 3f b3  |.o...t|N......?.|
00000070  e1 eb 64 be 5d 69 de e6  96 bc 0c 21 21 34 69 be  |..d.]i.....!!4i.|
00000080  4c 35 77 36 01 8c a6 de  b1 86 e9 eb e8 0c 11 df  |L5w6............|
00000090  0e bf b8 a3 94 14 a0 43  a2 10 0c 43 25 4b 61 c2  |.......C...C%Ka.|
000000a0  b6 0c 50 f8 f6 f1 89 0c  2a 82 21 0d 49 c7 27 ea  |..P.....*.!.I.'.|
000000b0  aa a0 90 bb 6f 24 70 f6  ec cd 9d 85 1a 30 77 1c  |....o$p......0w.|
000000c0  45 27 e8 4d fd 7f 61 88  f7 b0 2e 02 69 f3 fa 2b  |E'.M..a.....i..+|
000000d0  4b bf c7 3e 89 cb d5 f1  dd 13 a3 f2 36 e2 ce 31  |K..>........6..1|
000000e0  e2 d7 b4 fa 47 1a 5d c8  5f e5 65 3c 6b 04 66 ce  |....G.]._.e<k.f.|
000000f0  08 f6 e3 29 d5 dd 4b c2  0d 88 19 27 74 1d 5c 93  |...)..K....'t.\.|
00000100  9c 78 3e 59 21 6f e9 43  e6 a7 2d 4f a0 14 c5 e8  |.x>Y!o.C..-O....|
00000110  a8 d2 bb 8a e0 18 98 bb  68 f8 e8 86 23 2f 60 75  |........h...#/`u|
00000120  49 c8 a5 0f b1 dc 8d d7  b5 96 2f c8 57 36 e5 da  |I........./.W6..|
00000130  11 87 51 54 61 4a 8e 5a  7c cc c6 7f 49 75 18 7f  |..QTaJ.Z|...Iu..|
00000140  84 33 4f 97 dc 83 85 0e  10 97 11 f5 c6 84 42 1b  |.3O...........B.|
00000150  95 76 ed 43 2f 42 61 14  4f e0 8a 86 ab 87 84 28  |.v.C/Ba.O......(|
00000160  f9 26 24 a6 b8 bd 08 ef  57 03 71 f8 fa 7a 83 93  |.&$.....W.q..z..|
00000170  b9 5d 9c d6 90 a4 6e 16  f4 1c aa d1 5f bf 5d cd  |.]....n....._.].|
00000180  af e1 93 01 88 e3 33 df  d3 d5 59 45 3e 41 4e b8  |......3...YE>AN.|
00000190  79 49 7f ff ae 9e f9 5a  90 16 51 6c 72 03 45 b6  |yI.....Z..Qlr.E.|
000001a0  17 15 31 b0 27 78 37 aa  a9 1d b2 f6 1e a9 f0 4c  |..1.'x7........L|
000001b0  ea 7a c3 6f ff cb 02 ce  91 4e 36 86 0a 5b 00 fe  |.z.o.....N6..[..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 b0 ff 01 00 00  |................|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

cat: /tmp/BootInfo-8qzWxIWf/Tmp_Log: No such file or directory

ADDITIONAL INFORMATION :
=================== log of boot-repair 2014-06-24__22h04 ===================
boot-repair version : 3.199~ppa40~saucy
boot-sav version : 3.199~ppa40~saucy
glade2script version : 3.2.2~ppa47~saucy
boot-sav-extra version : 3.199~ppa40~saucy
boot-repair is executed in installed-session (Ubuntu 13.10, saucy, Ubuntu, x86_64)
CPU op-mode(s):        32-bit, 64-bit
BOOT_IMAGE=/boot/vmlinuz-3.11.0-24-generic root=UUID=52423430-ed6f-46b2-b259-60ddc64c17d0 ro

=================== os-prober:
/dev/sda1:Systemet er nu i brug - Ubuntu 13.10 CurrentSession:linux

=================== blkid:
/dev/sda1: UUID="52423430-ed6f-46b2-b259-60ddc64c17d0" TYPE="ext4"
/dev/sda5: UUID="da42303a-14a3-41c1-b402-da2dd6717e7c" TYPE="swap"


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

Advarsel: Udvidet partition starter ikke pÃ¥ en cylindergrÃ¦nse.
DOS og Linux vil opfatte indholdet forskelligt.

=================== /etc/grub.d/ :
drwxr-xr-x  2 root root     4096 mar 10 22:24 grub.d
totalt 72
-rwxr-xr-x 1 root root  7850 okt 10  2013 00_header
-rwxr-xr-x 1 root root  5949 aug 15  2013 05_debian_theme
-rwxr-xr-x 1 root root 11479 okt 10  2013 10_linux
-rwxr-xr-x 1 root root 10258 okt 10  2013 20_linux_xen
-rwxr-xr-x 1 root root  1798 jun 17  2013 20_memtest86+
-rwxr-xr-x 1 root root 11531 okt 10  2013 30_os-prober
-rwxr-xr-x 1 root root  1426 okt 10  2013 30_uefi-firmware
-rwxr-xr-x 1 root root   214 okt 10  2013 40_custom
-rwxr-xr-x 1 root root   216 okt 10  2013 41_custom
-rw-r--r-- 1 root root   483 okt 10  2013 README




=================== /etc/default/grub :

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"



=================== UEFI/Legacy mode:
This installed-session is not in EFI-mode.
SecureBoot disabled.


=================== PARTITIONS & DISKS:
sda1    : sda,    not-sepboot,    grubenv-ok    grub2,    grub-pc ,    update-grub,    64,    with-boot,    is-os,    not--efi--part,    fstab-without-boot,    fstab-without-efi,    no-nt,    no-winload,    no-recov-nor-hid,    no-bmgr,    notwinboot,    apt-get,    grub-install,    with--usr,    fstab-without-usr,    not-sep-usr,    standard,    farbios,    .

sda    : not-GPT,    BIOSboot-not-needed,    has-no-EFIpart,     not-usb,    has-os,    2048 sectors * 512 bytes


=================== parted -l:

Model: ATA ST9320423AS (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
1      1049kB  303GB  303GB   primary   ext4            boot
2      303GB   320GB  17.2GB  extended
5      303GB   320GB  17.2GB  logical   linux-swap(v1)

=================== parted -lm:

BYT;
/dev/sda:320GB:scsi:512:512:msdos:ATA ST9320423AS;
1:1049kB:303GB:303GB:ext4::boot;
2:303GB:320GB:17.2GB:::;
5:303GB:320GB:17.2GB:linux-swap(v1)::;


=================== mount:
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
tmpfs on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
cgroup on /sys/fs/cgroup/cpuset type cgroup (rw,relatime,cpuset)
cgroup on /sys/fs/cgroup/cpu type cgroup (rw,relatime,cpu)
cgroup on /sys/fs/cgroup/cpuacct type cgroup (rw,relatime,cpuacct)
cgroup on /sys/fs/cgroup/memory type cgroup (rw,relatime,memory)
cgroup on /sys/fs/cgroup/devices type cgroup (rw,relatime,devices)
cgroup on /sys/fs/cgroup/freezer type cgroup (rw,relatime,freezer)
cgroup on /sys/fs/cgroup/blkio type cgroup (rw,relatime,blkio)
cgroup on /sys/fs/cgroup/perf_event type cgroup (rw,relatime,perf_event)
cgroup on /sys/fs/cgroup/hugetlb type cgroup (rw,relatime,hugetlb)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=kush)


=================== ls:
/sys/block/sda (filtered):  alignment_offset bdi capability dev device discard_alignment events events_async events_poll_msecs ext_range holders inflight power queue range removable ro sda1 sda2 sda5 size slaves stat subsystem trace uevent
/dev (filtered):  autofs block bsg btrfs-control bus char console core cpu cpu_dma_latency disk dri ecryptfs fb0 fd freefall full fuse hidraw0 hpet input kmsg kvm log mapper mcelog mem net network_latency network_throughput null port ppp psaux ptmx pts random rfkill rtc rtc0 sda sda1 sda2 sda5 sg0 shm snapshot snd stderr stdin stdout uhid uinput urandom v4l vboxdrv vboxnetctl vboxusb vga_arbiter vhost-net video0 zero
ls /dev/mapper:  control

=================== df -Th:

Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sda1      ext4      278G   74G  190G  28% /
none           tmpfs     4.0K     0  4.0K   0% /sys/fs/cgroup
udev           devtmpfs  3.9G   12K  3.9G   1% /dev
tmpfs          tmpfs     798M  1.2M  797M   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
tmpfs          tmpfs     3.9G   80K  3.9G   1% /run/shm
none           tmpfs     100M   52K  100M   1% /run/user

=================== fdisk -l:

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004edbd

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   591605759   295801856   83  Linux
/dev/sda2       591607806   625141759    16766977    5  Extended
/dev/sda5       591607808   625141759    16766976   82  Linux swap / Solaris



=================== Recommended repair
Recommended-Repair
This setting will reinstall the grub2 of sda1 into the MBR of sda.
Additional repair will be performed: unhide-bootmenu-10s


Unhide GRUB boot menu in sda1/etc/default/grub

*******lspci -nnk | grep -iA3 vga
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] RV740/M97 [Mobility Radeon HD 4830] [1002:94a0]
Subsystem: Hewlett-Packard Company Device [103c:7009]
Kernel driver in use: radeon
01:00.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] RV710/730 HDMI Audio [Radeon HD 4000 series] [1002:aa38]
*******

grub-install (GRUB) 2.00-19ubuntu2.1,grub-install (GRUB) 2.

Reinstall the GRUB of sda1 into the MBR of sda
Installation finished. No error reported.
grub-install /dev/sda: exit code of grub-install /dev/sda:0

update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.11.0-24-generic
Found initrd image: /boot/initrd.img-3.11.0-24-generic
Found linux image: /boot/vmlinuz-3.11.0-19-generic
Found initrd image: /boot/initrd.img-3.11.0-19-generic
Found linux image: /boot/vmlinuz-3.11.0-18-generic
Found initrd image: /boot/initrd.img-3.11.0-18-generic
Found linux image: /boot/vmlinuz-3.11.0-12-generic
Found initrd image: /boot/initrd.img-3.11.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
Unhide GRUB boot menu in sda1/boot/grub/grub.cfg

```

3.11.0-12-generic, 3.11.0-18-generic, 3.11.0-19-generic and 3.11.0-24-generic.
Further more i did a non-interactive fwst-test inside Ubuntu to see if any major kernel-issues were found. 
This is the result.log:

```

Results generated by fwts: Version V13.09.01 (2013-09-17 07:41:02).

Some of this work - Copyright (c) 1999 - 2010, Intel Corp. All rights reserved.
Some of this work - Copyright (c) 2010 - 2013, Canonical.

This test run on 25/06/14 at 00:38:41 on host Linux NIXONKUSH 3.11.0-24-generic
#41-Ubuntu SMP Mon Jun 9 20:36:00 UTC 2014 x86_64.

Command: "fwts -b".
Running tests: version bios_info oops klog mtrr acpiinfo securebootcert csm
maxreadreq crs aspm hpet_check dmicheck microcode msr nx cpufreq maxfreq virt
pnp pciirq os2gap mpcheck hda_audio ebda bios32 apicedge wmi wakealarm
syntaxcheck pcc osilinux method mcfg fan fadt dmar cstates checksum apicinstance
acpitables.

version: Gather kernel system information.
--------------------------------------------------------------------------------
Test 1 of 4: Gather kernel signature.
Signature: Ubuntu 3.11.0-24.41-generic 3.11.10.11

Test 2 of 4: Gather kernel system information.
Kernel Version: Linux version 3.11.0-24-generic (buildd@toyol) (gcc version
4.8.1 (Ubuntu/Linaro 4.8.1-10ubuntu8) ) #41-Ubuntu SMP Mon Jun 9 20:36:00 UTC
2014

Test 3 of 4: Gather kernel boot command line.
Kernel boot command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-24-generic
root=UUID=52423430-ed6f-46b2-b259-60ddc64c17d0 ro

Test 4 of 4: Gather ACPI driver version.
ACPI Version: 20130517

================================================================================
0 passed, 0 failed, 0 warnings, 0 aborted, 0 skipped, 4 info only.
================================================================================

bios_info: Gather BIOS DMI information.
--------------------------------------------------------------------------------
Test 1 of 1: Gather BIOS DMI information
BIOS Vendor       : Hewlett-Packard
BIOS Version      : F.2C
BIOS Release Date : 18/02/2011
Board Name        : 7009
Board Serial #    : CNF94390SS
Board Version     : 36.35
Board Asset Tag   : Base Board Asset Tag
Chassis Serial #  : None
Chassis Type      : 10
Chassis Vendor    : Quanta
Chassis Version   : N/A
Chassic Asset Tag : 
Product Name      : HP Envy 15 Notebook PC
Product Serial #  : CNF94390SS
Product UUID      : 434E4639-3433-3930-5353-C80AA97A2C78
Product Version   : 0394100000241910001420000
System Vendor     : Hewlett-Packard

================================================================================
0 passed, 0 failed, 0 warnings, 0 aborted, 0 skipped, 1 info only.
================================================================================

oops: Scan kernel log for Oopses.
--------------------------------------------------------------------------------
Test 1 of 1: Kernel log oops check.
PASSED: Test 1, Found no oopses in kernel log.
PASSED: Test 1, Found no WARN_ON warnings in kernel log.

================================================================================
2 passed, 0 failed, 0 warnings, 0 aborted, 0 skipped, 0 info only.
================================================================================

klog: Scan kernel log for errors and warnings.
--------------------------------------------------------------------------------
Test 1 of 1: Kernel log error check.
FAILED [MEDIUM] KlogBiosMtrrsInconsistentAcrossCPUs: Test 1, MEDIUM Kernel
message: [ 0.682731] mtrr: your CPUs had inconsistent variable MTRR settings

ADVICE: The variable Memory Type Range Registers (MTRRs) which define memory
caching policy are not consistent across all CPUs which is a firmware bug. The
kernel has worked around this bug, but it may be worth getting the BIOS vendor
to fix this.

Kernel message: [ 0.698891] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored

ADVICE: This is not exactly a failure mode but a warning from the kernel. The
_OSI() method has implemented a match to the 'Linux' query in the DSDT and this
is redundant because the ACPI driver matches onto the Windows _OSI strings by
default.

FAILED [HIGH] KlogAcpiSleepStateEvalFailed: Test 1, HIGH Kernel message: [
0.731759] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_]
(20130517/hwxface-571)

ADVICE: Failed to evaluate _Sx namespace object that contains the register
values for the sleep state.

FAILED [HIGH] KlogAcpiSleepStateEvalFailed: Test 1, HIGH Kernel message: [
0.732048] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_]
(20130517/hwxface-571)

ADVICE: Failed to evaluate _Sx namespace object that contains the register
values for the sleep state.

FAILED [HIGH] KlogOscInvalidUuid: Test 1, HIGH Kernel message: [ 0.744087]
\_SB_.PCI0:_OSC invalid UUID
Message repeated 1 times.

ADVICE: The _OSC method indicates it has been passed an invalid UUID, see
section 6.2.10 _OSC (Operating System Capabilities) of the ACPI specification
for more details. Note that it has been observed on some systems that this error
is returned because the _OSC has evaluated incorrectly and it returns with an
incorrect error setting the OSC invalid UUID error bit.

FAILED [LOW] KlogAcpiSystemIOConflict: Test 1, LOW Kernel message: [ 14.720143]
ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with
Region \PMIO 1 (20130517/utaddress-251)

ADVICE: A resource conflict between an ACPI OperationRegion and a native driver
has been detected. By default the kernel will use a strict policy and will not
allow this region to conflict and -EBUSY will be returned to the caller that was
trying to allocate the already claimed region. If an ACPI driver is available
for this device then this should be used instead of a native driver, so
disabling the native driver may help. (Note that the lpc_ich driver can trigger
these warnings, in which case they can generally be ignored). One can specify
kernel boot parameter acpi_enforce_resources=lax to disable these checks but it
may lead to random problems and system instability. Alternatively, one can
specify acpi_enforce_resources=no and ACPI Operation Region resources will not
be registered.

FAILED [LOW] KlogAcpiSystemIOConflict: Test 1, LOW Kernel message: [ 14.720154]
ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with
Region \_SB_.PCI0.IEIT.SGPE 2 (20130517/utaddress-251)

ADVICE: A resource conflict between an ACPI OperationRegion and a native driver
has been detected. By default the kernel will use a strict policy and will not
allow this region to conflict and -EBUSY will be returned to the caller that was
trying to allocate the already claimed region. If an ACPI driver is available
for this device then this should be used instead of a native driver, so
disabling the native driver may help. (Note that the lpc_ich driver can trigger
these warnings, in which case they can generally be ignored). One can specify
kernel boot parameter acpi_enforce_resources=lax to disable these checks but it
may lead to random problems and system instability. Alternatively, one can
specify acpi_enforce_resources=no and ACPI Operation Region resources will not
be registered.

FAILED [LOW] KlogAcpiSystemIOConflict: Test 1, LOW Kernel message: [ 14.720170]
ACPI Warning: 0x0000000000000540-0x000000000000054f SystemIO conflicts with
Region \GPIO 1 (20130517/utaddress-251)

ADVICE: A resource conflict between an ACPI OperationRegion and a native driver
has been detected. By default the kernel will use a strict policy and will not
allow this region to conflict and -EBUSY will be returned to the caller that was
trying to allocate the already claimed region. If an ACPI driver is available
for this device then this should be used instead of a native driver, so
disabling the native driver may help. (Note that the lpc_ich driver can trigger
these warnings, in which case they can generally be ignored). One can specify
kernel boot parameter acpi_enforce_resources=lax to disable these checks but it
may lead to random problems and system instability. Alternatively, one can
specify acpi_enforce_resources=no and ACPI Operation Region resources will not
be registered.

FAILED [LOW] KlogAcpiSystemIOConflict: Test 1, LOW Kernel message: [ 14.720179]
ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with
Region \GPIO 1 (20130517/utaddress-251)

ADVICE: A resource conflict between an ACPI OperationRegion and a native driver
has been detected. By default the kernel will use a strict policy and will not
allow this region to conflict and -EBUSY will be returned to the caller that was
trying to allocate the already claimed region. If an ACPI driver is available
for this device then this should be used instead of a native driver, so
disabling the native driver may help. (Note that the lpc_ich driver can trigger
these warnings, in which case they can generally be ignored). One can specify
kernel boot parameter acpi_enforce_resources=lax to disable these checks but it
may lead to random problems and system instability. Alternatively, one can
specify acpi_enforce_resources=no and ACPI Operation Region resources will not
be registered.

FAILED [LOW] KlogAcpiSystemIOConflict: Test 1, LOW Kernel message: [ 14.720187]
ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with
Region \GPIO 1 (20130517/utaddress-251)

ADVICE: A resource conflict between an ACPI OperationRegion and a native driver
has been detected. By default the kernel will use a strict policy and will not
allow this region to conflict and -EBUSY will be returned to the caller that was
trying to allocate the already claimed region. If an ACPI driver is available
for this device then this should be used instead of a native driver, so
disabling the native driver may help. (Note that the lpc_ich driver can trigger
these warnings, in which case they can generally be ignored). One can specify
kernel boot parameter acpi_enforce_resources=lax to disable these checks but it
may lead to random problems and system instability. Alternatively, one can
specify acpi_enforce_resources=no and ACPI Operation Region resources will not
be registered.

FAILED [LOW] KlogAcpiSystemIOConflictLpcIchWatchDogTimer: Test 1, LOW Kernel
message: [ 14.720196] lpc_ich: Resource conflict(s) found affecting gpio_ich

ADVICE: A resource conflict has occurred between ACPI OperationRegions and the
same I/O region used by the lpc_ich driver for the General Purpose I/O (GPIO)
region. Sometimes this GPIO region is used by the firmware for rfkill or LED
controls or very rarely for the Embedded Controller System Control Interrupt.
This may require deeper inspection to check if the conflict will lead to any
real issues. However, in the vast majority of cases this warning can be ignored
as no harm will occur.

Found 10 unique errors in kernel log.

================================================================================
0 passed, 10 failed, 0 warnings, 0 aborted, 0 skipped, 0 info only.
================================================================================

mtrr: MTRR validation.
--------------------------------------------------------------------------------
MTRR overview
-------------
Reg 0: 0x0000000000000000 - 0x0000000080000000 (  2048 MB)   Write-Back
Reg 1: 0x00000000ffe00000 - 0x0000000100000000 (     2 MB)   Write-Protect
Reg 2: 0x0000000080000000 - 0x00000000c0000000 (  1024 MB)   Write-Back
Reg 3: 0x00000000bf800000 - 0x00000000c0000000 (     8 MB)   Uncached
Reg 4: 0x0000000100000000 - 0x0000000200000000 (  4096 MB)   Write-Back
Reg 5: 0x0000000200000000 - 0x0000000240000000 (  1024 MB)   Write-Back

Test 1 of 3: Validate the kernel MTRR IOMEM setup.
PASSED: Test 1, Memory ranges seem to have correct attributes.

Test 2 of 3: Validate the MTRR setup across all processors.
Detected CPUs with inconsistent variable MTRR settings which the kernel fixed.
FAILED [MEDIUM] MTRRCPUsMisconfigured: Test 2, It is probable that the BIOS does
not set up all the CPUs correctly and the kernel has now corrected this
misconfiguration.

Test 3 of 3: Check for AMD MtrrFixDramModEn being cleared by the BIOS.
SKIPPED: Test 3, CPU is not an AMD, cannot test.

================================================================================
1 passed, 1 failed, 0 warnings, 0 aborted, 1 skipped, 0 info only.
================================================================================

acpiinfo: General ACPI information check.
--------------------------------------------------------------------------------
Test 1 of 3: Determine Kernel ACPI version.
Kernel ACPICA driver version: 20130517, supports ACPI 5.0

Test 2 of 3: Determine machine's ACPI version.
FACP ACPI Version: 4.0 

Test 3 of 3: Determine AML compiler.
Determine the compiler used to generate the ACPI AML in the DSDT and SSDT.
Table DSDT, OEM HP , created with MSFT (Microsoft) compiler.
Table SSDT0, OEM TrmRef, created with INTL (Intel) compiler.
Table SSDT1, OEM VaRef, created with INTL (Intel) compiler.
Table SSDT2, OEM INTEL , created with INTL (Intel) compiler.
Table SSDT3, OEM INTEL , created with INTL (Intel) compiler.
Table SSDT4, OEM PmRef, created with INTL (Intel) compiler.

================================================================================
0 passed, 0 failed, 0 warnings, 0 aborted, 0 skipped, 3 info only.
================================================================================

securebootcert: Ubuntu UEFI secure boot test.
--------------------------------------------------------------------------------
Cannot detect any UEFI firmware. Aborted.
Aborted test, initialisation failed.
================================================================================
0 passed, 0 failed, 0 warnings, 1 aborted, 0 skipped, 0 info only.
================================================================================

csm: Check for UEFI Compatibility Support Module.
--------------------------------------------------------------------------------
Test 1 of 1: Check for UEFI Compatibility Support Module.
Checking for UEFI Compatibility Support Module (CSM)
Int 10h jumps to 0xc03f0 in option ROM at: 0xc0000..0xcfe00
No CSM: Legacy BIOS firmware has video option ROM with Int 10h support.

================================================================================
0 passed, 0 failed, 0 warnings, 0 aborted, 0 skipped, 1 info only.
================================================================================

maxreadreq: Checks firmware has set PCI Express MaxReadReq to a higher value on
non-motherboard devices.
--------------------------------------------------------------------------------
Test 1 of 1: Check firmware settings MaxReadReq for PCI Express devices.
MaxReadReq for pci://00:01:00.0 VGA compatible controller: Advanced Micro
Devices, Inc. [AMD/ATI] RV740/M97 [Mobility Radeon HD 4830] (prog-if 00 [VGA
controller]) is low (128) [VGA compatible controller].
MaxReadReq for pci://00:02:00.0 Network controller: Intel Corporation PRO
/Wireless 5100 AGN [Shiloh] Network Connection is low (128) [Network
controller].
FAILED [LOW] LowMaxReadReq: Test 1, 2 devices have low MaxReadReq settings.
Firmware may have configured these too low.

ADVICE: The MaxReadRequest size is set too low and will affect performance. It
will provide excellent bus sharing at the cost of bus data transfer rates.
Although not a critical issue, it may be worth considering setting the
MaxReadRequest size to 256 or 512 to increase throughput on the PCI Express bus.
Some drivers (for example the Brocade Fibre Channel driver) allow one to
override the firmware settings. Where possible, this BIOS configuration setting
is worth increasing it a little more for better performance at a small reduction
of bus sharing.


================================================================================
0 passed, 1 failed, 0 warnings, 0 aborted, 0 skipped, 0 info only.
================================================================================

crs: Check PCI host bridge configuration using _CRS.
--------------------------------------------------------------------------------
Test 1 of 1: Check PCI host bridge configuration using _CRS.
PASSED: Test 1, The kernel has detected a BIOS newer than the end of 2007 (18/2
/2011) and has assumed that your BIOS can correctly specify the host bridge MMIO
aperture using _CRS. If this does not work correctly you can override this by
booting with "pci=nocrs".

================================================================================
1 passed, 0 failed, 0 warnings, 0 aborted, 0 skipped, 0 info only.
================================================================================

aspm: PCIe ASPM check.
--------------------------------------------------------------------------------
Test 1 of 2: PCIe ASPM ACPI test.
PCIe ASPM is not controlled by Linux kernel.

ADVICE: BIOS reports that Linux kernel should not modify ASPM settings that BIOS
configured. It can be intentional because hardware vendors identified some
capability bugs between the motherboard and the add-on cards.


Test 2 of 2: PCIe ASPM registers test.
WARNING: Test 2, Device 01h:00h.00h L0s not enabled.

ADVICE: The ASPM L0s low power Link state is optimized for short entry and exit
latencies, while providing substantial power savings. Disabling L0s of a PCIe
device may increases power consumption, and will impact the battery life of a
mobile system.

FAILED [MEDIUM] PCIEASPM_Unmatched: Test 2, PCIe ASPM setting was not matched.
RP 00h:03h.00h has ASPM = 00h.
Device 01h:00h.00h has ASPM = 02h.

ADVICE: ASPM control registers between root port and device must match in order
for ASPM to be active. Unmatched configuration indicates software did not
configure ASPM correctly and the system is not saving power at its full
potential.

PASSED: Test 2, PCIe ASPM setting matched was matched.
WARNING: Test 2, RP 00h:1Ch.01h L0s not enabled.
WARNING: Test 2, Device 03h:00h.00h L0s not enabled.

ADVICE: The ASPM L0s low power Link state is optimized for short entry and exit
latencies, while providing substantial power savings. Disabling L0s of a PCIe
device may increases power consumption, and will impact the battery life of a
mobile system.

PASSED: Test 2, PCIe ASPM setting matched was matched.

================================================================================
2 passed, 1 failed, 3 warnings, 0 aborted, 0 skipped, 0 info only.
================================================================================

hpet_check: HPET configuration test.
--------------------------------------------------------------------------------
Test 1 of 4: Check HPET base in kernel log.
This test checks the HPET PCI BAR for each timer block in the timer. The base
address is passed by the firmware via an ACPI table. IRQ routing and
initialization is also verified by the test.
PASSED: Test 1, Found HPET base 0xfed00000 in kernel log.

Test 2 of 4: Check HPET base in HPET table. 
Hardware ID of Event Block:
  PCI Vendor ID              : 0x8086
  Legacy IRQ Routing Capable : 1
  COUNT_SIZE_CAP counter size: 1
  Number of comparitors      : 2
  Hardwre Revision ID        : 0x1
Lower 32 bit base Address    : 0xfed00000
  Address Space ID           : 0x0
  Register Bit Width         : 0x0
  Register Bit Offset        : 0x0
  Address Width              : 0x0
HPET sequence number         : 0x0
Minimum clock tick           : 0x80
Page Protection              : 0x0 (No guaranteed protection)
OEM attributes               : 0x0
PASSED: Test 2, HPET looks sane.

Test 3 of 4: Check HPET base in DSDT and/or SSDT. 
PASSED: Test 3, HPET base matches that between DSDT and the kernel (0xfed00000).

Test 4 of 4: Sanity check HPET configuration.
PASSED: Test 4, Vendor ID looks sane: 0x8086.
PASSED: Test 4, Valid clock period 69841279.

================================================================================
5 passed, 0 failed, 0 warnings, 0 aborted, 0 skipped, 0 info only.
================================================================================

dmicheck: Test DMI/SMBIOS tables for errors.
--------------------------------------------------------------------------------
Test 1 of 2: Find and Check SMBIOS Table Entry Point.
This test tries to find and sanity check the SMBIOS data structures.
PASSED: Test 1, Found SMBIOS Table Entry Point at 0xfe120
SMBIOS Entry Point Structure:
  Anchor String          : _SM_
  Checksum               : 0xcd
  Entry Point Length     : 0x1f
  Major Version          : 0x02
  Minor Version          : 0x06
  Maximum Struct Size    : 0xae
  Entry Point Revision   : 0x00
  Formatted Area         : 0x00 0x00 0x00 0x00 0x00
  Intermediate Anchor    : _DMI_
  Intermediate Checksum  : 0xfc
  Structure Table Length : 0x05aa
  Structure Table Address: 0x000ea9c0
  # of SMBIOS Structures : 0x0020
  SBMIOS BCD Revision    : 26

PASSED: Test 1, SMBIOS Table Entry Point Checksum is valid.
PASSED: Test 1, SMBIOS Table Entry Point Length is valid.
PASSED: Test 1, SMBIOS Table Entry Intermediate Anchor String _DMI_ is valid.
PASSED: Test 1, SMBIOS Table Entry Point Intermediate Checksum is valid.
PASSED: Test 1, SMBIOS Table Entry Structure Table Address and Length looks
valid.

Test 2 of 2: Test DMI/SMBIOS tables for errors.
PASSED: Test 2, Entry @ 0x000ea9c0 'BIOS Information (Type 0)'
PASSED: Test 2, Entry @ 0x000ea9f9 'System Information (Type 1)'
PASSED: Test 2, Entry @ 0x000eaa79 'Base Board Information (Type 2)'
PASSED: Test 2, Entry @ 0x000eaad8 'Chassis Information (Type 3)'
PASSED: Test 2, Entry @ 0x000eaaff 'System Slot Information (Type 9)'
PASSED: Test 2, Entry @ 0x000eab16 'System Slot Information (Type 9)'
PASSED: Test 2, Entry @ 0x000eab2d 'System Slot Information (Type 9)'
PASSED: Test 2, Entry @ 0x000eab44 'System Slot Information (Type 9)'
PASSED: Test 2, Entry @ 0x000eab5b 'System Slot Information (Type 9)'
PASSED: Test 2, Entry @ 0x000eab72 'System Slot Information (Type 9)'
PASSED: Test 2, Entry @ 0x000eab89 'System Slot Information (Type 9)'
PASSED: Test 2, Entry @ 0x000eaba0 'System Slot Information (Type 9)'
PASSED: Test 2, Entry @ 0x000eabb7 'On Board Devices (Type 10)'
PASSED: Test 2, Entry @ 0x000eabd8 'On Board Devices (Type 10)'
PASSED: Test 2, Entry @ 0x000eabf6 'OEM Strings (Type 11)'
PASSED: Test 2, Entry @ 0x000eac3e 'System Configuration Options (Type 12)'
PASSED: Test 2, Entry @ 0x000eacec 'System Event Log (Type 15)'
PASSED: Test 2, Entry @ 0x000ead0b 'Built-in Pointing Device (Type 21)'
PASSED: Test 2, Entry @ 0x000ead14 'System Boot Information (Type 32)'
PASSED: Test 2, Entry @ 0x000ead2a 'Physical Memory Array (Type 16)'
PASSED: Test 2, Entry @ 0x000ead3b 'Memory Device (Type 17)'
PASSED: Test 2, Entry @ 0x000ead90 'Memory Device Mapped Address (Type 20)'
PASSED: Test 2, Entry @ 0x000eada5 'Memory Device (Type 17)'
PASSED: Test 2, Entry @ 0x000eadfa 'Memory Device Mapped Address (Type 20)'
PASSED: Test 2, Entry @ 0x000eae0f 'Memory Device (Type 17)'
PASSED: Test 2, Entry @ 0x000eae66 'Memory Array Mapped Address (Type 19)'
PASSED: Test 2, Entry @ 0x000eae77 'Processor Information (Type 4)'
PASSED: Test 2, Entry @ 0x000eaef0 'Cache Information (Type 7)'
PASSED: Test 2, Entry @ 0x000eaf0d 'Cache Information (Type 7)'
PASSED: Test 2, Entry @ 0x000eaf2a 'Cache Information (Type 7)'
PASSED: Test 2, Entry @ 0x000eaf47 'Cache Information (Type 7)'
PASSED: Test 2, Entry @ 0x000eaf64 'End of Table (Type 127)'

================================================================================
38 passed, 0 failed, 0 warnings, 0 aborted, 0 skipped, 0 info only.
================================================================================

microcode: Check if system is using latest microcode.
--------------------------------------------------------------------------------
Test 1 of 1: Check for most recent microcode being loaded.
This test verifies if the firmware has put a recent revision of the microcode
into the processor at boot time. Recent microcode is important to have all the
required features and errata updates for the processor.
FAILED [MEDIUM] MicrocodeNotUpdated: Test 1, The kernel did not report that CPU
0 has had a microcode update. The current firmware is revision 0x4 and probably
has not been updated.
FAILED [MEDIUM] MicrocodeNotUpdated: Test 1, The kernel did not report that CPU
1 has had a microcode update. The current firmware is revision 0x4 and probably
has not been updated.
FAILED [MEDIUM] MicrocodeNotUpdated: Test 1, The kernel did not report that CPU
2 has had a microcode update. The current firmware is revision 0x4 and probably
has not been updated.
FAILED [MEDIUM] MicrocodeNotUpdated: Test 1, The kernel did not report that CPU
3 has had a microcode update. The current firmware is revision 0x4 and probably
has not been updated.
FAILED [MEDIUM] MicrocodeNotUpdated: Test 1, The kernel did not report that CPU
4 has had a microcode update. The current firmware is revision 0x4 and probably
has not been updated.
FAILED [MEDIUM] MicrocodeNotUpdated: Test 1, The kernel did not report that CPU
5 has had a microcode update. The current firmware is revision 0x4 and probably
has not been updated.
FAILED [MEDIUM] MicrocodeNotUpdated: Test 1, The kernel did not report that CPU
6 has had a microcode update. The current firmware is revision 0x4 and probably
has not been updated.
FAILED [MEDIUM] MicrocodeNotUpdated: Test 1, The kernel did not report that CPU
7 has had a microcode update. The current firmware is revision 0x4 and probably
has not been updated.

================================================================================
0 passed, 8 failed, 0 warnings, 0 aborted, 0 skipped, 0 info only.
================================================================================

msr: MSR register tests.
--------------------------------------------------------------------------------
Test 1 of 5: Check CPU generic MSRs.
PASSED: Test 1, MSR P5_MC_TYPE (0x1) (mask:ffffffffffffffff) was consistent
across 8 CPUs.
PASSED: Test 1, MSR MONITOR_FILTER_SIZE (0x6) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 1, MSR PLATFORM_ID (0x17) (mask:1c000000000000) was consistent
across 8 CPUs.
PASSED: Test 1, MSR EBL_CR_POWERON (0x2a) (mask:ffffffffffffffff) was consistent
across 8 CPUs.
PASSED: Test 1, MSR APIC_BASE (0x1b) (mask:fffffffffffffeff) was consistent
across 8 CPUs.
PASSED: Test 1, MSR FEATURE_CONTROL (0x3a) (mask:ff07) was consistent across 8
CPUs.
PASSED: Test 1, MSR BIOS_SIGN_ID (0x8b) (mask:ffffffff00000000) was consistent
across 8 CPUs.
PASSED: Test 1, MSR MTRRCAP (0xfe) (mask:fff) was consistent across 8 CPUs.
PASSED: Test 1, MSR SYSENTER_CS (0x174) (mask:ffff) was consistent across 8
CPUs.
PASSED: Test 1, MSR SYSENTER_ESP (0x175) (mask:ffffffffffffffff) was consistent
across 8 CPUs.
PASSED: Test 1, MSR SYSENTER_EIP (0x176) (mask:ffffffffffffffff) was consistent
across 8 CPUs.
PASSED: Test 1, MSR MCG_CAP (0x179) (mask:1ff0fff) was consistent across 8 CPUs.
PASSED: Test 1, MSR MCG_STATUS (0x17a) (mask:ffffffffffffffff) was consistent
across 8 CPUs.
FAILED [MEDIUM] MSRCPUsInconsistent: Test 1, MSR CLOCK_MODULATION (0x19a) has 7
inconsistent values across 8 CPUs for (shift: 0 mask: 0x1f).
MSR CPU 0 -> 0x8 vs CPU 1 -> 0x0
MSR CPU 0 -> 0x8 vs CPU 2 -> 0x0
MSR CPU 0 -> 0x8 vs CPU 3 -> 0x0
MSR CPU 0 -> 0x8 vs CPU 4 -> 0x0
MSR CPU 0 -> 0x8 vs CPU 5 -> 0x0
MSR CPU 0 -> 0x8 vs CPU 6 -> 0x0
MSR CPU 0 -> 0x8 vs CPU 7 -> 0x0
PASSED: Test 1, MSR THERM_INTERRUPT (0x19b) (mask:180801f) was consistent across
8 CPUs.
PASSED: Test 1, MSR MISC_ENABLE (0x1a0) (mask:400c51889) was consistent across 8
CPUs.
PASSED: Test 1, MSR SMRR_PHYSBASE (0x1f2) (mask:fffff0ff) was consistent across
8 CPUs.
PASSED: Test 1, MSR SMRR_PHYSMASK (0x1f3) (mask:fffff800) was consistent across
8 CPUs.
PASSED: Test 1, MSR MTRR_PHYSBASE0 (0x200) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 1, MSR MTRR_PHYSMASK0 (0x201) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 1, MSR MTRR_PHYSBASE1 (0x202) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 1, MSR MTRR_PHYSMASK1 (0x203) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 1, MSR MTRR_PHYSBASE2 (0x204) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 1, MSR MTRR_PHYSMASK2 (0x205) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 1, MSR MTRR_PHYSBASE3 (0x206) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 1, MSR MTRR_PHYSMASK3 (0x207) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 1, MSR MTRR_PHYSBASE4 (0x208) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 1, MSR MTRR_PHYSMASK4 (0x209) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 1, MSR MTRR_PHYSBASE5 (0x20a) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 1, MSR MTRR_PHYSMASK5 (0x20b) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 1, MSR MTRR_PHYSBASE6 (0x20c) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 1, MSR MTRR_PHYSMASK6 (0x20d) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 1, MSR MTRR_PHYSBASE7 (0x20e) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 1, MSR MTRR_PHYSMASK7 (0x20f) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 1, MSR MTRR_FIX64K_000 (0x250) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 1, MSR MTRR_FIX16K_800 (0x258) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 1, MSR MTRR_FIX16K_a00 (0x259) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 1, MSR MTRR_FIX4K_C000 (0x268) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 1, MSR MTRR_FIX4K_C800 (0x269) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 1, MSR MTRR_FIX4K_D000 (0x26a) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 1, MSR MTRR_FIX4K_D800 (0x26b) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 1, MSR MTRR_FIX4K_E000 (0x26c) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 1, MSR MTRR_FIX4K_E800 (0x26d) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 1, MSR MTRR_FIX4K_F000 (0x26e) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 1, MSR MTRR_FIX4K_F800 (0x26f) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 1, MSR PAT (0x277) (mask:707070707070703) was consistent across 8
CPUs.
PASSED: Test 1, MSR MC0_CTL2 (0x280) (mask:40007fff) was consistent across 8
CPUs.
PASSED: Test 1, MSR MC1_CTL2 (0x281) (mask:40007fff) was consistent across 8
CPUs.
PASSED: Test 1, MSR MC2_CTL2 (0x282) (mask:40007fff) was consistent across 8
CPUs.
PASSED: Test 1, MSR MC3_CTL2 (0x283) (mask:40007fff) was consistent across 8
CPUs.
PASSED: Test 1, MSR MC4_CTL2 (0x284) (mask:40007fff) was consistent across 8
CPUs.
PASSED: Test 1, MSR MC5_CTL2 (0x285) (mask:40007fff) was consistent across 8
CPUs.
PASSED: Test 1, MSR MC6_CTL2 (0x286) (mask:40007fff) was consistent across 8
CPUs.
PASSED: Test 1, MSR MC7_CTL2 (0x287) (mask:40007fff) was consistent across 8
CPUs.
PASSED: Test 1, MSR MC8_CTL2 (0x288) (mask:40007fff) was consistent across 8
CPUs.
PASSED: Test 1, MSR MTRR_DEF_TYPE (0x2ff) (mask:c0f) was consistent across 8
CPUs.
PASSED: Test 1, MSR PEBS_ENABLE (0x3f1) (mask:1) was consistent across 8 CPUs.
PASSED: Test 1, MSR VMX_BASIC (0x480) (mask:ffffffffffffffff) was consistent
across 8 CPUs.
PASSED: Test 1, MSR VMX_PINPASED_CTLS (0x481) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 1, MSR VMX_PROCBASED_CTLS (0x482) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 1, MSR VMX_EXIT_CTLS (0x483) (mask:ffffffffffffffff) was consistent
across 8 CPUs.
PASSED: Test 1, MSR VMX_ENTRY_CTLS (0x484) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 1, MSR VMX_MISC (0x485) (mask:ffffffffffffffff) was consistent
across 8 CPUs.
PASSED: Test 1, MSR VMX_CR0_FIXED0 (0x486) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 1, MSR VMX_CR0_FIXED1 (0x487) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 1, MSR VMX_CR4_FIXED0 (0x488) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 1, MSR VMX_CR4_FIXED1 (0x489) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 1, MSR VMX_VMX_VMCS_ENUM (0x48a) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 1, MSR VMX_PROCBASED_CTLS2 (0x48b) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 1, MSR VMX_EPT_VPID_CAP (0x48c) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 1, MSR VMX_TRUE_PINBASED_CTLS (0x48d) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 1, MSR VMX_TRUE_PROCBASED_CTLS (0x48e) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 1, MSR VMX_TRUE_EXIT_CTLS (0x48f) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 1, MSR VMX_TRUE_ENTRY_CTLS (0x490) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 1, MSR EFER (0xc0000080) (mask:d01) was consistent across 8 CPUs.
PASSED: Test 1, MSR STAR (0xc0000081) (mask:ffffffffffffffff) was consistent
across 8 CPUs.
PASSED: Test 1, MSR LSTAR (0xc0000082) (mask:ffffffffffffffff) was consistent
across 8 CPUs.
PASSED: Test 1, MSR FMASK (0xc0000084) (mask:ffffffffffffffff) was consistent
across 8 CPUs.
PASSED: Test 1, MSR KERNEL_GS_BASE (0xc0000102) (mask:ffffffffffffffff) was
consistent across 8 CPUs.

Test 2 of 5: Check CPU specific model MSRs.
PASSED: Test 2, MSR MSR_PLATFORM_INFO (0xce) (mask:ff003001ff00) was consistent
across 8 CPUs.
PASSED: Test 2, MSR MSR_PKG_CST_CONFIG_CONTROL (0xe2) (mask:7008407) was
consistent across 8 CPUs.
PASSED: Test 2, MSR MSR_PMG_IO_CAPTURE_BASE (0xe4) (mask:7ffff) was consistent
across 8 CPUs.
FAILED [MEDIUM] MSRCPUsInconsistent: Test 2, MSR CLOCK_MODULATION (0x19a) has 7
inconsistent values across 8 CPUs for (shift: 0 mask: 0x1f).
MSR CPU 0 -> 0x8 vs CPU 1 -> 0x0
MSR CPU 0 -> 0x8 vs CPU 2 -> 0x0
MSR CPU 0 -> 0x8 vs CPU 3 -> 0x0
MSR CPU 0 -> 0x8 vs CPU 4 -> 0x0
MSR CPU 0 -> 0x8 vs CPU 5 -> 0x0
MSR CPU 0 -> 0x8 vs CPU 6 -> 0x0
MSR CPU 0 -> 0x8 vs CPU 7 -> 0x0
PASSED: Test 2, MSR MSR_TEMPERATURE_TARGET (0x1a2) (mask:ff0000) was consistent
across 8 CPUs.
PASSED: Test 2, MSR MSR_OFFCORE_RSP_0 (0x1a6) (mask:ffffffffffffffff) was
consistent across 8 CPUs.
PASSED: Test 2, MSR MSR_MISC_PWR_MGMT (0x1aa) (mask:3) was consistent across 8
CPUs.
PASSED: Test 2, MSR MSR_TURBO_POWER_CURRENT_LIMIT (0x1ac) (mask:ffffffff) was
consistent across 8 CPUs.
PASSED: Test 2, MSR MSR_TURBO_RATIO_LIMIT (0x1ad) (mask:ffffffff) was consistent
across 8 CPUs.
PASSED: Test 2, MSR MSR_POWER_CTL (0x1fc) (mask:2) was consistent across 8 CPUs.

Test 3 of 5: Check all P State Ratios.
PASSED: Test 3, MSR Minimum P-State (0xce) (mask:ff) was consistent across 8
CPUs.
PASSED: Test 3, MSR Maximum P-State (0xce) (mask:ff) was consistent across 8
CPUs.

Test 4 of 5: Check C1 and C3 autodemotion.
PASSED: Test 4, MSR C1 and C3 Autodemotion (0xe2) (mask:3) was consistent across
8 CPUs.
C1 and C3 Autodemotion disabled.

Test 5 of 5: Check SMRR MSR registers.
PASSED: Test 5, MSR SMRR_PHYSBASE (0x1f2) (mask:fffff) was consistent across 8
CPUs.
PASSED: Test 5, MSR SMRR_TYPE (0x1f2) (mask:7) was consistent across 8 CPUs.
PASSED: Test 5, MSR SMRR_PHYSMASK (0x1f3) (mask:fffff) was consistent across 8
CPUs.
PASSED: Test 5, MSR SMRR_VALID (0x1f3) (mask:1) was consistent across 8 CPUs.

================================================================================
94 passed, 2 failed, 0 warnings, 0 aborted, 0 skipped, 0 info only.
================================================================================

nx: Test if CPU NX is disabled by the BIOS.
--------------------------------------------------------------------------------
Test 1 of 3: Check CPU NX capability.
PASSED: Test 1, CPU has NX flags, BIOS is not disabling it.

Test 2 of 3: Check all CPUs have same BIOS set NX flag.
This test verifies that all CPUs have the same NX flag setting. Although rare,
BIOS may set the NX flag differently per CPU. 
PASSED: Test 2, All 8 CPUs have the same NX flag set.

Test 3 of 3: Check all CPUs have same msr setting in MSR 0x1a0.
This test verifies that all CPUs have the same NX flag setting by examining the
per CPU MSR register 0x1a0.
PASSED: Test 3, All 8 CPUs have the NX flag in MSR 0x1a0 set.

================================================================================
3 passed, 0 failed, 0 warnings, 0 aborted, 0 skipped, 0 info only.
================================================================================

cpufreq: CPU frequency scaling tests.
--------------------------------------------------------------------------------
Test 1 of 1: CPU P-State Checks.
For each processor in the system, this test steps through the various frequency
states (P-states) that the BIOS advertises for the processor. For each processor
/frequency combination, a quick performance value is measured. The test then
validates that:
  1. Each processor has the same number of frequency states.
  2. Higher advertised frequencies have a higher performance.
  3. No duplicate frequency values are reported by the BIOS.
  4. BIOS doing Sw_All P-state coordination across cores.
  5. BIOS doing Sw_Any P-state coordination across cores.

CPU 0: 8 CPU frequency steps supported.
 Frequency | Relative Speed | Bogo loops
-----------+----------------+-----------
  1.78 GHz |     100.0 %    |    296189
  1.78 GHz |      60.5 %    |    179249
  1.65 GHz |      55.8 %    |    165336
  1463 MHz |      51.3 %    |    151800
  1330 MHz |      46.6 %    |    138028
  1197 MHz |      41.9 %    |    124226
  1064 MHz |      37.2 %    |    110328
   931 MHz |      32.5 %    |     96399

CPU 1: 8 CPU frequency steps supported.
 Frequency | Relative Speed | Bogo loops
-----------+----------------+-----------
  1.78 GHz |     100.0 %    |    297155
  1.78 GHz |      60.4 %    |    179450
  1.65 GHz |      55.8 %    |    165697
  1463 MHz |      51.1 %    |    151869
  1330 MHz |      46.5 %    |    138049
  1197 MHz |      41.8 %    |    124177
  1064 MHz |      36.9 %    |    109597
   931 MHz |      32.3 %    |     95944

CPU 2: 8 CPU frequency steps supported.
 Frequency | Relative Speed | Bogo loops
-----------+----------------+-----------
  1.78 GHz |     100.0 %    |    248217
  1.78 GHz |      72.1 %    |    178895
  1.65 GHz |      66.5 %    |    164952
  1463 MHz |      60.6 %    |    150498
  1330 MHz |      55.3 %    |    137209
  1197 MHz |      49.6 %    |    123172
  1064 MHz |      44.2 %    |    109708
   931 MHz |      38.7 %    |     95965

CPU 3: 8 CPU frequency steps supported.
 Frequency | Relative Speed | Bogo loops
-----------+----------------+-----------
  1.78 GHz |     100.0 %    |    279693
  1.78 GHz |      63.8 %    |    178510
  1.65 GHz |      58.6 %    |    163957
  1463 MHz |      54.0 %    |    151115
  1330 MHz |      48.9 %    |    136825
  1197 MHz |      44.3 %    |    123870
  1064 MHz |      39.1 %    |    109280
   931 MHz |      34.2 %    |     95700

CPU 4: 8 CPU frequency steps supported.
 Frequency | Relative Speed | Bogo loops
-----------+----------------+-----------
  1.78 GHz |     100.0 %    |    282055
  1.78 GHz |      63.5 %    |    179229
  1.65 GHz |      58.6 %    |    165279
  1463 MHz |      53.7 %    |    151574
  1330 MHz |      48.6 %    |    137082
  1197 MHz |      43.7 %    |    123357
  1064 MHz |      39.0 %    |    110139
   931 MHz |      34.1 %    |     96259

CPU 5: 8 CPU frequency steps supported.
 Frequency | Relative Speed | Bogo loops
-----------+----------------+-----------
  1.78 GHz |     100.0 %    |    260129
  1.78 GHz |      69.1 %    |    179670
  1.65 GHz |      63.7 %    |    165802
  1463 MHz |      58.4 %    |    152038
  1330 MHz |      53.1 %    |    138230
  1197 MHz |      47.8 %    |    124373
  1064 MHz |      42.5 %    |    110566
   931 MHz |      37.2 %    |     96713

CPU 6: 8 CPU frequency steps supported.
 Frequency | Relative Speed | Bogo loops
-----------+----------------+-----------
  1.78 GHz |     100.0 %    |    288709
  1.78 GHz |      62.1 %    |    179426
  1.65 GHz |      57.4 %    |    165616
  1463 MHz |      52.6 %    |    151734
  1330 MHz |      47.8 %    |    137941
  1197 MHz |      43.0 %    |    124098
  1064 MHz |      38.2 %    |    110360
   931 MHz |      33.4 %    |     96530

CPU 7: 8 CPU frequency steps supported.
 Frequency | Relative Speed | Bogo loops
-----------+----------------+-----------
  1.78 GHz |     100.0 %    |    272605
  1.78 GHz |      65.7 %    |    179156
  1.65 GHz |      60.6 %    |    165171
  1463 MHz |      55.7 %    |    151888
  1330 MHz |      50.6 %    |    137862
  1197 MHz |      45.5 %    |    124089
  1064 MHz |      40.4 %    |    110081
   931 MHz |      35.3 %    |     96315

FAILED [MEDIUM] CPUFreqCPUsSetToSW_ANY: Test 1, Processors are set to SW_ANY.

================================================================================
0 passed, 1 failed, 0 warnings, 0 aborted, 0 skipped, 0 info only.
================================================================================

maxfreq: Check max CPU frequencies against max scaling frequency.
--------------------------------------------------------------------------------
Test 1 of 1: Maximum CPU frequency check.
This test checks the maximum CPU frequency as detected by the kernel for each
CPU against maxiumum frequency as specified by the BIOS frequency scaling
settings.
PASSED: Test 1, 8 CPUs passed the maximum frequency check.

================================================================================
1 passed, 0 failed, 0 warnings, 0 aborted, 0 skipped, 0 info only.
================================================================================

virt: Test CPU Virtualisation Configuration.
--------------------------------------------------------------------------------
Test 1 of 1: Check CPU Virtualisation Configuration.
Check VT/VMX Virtualization extensions are set up correctly.
PASSED: Test 1, Virtualization extensions supported and enabled by BIOS.

================================================================================
1 passed, 0 failed, 0 warnings, 0 aborted, 0 skipped, 0 info only.
================================================================================

pnp: Check BIOS Support Installation structure.
--------------------------------------------------------------------------------
Test 1 of 1: Check PnP BIOS Support Installation structure.
This test tries to find and sanity check the Plug and Play BIOS Support
Installation Check structure. 

Found PnP Installation Check structure at 0x000fe0f0
  Signature                          : $PnP
  Version                            : 0x10 (1.0)
  Length                             : 0x0021 bytes
  Control Field                      : 0x0000 (Not supported)
  Event Notification Flag Address    : 0x00000000 (undefined)
  Real Mode 16 bit Code Address      : 0xf000:b9b5
  Real Mode 16 bit Data Address      : 0x0040:0000
  16 bit Protected Mode Code Address : 0x000fb9c0
  16 bit Protected Mode Data Address : 0x00000400
  OEM Device Identifier              : 0x8224744e (SST2482)

PASSED: Test 1, Version 1.0 detected.
PASSED: Test 1, PnP Installation Check structure is the correct length of 33
bytes.

================================================================================
2 passed, 0 failed, 0 warnings, 0 aborted, 0 skipped, 0 info only.
================================================================================

pciirq: Check PCI IRQ Routing Table.
--------------------------------------------------------------------------------
Test 1 of 1: PCI IRQ Routing Table.
This test tries to find and sanity check the PCI IRQ Routing Table, as defined
by http://www.microsoft.com/taiwan/whdc/archive/pciirq.mspx and described in
pages 233-238 of PCI System Architecture, Fourth Edition, Mindshare, Inc.
(1999). NOTE: The PCI IRQ Routing Table only really knows about ISA IRQs and is
generally not used with APIC. 

Could not find PCI IRQ Routing Table. Since this table is for legacy BIOS
systems which don't have ACPI support this is generally not a problem.

================================================================================
0 passed, 0 failed, 0 warnings, 0 aborted, 0 skipped, 0 info only.
================================================================================

os2gap: OS/2 memory hole test.
--------------------------------------------------------------------------------
Test 1 of 1: Check the OS/2 15Mb memory hole is absent.
PASSED: Test 1, No OS/2 memory hole found.

================================================================================
1 passed, 0 failed, 0 warnings, 0 aborted, 0 skipped, 0 info only.
================================================================================

mpcheck: Check MultiProcessor Tables.
--------------------------------------------------------------------------------
Failed to get _MP_ data from firmware.
================================================================================
0 passed, 0 failed, 0 warnings, 0 aborted, 9 skipped, 0 info only.
================================================================================

hda_audio: Check HDA Audio Pin Configs.
--------------------------------------------------------------------------------
Test 1 of 1: Check HDA Audio Pin Configs.
Checking 'hwC0D0':
Vendor Name    : IDT
Vendor ID      : 0x111d7608
Subsystem ID   : 0x103c7009
Revision ID    : 0x100202
BIOS pin configurations:
  Pin  Setting
  0x000a 0x0121101f
  0x000b 0x01a11020
  0x000c 0x40f000f3
  0x000d 0x90110110
  0x000e 0x40f000f9
  0x0014 0x40f000f1
  0x0018 0x90a60350
  0x001e 0x40f000f4
  0x001f 0x40f000f5
  0x0020 0x40f000f6
Driver defined pin configurations:
  Pin  Setting
  0x000f 0x40f000f0
  0x0019 0x40f000f3
BIOS pin configurations required software override to make HDA audio work
correctly.
The driver or user provided overrides should be corrected in BIOS firmware.

Checking 'hwC1D0':
Vendor Name    : ATI
Vendor ID      : 0x1002aa01
Subsystem ID   : 0xaa0100
Revision ID    : 0x100100
BIOS pin configurations:
  Pin  Setting
  0x0003 0x18560010
PASSED: Test 1, Default BIOS pin configurations did not have software override.


================================================================================
1 passed, 0 failed, 0 warnings, 0 aborted, 0 skipped, 0 info only.
================================================================================

ebda: Validate EBDA region is mapped and reserved in memory map table.
--------------------------------------------------------------------------------
Test 1 of 1: Check EBDA is reserved in E820 table.
The Extended BIOS Data Area (EBDA) is normally located at the end of the low
640K region and is typically 2-4K in size. It should be reserved in the Int 15
AX=E820 BIOS memory map table.
PASSED: Test 1, EBDA region mapped at 0x9bc00 and reserved as a 16K region in
the Int 15 AX=E820 BIOS memory map table at 0x9bc00..0x9ffff.

================================================================================
1 passed, 0 failed, 0 warnings, 0 aborted, 0 skipped, 0 info only.
================================================================================

bios32: Check BIOS32 Service Directory.
--------------------------------------------------------------------------------
Test 1 of 1: Check BIOS32 Service Directory.
This test tries to find and sanity check the BIOS32 Service Directory as defined
in the Standard BIOS 32-bit Service Directory Proposal, Revision 0.4 May 24,
1993, Phoenix Technologies Ltd and also the PCI BIOS specification.
Could not find BIOS32 Service Directory.

================================================================================
0 passed, 0 failed, 0 warnings, 0 aborted, 0 skipped, 0 info only.
================================================================================

apicedge: APIC Edge/Level Check.
--------------------------------------------------------------------------------
Test 1 of 1: Legacy and PCI Interrupt Edge/Level trigger checks.
PASSED: Test 1, Legacy interrupts are edge and PCI interrupts are level
triggered.

================================================================================
1 passed, 0 failed, 0 warnings, 0 aborted, 0 skipped, 0 info only.
================================================================================

wmi: Extract and analyse Windows Management Instrumentation (WMI).
--------------------------------------------------------------------------------
Test 1 of 1: Check Windows Management Instrumentation

\_SB_.WMID._WDG (1 of 4)
  GUID: 5FB7F034-2C63-45E9-BE91-3D44E2C707E4
  WMI Method:
    Flags          : 0x02 (Method)
    Object ID      : AD
    Instance       : 0x01
PASSED: Test 1, 5FB7F034-2C63-45E9-BE91-3D44E2C707E4 has associated method
\_SB_.WMID.WMAD

\_SB_.WMID._WDG (2 of 4)
  GUID: 95F24279-4D7B-4334-9387-ACCDC67EF61C
  WMI Event:
    Flags          : 0x08 (Event)
    Notification ID: 0x80
    Reserved       : 0x00
    Instance       : 0x01
    Driver         : hp-wmi (HP)

\_SB_.WMID._WDG (3 of 4)
  GUID: 05901221-D566-11D1-B2F0-00A0C9062910
  WMI Object:
    Flags          : 0x00 (None)
    Object ID      : AE
    Instance       : 0x01

\_SB_.WMID._WDG (4 of 4)
  GUID: D0992BD4-A47C-4EFE-B072-324AEC92296C
  WMI Object:
    Flags          : 0x00 (None)
    Object ID      : BC
    Instance       : 0x01
PASSED: Test 1, All events associated with \_SB_.WMID._WDG are handled by a
kernel driver.

================================================================================
2 passed, 0 failed, 0 warnings, 0 aborted, 0 skipped, 0 info only.
================================================================================

wakealarm: Test ACPI Wakealarm.
--------------------------------------------------------------------------------
Test 1 of 4: Check existence of /sys/class/rtc/rtc0/wakealarm.
PASSED: Test 1, /sys/class/rtc/rtc0/wakealarm found.

Test 2 of 4: Trigger wakealarm for 1 seconds in the future.
Trigger wakealarm for 1 seconds in the future.
PASSED: Test 2, RTC wakealarm was triggered successfully.

Test 3 of 4: Check if wakealarm is fired.
PASSED: Test 3, RTC wakealarm triggered and fired successfully.

Test 4 of 4: Multiple wakealarm firing tests.
Trigger wakealarm for 1 seconds in the future.
Trigger wakealarm for 2 seconds in the future.
Trigger wakealarm for 3 seconds in the future.
Trigger wakealarm for 4 seconds in the future.
PASSED: Test 4, RTC wakealarm triggered and fired successfully.

================================================================================
4 passed, 0 failed, 0 warnings, 0 aborted, 0 skipped, 0 info only.
================================================================================

syntaxcheck: Re-assemble DSDT and find syntax errors and warnings.
--------------------------------------------------------------------------------
Test 1 of 2: Disassemble and reassemble DSDT

Checking ACPI table DSDT (#0)

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 2637
Line | AML source
--------------------------------------------------------------------------------
02634|             {
02635|                 If (ECON)
02636|                 {
02637|                     If (LEqual (^^PCI0.LPCB.EC0.ECLS, One))
     |                                                   ^
     | Error 6085: Object not found or not accessible from scope    (  PCI0.LPCB.EC0.ECLS)
02638|                     {
02639|                         Store (Zero, LSTS)
02640|                     }
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 2735
Line | AML source
--------------------------------------------------------------------------------
02732|             {
02733|                 If (ECON)
02734|                 {
02735|                     And (One, ^^PCI0.LPCB.EC0.SW2S, Local0)
     |                                                 ^
     | Error 6085: Object not found or not accessible from scope    (  PCI0.LPCB.EC0.SW2S)
02736|                     Store (Local0, PWRS)
02737|                     If (LNotEqual (PWRS, CSFG))
02738|                     {
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 2795
Line | AML source
--------------------------------------------------------------------------------
02792|             {
02793|                 If (ECON)
02794|                 {
02795|                     If (^^PCI0.LPCB.EC0.MBTS)
     |                                           ^
     | Error 6085: Object not found or not accessible from scope    (  PCI0.LPCB.EC0.MBTS)
02796|                     {
02797|                         Store (0x1F, B1ST)
02798|                     }
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 2816
Line | AML source
--------------------------------------------------------------------------------
02813|             {
02814|                 If (ECON)
02815|                 {
02816|                     If (^^PCI0.LPCB.EC0.MBTS)
     |                                           ^
     | Error 6085: Object not found or not accessible from scope    (  PCI0.LPCB.EC0.MBTS)
02817|                     {
02818|                         UPBI ()
02819|                     }
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 2837
Line | AML source
--------------------------------------------------------------------------------
02834|             {
02835|                 If (ECON)
02836|                 {
02837|                     If (^^PCI0.LPCB.EC0.MBTS)
     |                                           ^
     | Error 6085: Object not found or not accessible from scope    (  PCI0.LPCB.EC0.MBTS)
02838|                     {
02839|                         UPBS ()
02840|                     }
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 2856
Line | AML source
--------------------------------------------------------------------------------
02853| 
02854|             Method (UPBI, 0, NotSerialized)
02855|             {
02856|                 Store (^^PCI0.LPCB.EC0.MFCA, Local5)
     |                                          ^
     | Error 6085: Object not found or not accessible from scope    (  PCI0.LPCB.EC0.MFCA)
02857|                 If (LAnd (Local5, LNot (And (Local5, 0x8000))))
02858|                 {
02859|                     ShiftRight (Local5, 0x05, Local5)
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 2872
Line | AML source
--------------------------------------------------------------------------------
02869|                     Add (Local4, 0x02, FABL)
02870|                 }
02871| 
02872|                 Store (^^PCI0.LPCB.EC0.MFCA, Local0)
     |                                          ^
     | Error 6085: Object not found or not accessible from scope    (  PCI0.LPCB.EC0.MFCA)
02873|                 Store (Local0, Index (PBIF, One))
02874|                 Store (^^PCI0.LPCB.EC0.BVLB, Local0)
02875|                 Store (^^PCI0.LPCB.EC0.BVHB, Local1)
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 2874
Line | AML source
--------------------------------------------------------------------------------
02871| 
02872|                 Store (^^PCI0.LPCB.EC0.MFCA, Local0)
02873|                 Store (Local0, Index (PBIF, One))
02874|                 Store (^^PCI0.LPCB.EC0.BVLB, Local0)
     |                                          ^
     | Error 6085: Object not found or not accessible from scope    (  PCI0.LPCB.EC0.BVLB)
02875|                 Store (^^PCI0.LPCB.EC0.BVHB, Local1)
02876|                 ShiftLeft (Local1, 0x08, Local1)
02877|                 Or (Local0, Local1, Local0)
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 2875
Line | AML source
--------------------------------------------------------------------------------
02872|                 Store (^^PCI0.LPCB.EC0.MFCA, Local0)
02873|                 Store (Local0, Index (PBIF, One))
02874|                 Store (^^PCI0.LPCB.EC0.BVLB, Local0)
02875|                 Store (^^PCI0.LPCB.EC0.BVHB, Local1)
     |                                          ^
     | Error 6085: Object not found or not accessible from scope    (  PCI0.LPCB.EC0.BVHB)
02876|                 ShiftLeft (Local1, 0x08, Local1)
02877|                 Or (Local0, Local1, Local0)
02878|                 Store (Local0, Index (PBIF, 0x04))
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 2907
Line | AML source
--------------------------------------------------------------------------------
02904|             Method (UPBS, 0, NotSerialized)
02905|             {
02906|                 Store (Zero, Index (PBST, One))
02907|                 Store (^^PCI0.LPCB.EC0.MBRM, Local5)
     |                                          ^
     | Error 6085: Object not found or not accessible from scope    (  PCI0.LPCB.EC0.MBRM)
02908|                 If (LNot (And (Local5, 0x8000)))
02909|                 {
02910|                     ShiftRight (Local5, 0x05, Local5)
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 2914
Line | AML source
--------------------------------------------------------------------------------
02911|                     ShiftLeft (Local5, 0x05, Local5)
02912|                     If (LNotEqual (Local5, DerefOf (Index (PBST, 0x02))))
02913|                     {
02914|                         If (LEqual (^^PCI0.LPCB.EC0.BACR, One))
     |                                                       ^
     | Error 6085: Object not found or not accessible from scope    (  PCI0.LPCB.EC0.BACR)
02915|                         {
02916|                             Store (FABL, Index (PBST, 0x02))
02917|                             Store (One, ^^PCI0.LPCB.EC0.ORMR)
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 2917
Line | AML source
--------------------------------------------------------------------------------
02914|                         If (LEqual (^^PCI0.LPCB.EC0.BACR, One))
02915|                         {
02916|                             Store (FABL, Index (PBST, 0x02))
02917|                             Store (One, ^^PCI0.LPCB.EC0.ORMR)
     |                                                           ^
     | Error 6085: Object not found or not accessible from scope    (  PCI0.LPCB.EC0.ORMR)
02918|                         }
02919|                         Else
02920|                         {
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 2922
Line | AML source
--------------------------------------------------------------------------------
02919|                         Else
02920|                         {
02921|                             Store (Local5, Index (PBST, 0x02))
02922|                             Store (Zero, ^^PCI0.LPCB.EC0.ORMR)
     |                                                            ^
     | Error 6085: Object not found or not accessible from scope    (  PCI0.LPCB.EC0.ORMR)
02923|                         }
02924|                     }
02925|                 }
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 2927
Line | AML source
--------------------------------------------------------------------------------
02924|                     }
02925|                 }
02926| 
02927|                 Store (^^PCI0.LPCB.EC0.MBCV, Index (PBST, 0x03))
     |                                          ^
     | Error 6085: Object not found or not accessible from scope    (  PCI0.LPCB.EC0.MBCV)
02928|                 Store (^^PCI0.LPCB.EC0.MBST, Local5)
02929|                 Store (And (Local5, 0x07), Index (PBST, Zero))
02930|             }
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 2928
Line | AML source
--------------------------------------------------------------------------------
02925|                 }
02926| 
02927|                 Store (^^PCI0.LPCB.EC0.MBCV, Index (PBST, 0x03))
02928|                 Store (^^PCI0.LPCB.EC0.MBST, Local5)
     |                                          ^
     | Error 6085: Object not found or not accessible from scope    (  PCI0.LPCB.EC0.MBST)
02929|                 Store (And (Local5, 0x07), Index (PBST, Zero))
02930|             }
02931| 
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 2991
Line | AML source
--------------------------------------------------------------------------------
02988|             {
02989|                 If (ECON)
02990|                 {
02991|                     If (^^PCI0.LPCB.EC0.SBTS)
     |                                           ^
     | Error 6085: Object not found or not accessible from scope    (  PCI0.LPCB.EC0.SBTS)
02992|                     {
02993|                         Store (0x1F, B2ST)
02994|                     }
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 3012
Line | AML source
--------------------------------------------------------------------------------
03009|             {
03010|                 If (ECON)
03011|                 {
03012|                     If (^^PCI0.LPCB.EC0.SBTS)
     |                                           ^
     | Error 6085: Object not found or not accessible from scope    (  PCI0.LPCB.EC0.SBTS)
03013|                     {
03014|                         USBI ()
03015|                     }
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 3033
Line | AML source
--------------------------------------------------------------------------------
03030|             {
03031|                 If (ECON)
03032|                 {
03033|                     If (^^PCI0.LPCB.EC0.SBTS)
     |                                           ^
     | Error 6085: Object not found or not accessible from scope    (  PCI0.LPCB.EC0.SBTS)
03034|                     {
03035|                         USBS ()
03036|                     }
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 3052
Line | AML source
--------------------------------------------------------------------------------
03049| 
03050|             Method (USBI, 0, NotSerialized)
03051|             {
03052|                 Store (^^PCI0.LPCB.EC0.SFCA, Local5)
     |                                          ^
     | Error 6085: Object not found or not accessible from scope    (  PCI0.LPCB.EC0.SFCA)
03053|                 If (LAnd (Local5, LNot (And (Local5, 0x8000))))
03054|                 {
03055|                     ShiftRight (Local5, 0x05, Local5)
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 3068
Line | AML source
--------------------------------------------------------------------------------
03065|                     Add (Local4, 0x02, FABL)
03066|                 }
03067| 
03068|                 Store (^^PCI0.LPCB.EC0.SFCA, Index (SBIF, One))
     |                                          ^
     | Error 6085: Object not found or not accessible from scope    (  PCI0.LPCB.EC0.SFCA)
03069|                 Store (^^PCI0.LPCB.EC0.SDVT, Index (SBIF, 0x04))
03070|                 Store ("OANI$", Index (SBIF, 0x09))
03071|                 Store ("LION", Index (SBIF, 0x0B))
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 3069
Line | AML source
--------------------------------------------------------------------------------
03066|                 }
03067| 
03068|                 Store (^^PCI0.LPCB.EC0.SFCA, Index (SBIF, One))
03069|                 Store (^^PCI0.LPCB.EC0.SDVT, Index (SBIF, 0x04))
     |                                          ^
     | Error 6085: Object not found or not accessible from scope    (  PCI0.LPCB.EC0.SDVT)
03070|                 Store ("OANI$", Index (SBIF, 0x09))
03071|                 Store ("LION", Index (SBIF, 0x0B))
03072|                 Store ("Seconday", Index (SBIF, 0x09))
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 3098
Line | AML source
--------------------------------------------------------------------------------
03095|             Method (USBS, 0, NotSerialized)
03096|             {
03097|                 Store (Zero, Index (SBST, One))
03098|                 Store (^^PCI0.LPCB.EC0.SBRM, Local5)
     |                                          ^
     | Error 6085: Object not found or not accessible from scope    (  PCI0.LPCB.EC0.SBRM)
03099|                 If (LNot (And (Local5, 0x8000)))
03100|                 {
03101|                     ShiftRight (Local5, 0x05, Local5)
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 3105
Line | AML source
--------------------------------------------------------------------------------
03102|                     ShiftLeft (Local5, 0x05, Local5)
03103|                     If (LNotEqual (Local5, DerefOf (Index (SBST, 0x02))))
03104|                     {
03105|                         If (LEqual (^^PCI0.LPCB.EC0.BACR, One))
     |                                                       ^
     | Error 6085: Object not found or not accessible from scope    (  PCI0.LPCB.EC0.BACR)
03106|                         {
03107|                             Store (FABL, Index (SBST, 0x02))
03108|                             Store (One, ^^PCI0.LPCB.EC0.ORSR)
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 3108
Line | AML source
--------------------------------------------------------------------------------
03105|                         If (LEqual (^^PCI0.LPCB.EC0.BACR, One))
03106|                         {
03107|                             Store (FABL, Index (SBST, 0x02))
03108|                             Store (One, ^^PCI0.LPCB.EC0.ORSR)
     |                                                           ^
     | Error 6085: Object not found or not accessible from scope    (  PCI0.LPCB.EC0.ORSR)
03109|                         }
03110|                         Else
03111|                         {
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 3113
Line | AML source
--------------------------------------------------------------------------------
03110|                         Else
03111|                         {
03112|                             Store (Local5, Index (SBST, 0x02))
03113|                             Store (Zero, ^^PCI0.LPCB.EC0.ORSR)
     |                                                            ^
     | Error 6085: Object not found or not accessible from scope    (  PCI0.LPCB.EC0.ORSR)
03114|                         }
03115|                     }
03116|                 }
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 3118
Line | AML source
--------------------------------------------------------------------------------
03115|                     }
03116|                 }
03117| 
03118|                 Store (^^PCI0.LPCB.EC0.SBCV, Index (SBST, 0x03))
     |                                          ^
     | Error 6085: Object not found or not accessible from scope    (  PCI0.LPCB.EC0.SBCV)
03119|                 Store (^^PCI0.LPCB.EC0.MBST, Local5)
03120|                 ShiftRight (And (Local5, 0xF0), 0x04, Index (SBST, Zero))
03121|             }
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 3119
Line | AML source
--------------------------------------------------------------------------------
03116|                 }
03117| 
03118|                 Store (^^PCI0.LPCB.EC0.SBCV, Index (SBST, 0x03))
03119|                 Store (^^PCI0.LPCB.EC0.MBST, Local5)
     |                                          ^
     | Error 6085: Object not found or not accessible from scope    (  PCI0.LPCB.EC0.MBST)
03120|                 ShiftRight (And (Local5, 0xF0), 0x04, Index (SBST, Zero))
03121|             }
03122| 
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 3161
Line | AML source
--------------------------------------------------------------------------------
03158|             Name (_UID, Zero)  // _UID: Unique ID
03159|             Method (_PRT, 0, NotSerialized)  // _PRT: PCI Routing Table
03160|             {
03161|                 If (PICM)
     |                       ^
     | Error 6084: Object does not exist    (PICM)
03162|                 {
03163|                     Return (AR00)
03164|                 }
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_INVALID_ADDR_FLAGS: Test 1, Assembler error in line
3349
Line | AML source
--------------------------------------------------------------------------------
03346|                     0x00000000,         // Range Minimum
03347|                     0xFEBFFFFF,         // Range Maximum
03348|                     0x00000000,         // Translation Offset
03349|                     0x00000000,         // Length
     |                             ^
     | Error 6043: Invalid combination of Length and Min/Max fixed flags
03350|                     ,, _Y0D, AddressRangeMemory, TypeStatic)
03351|                 DWordMemory (ResourceProducer, PosDecode, MinFixed, MaxFixed, Cacheable, ReadWrite,
03352|                     0x00000000,         // Granularity
================================================================================

ADVICE: (for Error #6043, ASL_MSG_INVALID_ADDR_FLAGS): This occurs if the length
is zero and just one of the resource MIF/MAF flags are set, or the length is
non-zero and resource MIF/MAF flags are both set. These are illegal combinations
and need to be fixed. See section 6.4.3.5 Address Space Resource Descriptors of
the ACPI specification for more details.

FAILED [HIGH] AMLAsmASL_MSG_INVALID_ADDR_FLAGS: Test 1, Assembler error in line
3356
Line | AML source
--------------------------------------------------------------------------------
03353|                     0xFED40000,         // Range Minimum
03354|                     0xFED44FFF,         // Range Maximum
03355|                     0x00000000,         // Translation Offset
03356|                     0x00000000,         // Length
     |                             ^
     | Error 6043: Invalid combination of Length and Min/Max fixed flags
03357|                     ,, , AddressRangeMemory, TypeStatic)
03358|             })
03359|             Method (_CRS, 0, Serialized)  // _CRS: Current Resource Settings
================================================================================

ADVICE: (for Error #6043, ASL_MSG_INVALID_ADDR_FLAGS): This occurs if the length
is zero and just one of the resource MIF/MAF flags are set, or the length is
non-zero and resource MIF/MAF flags are both set. These are illegal combinations
and need to be fixed. See section 6.4.3.5 Address Space Resource Descriptors of
the ACPI specification for more details.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 3361
Line | AML source
--------------------------------------------------------------------------------
03358|             })
03359|             Method (_CRS, 0, Serialized)  // _CRS: Current Resource Settings
03360|             {
03361|                 If (^^CPBG.IMCH.PM1L)
     |                                   ^
     | Error 6085: Object not found or not accessible from scope    (  CPBG.IMCH.PM1L)
03362|                 {
03363|                     CreateDWordField (BUF0, \_SB.PCI0._Y00._LEN, C0LN)  // _LEN: Length
03364|                     Store (Zero, C0LN)
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 3367
Line | AML source
--------------------------------------------------------------------------------
03364|                     Store (Zero, C0LN)
03365|                 }
03366| 
03367|                 If (LEqual (^^CPBG.IMCH.PM1L, One))
     |                                           ^
     | Error 6085: Object not found or not accessible from scope    (  CPBG.IMCH.PM1L)
03368|                 {
03369|                     CreateBitField (BUF0, \_SB.PCI0._Y00._RW, C0RW)  // _RW_: Read-Write Status
03370|                     Store (Zero, C0RW)
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 3373
Line | AML source
--------------------------------------------------------------------------------
03370|                     Store (Zero, C0RW)
03371|                 }
03372| 
03373|                 If (^^CPBG.IMCH.PM1H)
     |                                   ^
     | Error 6085: Object not found or not accessible from scope    (  CPBG.IMCH.PM1H)
03374|                 {
03375|                     CreateDWordField (BUF0, \_SB.PCI0._Y01._LEN, C4LN)  // _LEN: Length
03376|                     Store (Zero, C4LN)
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 3379
Line | AML source
--------------------------------------------------------------------------------
03376|                     Store (Zero, C4LN)
03377|                 }
03378| 
03379|                 If (LEqual (^^CPBG.IMCH.PM1H, One))
     |                                           ^
     | Error 6085: Object not found or not accessible from scope    (  CPBG.IMCH.PM1H)
03380|                 {
03381|                     CreateBitField (BUF0, \_SB.PCI0._Y01._RW, C4RW)  // _RW_: Read-Write Status
03382|                     Store (Zero, C4RW)
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 3385
Line | AML source
--------------------------------------------------------------------------------
03382|                     Store (Zero, C4RW)
03383|                 }
03384| 
03385|                 If (^^CPBG.IMCH.PM2L)
     |                                   ^
     | Error 6085: Object not found or not accessible from scope    (  CPBG.IMCH.PM2L)
03386|                 {
03387|                     CreateDWordField (BUF0, \_SB.PCI0._Y02._LEN, C8LN)  // _LEN: Length
03388|                     Store (Zero, C8LN)
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 3391
Line | AML source
--------------------------------------------------------------------------------
03388|                     Store (Zero, C8LN)
03389|                 }
03390| 
03391|                 If (LEqual (^^CPBG.IMCH.PM2L, One))
     |                                           ^
     | Error 6085: Object not found or not accessible from scope    (  CPBG.IMCH.PM2L)
03392|                 {
03393|                     CreateBitField (BUF0, \_SB.PCI0._Y02._RW, C8RW)  // _RW_: Read-Write Status
03394|                     Store (Zero, C8RW)
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 3397
Line | AML source
--------------------------------------------------------------------------------
03394|                     Store (Zero, C8RW)
03395|                 }
03396| 
03397|                 If (^^CPBG.IMCH.PM2H)
     |                                   ^
     | Error 6085: Object not found or not accessible from scope    (  CPBG.IMCH.PM2H)
03398|                 {
03399|                     CreateDWordField (BUF0, \_SB.PCI0._Y03._LEN, CCLN)  // _LEN: Length
03400|                     Store (Zero, CCLN)
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 3403
Line | AML source
--------------------------------------------------------------------------------
03400|                     Store (Zero, CCLN)
03401|                 }
03402| 
03403|                 If (LEqual (^^CPBG.IMCH.PM2H, One))
     |                                           ^
     | Error 6085: Object not found or not accessible from scope    (  CPBG.IMCH.PM2H)
03404|                 {
03405|                     CreateBitField (BUF0, \_SB.PCI0._Y03._RW, CCRW)  // _RW_: Read-Write Status
03406|                     Store (Zero, CCRW)
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 3409
Line | AML source
--------------------------------------------------------------------------------
03406|                     Store (Zero, CCRW)
03407|                 }
03408| 
03409|                 If (^^CPBG.IMCH.PM3L)
     |                                   ^
     | Error 6085: Object not found or not accessible from scope    (  CPBG.IMCH.PM3L)
03410|                 {
03411|                     CreateDWordField (BUF0, \_SB.PCI0._Y04._LEN, D0LN)  // _LEN: Length
03412|                     Store (Zero, D0LN)
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 3415
Line | AML source
--------------------------------------------------------------------------------
03412|                     Store (Zero, D0LN)
03413|                 }
03414| 
03415|                 If (LEqual (^^CPBG.IMCH.PM3L, One))
     |                                           ^
     | Error 6085: Object not found or not accessible from scope    (  CPBG.IMCH.PM3L)
03416|                 {
03417|                     CreateBitField (BUF0, \_SB.PCI0._Y04._RW, D0RW)  // _RW_: Read-Write Status
03418|                     Store (Zero, D0RW)
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 3421
Line | AML source
--------------------------------------------------------------------------------
03418|                     Store (Zero, D0RW)
03419|                 }
03420| 
03421|                 If (^^CPBG.IMCH.PM3H)
     |                                   ^
     | Error 6085: Object not found or not accessible from scope    (  CPBG.IMCH.PM3H)
03422|                 {
03423|                     CreateDWordField (BUF0, \_SB.PCI0._Y05._LEN, D4LN)  // _LEN: Length
03424|                     Store (Zero, D4LN)
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 3427
Line | AML source
--------------------------------------------------------------------------------
03424|                     Store (Zero, D4LN)
03425|                 }
03426| 
03427|                 If (LEqual (^^CPBG.IMCH.PM3H, One))
     |                                           ^
     | Error 6085: Object not found or not accessible from scope    (  CPBG.IMCH.PM3H)
03428|                 {
03429|                     CreateBitField (BUF0, \_SB.PCI0._Y05._RW, D4RW)  // _RW_: Read-Write Status
03430|                     Store (Zero, D4RW)
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 3433
Line | AML source
--------------------------------------------------------------------------------
03430|                     Store (Zero, D4RW)
03431|                 }
03432| 
03433|                 If (^^CPBG.IMCH.PM4L)
     |                                   ^
     | Error 6085: Object not found or not accessible from scope    (  CPBG.IMCH.PM4L)
03434|                 {
03435|                     CreateDWordField (BUF0, \_SB.PCI0._Y06._LEN, D8LN)  // _LEN: Length
03436|                     Store (Zero, D8LN)
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 3439
Line | AML source
--------------------------------------------------------------------------------
03436|                     Store (Zero, D8LN)
03437|                 }
03438| 
03439|                 If (LEqual (^^CPBG.IMCH.PM4L, One))
     |                                           ^
     | Error 6085: Object not found or not accessible from scope    (  CPBG.IMCH.PM4L)
03440|                 {
03441|                     CreateBitField (BUF0, \_SB.PCI0._Y06._RW, D8RW)  // _RW_: Read-Write Status
03442|                     Store (Zero, D8RW)
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 3445
Line | AML source
--------------------------------------------------------------------------------
03442|                     Store (Zero, D8RW)
03443|                 }
03444| 
03445|                 If (^^CPBG.IMCH.PM4H)
     |                                   ^
     | Error 6085: Object not found or not accessible from scope    (  CPBG.IMCH.PM4H)
03446|                 {
03447|                     CreateDWordField (BUF0, \_SB.PCI0._Y07._LEN, DCLN)  // _LEN: Length
03448|                     Store (Zero, DCLN)
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 3451
Line | AML source
--------------------------------------------------------------------------------
03448|                     Store (Zero, DCLN)
03449|                 }
03450| 
03451|                 If (LEqual (^^CPBG.IMCH.PM4H, One))
     |                                           ^
     | Error 6085: Object not found or not accessible from scope    (  CPBG.IMCH.PM4H)
03452|                 {
03453|                     CreateBitField (BUF0, \_SB.PCI0._Y07._RW, DCRW)  // _RW_: Read-Write Status
03454|                     Store (Zero, DCRW)
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 3457
Line | AML source
--------------------------------------------------------------------------------
03454|                     Store (Zero, DCRW)
03455|                 }
03456| 
03457|                 If (^^CPBG.IMCH.PM5L)
     |                                   ^
     | Error 6085: Object not found or not accessible from scope    (  CPBG.IMCH.PM5L)
03458|                 {
03459|                     CreateDWordField (BUF0, \_SB.PCI0._Y08._LEN, E0LN)  // _LEN: Length
03460|                     Store (Zero, E0LN)
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 3463
Line | AML source
--------------------------------------------------------------------------------
03460|                     Store (Zero, E0LN)
03461|                 }
03462| 
03463|                 If (LEqual (^^CPBG.IMCH.PM5L, One))
     |                                           ^
     | Error 6085: Object not found or not accessible from scope    (  CPBG.IMCH.PM5L)
03464|                 {
03465|                     CreateBitField (BUF0, \_SB.PCI0._Y08._RW, E0RW)  // _RW_: Read-Write Status
03466|                     Store (Zero, E0RW)
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 3469
Line | AML source
--------------------------------------------------------------------------------
03466|                     Store (Zero, E0RW)
03467|                 }
03468| 
03469|                 If (^^CPBG.IMCH.PM5H)
     |                                   ^
     | Error 6085: Object not found or not accessible from scope    (  CPBG.IMCH.PM5H)
03470|                 {
03471|                     CreateDWordField (BUF0, \_SB.PCI0._Y09._LEN, E4LN)  // _LEN: Length
03472|                     Store (Zero, E4LN)
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 3475
Line | AML source
--------------------------------------------------------------------------------
03472|                     Store (Zero, E4LN)
03473|                 }
03474| 
03475|                 If (LEqual (^^CPBG.IMCH.PM5H, One))
     |                                           ^
     | Error 6085: Object not found or not accessible from scope    (  CPBG.IMCH.PM5H)
03476|                 {
03477|                     CreateBitField (BUF0, \_SB.PCI0._Y09._RW, E4RW)  // _RW_: Read-Write Status
03478|                     Store (Zero, E4RW)
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 3481
Line | AML source
--------------------------------------------------------------------------------
03478|                     Store (Zero, E4RW)
03479|                 }
03480| 
03481|                 If (^^CPBG.IMCH.PM6L)
     |                                   ^
     | Error 6085: Object not found or not accessible from scope    (  CPBG.IMCH.PM6L)
03482|                 {
03483|                     CreateDWordField (BUF0, \_SB.PCI0._Y0A._LEN, E8LN)  // _LEN: Length
03484|                     Store (Zero, E8LN)
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 3487
Line | AML source
--------------------------------------------------------------------------------
03484|                     Store (Zero, E8LN)
03485|                 }
03486| 
03487|                 If (LEqual (^^CPBG.IMCH.PM6L, One))
     |                                           ^
     | Error 6085: Object not found or not accessible from scope    (  CPBG.IMCH.PM6L)
03488|                 {
03489|                     CreateBitField (BUF0, \_SB.PCI0._Y0A._RW, E8RW)  // _RW_: Read-Write Status
03490|                     Store (Zero, E8RW)
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 3493
Line | AML source
--------------------------------------------------------------------------------
03490|                     Store (Zero, E8RW)
03491|                 }
03492| 
03493|                 If (^^CPBG.IMCH.PM6H)
     |                                   ^
     | Error 6085: Object not found or not accessible from scope    (  CPBG.IMCH.PM6H)
03494|                 {
03495|                     CreateDWordField (BUF0, \_SB.PCI0._Y0B._LEN, ECLN)  // _LEN: Length
03496|                     Store (Zero, ECLN)
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 3499
Line | AML source
--------------------------------------------------------------------------------
03496|                     Store (Zero, ECLN)
03497|                 }
03498| 
03499|                 If (LEqual (^^CPBG.IMCH.PM6H, One))
     |                                           ^
     | Error 6085: Object not found or not accessible from scope    (  CPBG.IMCH.PM6H)
03500|                 {
03501|                     CreateBitField (BUF0, \_SB.PCI0._Y0B._RW, ECRW)  // _RW_: Read-Write Status
03502|                     Store (Zero, ECRW)
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 3505
Line | AML source
--------------------------------------------------------------------------------
03502|                     Store (Zero, ECRW)
03503|                 }
03504| 
03505|                 If (^^CPBG.IMCH.PM0H)
     |                                   ^
     | Error 6085: Object not found or not accessible from scope    (  CPBG.IMCH.PM0H)
03506|                 {
03507|                     CreateDWordField (BUF0, \_SB.PCI0._Y0C._LEN, F0LN)  // _LEN: Length
03508|                     Store (Zero, F0LN)
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 3511
Line | AML source
--------------------------------------------------------------------------------
03508|                     Store (Zero, F0LN)
03509|                 }
03510| 
03511|                 If (LEqual (^^CPBG.IMCH.PM0H, One))
     |                                           ^
     | Error 6085: Object not found or not accessible from scope    (  CPBG.IMCH.PM0H)
03512|                 {
03513|                     CreateBitField (BUF0, \_SB.PCI0._Y0C._RW, F0RW)  // _RW_: Read-Write Status
03514|                     Store (Zero, F0RW)
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 3525
Line | AML source
--------------------------------------------------------------------------------
03522|                 {
03523|                     If (LGreaterEqual (PNHM, 0x000106E1))
03524|                     {
03525|                         Store (^IO10.TOLM, Local0)
     |                                        ^
     | Error 6085: Object not found or not accessible from scope    ( IO10.TOLM)
03526|                         ShiftLeft (Increment (Local0), 0x1A, M1MN)
03527|                     }
03528|                     Else
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_FOUND: Test 1, Assembler error in line 3530
Line | AML source
--------------------------------------------------------------------------------
03527|                     }
03528|                     Else
03529|                     {
03530|                         Store (^IIO0.TOLM, Local0)
     |                                        ^
     | Error 6085: Object not found or not accessible from scope    ( IIO0.TOLM)
03531|                         ShiftLeft (Increment (Local0), 0x1A, M1MN)
03532|                     }
03533|                 }
================================================================================

ADVICE: (for Error #6085, ASL_MSG_NOT_FOUND): The name referenced by Scope()
should exist, but does not; forward references for Scope() are not supported by
the Microsoft Windows ACPI interpreter.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 3564
Line | AML source
--------------------------------------------------------------------------------
03561|                     {
03562|                         If (And (CTRL, 0x02))
03563|                         {
03564|                             NHPG ()
     |                               ^
     | Error 6084: Object does not exist    (NHPG)
03565|                         }
03566| 
03567|                         If (And (CTRL, 0x04))
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 3569
Line | AML source
--------------------------------------------------------------------------------
03566| 
03567|                         If (And (CTRL, 0x04))
03568|                         {
03569|                             NPME ()
     |                               ^
     | Error 6084: Object does not exist    (NPME)
03570|                         }
03571|                     }
03572| 
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_SYNTAX: Test 1, Assembler error in line 4381
Line | AML source
--------------------------------------------------------------------------------
04378|                     BDDC,   2048
04379|                 }
04380| 
04381|                 If (CondRefOf (FPED))
     |                 ^
     | Error 6126: syntax error, unexpected PARSEOP_IF
04382|                 {
04383|                     FPED ()
04384|                 }
================================================================================

ADVICE: (for Error #6126, ASL_MSG_SYNTAX): The disassembled code cannot be
reassembled using the strict IASL compiler as it contains syntax errors.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4450
Line | AML source
--------------------------------------------------------------------------------
04447|                 {
04448|                     Method (GBDA, 0, Serialized)
04449|                     {
04450|                         If (LEqual (GESF, Zero))
     |                                       ^
     | Error 6084: Object does not exist    (GESF)
04451|                         {
04452|                             Store (0x0679, PARM)
04453|                             Store (Zero, GESF)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4452
Line | AML source
--------------------------------------------------------------------------------
04449|                     {
04450|                         If (LEqual (GESF, Zero))
04451|                         {
04452|                             Store (0x0679, PARM)
     |                                              ^
     | Error 6084: Object does not exist    (PARM)
04453|                             Store (Zero, GESF)
04454|                             Return (SUCC)
04455|                         }
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4453
Line | AML source
--------------------------------------------------------------------------------
04450|                         If (LEqual (GESF, Zero))
04451|                         {
04452|                             Store (0x0679, PARM)
04453|                             Store (Zero, GESF)
     |                                            ^
     | Error 6084: Object does not exist    (GESF)
04454|                             Return (SUCC)
04455|                         }
04456| 
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4457
Line | AML source
--------------------------------------------------------------------------------
04454|                             Return (SUCC)
04455|                         }
04456| 
04457|                         If (LEqual (GESF, One))
     |                                       ^
     | Error 6084: Object does not exist    (GESF)
04458|                         {
04459|                             Store (0x0240, PARM)
04460|                             Store (Zero, GESF)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4459
Line | AML source
--------------------------------------------------------------------------------
04456| 
04457|                         If (LEqual (GESF, One))
04458|                         {
04459|                             Store (0x0240, PARM)
     |                                              ^
     | Error 6084: Object does not exist    (PARM)
04460|                             Store (Zero, GESF)
04461|                             Return (SUCC)
04462|                         }
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4460
Line | AML source
--------------------------------------------------------------------------------
04457|                         If (LEqual (GESF, One))
04458|                         {
04459|                             Store (0x0240, PARM)
04460|                             Store (Zero, GESF)
     |                                            ^
     | Error 6084: Object does not exist    (GESF)
04461|                             Return (SUCC)
04462|                         }
04463| 
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4464
Line | AML source
--------------------------------------------------------------------------------
04461|                             Return (SUCC)
04462|                         }
04463| 
04464|                         If (LEqual (GESF, 0x04))
     |                                       ^
     | Error 6084: Object does not exist    (GESF)
04465|                         {
04466|                             And (PARM, 0xEFFF0000, PARM)
04467|                             And (PARM, ShiftLeft (DerefOf (Index (DBTB, IBTT)), 0x10), 
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4466
Line | AML source
--------------------------------------------------------------------------------
04463| 
04464|                         If (LEqual (GESF, 0x04))
04465|                         {
04466|                             And (PARM, 0xEFFF0000, PARM)
     |                                    ^
     | Error 6084: Object does not exist    (PARM)
04467|                             And (PARM, ShiftLeft (DerefOf (Index (DBTB, IBTT)), 0x10), 
04468|                                 PARM)
04469|                             Or (IBTT, PARM, PARM)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4466
Line | AML source
--------------------------------------------------------------------------------
04463| 
04464|                         If (LEqual (GESF, 0x04))
04465|                         {
04466|                             And (PARM, 0xEFFF0000, PARM)
     |                                                      ^
     | Error 6084: Object does not exist    (PARM)
04467|                             And (PARM, ShiftLeft (DerefOf (Index (DBTB, IBTT)), 0x10), 
04468|                                 PARM)
04469|                             Or (IBTT, PARM, PARM)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4467
Line | AML source
--------------------------------------------------------------------------------
04464|                         If (LEqual (GESF, 0x04))
04465|                         {
04466|                             And (PARM, 0xEFFF0000, PARM)
04467|                             And (PARM, ShiftLeft (DerefOf (Index (DBTB, IBTT)), 0x10), 
     |                                    ^
     | Error 6084: Object does not exist    (PARM)
04468|                                 PARM)
04469|                             Or (IBTT, PARM, PARM)
04470|                             Store (Zero, GESF)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4468
Line | AML source
--------------------------------------------------------------------------------
04465|                         {
04466|                             And (PARM, 0xEFFF0000, PARM)
04467|                             And (PARM, ShiftLeft (DerefOf (Index (DBTB, IBTT)), 0x10), 
04468|                                 PARM)
     |                                   ^
     | Error 6084: Object does not exist    (PARM)
04469|                             Or (IBTT, PARM, PARM)
04470|                             Store (Zero, GESF)
04471|                             Return (SUCC)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4469
Line | AML source
--------------------------------------------------------------------------------
04466|                             And (PARM, 0xEFFF0000, PARM)
04467|                             And (PARM, ShiftLeft (DerefOf (Index (DBTB, IBTT)), 0x10), 
04468|                                 PARM)
04469|                             Or (IBTT, PARM, PARM)
     |                                         ^
     | Error 6084: Object does not exist    (PARM)
04470|                             Store (Zero, GESF)
04471|                             Return (SUCC)
04472|                         }
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4469
Line | AML source
--------------------------------------------------------------------------------
04466|                             And (PARM, 0xEFFF0000, PARM)
04467|                             And (PARM, ShiftLeft (DerefOf (Index (DBTB, IBTT)), 0x10), 
04468|                                 PARM)
04469|                             Or (IBTT, PARM, PARM)
     |                                               ^
     | Error 6084: Object does not exist    (PARM)
04470|                             Store (Zero, GESF)
04471|                             Return (SUCC)
04472|                         }
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4470
Line | AML source
--------------------------------------------------------------------------------
04467|                             And (PARM, ShiftLeft (DerefOf (Index (DBTB, IBTT)), 0x10), 
04468|                                 PARM)
04469|                             Or (IBTT, PARM, PARM)
04470|                             Store (Zero, GESF)
     |                                            ^
     | Error 6084: Object does not exist    (GESF)
04471|                             Return (SUCC)
04472|                         }
04473| 
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4474
Line | AML source
--------------------------------------------------------------------------------
04471|                             Return (SUCC)
04472|                         }
04473| 
04474|                         If (LEqual (GESF, 0x05))
     |                                       ^
     | Error 6084: Object does not exist    (GESF)
04475|                         {
04476|                             Store (IPSC, PARM)
04477|                             Or (PARM, ShiftLeft (IPAT, 0x08), PARM)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4476
Line | AML source
--------------------------------------------------------------------------------
04473| 
04474|                         If (LEqual (GESF, 0x05))
04475|                         {
04476|                             Store (IPSC, PARM)
     |                                            ^
     | Error 6084: Object does not exist    (PARM)
04477|                             Or (PARM, ShiftLeft (IPAT, 0x08), PARM)
04478|                             Add (PARM, 0x0100, PARM)
04479|                             Or (PARM, ShiftLeft (LIDS, 0x10), PARM)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4477
Line | AML source
--------------------------------------------------------------------------------
04474|                         If (LEqual (GESF, 0x05))
04475|                         {
04476|                             Store (IPSC, PARM)
04477|                             Or (PARM, ShiftLeft (IPAT, 0x08), PARM)
     |                                   ^
     | Error 6084: Object does not exist    (PARM)
04478|                             Add (PARM, 0x0100, PARM)
04479|                             Or (PARM, ShiftLeft (LIDS, 0x10), PARM)
04480|                             Add (PARM, 0x00010000, PARM)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4477
Line | AML source
--------------------------------------------------------------------------------
04474|                         If (LEqual (GESF, 0x05))
04475|                         {
04476|                             Store (IPSC, PARM)
04477|                             Or (PARM, ShiftLeft (IPAT, 0x08), PARM)
     |                                                                 ^
     | Error 6084: Object does not exist    (PARM)
04478|                             Add (PARM, 0x0100, PARM)
04479|                             Or (PARM, ShiftLeft (LIDS, 0x10), PARM)
04480|                             Add (PARM, 0x00010000, PARM)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4478
Line | AML source
--------------------------------------------------------------------------------
04475|                         {
04476|                             Store (IPSC, PARM)
04477|                             Or (PARM, ShiftLeft (IPAT, 0x08), PARM)
04478|                             Add (PARM, 0x0100, PARM)
     |                                    ^
     | Error 6084: Object does not exist    (PARM)
04479|                             Or (PARM, ShiftLeft (LIDS, 0x10), PARM)
04480|                             Add (PARM, 0x00010000, PARM)
04481|                             Or (PARM, ShiftLeft (IBIA, 0x14), PARM)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4478
Line | AML source
--------------------------------------------------------------------------------
04475|                         {
04476|                             Store (IPSC, PARM)
04477|                             Or (PARM, ShiftLeft (IPAT, 0x08), PARM)
04478|                             Add (PARM, 0x0100, PARM)
     |                                                  ^
     | Error 6084: Object does not exist    (PARM)
04479|                             Or (PARM, ShiftLeft (LIDS, 0x10), PARM)
04480|                             Add (PARM, 0x00010000, PARM)
04481|                             Or (PARM, ShiftLeft (IBIA, 0x14), PARM)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4479
Line | AML source
--------------------------------------------------------------------------------
04476|                             Store (IPSC, PARM)
04477|                             Or (PARM, ShiftLeft (IPAT, 0x08), PARM)
04478|                             Add (PARM, 0x0100, PARM)
04479|                             Or (PARM, ShiftLeft (LIDS, 0x10), PARM)
     |                                   ^
     | Error 6084: Object does not exist    (PARM)
04480|                             Add (PARM, 0x00010000, PARM)
04481|                             Or (PARM, ShiftLeft (IBIA, 0x14), PARM)
04482|                             Store (Zero, GESF)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4479
Line | AML source
--------------------------------------------------------------------------------
04476|                             Store (IPSC, PARM)
04477|                             Or (PARM, ShiftLeft (IPAT, 0x08), PARM)
04478|                             Add (PARM, 0x0100, PARM)
04479|                             Or (PARM, ShiftLeft (LIDS, 0x10), PARM)
     |                                                                 ^
     | Error 6084: Object does not exist    (PARM)
04480|                             Add (PARM, 0x00010000, PARM)
04481|                             Or (PARM, ShiftLeft (IBIA, 0x14), PARM)
04482|                             Store (Zero, GESF)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4480
Line | AML source
--------------------------------------------------------------------------------
04477|                             Or (PARM, ShiftLeft (IPAT, 0x08), PARM)
04478|                             Add (PARM, 0x0100, PARM)
04479|                             Or (PARM, ShiftLeft (LIDS, 0x10), PARM)
04480|                             Add (PARM, 0x00010000, PARM)
     |                                    ^
     | Error 6084: Object does not exist    (PARM)
04481|                             Or (PARM, ShiftLeft (IBIA, 0x14), PARM)
04482|                             Store (Zero, GESF)
04483|                             Return (SUCC)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4480
Line | AML source
--------------------------------------------------------------------------------
04477|                             Or (PARM, ShiftLeft (IPAT, 0x08), PARM)
04478|                             Add (PARM, 0x0100, PARM)
04479|                             Or (PARM, ShiftLeft (LIDS, 0x10), PARM)
04480|                             Add (PARM, 0x00010000, PARM)
     |                                                      ^
     | Error 6084: Object does not exist    (PARM)
04481|                             Or (PARM, ShiftLeft (IBIA, 0x14), PARM)
04482|                             Store (Zero, GESF)
04483|                             Return (SUCC)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4481
Line | AML source
--------------------------------------------------------------------------------
04478|                             Add (PARM, 0x0100, PARM)
04479|                             Or (PARM, ShiftLeft (LIDS, 0x10), PARM)
04480|                             Add (PARM, 0x00010000, PARM)
04481|                             Or (PARM, ShiftLeft (IBIA, 0x14), PARM)
     |                                   ^
     | Error 6084: Object does not exist    (PARM)
04482|                             Store (Zero, GESF)
04483|                             Return (SUCC)
04484|                         }
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4481
Line | AML source
--------------------------------------------------------------------------------
04478|                             Add (PARM, 0x0100, PARM)
04479|                             Or (PARM, ShiftLeft (LIDS, 0x10), PARM)
04480|                             Add (PARM, 0x00010000, PARM)
04481|                             Or (PARM, ShiftLeft (IBIA, 0x14), PARM)
     |                                                                 ^
     | Error 6084: Object does not exist    (PARM)
04482|                             Store (Zero, GESF)
04483|                             Return (SUCC)
04484|                         }
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4482
Line | AML source
--------------------------------------------------------------------------------
04479|                             Or (PARM, ShiftLeft (LIDS, 0x10), PARM)
04480|                             Add (PARM, 0x00010000, PARM)
04481|                             Or (PARM, ShiftLeft (IBIA, 0x14), PARM)
04482|                             Store (Zero, GESF)
     |                                            ^
     | Error 6084: Object does not exist    (GESF)
04483|                             Return (SUCC)
04484|                         }
04485| 
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4486
Line | AML source
--------------------------------------------------------------------------------
04483|                             Return (SUCC)
04484|                         }
04485| 
04486|                         If (LEqual (GESF, 0x06))
     |                                       ^
     | Error 6084: Object does not exist    (GESF)
04487|                         {
04488|                             Store (ITVF, PARM)
04489|                             Or (PARM, ShiftLeft (ITVM, 0x04), PARM)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4488
Line | AML source
--------------------------------------------------------------------------------
04485| 
04486|                         If (LEqual (GESF, 0x06))
04487|                         {
04488|                             Store (ITVF, PARM)
     |                                            ^
     | Error 6084: Object does not exist    (PARM)
04489|                             Or (PARM, ShiftLeft (ITVM, 0x04), PARM)
04490|                             Store (Zero, GESF)
04491|                             Return (SUCC)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4489
Line | AML source
--------------------------------------------------------------------------------
04486|                         If (LEqual (GESF, 0x06))
04487|                         {
04488|                             Store (ITVF, PARM)
04489|                             Or (PARM, ShiftLeft (ITVM, 0x04), PARM)
     |                                   ^
     | Error 6084: Object does not exist    (PARM)
04490|                             Store (Zero, GESF)
04491|                             Return (SUCC)
04492|                         }
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4489
Line | AML source
--------------------------------------------------------------------------------
04486|                         If (LEqual (GESF, 0x06))
04487|                         {
04488|                             Store (ITVF, PARM)
04489|                             Or (PARM, ShiftLeft (ITVM, 0x04), PARM)
     |                                                                 ^
     | Error 6084: Object does not exist    (PARM)
04490|                             Store (Zero, GESF)
04491|                             Return (SUCC)
04492|                         }
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4490
Line | AML source
--------------------------------------------------------------------------------
04487|                         {
04488|                             Store (ITVF, PARM)
04489|                             Or (PARM, ShiftLeft (ITVM, 0x04), PARM)
04490|                             Store (Zero, GESF)
     |                                            ^
     | Error 6084: Object does not exist    (GESF)
04491|                             Return (SUCC)
04492|                         }
04493| 
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4494
Line | AML source
--------------------------------------------------------------------------------
04491|                             Return (SUCC)
04492|                         }
04493| 
04494|                         If (LEqual (GESF, 0x07))
     |                                       ^
     | Error 6084: Object does not exist    (GESF)
04495|                         {
04496|                             Store (GIVD, PARM)
04497|                             XOr (PARM, One, PARM)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4496
Line | AML source
--------------------------------------------------------------------------------
04493| 
04494|                         If (LEqual (GESF, 0x07))
04495|                         {
04496|                             Store (GIVD, PARM)
     |                                      ^
     | Error 6084: Object does not exist    (GIVD)
04497|                             XOr (PARM, One, PARM)
04498|                             Or (PARM, ShiftLeft (GMFN, One), PARM)
04499|                             Or (PARM, 0x1800, PARM)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4496
Line | AML source
--------------------------------------------------------------------------------
04493| 
04494|                         If (LEqual (GESF, 0x07))
04495|                         {
04496|                             Store (GIVD, PARM)
     |                                            ^
     | Error 6084: Object does not exist    (PARM)
04497|                             XOr (PARM, One, PARM)
04498|                             Or (PARM, ShiftLeft (GMFN, One), PARM)
04499|                             Or (PARM, 0x1800, PARM)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4497
Line | AML source
--------------------------------------------------------------------------------
04494|                         If (LEqual (GESF, 0x07))
04495|                         {
04496|                             Store (GIVD, PARM)
04497|                             XOr (PARM, One, PARM)
     |                                    ^
     | Error 6084: Object does not exist    (PARM)
04498|                             Or (PARM, ShiftLeft (GMFN, One), PARM)
04499|                             Or (PARM, 0x1800, PARM)
04500|                             Or (PARM, ShiftLeft (IDMS, 0x11), PARM)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4497
Line | AML source
--------------------------------------------------------------------------------
04494|                         If (LEqual (GESF, 0x07))
04495|                         {
04496|                             Store (GIVD, PARM)
04497|                             XOr (PARM, One, PARM)
     |                                               ^
     | Error 6084: Object does not exist    (PARM)
04498|                             Or (PARM, ShiftLeft (GMFN, One), PARM)
04499|                             Or (PARM, 0x1800, PARM)
04500|                             Or (PARM, ShiftLeft (IDMS, 0x11), PARM)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4498
Line | AML source
--------------------------------------------------------------------------------
04495|                         {
04496|                             Store (GIVD, PARM)
04497|                             XOr (PARM, One, PARM)
04498|                             Or (PARM, ShiftLeft (GMFN, One), PARM)
     |                                   ^
     | Error 6084: Object does not exist    (PARM)
04499|                             Or (PARM, 0x1800, PARM)
04500|                             Or (PARM, ShiftLeft (IDMS, 0x11), PARM)
04501|                             Or (ShiftLeft (DerefOf (Index (DerefOf (Index (CDCT, HVCO)), CDVL
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4498
Line | AML source
--------------------------------------------------------------------------------
04495|                         {
04496|                             Store (GIVD, PARM)
04497|                             XOr (PARM, One, PARM)
04498|                             Or (PARM, ShiftLeft (GMFN, One), PARM)
     |                                                    ^
     | Error 6084: Object does not exist    (GMFN)
04499|                             Or (PARM, 0x1800, PARM)
04500|                             Or (PARM, ShiftLeft (IDMS, 0x11), PARM)
04501|                             Or (ShiftLeft (DerefOf (Index (DerefOf (Index (CDCT, HVCO)), CDVL
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4498
Line | AML source
--------------------------------------------------------------------------------
04495|                         {
04496|                             Store (GIVD, PARM)
04497|                             XOr (PARM, One, PARM)
04498|                             Or (PARM, ShiftLeft (GMFN, One), PARM)
     |                                                                ^
     | Error 6084: Object does not exist    (PARM)
04499|                             Or (PARM, 0x1800, PARM)
04500|                             Or (PARM, ShiftLeft (IDMS, 0x11), PARM)
04501|                             Or (ShiftLeft (DerefOf (Index (DerefOf (Index (CDCT, HVCO)), CDVL
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4499
Line | AML source
--------------------------------------------------------------------------------
04496|                             Store (GIVD, PARM)
04497|                             XOr (PARM, One, PARM)
04498|                             Or (PARM, ShiftLeft (GMFN, One), PARM)
04499|                             Or (PARM, 0x1800, PARM)
     |                                   ^
     | Error 6084: Object does not exist    (PARM)
04500|                             Or (PARM, ShiftLeft (IDMS, 0x11), PARM)
04501|                             Or (ShiftLeft (DerefOf (Index (DerefOf (Index (CDCT, HVCO)), CDVL
04502|                                 )), 0x15), PARM, PARM)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4499
Line | AML source
--------------------------------------------------------------------------------
04496|                             Store (GIVD, PARM)
04497|                             XOr (PARM, One, PARM)
04498|                             Or (PARM, ShiftLeft (GMFN, One), PARM)
04499|                             Or (PARM, 0x1800, PARM)
     |                                                 ^
     | Error 6084: Object does not exist    (PARM)
04500|                             Or (PARM, ShiftLeft (IDMS, 0x11), PARM)
04501|                             Or (ShiftLeft (DerefOf (Index (DerefOf (Index (CDCT, HVCO)), CDVL
04502|                                 )), 0x15), PARM, PARM)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4500
Line | AML source
--------------------------------------------------------------------------------
04497|                             XOr (PARM, One, PARM)
04498|                             Or (PARM, ShiftLeft (GMFN, One), PARM)
04499|                             Or (PARM, 0x1800, PARM)
04500|                             Or (PARM, ShiftLeft (IDMS, 0x11), PARM)
     |                                   ^
     | Error 6084: Object does not exist    (PARM)
04501|                             Or (ShiftLeft (DerefOf (Index (DerefOf (Index (CDCT, HVCO)), CDVL
04502|                                 )), 0x15), PARM, PARM)
04503|                             Store (One, GESF)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4500
Line | AML source
--------------------------------------------------------------------------------
04497|                             XOr (PARM, One, PARM)
04498|                             Or (PARM, ShiftLeft (GMFN, One), PARM)
04499|                             Or (PARM, 0x1800, PARM)
04500|                             Or (PARM, ShiftLeft (IDMS, 0x11), PARM)
     |                                                                 ^
     | Error 6084: Object does not exist    (PARM)
04501|                             Or (ShiftLeft (DerefOf (Index (DerefOf (Index (CDCT, HVCO)), CDVL
04502|                                 )), 0x15), PARM, PARM)
04503|                             Store (One, GESF)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4501
Line | AML source
--------------------------------------------------------------------------------
04498|                             Or (PARM, ShiftLeft (GMFN, One), PARM)
04499|                             Or (PARM, 0x1800, PARM)
04500|                             Or (PARM, ShiftLeft (IDMS, 0x11), PARM)
04501|                             Or (ShiftLeft (DerefOf (Index (DerefOf (Index (CDCT, HVCO)), CDVL
     |                                                                                            ^
     | Error 6084: Object does not exist    (CDVL)
04502|                                 )), 0x15), PARM, PARM)
04503|                             Store (One, GESF)
04504|                             Return (SUCC)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4502
Line | AML source
--------------------------------------------------------------------------------
04499|                             Or (PARM, 0x1800, PARM)
04500|                             Or (PARM, ShiftLeft (IDMS, 0x11), PARM)
04501|                             Or (ShiftLeft (DerefOf (Index (DerefOf (Index (CDCT, HVCO)), CDVL
04502|                                 )), 0x15), PARM, PARM)
     |                                              ^
     | Error 6084: Object does not exist    (PARM)
04503|                             Store (One, GESF)
04504|                             Return (SUCC)
04505|                         }
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4502
Line | AML source
--------------------------------------------------------------------------------
04499|                             Or (PARM, 0x1800, PARM)
04500|                             Or (PARM, ShiftLeft (IDMS, 0x11), PARM)
04501|                             Or (ShiftLeft (DerefOf (Index (DerefOf (Index (CDCT, HVCO)), CDVL
04502|                                 )), 0x15), PARM, PARM)
     |                                                    ^
     | Error 6084: Object does not exist    (PARM)
04503|                             Store (One, GESF)
04504|                             Return (SUCC)
04505|                         }
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4503
Line | AML source
--------------------------------------------------------------------------------
04500|                             Or (PARM, ShiftLeft (IDMS, 0x11), PARM)
04501|                             Or (ShiftLeft (DerefOf (Index (DerefOf (Index (CDCT, HVCO)), CDVL
04502|                                 )), 0x15), PARM, PARM)
04503|                             Store (One, GESF)
     |                                           ^
     | Error 6084: Object does not exist    (GESF)
04504|                             Return (SUCC)
04505|                         }
04506| 
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4507
Line | AML source
--------------------------------------------------------------------------------
04504|                             Return (SUCC)
04505|                         }
04506| 
04507|                         If (LEqual (GESF, 0x0A))
     |                                       ^
     | Error 6084: Object does not exist    (GESF)
04508|                         {
04509|                             Store (Zero, PARM)
04510|                             If (ISSC)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4509
Line | AML source
--------------------------------------------------------------------------------
04506| 
04507|                         If (LEqual (GESF, 0x0A))
04508|                         {
04509|                             Store (Zero, PARM)
     |                                            ^
     | Error 6084: Object does not exist    (PARM)
04510|                             If (ISSC)
04511|                             {
04512|                                 Or (PARM, 0x03, PARM)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4512
Line | AML source
--------------------------------------------------------------------------------
04509|                             Store (Zero, PARM)
04510|                             If (ISSC)
04511|                             {
04512|                                 Or (PARM, 0x03, PARM)
     |                                       ^
     | Error 6084: Object does not exist    (PARM)
04513|                             }
04514| 
04515|                             Store (Zero, GESF)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4512
Line | AML source
--------------------------------------------------------------------------------
04509|                             Store (Zero, PARM)
04510|                             If (ISSC)
04511|                             {
04512|                                 Or (PARM, 0x03, PARM)
     |                                                   ^
     | Error 6084: Object does not exist    (PARM)
04513|                             }
04514| 
04515|                             Store (Zero, GESF)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4515
Line | AML source
--------------------------------------------------------------------------------
04512|                                 Or (PARM, 0x03, PARM)
04513|                             }
04514| 
04515|                             Store (Zero, GESF)
     |                                            ^
     | Error 6084: Object does not exist    (GESF)
04516|                             Return (SUCC)
04517|                         }
04518| 
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4519
Line | AML source
--------------------------------------------------------------------------------
04516|                             Return (SUCC)
04517|                         }
04518| 
04519|                         If (LEqual (GESF, 0x0B))
     |                                       ^
     | Error 6084: Object does not exist    (GESF)
04520|                         {
04521|                             Store (KSV0, PARM)
04522|                             Store (KSV1, GESF)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4521
Line | AML source
--------------------------------------------------------------------------------
04518| 
04519|                         If (LEqual (GESF, 0x0B))
04520|                         {
04521|                             Store (KSV0, PARM)
     |                                            ^
     | Error 6084: Object does not exist    (PARM)
04522|                             Store (KSV1, GESF)
04523|                             Return (SUCC)
04524|                         }
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4522
Line | AML source
--------------------------------------------------------------------------------
04519|                         If (LEqual (GESF, 0x0B))
04520|                         {
04521|                             Store (KSV0, PARM)
04522|                             Store (KSV1, GESF)
     |                                            ^
     | Error 6084: Object does not exist    (GESF)
04523|                             Return (SUCC)
04524|                         }
04525| 
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4526
Line | AML source
--------------------------------------------------------------------------------
04523|                             Return (SUCC)
04524|                         }
04525| 
04526|                         Store (Zero, GESF)
     |                                        ^
     | Error 6084: Object does not exist    (GESF)
04527|                         Return (CRIT)
04528|                     }
04529| 
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4532
Line | AML source
--------------------------------------------------------------------------------
04529| 
04530|                     Method (SBCB, 0, Serialized)
04531|                     {
04532|                         If (LEqual (GESF, Zero))
     |                                       ^
     | Error 6084: Object does not exist    (GESF)
04533|                         {
04534|                             Store (Zero, PARM)
04535|                             Store (0x000F87FD, PARM)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4534
Line | AML source
--------------------------------------------------------------------------------
04531|                     {
04532|                         If (LEqual (GESF, Zero))
04533|                         {
04534|                             Store (Zero, PARM)
     |                                            ^
     | Error 6084: Object does not exist    (PARM)
04535|                             Store (0x000F87FD, PARM)
04536|                             Store (Zero, GESF)
04537|                             Return (SUCC)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4535
Line | AML source
--------------------------------------------------------------------------------
04532|                         If (LEqual (GESF, Zero))
04533|                         {
04534|                             Store (Zero, PARM)
04535|                             Store (0x000F87FD, PARM)
     |                                                  ^
     | Error 6084: Object does not exist    (PARM)
04536|                             Store (Zero, GESF)
04537|                             Return (SUCC)
04538|                         }
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4536
Line | AML source
--------------------------------------------------------------------------------
04533|                         {
04534|                             Store (Zero, PARM)
04535|                             Store (0x000F87FD, PARM)
04536|                             Store (Zero, GESF)
     |                                            ^
     | Error 6084: Object does not exist    (GESF)
04537|                             Return (SUCC)
04538|                         }
04539| 
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4540
Line | AML source
--------------------------------------------------------------------------------
04537|                             Return (SUCC)
04538|                         }
04539| 
04540|                         If (LEqual (GESF, One))
     |                                       ^
     | Error 6084: Object does not exist    (GESF)
04541|                         {
04542|                             Store (Zero, GESF)
04543|                             Store (Zero, PARM)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4542
Line | AML source
--------------------------------------------------------------------------------
04539| 
04540|                         If (LEqual (GESF, One))
04541|                         {
04542|                             Store (Zero, GESF)
     |                                            ^
     | Error 6084: Object does not exist    (GESF)
04543|                             Store (Zero, PARM)
04544|                             Return (SUCC)
04545|                         }
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4543
Line | AML source
--------------------------------------------------------------------------------
04540|                         If (LEqual (GESF, One))
04541|                         {
04542|                             Store (Zero, GESF)
04543|                             Store (Zero, PARM)
     |                                            ^
     | Error 6084: Object does not exist    (PARM)
04544|                             Return (SUCC)
04545|                         }
04546| 
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4547
Line | AML source
--------------------------------------------------------------------------------
04544|                             Return (SUCC)
04545|                         }
04546| 
04547|                         If (LEqual (GESF, 0x03))
     |                                       ^
     | Error 6084: Object does not exist    (GESF)
04548|                         {
04549|                             Store (Zero, GESF)
04550|                             Store (Zero, PARM)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4549
Line | AML source
--------------------------------------------------------------------------------
04546| 
04547|                         If (LEqual (GESF, 0x03))
04548|                         {
04549|                             Store (Zero, GESF)
     |                                            ^
     | Error 6084: Object does not exist    (GESF)
04550|                             Store (Zero, PARM)
04551|                             Return (SUCC)
04552|                         }
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4550
Line | AML source
--------------------------------------------------------------------------------
04547|                         If (LEqual (GESF, 0x03))
04548|                         {
04549|                             Store (Zero, GESF)
04550|                             Store (Zero, PARM)
     |                                            ^
     | Error 6084: Object does not exist    (PARM)
04551|                             Return (SUCC)
04552|                         }
04553| 
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4554
Line | AML source
--------------------------------------------------------------------------------
04551|                             Return (SUCC)
04552|                         }
04553| 
04554|                         If (LEqual (GESF, 0x04))
     |                                       ^
     | Error 6084: Object does not exist    (GESF)
04555|                         {
04556|                             Store (Zero, GESF)
04557|                             Store (Zero, PARM)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4556
Line | AML source
--------------------------------------------------------------------------------
04553| 
04554|                         If (LEqual (GESF, 0x04))
04555|                         {
04556|                             Store (Zero, GESF)
     |                                            ^
     | Error 6084: Object does not exist    (GESF)
04557|                             Store (Zero, PARM)
04558|                             Return (SUCC)
04559|                         }
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4557
Line | AML source
--------------------------------------------------------------------------------
04554|                         If (LEqual (GESF, 0x04))
04555|                         {
04556|                             Store (Zero, GESF)
04557|                             Store (Zero, PARM)
     |                                            ^
     | Error 6084: Object does not exist    (PARM)
04558|                             Return (SUCC)
04559|                         }
04560| 
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4561
Line | AML source
--------------------------------------------------------------------------------
04558|                             Return (SUCC)
04559|                         }
04560| 
04561|                         If (LEqual (GESF, 0x05))
     |                                       ^
     | Error 6084: Object does not exist    (GESF)
04562|                         {
04563|                             Store (Zero, GESF)
04564|                             Store (Zero, PARM)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4563
Line | AML source
--------------------------------------------------------------------------------
04560| 
04561|                         If (LEqual (GESF, 0x05))
04562|                         {
04563|                             Store (Zero, GESF)
     |                                            ^
     | Error 6084: Object does not exist    (GESF)
04564|                             Store (Zero, PARM)
04565|                             Return (SUCC)
04566|                         }
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4564
Line | AML source
--------------------------------------------------------------------------------
04561|                         If (LEqual (GESF, 0x05))
04562|                         {
04563|                             Store (Zero, GESF)
04564|                             Store (Zero, PARM)
     |                                            ^
     | Error 6084: Object does not exist    (PARM)
04565|                             Return (SUCC)
04566|                         }
04567| 
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4568
Line | AML source
--------------------------------------------------------------------------------
04565|                             Return (SUCC)
04566|                         }
04567| 
04568|                         If (LEqual (GESF, 0x06))
     |                                       ^
     | Error 6084: Object does not exist    (GESF)
04569|                         {
04570|                             Store (And (PARM, 0x0F), ITVF)
04571|                             Store (ShiftRight (And (PARM, 0xF0), 0x04), ITVM)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4570
Line | AML source
--------------------------------------------------------------------------------
04567| 
04568|                         If (LEqual (GESF, 0x06))
04569|                         {
04570|                             Store (And (PARM, 0x0F), ITVF)
     |                                           ^
     | Error 6084: Object does not exist    (PARM)
04571|                             Store (ShiftRight (And (PARM, 0xF0), 0x04), ITVM)
04572|                             Store (Zero, GESF)
04573|                             Store (Zero, PARM)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4571
Line | AML source
--------------------------------------------------------------------------------
04568|                         If (LEqual (GESF, 0x06))
04569|                         {
04570|                             Store (And (PARM, 0x0F), ITVF)
04571|                             Store (ShiftRight (And (PARM, 0xF0), 0x04), ITVM)
     |                                                       ^
     | Error 6084: Object does not exist    (PARM)
04572|                             Store (Zero, GESF)
04573|                             Store (Zero, PARM)
04574|                             Return (SUCC)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4572
Line | AML source
--------------------------------------------------------------------------------
04569|                         {
04570|                             Store (And (PARM, 0x0F), ITVF)
04571|                             Store (ShiftRight (And (PARM, 0xF0), 0x04), ITVM)
04572|                             Store (Zero, GESF)
     |                                            ^
     | Error 6084: Object does not exist    (GESF)
04573|                             Store (Zero, PARM)
04574|                             Return (SUCC)
04575|                         }
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4573
Line | AML source
--------------------------------------------------------------------------------
04570|                             Store (And (PARM, 0x0F), ITVF)
04571|                             Store (ShiftRight (And (PARM, 0xF0), 0x04), ITVM)
04572|                             Store (Zero, GESF)
04573|                             Store (Zero, PARM)
     |                                            ^
     | Error 6084: Object does not exist    (PARM)
04574|                             Return (SUCC)
04575|                         }
04576| 
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4577
Line | AML source
--------------------------------------------------------------------------------
04574|                             Return (SUCC)
04575|                         }
04576| 
04577|                         If (LEqual (GESF, 0x07))
     |                                       ^
     | Error 6084: Object does not exist    (GESF)
04578|                         {
04579|                             If (LEqual (PARM, Zero))
04580|                             {
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4579
Line | AML source
--------------------------------------------------------------------------------
04576| 
04577|                         If (LEqual (GESF, 0x07))
04578|                         {
04579|                             If (LEqual (PARM, Zero))
     |                                           ^
     | Error 6084: Object does not exist    (PARM)
04580|                             {
04581|                                 Store (CLID, Local0)
04582|                                 If (And (0x80000000, Local0))
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4581
Line | AML source
--------------------------------------------------------------------------------
04578|                         {
04579|                             If (LEqual (PARM, Zero))
04580|                             {
04581|                                 Store (CLID, Local0)
     |                                          ^
     | Error 6084: Object does not exist    (CLID)
04582|                                 If (And (0x80000000, Local0))
04583|                                 {
04584|                                     And (CLID, 0x0F, CLID)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4584
Line | AML source
--------------------------------------------------------------------------------
04581|                                 Store (CLID, Local0)
04582|                                 If (And (0x80000000, Local0))
04583|                                 {
04584|                                     And (CLID, 0x0F, CLID)
     |                                            ^
     | Error 6084: Object does not exist    (CLID)
04585|                                     GLID (CLID)
04586|                                 }
04587|                             }
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4584
Line | AML source
--------------------------------------------------------------------------------
04581|                                 Store (CLID, Local0)
04582|                                 If (And (0x80000000, Local0))
04583|                                 {
04584|                                     And (CLID, 0x0F, CLID)
     |                                                        ^
     | Error 6084: Object does not exist    (CLID)
04585|                                     GLID (CLID)
04586|                                 }
04587|                             }
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4585
Line | AML source
--------------------------------------------------------------------------------
04582|                                 If (And (0x80000000, Local0))
04583|                                 {
04584|                                     And (CLID, 0x0F, CLID)
04585|                                     GLID (CLID)
     |                                             ^
     | Error 6084: Object does not exist    (CLID)
04586|                                 }
04587|                             }
04588| 
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4589
Line | AML source
--------------------------------------------------------------------------------
04586|                                 }
04587|                             }
04588| 
04589|                             Store (Zero, GESF)
     |                                            ^
     | Error 6084: Object does not exist    (GESF)
04590|                             Store (Zero, PARM)
04591|                             Return (SUCC)
04592|                         }
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4590
Line | AML source
--------------------------------------------------------------------------------
04587|                             }
04588| 
04589|                             Store (Zero, GESF)
04590|                             Store (Zero, PARM)
     |                                            ^
     | Error 6084: Object does not exist    (PARM)
04591|                             Return (SUCC)
04592|                         }
04593| 
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4594
Line | AML source
--------------------------------------------------------------------------------
04591|                             Return (SUCC)
04592|                         }
04593| 
04594|                         If (LEqual (GESF, 0x08))
     |                                       ^
     | Error 6084: Object does not exist    (GESF)
04595|                         {
04596|                             Store (Zero, GESF)
04597|                             Store (Zero, PARM)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4596
Line | AML source
--------------------------------------------------------------------------------
04593| 
04594|                         If (LEqual (GESF, 0x08))
04595|                         {
04596|                             Store (Zero, GESF)
     |                                            ^
     | Error 6084: Object does not exist    (GESF)
04597|                             Store (Zero, PARM)
04598|                             Return (SUCC)
04599|                         }
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4597
Line | AML source
--------------------------------------------------------------------------------
04594|                         If (LEqual (GESF, 0x08))
04595|                         {
04596|                             Store (Zero, GESF)
04597|                             Store (Zero, PARM)
     |                                            ^
     | Error 6084: Object does not exist    (PARM)
04598|                             Return (SUCC)
04599|                         }
04600| 
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4601
Line | AML source
--------------------------------------------------------------------------------
04598|                             Return (SUCC)
04599|                         }
04600| 
04601|                         If (LEqual (GESF, 0x09))
     |                                       ^
     | Error 6084: Object does not exist    (GESF)
04602|                         {
04603|                             And (PARM, 0xFF, IBTT)
04604|                             Store (Zero, GESF)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4603
Line | AML source
--------------------------------------------------------------------------------
04600| 
04601|                         If (LEqual (GESF, 0x09))
04602|                         {
04603|                             And (PARM, 0xFF, IBTT)
     |                                    ^
     | Error 6084: Object does not exist    (PARM)
04604|                             Store (Zero, GESF)
04605|                             Store (Zero, PARM)
04606|                             Return (SUCC)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4604
Line | AML source
--------------------------------------------------------------------------------
04601|                         If (LEqual (GESF, 0x09))
04602|                         {
04603|                             And (PARM, 0xFF, IBTT)
04604|                             Store (Zero, GESF)
     |                                            ^
     | Error 6084: Object does not exist    (GESF)
04605|                             Store (Zero, PARM)
04606|                             Return (SUCC)
04607|                         }
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4605
Line | AML source
--------------------------------------------------------------------------------
04602|                         {
04603|                             And (PARM, 0xFF, IBTT)
04604|                             Store (Zero, GESF)
04605|                             Store (Zero, PARM)
     |                                            ^
     | Error 6084: Object does not exist    (PARM)
04606|                             Return (SUCC)
04607|                         }
04608| 
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4609
Line | AML source
--------------------------------------------------------------------------------
04606|                             Return (SUCC)
04607|                         }
04608| 
04609|                         If (LEqual (GESF, 0x0A))
     |                                       ^
     | Error 6084: Object does not exist    (GESF)
04610|                         {
04611|                             And (PARM, 0xFF, IPSC)
04612|                             If (And (ShiftRight (PARM, 0x08), 0xFF))
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4611
Line | AML source
--------------------------------------------------------------------------------
04608| 
04609|                         If (LEqual (GESF, 0x0A))
04610|                         {
04611|                             And (PARM, 0xFF, IPSC)
     |                                    ^
     | Error 6084: Object does not exist    (PARM)
04612|                             If (And (ShiftRight (PARM, 0x08), 0xFF))
04613|                             {
04614|                                 And (ShiftRight (PARM, 0x08), 0xFF, IPAT)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4612
Line | AML source
--------------------------------------------------------------------------------
04609|                         If (LEqual (GESF, 0x0A))
04610|                         {
04611|                             And (PARM, 0xFF, IPSC)
04612|                             If (And (ShiftRight (PARM, 0x08), 0xFF))
     |                                                    ^
     | Error 6084: Object does not exist    (PARM)
04613|                             {
04614|                                 And (ShiftRight (PARM, 0x08), 0xFF, IPAT)
04615|                                 Decrement (IPAT)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4614
Line | AML source
--------------------------------------------------------------------------------
04611|                             And (PARM, 0xFF, IPSC)
04612|                             If (And (ShiftRight (PARM, 0x08), 0xFF))
04613|                             {
04614|                                 And (ShiftRight (PARM, 0x08), 0xFF, IPAT)
     |                                                    ^
     | Error 6084: Object does not exist    (PARM)
04615|                                 Decrement (IPAT)
04616|                             }
04617| 
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4618
Line | AML source
--------------------------------------------------------------------------------
04615|                                 Decrement (IPAT)
04616|                             }
04617| 
04618|                             And (ShiftRight (PARM, 0x14), 0x07, IBIA)
     |                                                ^
     | Error 6084: Object does not exist    (PARM)
04619|                             Store (Zero, GESF)
04620|                             Store (Zero, PARM)
04621|                             Return (SUCC)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4619
Line | AML source
--------------------------------------------------------------------------------
04616|                             }
04617| 
04618|                             And (ShiftRight (PARM, 0x14), 0x07, IBIA)
04619|                             Store (Zero, GESF)
     |                                            ^
     | Error 6084: Object does not exist    (GESF)
04620|                             Store (Zero, PARM)
04621|                             Return (SUCC)
04622|                         }
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4620
Line | AML source
--------------------------------------------------------------------------------
04617| 
04618|                             And (ShiftRight (PARM, 0x14), 0x07, IBIA)
04619|                             Store (Zero, GESF)
04620|                             Store (Zero, PARM)
     |                                            ^
     | Error 6084: Object does not exist    (PARM)
04621|                             Return (SUCC)
04622|                         }
04623| 
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4624
Line | AML source
--------------------------------------------------------------------------------
04621|                             Return (SUCC)
04622|                         }
04623| 
04624|                         If (LEqual (GESF, 0x0B))
     |                                       ^
     | Error 6084: Object does not exist    (GESF)
04625|                         {
04626|                             And (ShiftRight (PARM, One), One, IF1E)
04627|                             If (And (PARM, 0x0001E000))
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4626
Line | AML source
--------------------------------------------------------------------------------
04623| 
04624|                         If (LEqual (GESF, 0x0B))
04625|                         {
04626|                             And (ShiftRight (PARM, One), One, IF1E)
     |                                                ^
     | Error 6084: Object does not exist    (PARM)
04627|                             If (And (PARM, 0x0001E000))
04628|                             {
04629|                                 And (ShiftRight (PARM, 0x0D), 0x0F, IDMS)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4627
Line | AML source
--------------------------------------------------------------------------------
04624|                         If (LEqual (GESF, 0x0B))
04625|                         {
04626|                             And (ShiftRight (PARM, One), One, IF1E)
04627|                             If (And (PARM, 0x0001E000))
     |                                        ^
     | Error 6084: Object does not exist    (PARM)
04628|                             {
04629|                                 And (ShiftRight (PARM, 0x0D), 0x0F, IDMS)
04630|                             }
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4629
Line | AML source
--------------------------------------------------------------------------------
04626|                             And (ShiftRight (PARM, One), One, IF1E)
04627|                             If (And (PARM, 0x0001E000))
04628|                             {
04629|                                 And (ShiftRight (PARM, 0x0D), 0x0F, IDMS)
     |                                                    ^
     | Error 6084: Object does not exist    (PARM)
04630|                             }
04631|                             Else
04632|                             {
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4633
Line | AML source
--------------------------------------------------------------------------------
04630|                             }
04631|                             Else
04632|                             {
04633|                                 And (ShiftRight (PARM, 0x11), 0x0F, IDMS)
     |                                                    ^
     | Error 6084: Object does not exist    (PARM)
04634|                             }
04635| 
04636|                             Store (Zero, GESF)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4636
Line | AML source
--------------------------------------------------------------------------------
04633|                                 And (ShiftRight (PARM, 0x11), 0x0F, IDMS)
04634|                             }
04635| 
04636|                             Store (Zero, GESF)
     |                                            ^
     | Error 6084: Object does not exist    (GESF)
04637|                             Store (Zero, PARM)
04638|                             Return (SUCC)
04639|                         }
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4637
Line | AML source
--------------------------------------------------------------------------------
04634|                             }
04635| 
04636|                             Store (Zero, GESF)
04637|                             Store (Zero, PARM)
     |                                            ^
     | Error 6084: Object does not exist    (PARM)
04638|                             Return (SUCC)
04639|                         }
04640| 
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4641
Line | AML source
--------------------------------------------------------------------------------
04638|                             Return (SUCC)
04639|                         }
04640| 
04641|                         If (LEqual (GESF, 0x10))
     |                                       ^
     | Error 6084: Object does not exist    (GESF)
04642|                         {
04643|                             Store (Zero, GESF)
04644|                             Store (Zero, PARM)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4643
Line | AML source
--------------------------------------------------------------------------------
04640| 
04641|                         If (LEqual (GESF, 0x10))
04642|                         {
04643|                             Store (Zero, GESF)
     |                                            ^
     | Error 6084: Object does not exist    (GESF)
04644|                             Store (Zero, PARM)
04645|                             Return (SUCC)
04646|                         }
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4644
Line | AML source
--------------------------------------------------------------------------------
04641|                         If (LEqual (GESF, 0x10))
04642|                         {
04643|                             Store (Zero, GESF)
04644|                             Store (Zero, PARM)
     |                                            ^
     | Error 6084: Object does not exist    (PARM)
04645|                             Return (SUCC)
04646|                         }
04647| 
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4648
Line | AML source
--------------------------------------------------------------------------------
04645|                             Return (SUCC)
04646|                         }
04647| 
04648|                         If (LEqual (GESF, 0x11))
     |                                       ^
     | Error 6084: Object does not exist    (GESF)
04649|                         {
04650|                             Store (ShiftLeft (LIDS, 0x08), PARM)
04651|                             Add (PARM, 0x0100, PARM)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4650
Line | AML source
--------------------------------------------------------------------------------
04647| 
04648|                         If (LEqual (GESF, 0x11))
04649|                         {
04650|                             Store (ShiftLeft (LIDS, 0x08), PARM)
     |                                                              ^
     | Error 6084: Object does not exist    (PARM)
04651|                             Add (PARM, 0x0100, PARM)
04652|                             Store (Zero, GESF)
04653|                             Return (SUCC)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4651
Line | AML source
--------------------------------------------------------------------------------
04648|                         If (LEqual (GESF, 0x11))
04649|                         {
04650|                             Store (ShiftLeft (LIDS, 0x08), PARM)
04651|                             Add (PARM, 0x0100, PARM)
     |                                    ^
     | Error 6084: Object does not exist    (PARM)
04652|                             Store (Zero, GESF)
04653|                             Return (SUCC)
04654|                         }
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4651
Line | AML source
--------------------------------------------------------------------------------
04648|                         If (LEqual (GESF, 0x11))
04649|                         {
04650|                             Store (ShiftLeft (LIDS, 0x08), PARM)
04651|                             Add (PARM, 0x0100, PARM)
     |                                                  ^
     | Error 6084: Object does not exist    (PARM)
04652|                             Store (Zero, GESF)
04653|                             Return (SUCC)
04654|                         }
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4652
Line | AML source
--------------------------------------------------------------------------------
04649|                         {
04650|                             Store (ShiftLeft (LIDS, 0x08), PARM)
04651|                             Add (PARM, 0x0100, PARM)
04652|                             Store (Zero, GESF)
     |                                            ^
     | Error 6084: Object does not exist    (GESF)
04653|                             Return (SUCC)
04654|                         }
04655| 
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4656
Line | AML source
--------------------------------------------------------------------------------
04653|                             Return (SUCC)
04654|                         }
04655| 
04656|                         If (LEqual (GESF, 0x12))
     |                                       ^
     | Error 6084: Object does not exist    (GESF)
04657|                         {
04658|                             If (And (PARM, One))
04659|                             {
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4658
Line | AML source
--------------------------------------------------------------------------------
04655| 
04656|                         If (LEqual (GESF, 0x12))
04657|                         {
04658|                             If (And (PARM, One))
     |                                        ^
     | Error 6084: Object does not exist    (PARM)
04659|                             {
04660|                                 If (LEqual (ShiftRight (PARM, One), One))
04661|                                 {
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4660
Line | AML source
--------------------------------------------------------------------------------
04657|                         {
04658|                             If (And (PARM, One))
04659|                             {
04660|                                 If (LEqual (ShiftRight (PARM, One), One))
     |                                                           ^
     | Error 6084: Object does not exist    (PARM)
04661|                                 {
04662|                                     Store (One, ISSC)
04663|                                 }
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4666
Line | AML source
--------------------------------------------------------------------------------
04663|                                 }
04664|                                 Else
04665|                                 {
04666|                                     Store (Zero, GESF)
     |                                                    ^
     | Error 6084: Object does not exist    (GESF)
04667|                                     Return (CRIT)
04668|                                 }
04669|                             }
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4675
Line | AML source
--------------------------------------------------------------------------------
04672|                                 Store (Zero, ISSC)
04673|                             }
04674| 
04675|                             Store (Zero, GESF)
     |                                            ^
     | Error 6084: Object does not exist    (GESF)
04676|                             Store (Zero, PARM)
04677|                             Return (SUCC)
04678|                         }
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4676
Line | AML source
--------------------------------------------------------------------------------
04673|                             }
04674| 
04675|                             Store (Zero, GESF)
04676|                             Store (Zero, PARM)
     |                                            ^
     | Error 6084: Object does not exist    (PARM)
04677|                             Return (SUCC)
04678|                         }
04679| 
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4680
Line | AML source
--------------------------------------------------------------------------------
04677|                             Return (SUCC)
04678|                         }
04679| 
04680|                         If (LEqual (GESF, 0x13))
     |                                       ^
     | Error 6084: Object does not exist    (GESF)
04681|                         {
04682|                             Store (Zero, GESF)
04683|                             Store (Zero, PARM)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4682
Line | AML source
--------------------------------------------------------------------------------
04679| 
04680|                         If (LEqual (GESF, 0x13))
04681|                         {
04682|                             Store (Zero, GESF)
     |                                            ^
     | Error 6084: Object does not exist    (GESF)
04683|                             Store (Zero, PARM)
04684|                             Return (SUCC)
04685|                         }
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4683
Line | AML source
--------------------------------------------------------------------------------
04680|                         If (LEqual (GESF, 0x13))
04681|                         {
04682|                             Store (Zero, GESF)
04683|                             Store (Zero, PARM)
     |                                            ^
     | Error 6084: Object does not exist    (PARM)
04684|                             Return (SUCC)
04685|                         }
04686| 
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4687
Line | AML source
--------------------------------------------------------------------------------
04684|                             Return (SUCC)
04685|                         }
04686| 
04687|                         If (LEqual (GESF, 0x14))
     |                                       ^
     | Error 6084: Object does not exist    (GESF)
04688|                         {
04689|                             And (PARM, 0x0F, PAVP)
04690|                             Store (Zero, GESF)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4689
Line | AML source
--------------------------------------------------------------------------------
04686| 
04687|                         If (LEqual (GESF, 0x14))
04688|                         {
04689|                             And (PARM, 0x0F, PAVP)
     |                                    ^
     | Error 6084: Object does not exist    (PARM)
04690|                             Store (Zero, GESF)
04691|                             Store (Zero, PARM)
04692|                             Return (SUCC)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4690
Line | AML source
--------------------------------------------------------------------------------
04687|                         If (LEqual (GESF, 0x14))
04688|                         {
04689|                             And (PARM, 0x0F, PAVP)
04690|                             Store (Zero, GESF)
     |                                            ^
     | Error 6084: Object does not exist    (GESF)
04691|                             Store (Zero, PARM)
04692|                             Return (SUCC)
04693|                         }
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4691
Line | AML source
--------------------------------------------------------------------------------
04688|                         {
04689|                             And (PARM, 0x0F, PAVP)
04690|                             Store (Zero, GESF)
04691|                             Store (Zero, PARM)
     |                                            ^
     | Error 6084: Object does not exist    (PARM)
04692|                             Return (SUCC)
04693|                         }
04694| 
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4695
Line | AML source
--------------------------------------------------------------------------------
04692|                             Return (SUCC)
04693|                         }
04694| 
04695|                         Store (Zero, GESF)
     |                                        ^
     | Error 6084: Object does not exist    (GESF)
04696|                         Return (SUCC)
04697|                     }
04698| 
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4699
Line | AML source
--------------------------------------------------------------------------------
04696|                         Return (SUCC)
04697|                     }
04698| 
04699|                     If (LEqual (GEFC, 0x04))
     |                                   ^
     | Error 6084: Object does not exist    (GEFC)
04700|                     {
04701|                         Store (GBDA (), GXFC)
04702|                     }
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4701
Line | AML source
--------------------------------------------------------------------------------
04698| 
04699|                     If (LEqual (GEFC, 0x04))
04700|                     {
04701|                         Store (GBDA (), GXFC)
     |                                           ^
     | Error 6084: Object does not exist    (GXFC)
04702|                     }
04703| 
04704|                     If (LEqual (GEFC, 0x06))
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4704
Line | AML source
--------------------------------------------------------------------------------
04701|                         Store (GBDA (), GXFC)
04702|                     }
04703| 
04704|                     If (LEqual (GEFC, 0x06))
     |                                   ^
     | Error 6084: Object does not exist    (GEFC)
04705|                     {
04706|                         Store (SBCB (), GXFC)
04707|                     }
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4706
Line | AML source
--------------------------------------------------------------------------------
04703| 
04704|                     If (LEqual (GEFC, 0x06))
04705|                     {
04706|                         Store (SBCB (), GXFC)
     |                                           ^
     | Error 6084: Object does not exist    (GXFC)
04707|                     }
04708| 
04709|                     Store (Zero, GEFC)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4709
Line | AML source
--------------------------------------------------------------------------------
04706|                         Store (SBCB (), GXFC)
04707|                     }
04708| 
04709|                     Store (Zero, GEFC)
     |                                    ^
     | Error 6084: Object does not exist    (GEFC)
04710|                     Store (One, SCIS)
04711|                     Store (Zero, GSSE)
04712|                     Store (Zero, SCIE)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4710
Line | AML source
--------------------------------------------------------------------------------
04707|                     }
04708| 
04709|                     Store (Zero, GEFC)
04710|                     Store (One, SCIS)
     |                                   ^
     | Error 6084: Object does not exist    (SCIS)
04711|                     Store (Zero, GSSE)
04712|                     Store (Zero, SCIE)
04713|                     Return (Zero)
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4711
Line | AML source
--------------------------------------------------------------------------------
04708| 
04709|                     Store (Zero, GEFC)
04710|                     Store (One, SCIS)
04711|                     Store (Zero, GSSE)
     |                                    ^
     | Error 6084: Object does not exist    (GSSE)
04712|                     Store (Zero, SCIE)
04713|                     Return (Zero)
04714|                 }
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4712
Line | AML source
--------------------------------------------------------------------------------
04709|                     Store (Zero, GEFC)
04710|                     Store (One, SCIS)
04711|                     Store (Zero, GSSE)
04712|                     Store (Zero, SCIE)
     |                                    ^
     | Error 6084: Object does not exist    (SCIE)
04713|                     Return (Zero)
04714|                 }
04715| 
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4718
Line | AML source
--------------------------------------------------------------------------------
04715| 
04716|                 Method (PDRD, 0, NotSerialized)
04717|                 {
04718|                     If (LNot (DRDY))
     |                                 ^
     | Error 6084: Object does not exist    (DRDY)
04719|                     {
04720|                         Sleep (ASLP)
04721|                     }
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_NOT_EXIST: Test 1, Assembler error in line 4720
Line | AML source
--------------------------------------------------------------------------------
04717|                 {
04718|                     If (LNot (DRDY))
04719|                     {
04720|                         Sleep (ASLP)
     |                                  ^
     | Error 6084: Object does not exist    (ASLP)
04721|                     }
04722| 
04723|                     Return (LNot (DRDY))
================================================================================

ADVICE: (for Error #6084, ASL_MSG_NOT_EXIST): The referenced object could not be
found during a name space lookup, it does not seem to exist.

FAILED [HIGH] AMLAsmASL_MSG_SYNTAX: Test 1, Assembler error in line 10258
Line | AML source
--------------------------------------------------------------------------------
10255|         }
10256|     }
10257| 
10258|     Scope (_PR)
     |        ^
     | Error 6126: syntax error, unexpected PARSEOP_SCOPE, expecting $end
10259|     {
10260|         Processor (CPU0, 0x01, 0x00000410, 0x06) {}
10261|         Processor (CPU1, 0x02, 0x00000410, 0x06) {}
================================================================================

ADVICE: (for Error #6126, ASL_MSG_SYNTAX): The disassembled code cannot be
reassembled using the strict IASL compiler as it contains syntax errors.

Table DSDT (0) reassembly: Found 201 errors, 0 warnings.


Test 2 of 2: Disassemble and reassemble SSDT

Checking ACPI table SSDT (#0)

PASSED: Test 2, SSDT (0) reassembly, Found 0 errors, 0 warnings.


Checking ACPI table SSDT (#1)

PASSED: Test 2, SSDT (1) reassembly, Found 0 errors, 0 warnings.


Checking ACPI table SSDT (#2)

PASSED: Test 2, SSDT (2) reassembly, Found 0 errors, 0 warnings.


Checking ACPI table SSDT (#3)

PASSED: Test 2, SSDT (3) reassembly, Found 0 errors, 0 warnings.


Checking ACPI table SSDT (#4)

FAILED [MEDIUM] AMLAsmASL_MSG_RESERVED_NO_RETURN_VAL: Test 2, Assembler warning
in line 68
Line | AML source
--------------------------------------------------------------------------------
00065|         {
00066|             Store (CPDC (Arg0), Local0)
00067|             GCAP (Local0)
00068|             Return (Local0)
     |                         ^
     | Warning 3104: Reserved method should not return a value (_PDC)
00069|         }
00070| 
00071|         Method (_OSC, 4, NotSerialized)  // _OSC: Operating System Capabilities
================================================================================

ADVICE: (for Warning #3104, ASL_MSG_RESERVED_NO_RETURN_VAL): A reserved method
returned a value however it is not expected to return anything, so this does not
conform to the expected behaviour. The kernel will most probably ignore the
return value, so this is not going to produce any run time errors.

FAILED [MEDIUM] AMLAsmASL_MSG_RESERVED_NO_RETURN_VAL: Test 2, Assembler warning
in line 182
Line | AML source
--------------------------------------------------------------------------------
00179|         {
00180|             Store (\_PR.CPU0.CPDC (Arg0), Local0)
00181|             GCAP (Local0)
00182|             Return (Local0)
     |                         ^
     | Warning 3104: Reserved method should not return a value (_PDC)
00183|         }
00184| 
00185|         Method (_OSC, 4, NotSerialized)  // _OSC: Operating System Capabilities
================================================================================

ADVICE: (for Warning #3104, ASL_MSG_RESERVED_NO_RETURN_VAL): A reserved method
returned a value however it is not expected to return anything, so this does not
conform to the expected behaviour. The kernel will most probably ignore the
return value, so this is not going to produce any run time errors.

FAILED [MEDIUM] AMLAsmASL_MSG_RESERVED_NO_RETURN_VAL: Test 2, Assembler warning
in line 252
Line | AML source
--------------------------------------------------------------------------------
00249|         {
00250|             Store (\_PR.CPU0.CPDC (Arg0), Local0)
00251|             GCAP (Local0)
00252|             Return (Local0)
     |                         ^
     | Warning 3104: Reserved method should not return a value (_PDC)
00253|         }
00254| 
00255|         Method (_OSC, 4, NotSerialized)  // _OSC: Operating System Capabilities
================================================================================

ADVICE: (for Warning #3104, ASL_MSG_RESERVED_NO_RETURN_VAL): A reserved method
returned a value however it is not expected to return anything, so this does not
conform to the expected behaviour. The kernel will most probably ignore the
return value, so this is not going to produce any run time errors.

FAILED [MEDIUM] AMLAsmASL_MSG_RESERVED_NO_RETURN_VAL: Test 2, Assembler warning
in line 298
Line | AML source
--------------------------------------------------------------------------------
00295|         {
00296|             Store (\_PR.CPU0.CPDC (Arg0), Local0)
00297|             GCAP (Local0)
00298|             Return (Local0)
     |                         ^
     | Warning 3104: Reserved method should not return a value (_PDC)
00299|         }
00300| 
00301|         Method (_OSC, 4, NotSerialized)  // _OSC: Operating System Capabilities
================================================================================

ADVICE: (for Warning #3104, ASL_MSG_RESERVED_NO_RETURN_VAL): A reserved method
returned a value however it is not expected to return anything, so this does not
conform to the expected behaviour. The kernel will most probably ignore the
return value, so this is not going to produce any run time errors.

FAILED [MEDIUM] AMLAsmASL_MSG_RESERVED_NO_RETURN_VAL: Test 2, Assembler warning
in line 344
Line | AML source
--------------------------------------------------------------------------------
00341|         {
00342|             Store (\_PR.CPU0.CPDC (Arg0), Local0)
00343|             GCAP (Local0)
00344|             Return (Local0)
     |                         ^
     | Warning 3104: Reserved method should not return a value (_PDC)
00345|         }
00346| 
00347|         Method (_OSC, 4, NotSerialized)  // _OSC: Operating System Capabilities
================================================================================

ADVICE: (for Warning #3104, ASL_MSG_RESERVED_NO_RETURN_VAL): A reserved method
returned a value however it is not expected to return anything, so this does not
conform to the expected behaviour. The kernel will most probably ignore the
return value, so this is not going to produce any run time errors.

FAILED [MEDIUM] AMLAsmASL_MSG_RESERVED_NO_RETURN_VAL: Test 2, Assembler warning
in line 390
Line | AML source
--------------------------------------------------------------------------------
00387|         {
00388|             Store (\_PR.CPU0.CPDC (Arg0), Local0)
00389|             GCAP (Local0)
00390|             Return (Local0)
     |                         ^
     | Warning 3104: Reserved method should not return a value (_PDC)
00391|         }
00392| 
00393|         Method (_OSC, 4, NotSerialized)  // _OSC: Operating System Capabilities
================================================================================

ADVICE: (for Warning #3104, ASL_MSG_RESERVED_NO_RETURN_VAL): A reserved method
returned a value however it is not expected to return anything, so this does not
conform to the expected behaviour. The kernel will most probably ignore the
return value, so this is not going to produce any run time errors.

FAILED [MEDIUM] AMLAsmASL_MSG_RESERVED_NO_RETURN_VAL: Test 2, Assembler warning
in line 436
Line | AML source
--------------------------------------------------------------------------------
00433|         {
00434|             Store (\_PR.CPU0.CPDC (Arg0), Local0)
00435|             GCAP (Local0)
00436|             Return (Local0)
     |                         ^
     | Warning 3104: Reserved method should not return a value (_PDC)
00437|         }
00438| 
00439|         Method (_OSC, 4, NotSerialized)  // _OSC: Operating System Capabilities
================================================================================

ADVICE: (for Warning #3104, ASL_MSG_RESERVED_NO_RETURN_VAL): A reserved method
returned a value however it is not expected to return anything, so this does not
conform to the expected behaviour. The kernel will most probably ignore the
return value, so this is not going to produce any run time errors.

FAILED [MEDIUM] AMLAsmASL_MSG_RESERVED_NO_RETURN_VAL: Test 2, Assembler warning
in line 482
Line | AML source
--------------------------------------------------------------------------------
00479|         {
00480|             Store (\_PR.CPU0.CPDC (Arg0), Local0)
00481|             GCAP (Local0)
00482|             Return (Local0)
     |                         ^
     | Warning 3104: Reserved method should not return a value (_PDC)
00483|         }
00484| 
00485|         Method (_OSC, 4, NotSerialized)  // _OSC: Operating System Capabilities
================================================================================

ADVICE: (for Warning #3104, ASL_MSG_RESERVED_NO_RETURN_VAL): A reserved method
returned a value however it is not expected to return anything, so this does not
conform to the expected behaviour. The kernel will most probably ignore the
return value, so this is not going to produce any run time errors.

Table SSDT (4) reassembly: Found 0 errors, 8 warnings.


================================================================================
4 passed, 209 failed, 0 warnings, 0 aborted, 0 skipped, 0 info only.
================================================================================

pcc: Processor Clocking Control (PCC) Test.
--------------------------------------------------------------------------------
Test 1 of 1: Check PCCH.
This test checks the sanity of the Processor Clocking Control as found on some
HP ProLiant machines. Most computers do not use this interface to control the
CPU clock frequency, so this test will be skipped.

This machine does not use Processor Clocking Control (PCC).

================================================================================
0 passed, 0 failed, 0 warnings, 0 aborted, 0 skipped, 1 info only.
================================================================================

osilinux: Disassemble DSDT to check for _OSI("Linux").
--------------------------------------------------------------------------------
Test 1 of 1: Disassemble DSDT to check for _OSI("Linux").
This is not strictly a failure mode, it just alerts one that this has been
defined in the DSDT and probably should be avoided since the Linux ACPI driver
matches onto the Windows _OSI strings
            {
                If (_OSI ("Linux"))
                {
                    Store (0x03E8, OSYS)
                }
                If (_OSI ("Windows 2001"))
                {
                    Store (0x07D1, OSYS)
                }
                If (_OSI ("Windows 2001 SP1"))
                {
                    Store (0x07D1, OSYS)
                }
                If (_OSI ("Windows 2001 SP2"))
                {
                    Store (0x07D2, OSYS)
                }
                If (_OSI ("Windows 2006"))
                {
                    Store (0x07D6, OSYS)
                }
                If (_OSI ("Windows 2009"))
                {
                    Store (0x07D9, OSYS)
                }
            }
WARNING: Test 1, DSDT implements a deprecated _OSI("Linux") test.

================================================================================
0 passed, 0 failed, 1 warnings, 0 aborted, 0 skipped, 0 info only.
================================================================================

method: ACPI DSDT Method Semantic Tests.
--------------------------------------------------------------------------------
Test 1 of 144: Check Method Names.
Found 2126 Objects 
PASSED: Test 1, Method names contain legal characters.

Test 2 of 144: Check _AEI.
SKIPPED: Test 2, Skipping test for non-existant object _AEI.

Test 3 of 144: Check _DDN (DOS Device Name).
SKIPPED: Test 3, Skipping test for non-existant object _DDN.

Test 4 of 144: Check _HID (Hardware ID).
PASSED: Test 4, \_SB_.PWRB._HID returned an integer 0x0c0cd041 (EISA ID
PNP0C0C).
PASSED: Test 4, \_SB_.LID0._HID returned an integer 0x0d0cd041 (EISA ID
PNP0C0D).
PASSED: Test 4, \_SB_.ACAD._HID returned a string 'ACPI0003' as expected.
PASSED: Test 4, \_SB_.BAT0._HID returned an integer 0x0a0cd041 (EISA ID
PNP0C0A).
PASSED: Test 4, \_SB_.BAT1._HID returned an integer 0x0a0cd041 (EISA ID
PNP0C0A).
PASSED: Test 4, \_SB_.PCI0._HID returned an integer 0x080ad041 (EISA ID
PNP0A08).
PASSED: Test 4, \_SB_.PCI0.LPCB.EC0_._HID returned an integer 0x090cd041 (EISA
ID PNP0C09).
PASSED: Test 4, \_SB_.PCI0.LPCB.EC0_.ALSD._HID returned a string 'ACPI0008' as
expected.
PASSED: Test 4, \_SB_.PCI0.LPCB.DMAC._HID returned an integer 0x0002d041 (EISA
ID PNP0200).
PASSED: Test 4, \_SB_.PCI0.LPCB.FWHD._HID returned an integer 0x0008d425 (EISA
ID INT0800).
PASSED: Test 4, \_SB_.PCI0.LPCB.HPET._HID returned an integer 0x0301d041 (EISA
ID PNP0103).
PASSED: Test 4, \_SB_.PCI0.LPCB.IPIC._HID returned an integer 0x0000d041 (EISA
ID PNP0000).
PASSED: Test 4, \_SB_.PCI0.LPCB.MATH._HID returned an integer 0x040cd041 (EISA
ID PNP0C04).
PASSED: Test 4, \_SB_.PCI0.LPCB.LDRC._HID returned an integer 0x020cd041 (EISA
ID PNP0C02).
PASSED: Test 4, \_SB_.PCI0.LPCB.RTC_._HID returned an integer 0x000bd041 (EISA
ID PNP0B00).
PASSED: Test 4, \_SB_.PCI0.LPCB.TIMR._HID returned an integer 0x0001d041 (EISA
ID PNP0100).
PASSED: Test 4, \_SB_.PCI0.LPCB.PS2K._HID returned an integer 0x0303d041 (EISA
ID PNP0303).
PASSED: Test 4, \_SB_.PCI0.LPCB.PS2M._HID returned a string 'SYN1E0D' as
expected.
PASSED: Test 4, \_SB_.PCI0.ACEL._HID returned an integer 0x04001122 (EISA ID
HPQ0004).
PASSED: Test 4, \_SB_.PCI0.PDRC._HID returned an integer 0x020cd041 (EISA ID
PNP0C02).
FAILED [MEDIUM] MethodHIDInvalidString: Test 4, \_SB_.PCI0.DOCK._HID returned a
string 'ABCDEFGH' but it was not a valid PNP ID or a valid ACPI ID.
PASSED: Test 4, \_SB_.PCI0.IEIT._HID returned an integer 0x0054d425 (EISA ID
INT5400).
PASSED: Test 4, \_SB_.LNKA._HID returned an integer 0x0f0cd041 (EISA ID
PNP0C0F).
PASSED: Test 4, \_SB_.LNKB._HID returned an integer 0x0f0cd041 (EISA ID
PNP0C0F).
PASSED: Test 4, \_SB_.LNKC._HID returned an integer 0x0f0cd041 (EISA ID
PNP0C0F).
PASSED: Test 4, \_SB_.LNKD._HID returned an integer 0x0f0cd041 (EISA ID
PNP0C0F).
PASSED: Test 4, \_SB_.LNKE._HID returned an integer 0x0f0cd041 (EISA ID
PNP0C0F).
PASSED: Test 4, \_SB_.LNKF._HID returned an integer 0x0f0cd041 (EISA ID
PNP0C0F).
PASSED: Test 4, \_SB_.LNKG._HID returned an integer 0x0f0cd041 (EISA ID
PNP0C0F).
PASSED: Test 4, \_SB_.LNKH._HID returned an integer 0x0f0cd041 (EISA ID
PNP0C0F).
PASSED: Test 4, \_SB_.WMID._HID returned a string 'PNP0C14' as expected.
PASSED: Test 4, \_SB_.QBTN._HID returned an integer 0x320cd041 (EISA ID
PNP0C32).
PASSED: Test 4, \_SB_.DBTN._HID returned an integer 0x320cd041 (EISA ID
PNP0C32).
PASSED: Test 4, \_SB_.MBTN._HID returned an integer 0x320cd041 (EISA ID
PNP0C32).
PASSED: Test 4, \_SB_.EBTN._HID returned an integer 0x320cd041 (EISA ID
PNP0C32).
PASSED: Test 4, \_SB_.PBTN._HID returned an integer 0x320cd041 (EISA ID
PNP0C32).
PASSED: Test 4, \_SB_.VBTN._HID returned an integer 0x320cd041 (EISA ID
PNP0C32).
PASSED: Test 4, \_SB_.TBTN._HID returned an integer 0x320cd041 (EISA ID
PNP0C32).
PASSED: Test 4, \_SB_.CPBG._HID returned an integer 0x030ad041 (EISA ID
PNP0A03).
PASSED: Test 4, \_SB_.PTID._HID returned an integer 0x0e34d425 (EISA ID
INT340E).

Test 5 of 144: Check _HRV (Hardware Revision Number).
SKIPPED: Test 5, Skipping test for non-existant object _HRV.

Test 6 of 144: Check _PLD (Physical Device Location).
PASSED: Test 6, \_SB_.PCI0.EHC1.RHUB.IHUB._PLD correctly returned a sane looking
package.
PASSED: Test 6, \_SB_.PCI0.EHC1.RHUB.IHUB.PRT3._PLD correctly returned a sane
looking package.
PASSED: Test 6, \_SB_.PCI0.EHC1.RHUB.IHUB.PRT5._PLD correctly returned a sane
looking package.
PASSED: Test 6, \_SB_.PCI0.EHC1.RHUB.IHUB.PRT6._PLD correctly returned a sane
looking package.

Test 7 of 144: Check _SUB (Subsystem ID).
SKIPPED: Test 7, Skipping test for non-existant object _SUB.

Test 8 of 144: Check _SUN (Slot User Number).
SKIPPED: Test 8, Skipping test for non-existant object _SUN.

Test 9 of 144: Check _STR (String).
SKIPPED: Test 9, Skipping test for non-existant object _STR.

Test 10 of 144: Check _UID (Unique ID).
PASSED: Test 10, \_SB_.BAT0._UID correctly returned sane looking value
0x00000001.
PASSED: Test 10, \_SB_.BAT1._UID correctly returned sane looking value
0x00000002.
PASSED: Test 10, \_SB_.PCI0._UID correctly returned sane looking value
0x00000000.
PASSED: Test 10, \_SB_.PCI0.LPCB.EC0_._UID correctly returned sane looking value
0x00000001.
PASSED: Test 10, \_SB_.PCI0.LPCB.HPET._UID correctly returned sane looking value
0x00000000.
PASSED: Test 10, \_SB_.PCI0.LPCB.LDRC._UID correctly returned sane looking value
0x00000002.
PASSED: Test 10, \_SB_.PCI0.PDRC._UID correctly returned sane looking value
0x00000001.
PASSED: Test 10, \_SB_.PCI0.DOCK._UID returned a string 'SADDLESTRING' as
expected.
PASSED: Test 10, \_SB_.PCI0.IEIT._UID correctly returned sane looking value
0x00000000.
PASSED: Test 10, \_SB_.LNKA._UID correctly returned sane looking value
0x00000001.
PASSED: Test 10, \_SB_.LNKB._UID correctly returned sane looking value
0x00000002.
PASSED: Test 10, \_SB_.LNKC._UID correctly returned sane looking value
0x00000003.
PASSED: Test 10, \_SB_.LNKD._UID correctly returned sane looking value
0x00000004.
PASSED: Test 10, \_SB_.LNKE._UID correctly returned sane looking value
0x00000005.
PASSED: Test 10, \_SB_.LNKF._UID correctly returned sane looking value
0x00000006.
PASSED: Test 10, \_SB_.LNKG._UID correctly returned sane looking value
0x00000007.
PASSED: Test 10, \_SB_.LNKH._UID correctly returned sane looking value
0x00000008.
PASSED: Test 10, \_SB_.WMID._UID correctly returned sane looking value
0x00000000.
PASSED: Test 10, \_SB_.QBTN._UID correctly returned sane looking value
0x00000001.
PASSED: Test 10, \_SB_.DBTN._UID correctly returned sane looking value
0x00000002.
PASSED: Test 10, \_SB_.MBTN._UID correctly returned sane looking value
0x00000003.
PASSED: Test 10, \_SB_.EBTN._UID correctly returned sane looking value
0x00000004.
PASSED: Test 10, \_SB_.PBTN._UID correctly returned sane looking value
0x00000006.
PASSED: Test 10, \_SB_.VBTN._UID correctly returned sane looking value
0x00000007.
PASSED: Test 10, \_SB_.TBTN._UID correctly returned sane looking value
0x00000008.
PASSED: Test 10, \_SB_.CPBG._UID correctly returned sane looking value
0x000000ff.

Test 11 of 144: Check _CRS (Current Resource Settings).
PASSED: Test 11, \_SB_.PCI0._CRS (WORD Address Space Descriptor) looks sane.
PASSED: Test 11, \_SB_.PCI0.LPCB.EC0_._CRS (I/O Port Descriptor) looks sane.
PASSED: Test 11, \_SB_.PCI0.LPCB.DMAC._CRS (I/O Port Descriptor) looks sane.
PASSED: Test 11, \_SB_.PCI0.LPCB.FWHD._CRS (32-bit Fixed Location Memory Range
Descriptor) looks sane.
PASSED: Test 11, \_SB_.PCI0.LPCB.HPET._CRS (32-bit Fixed Location Memory Range
Descriptor) looks sane.
PASSED: Test 11, \_SB_.PCI0.LPCB.IPIC._CRS (I/O Port Descriptor) looks sane.
PASSED: Test 11, \_SB_.PCI0.LPCB.MATH._CRS (I/O Port Descriptor) looks sane.
PASSED: Test 11, \_SB_.PCI0.LPCB.LDRC._CRS (I/O Port Descriptor) looks sane.
PASSED: Test 11, \_SB_.PCI0.LPCB.RTC_._CRS (I/O Port Descriptor) looks sane.
PASSED: Test 11, \_SB_.PCI0.LPCB.TIMR._CRS (I/O Port Descriptor) looks sane.
PASSED: Test 11, \_SB_.PCI0.LPCB.PS2K._CRS (I/O Port Descriptor) looks sane.
PASSED: Test 11, \_SB_.PCI0.LPCB.PS2M._CRS (IRQ Descriptor) looks sane.
PASSED: Test 11, \_SB_.PCI0.ACEL._CRS (Extended IRQ Descriptor) looks sane.
PASSED: Test 11, \_SB_.PCI0.PDRC._CRS (32-bit Fixed Location Memory Range
Descriptor) looks sane.
PASSED: Test 11, \_SB_.LNKA._CRS (IRQ Descriptor) looks sane.
PASSED: Test 11, \_SB_.LNKB._CRS (IRQ Descriptor) looks sane.
PASSED: Test 11, \_SB_.LNKC._CRS (IRQ Descriptor) looks sane.
PASSED: Test 11, \_SB_.LNKD._CRS (IRQ Descriptor) looks sane.
PASSED: Test 11, \_SB_.LNKE._CRS (IRQ Descriptor) looks sane.
PASSED: Test 11, \_SB_.LNKF._CRS (IRQ Descriptor) looks sane.
PASSED: Test 11, \_SB_.LNKG._CRS (IRQ Descriptor) looks sane.
PASSED: Test 11, \_SB_.LNKH._CRS (IRQ Descriptor) looks sane.
PASSED: Test 11, \_SB_.CPBG._CRS (WORD Address Space Descriptor) looks sane.

Test 12 of 144: Check _DIS (Disable).
PASSED: Test 12, \_SB_.LNKA._DIS returned no values as expected.
PASSED: Test 12, \_SB_.LNKB._DIS returned no values as expected.
PASSED: Test 12, \_SB_.LNKC._DIS returned no values as expected.
PASSED: Test 12, \_SB_.LNKD._DIS returned no values as expected.
PASSED: Test 12, \_SB_.LNKE._DIS returned no values as expected.
PASSED: Test 12, \_SB_.LNKF._DIS returned no values as expected.
PASSED: Test 12, \_SB_.LNKG._DIS returned no values as expected.
PASSED: Test 12, \_SB_.LNKH._DIS returned no values as expected.

Test 13 of 144: Check _DMA (Direct Memory Access).
SKIPPED: Test 13, Skipping test for non-existant object _DMA.

Test 14 of 144: Check _FIX (Fixed Register Resource Provider).
SKIPPED: Test 14, Skipping test for non-existant object _FIX.

Test 15 of 144: Check _GSB (Global System Interrupt Base).
SKIPPED: Test 15, Skipping test for non-existant object _GSB.

Test 16 of 144: Check _HPP (Hot Plug Parameters).
SKIPPED: Test 16, Skipping test for non-existant object _HPP.

Test 17 of 144: Check _PRS (Possible Resource Settings).
PASSED: Test 17, \_SB_.PCI0.LPCB.PS2K._PRS (Start Dependent Functions
Descriptor) looks sane.
PASSED: Test 17, \_SB_.LNKA._PRS (IRQ Descriptor) looks sane.
PASSED: Test 17, \_SB_.LNKB._PRS (IRQ Descriptor) looks sane.
PASSED: Test 17, \_SB_.LNKC._PRS (IRQ Descriptor) looks sane.
PASSED: Test 17, \_SB_.LNKD._PRS (IRQ Descriptor) looks sane.
PASSED: Test 17, \_SB_.LNKE._PRS (IRQ Descriptor) looks sane.
PASSED: Test 17, \_SB_.LNKF._PRS (IRQ Descriptor) looks sane.
PASSED: Test 17, \_SB_.LNKG._PRS (IRQ Descriptor) looks sane.
PASSED: Test 17, \_SB_.LNKH._PRS (IRQ Descriptor) looks sane.

Test 18 of 144: Check _PXM (Proximity).
SKIPPED: Test 18, Skipping test for non-existant object _PXM.

Test 19 of 144: Check _EDL (Eject Device List).
PASSED: Test 19, \_SB_.PCI0.DOCK._EDL correctly returned a sane looking package.

Test 20 of 144: Check _EJD (Ejection Dependent Device).
SKIPPED: Test 20, Skipping test for non-existant object _EJD.

Test 21 of 144: Check _EJ0 (Eject).
FAILED [MEDIUM] MethodShouldReturnNothing: Test 21, \_SB_.PCI0.DOCK._EJ0
returned values, but was expected to return nothing.
Object returned:
  INTEGER: 0x00000001

ADVICE: This probably won't cause any errors, but it should be fixed as the AML
code is not conforming to the expected behaviour as described in the ACPI
specification.


Test 22 of 144: Check _EJ1 (Eject).
SKIPPED: Test 22, Skipping test for non-existant object _EJ1.

Test 23 of 144: Check _EJ2 (Eject).
SKIPPED: Test 23, Skipping test for non-existant object _EJ2.

Test 24 of 144: Check _EJ3 (Eject).
SKIPPED: Test 24, Skipping test for non-existant object _EJ3.

Test 25 of 144: Check _EJ4 (Eject).
SKIPPED: Test 25, Skipping test for non-existant object _EJ4.

Test 26 of 144: Check _LCK (Lock).
SKIPPED: Test 26, Skipping test for non-existant object _LCK.

Test 27 of 144: Check _RMV (Remove).
SKIPPED: Test 27, Skipping test for non-existant object _RMV.

Test 28 of 144: Check _STA (Status).
PASSED: Test 28, \_SB_.ACAD._STA correctly returned sane looking value
0x0000000f.
PASSED: Test 28, \_SB_.BAT0._STA correctly returned sane looking value
0x0000000f.
PASSED: Test 28, \_SB_.BAT1._STA correctly returned sane looking value
0x0000000f.
PASSED: Test 28, \_SB_.PCI0.LPCB.EC0_.ALSD._STA correctly returned sane looking
value 0x00000000.
PASSED: Test 28, \_SB_.PCI0.LPCB.HPET._STA correctly returned sane looking value
0x00000000.
PASSED: Test 28, \_SB_.PCI0.LPCB.PS2M._STA correctly returned sane looking value
0x0000000f.
PASSED: Test 28, \_SB_.PCI0.RP02.PXS1._STA correctly returned sane looking value
0x0000000f.
PASSED: Test 28, \_SB_.PCI0.PEG3.VGA_._STA correctly returned sane looking value
0x0000000f.
PASSED: Test 28, \_SB_.PCI0.ACEL._STA correctly returned sane looking value
0x00000000.
PASSED: Test 28, \_SB_.PCI0.DOCK._STA correctly returned sane looking value
0x00000000.
PASSED: Test 28, \_SB_.PCI0.IEIT._STA correctly returned sane looking value
0x0000000f.
PASSED: Test 28, \_SB_.LNKA._STA correctly returned sane looking value
0x0000000b.
PASSED: Test 28, \_SB_.LNKB._STA correctly returned sane looking value
0x0000000b.
PASSED: Test 28, \_SB_.LNKC._STA correctly returned sane looking value
0x0000000b.
PASSED: Test 28, \_SB_.LNKD._STA correctly returned sane looking value
0x0000000b.
PASSED: Test 28, \_SB_.LNKE._STA correctly returned sane looking value
0x0000000b.
PASSED: Test 28, \_SB_.LNKF._STA correctly returned sane looking value
0x0000000b.
PASSED: Test 28, \_SB_.LNKG._STA correctly returned sane looking value
0x0000000b.
PASSED: Test 28, \_SB_.LNKH._STA correctly returned sane looking value
0x0000000b.
PASSED: Test 28, \_SB_.QBTN._STA correctly returned sane looking value
0x00000000.
PASSED: Test 28, \_SB_.DBTN._STA correctly returned sane looking value
0x00000000.
PASSED: Test 28, \_SB_.MBTN._STA correctly returned sane looking value
0x00000000.
PASSED: Test 28, \_SB_.EBTN._STA correctly returned sane looking value
0x00000000.
PASSED: Test 28, \_SB_.PBTN._STA correctly returned sane looking value
0x00000000.
PASSED: Test 28, \_SB_.VBTN._STA correctly returned sane looking value
0x00000000.
PASSED: Test 28, \_SB_.TBTN._STA correctly returned sane looking value
0x00000000.
PASSED: Test 28, \_SB_.PTID._STA correctly returned sane looking value
0x0000000f.

Test 29 of 144: Check _BDN (BIOS Dock Name).
SKIPPED: Test 29, Skipping test for non-existant object _BDN.

Test 30 of 144: Check _BBN (Base Bus Number).
PASSED: Test 30, \_SB_.PCI0._BBN correctly returned an integer.
PASSED: Test 30, \_SB_.CPBG._BBN correctly returned an integer.

Test 31 of 144: Check _DCK (Dock).
PASSED: Test 31, \_SB_.PCI0.DOCK._DCK correctly returned sane looking value
0x00000001.

PASSED: Test 31, \_SB_.PCI0.DOCK._DCK correctly returned sane looking value
0x00000001.


Test 32 of 144: Check _INI (Initialize).
PASSED: Test 32, \_SB_.PCI0.ACEL._INI returned no values as expected.
PASSED: Test 32, \_SB_.PCI0._INI returned no values as expected.

Test 33 of 144: Check _SEG (Segment).
SKIPPED: Test 33, Skipping test for non-existant object _SEG.

Test 34 of 144: Check _OFF (Set resource off).
SKIPPED: Test 34, Skipping test for non-existant object _OFF.

Test 35 of 144: Check _ON (Set resource on).
SKIPPED: Test 35, Skipping test for non-existant object _ON.

Test 36 of 144: Check _DSW (Device Sleep Wake).
SKIPPED: Test 36, Skipping test for non-existant object _DSW.

Test 37 of 144: Check _IRC (In Rush Current).
SKIPPED: Test 37, Skipping test for non-existant object _IRC.

Test 38 of 144: Check _PRE (Power Resources for Enumeration).
SKIPPED: Test 38, Skipping test for non-existant object _PRE.

Test 39 of 144: Check _PR0 (Power Resources for D0).
SKIPPED: Test 39, Skipping test for non-existant object _PR0.

Test 40 of 144: Check _PR1 (Power Resources for D1).
SKIPPED: Test 40, Skipping test for non-existant object _PR1.

Test 41 of 144: Check _PR2 (Power Resources for D2).
SKIPPED: Test 41, Skipping test for non-existant object _PR2.

Test 42 of 144: Check _PR3 (Power Resources for D3).
SKIPPED: Test 42, Skipping test for non-existant object _PR3.

Test 43 of 144: Check _PS0 (Power State 0).
PASSED: Test 43, \_SB_.PCI0.PEG3.VGA_._PS0 returned no values as expected.

Test 44 of 144: Check _PS1 (Power State 1).
SKIPPED: Test 44, Skipping test for non-existant object _PS1.

Test 45 of 144: Check _PS2 (Power State 2).
SKIPPED: Test 45, Skipping test for non-existant object _PS2.

Test 46 of 144: Check _PS3 (Power State 3).
PASSED: Test 46, \_SB_.PCI0.PEG3.VGA_._PS3 returned no values as expected.

Test 47 of 144: Check _PSC (Power State Current).
PASSED: Test 47, \_SB_.PCI0.PEG3.VGA_._PSC correctly returned an integer.

Test 48 of 144: Check _PSE (Power State for Enumeration).
SKIPPED: Test 48, Skipping test for non-existant object _PSE.

Test 49 of 144: Check _PSW (Power State Wake).
PASSED: Test 49, \_SB_.PCI0.LPCB.PS2K._PSW returned no values as expected.
PASSED: Test 49, \_SB_.PCI0.LPCB.PS2M._PSW returned no values as expected.
PASSED: Test 49, \_SB_.PCI0.EHC1._PSW returned no values as expected.
PASSED: Test 49, \_SB_.PCI0.RP02.PXS1._PSW returned no values as expected.

Test 50 of 144: Check _S1D (S1 Device State).
SKIPPED: Test 50, Skipping test for non-existant object _S1D.

Test 51 of 144: Check _S2D (S2 Device State).
SKIPPED: Test 51, Skipping test for non-existant object _S2D.

Test 52 of 144: Check _S3D (S3 Device State).
SKIPPED: Test 52, Skipping test for non-existant object _S3D.

Test 53 of 144: Check _S4D (S4 Device State).
SKIPPED: Test 53, Skipping test for non-existant object _S4D.

Test 54 of 144: Check _S0W (S0 Device Wake State).
SKIPPED: Test 54, Skipping test for non-existant object _S0W.

Test 55 of 144: Check _S1W (S1 Device Wake State).
SKIPPED: Test 55, Skipping test for non-existant object _S1W.

Test 56 of 144: Check _S2W (S2 Device Wake State).
SKIPPED: Test 56, Skipping test for non-existant object _S2W.

Test 57 of 144: Check _S3W (S3 Device Wake State).
SKIPPED: Test 57, Skipping test for non-existant object _S3W.

Test 58 of 144: Check _S4W (S4 Device Wake State).
SKIPPED: Test 58, Skipping test for non-existant object _S4W.

Test 59 of 144: Check _S0_ (S0 System State).
\_S0_ PM1a_CNT.SLP_TYP value: 0x00000000
\_S0_ PM1b_CNT.SLP_TYP value: 0x00000000
PASSED: Test 59, \_S0_ correctly returned a sane looking package.

Test 60 of 144: Check _S1_ (S1 System State).
SKIPPED: Test 60, Skipping test for non-existant object _S1_.

Test 61 of 144: Check _S2_ (S2 System State).
SKIPPED: Test 61, Skipping test for non-existant object _S2_.

Test 62 of 144: Check _S3_ (S3 System State).
SKIPPED: Test 62, Skipping test for non-existant object _S3_.

Test 63 of 144: Check _S4_ (S4 System State).
\_S4_ PM1a_CNT.SLP_TYP value: 0x00000006
\_S4_ PM1b_CNT.SLP_TYP value: 0x00000000
PASSED: Test 63, \_S4_ correctly returned a sane looking package.

Test 64 of 144: Check _S5_ (S5 System State).
\_S5_ PM1a_CNT.SLP_TYP value: 0x00000007
\_S5_ PM1b_CNT.SLP_TYP value: 0x00000000
PASSED: Test 64, \_S5_ correctly returned a sane looking package.

Test 65 of 144: Check _SWS (System Wake Source).
SKIPPED: Test 65, Skipping test for non-existant object _SWS.

Test 66 of 144: Check _PSS (Performance Supported States).
SKIPPED: Test 66, Skipping test for non-existant object _PSS.

Test 67 of 144: Check _CPC (Continuous Performance Control).
SKIPPED: Test 67, Skipping test for non-existant object _CPC.

Test 68 of 144: Check _CSD (C State Dependencies).
SKIPPED: Test 68, Skipping test for non-existant object _CSD.

Test 69 of 144: Check _CST (C States).
SKIPPED: Test 69, Skipping test for non-existant object _CST.

Test 70 of 144: Check _PCT (Performance Control).
SKIPPED: Test 70, Skipping test for non-existant object _PCT.

Test 71 of 144: Check _PDL (P-State Depth Limit).
SKIPPED: Test 71, Skipping test for non-existant object _PDL.

Test 72 of 144: Check _PPC (Performance Present Capabilities).
SKIPPED: Test 72, Skipping test for non-existant object _PPC.

Test 73 of 144: Check _PPE (Polling for Platform Error).
SKIPPED: Test 73, Skipping test for non-existant object _PPE.

Test 74 of 144: Check _TDL (T-State Depth Limit).
SKIPPED: Test 74, Skipping test for non-existant object _TDL.

Test 75 of 144: Check _TPC (Throttling Present Capabilities).
SKIPPED: Test 75, Skipping test for non-existant object _TPC.

Test 76 of 144: Check _TSD (Throttling State Dependencies).
SKIPPED: Test 76, Skipping test for non-existant object _TSD.

Test 77 of 144: Check _TSS (Throttling Supported States).
SKIPPED: Test 77, Skipping test for non-existant object _TSS.

Test 78 of 144: Check _ALC (Ambient Light Colour Chromaticity).
PASSED: Test 78, \_SB_.PCI0.LPCB.EC0_.ALSD._ALC correctly returned an integer.

Test 79 of 144: Check _ALI (Ambient Light Illuminance).
PASSED: Test 79, \_SB_.PCI0.LPCB.EC0_.ALSD._ALI correctly returned an integer.

Test 80 of 144: Check _ALT (Ambient Light Temperature).
PASSED: Test 80, \_SB_.PCI0.LPCB.EC0_.ALSD._ALT correctly returned an integer.

Test 81 of 144: Check _ALP (Ambient Light Polling). 
PASSED: Test 81, _ALP correctly returned sane looking value 4.800000 seconds

Test 82 of 144: Check _LID (Lid Status).
PASSED: Test 82, \_SB_.LID0._LID correctly returned sane looking value
0x00000000.

Test 83 of 144: Check _GCP (Get Capabilities).
SKIPPED: Test 83, Skipping test for non-existant object _GCP.

Test 84 of 144: Check _GRT (Get Real Time).
SKIPPED: Test 84, Skipping test for non-existant object _GRT.

Test 85 of 144: Check _GWS (Get Wake Status).
SKIPPED: Test 85, Skipping test for non-existant object _GWS.

Test 86 of 144: Check _STP (Set Expired Timer Wake Policy).
SKIPPED: Test 86, Skipping test for non-existant object _STP.

Test 87 of 144: Check _STV (Set Timer Value).
SKIPPED: Test 87, Skipping test for non-existant object _STV.

Test 88 of 144: Check _TIP (Expired Timer Wake Policy).
SKIPPED: Test 88, Skipping test for non-existant object _TIP.

Test 89 of 144: Check _TIV (Timer Values).
SKIPPED: Test 89, Skipping test for non-existant object _TIV.

Test 90 of 144: Check _SBS (Smart Battery Subsystem).
SKIPPED: Test 90, Skipping test for non-existant object _SBS.

Test 91 of 144: Check _BCT (Battery Charge Time).
SKIPPED: Test 91, Skipping test for non-existant object _BCT.

Test 92 of 144: Check _BIF (Battery Information).
PASSED: Test 92, \_SB_.BAT0._BIF correctly returned a sane looking package.
PASSED: Test 92, \_SB_.BAT1._BIF correctly returned a sane looking package.

Test 93 of 144: Check _BIX (Battery Information Extended).
SKIPPED: Test 93, Skipping test for non-existant object _BIX.

Test 94 of 144: Check _BMA (Battery Measurement Averaging).
SKIPPED: Test 94, Skipping test for non-existant object _BMA.

Test 95 of 144: Check _BMC (Battery Maintenance Control).
SKIPPED: Test 95, Skipping test for non-existant object _BMC.

Test 96 of 144: Check _BMD (Battery Maintenance Data).
SKIPPED: Test 96, Skipping test for non-existant object _BMD.

Test 97 of 144: Check _BMS (Battery Measurement Sampling Time).
SKIPPED: Test 97, Skipping test for non-existant object _BMS.

Test 98 of 144: Check _BST (Battery Status).
PASSED: Test 98, \_SB_.BAT0._BST correctly returned a sane looking package.
PASSED: Test 98, \_SB_.BAT1._BST correctly returned a sane looking package.

Test 99 of 144: Check _BTP (Battery Trip Point).
SKIPPED: Test 99, Skipping test for non-existant object _BTP.

Test 100 of 144: Check _BTM (Battery Time).
SKIPPED: Test 100, Skipping test for non-existant object _BTM.

Test 101 of 144: Check _PCL (Power Consumer List).

Test 102 of 144: Check _PIF (Power Source Information).
SKIPPED: Test 102, Skipping test for non-existant object _PIF.

Test 103 of 144: Check _PSR (Power Source).
PASSED: Test 103, \_SB_.ACAD._PSR correctly returned sane looking value
0x00000000.

Test 104 of 144: Check _FIF (Fan Information).
SKIPPED: Test 104, Skipping test for non-existant object _FIF.

Test 105 of 144: Check _FSL (Fan Set Level).
SKIPPED: Test 105, Skipping test for non-existant object _FSL.

Test 106 of 144: Check _FST (Fan Status).
SKIPPED: Test 106, Skipping test for non-existant object _FST.

Test 107 of 144: Check _ACx (Active Cooling).
SKIPPED: Test 107, Skipping test for non-existant object AC0.

SKIPPED: Test 107, Skipping test for non-existant object AC1.

SKIPPED: Test 107, Skipping test for non-existant object AC2.

SKIPPED: Test 107, Skipping test for non-existant object AC3.

SKIPPED: Test 107, Skipping test for non-existant object AC4.

SKIPPED: Test 107, Skipping test for non-existant object AC5.

SKIPPED: Test 107, Skipping test for non-existant object AC6.

SKIPPED: Test 107, Skipping test for non-existant object AC7.

SKIPPED: Test 107, Skipping test for non-existant object AC8.

SKIPPED: Test 107, Skipping test for non-existant object AC9.


Test 108 of 144: Check _CRT (Critical Trip Point).
FAILED [MEDIUM] MethodReturnNullObj: Test 108, \_TZ_.TZ01._CRT returned a NULL
object, and did not return ACPI_TYPE_INTEGER.

Test 109 of 144: Check _DTI (Device Temperature Indication).
SKIPPED: Test 109, Skipping test for non-existant object _DTI.

Test 110 of 144: Check _HOT (Hot Temperature).
FAILED [MEDIUM] MethodReturnNullObj: Test 110, \_TZ_.TZ01._HOT returned a NULL
object, and did not return ACPI_TYPE_INTEGER.

Test 111 of 144: Check _NTT (Notification Temp Threshold).
SKIPPED: Test 111, Skipping test for non-existant object _NTT.

Test 112 of 144: Check _PSV (Passive Temp).
FAILED [MEDIUM] MethodReturnNullObj: Test 112, \_TZ_.TZ01._PSV returned a NULL
object, and did not return ACPI_TYPE_INTEGER.

Test 113 of 144: Check _RTV (Relative Temp Values).
SKIPPED: Test 113, Skipping test for non-existant object _RTV.

Test 114 of 144: Check _SCP (Set Cooling Policy).
SKIPPED: Test 114, Skipping test for non-existant object _DTI.

Test 115 of 144: Check _TC1 (Thermal Constant 1).
PASSED: Test 115, _TC1 correctly returned sane looking value 0x00000002.

Test 116 of 144: Check _TC2 (Thermal Constant 2).
PASSED: Test 116, _TC1 correctly returned sane looking value 0x00000005.

Test 117 of 144: Check _TMP (Thermal Zone Current Temp).
ACPICA Exception AE_AML_UNINITIALIZED_LOCAL during execution of method OTHD
FAILED [HIGH] AEAMLUninitLocal: Test 117, Detected error 'Uninitialized local
variable' when evaluating '\_TZ_.TZ01._TMP'.

Test 118 of 144: Check _TPT (Trip Point Temperature).
SKIPPED: Test 118, Skipping test for non-existant object _TPT.

Test 119 of 144: Check _TSP (Thermal Sampling Period).
PASSED: Test 119, _TSP correctly returned sane looking value 5.000000 seconds

Test 120 of 144: Check _TST (Temperature Sensor Threshold).
SKIPPED: Test 120, Skipping test for non-existant object _TST.

Test 121 of 144: Check _TZP (Thermal Zone Polling).
SKIPPED: Test 121, Skipping test for non-existant object _TZP.

Test 122 of 144: Check _PTS (Prepare to Sleep).
Test _PTS(1).
ACPICA Exception AE_AML_INFINITE_LOOP during execution of method COMP
WARNING: Test 122, Detected an infinite loop when evaluating method '\_PTS'. 

ADVICE: This may occur because we are emulating the execution in this test
environment and cannot handshake with the embedded controller or jump to the
BIOS via SMIs. However, the fact that AML code spins forever means that lockup
conditions are not being checked for in the AML bytecode.


Test _PTS(2).
ACPICA Exception AE_AML_INFINITE_LOOP during execution of method COMP
WARNING: Test 122, Detected an infinite loop when evaluating method '\_PTS'. 

ADVICE: This may occur because we are emulating the execution in this test
environment and cannot handshake with the embedded controller or jump to the
BIOS via SMIs. However, the fact that AML code spins forever means that lockup
conditions are not being checked for in the AML bytecode.


Test _PTS(3).
ACPICA Exception AE_AML_INFINITE_LOOP during execution of method COMP
WARNING: Test 122, Detected an infinite loop when evaluating method '\_PTS'. 

ADVICE: This may occur because we are emulating the execution in this test
environment and cannot handshake with the embedded controller or jump to the
BIOS via SMIs. However, the fact that AML code spins forever means that lockup
conditions are not being checked for in the AML bytecode.


Test _PTS(4).
ACPICA Exception AE_AML_INFINITE_LOOP during execution of method COMP
WARNING: Test 122, Detected an infinite loop when evaluating method '\_PTS'. 

ADVICE: This may occur because we are emulating the execution in this test
environment and cannot handshake with the embedded controller or jump to the
BIOS via SMIs. However, the fact that AML code spins forever means that lockup
conditions are not being checked for in the AML bytecode.


Test _PTS(5).
ACPICA Exception AE_AML_INFINITE_LOOP during execution of method COMP
WARNING: Test 122, Detected an infinite loop when evaluating method '\_PTS'. 

ADVICE: This may occur because we are emulating the execution in this test
environment and cannot handshake with the embedded controller or jump to the
BIOS via SMIs. However, the fact that AML code spins forever means that lockup
conditions are not being checked for in the AML bytecode.



Test 123 of 144: Check _TTS (Transition to State).
SKIPPED: Test 123, Optional control method _TTS does not exist.

Test 124 of 144: Check _S0 (System S0 State).
SKIPPED: Test 124, Skipping test for non-existant object _S0.

Test 125 of 144: Check _S1 (System S1 State).
SKIPPED: Test 125, Skipping test for non-existant object _S1.

Test 126 of 144: Check _S2 (System S2 State).
SKIPPED: Test 126, Skipping test for non-existant object _S2.

Test 127 of 144: Check _S3 (System S3 State).
SKIPPED: Test 127, Skipping test for non-existant object _S3.

Test 128 of 144: Check _S4 (System S4 State).
SKIPPED: Test 128, Skipping test for non-existant object _S4.

Test 129 of 144: Check _S5 (System S5 State).
SKIPPED: Test 129, Skipping test for non-existant object _S5.

Test 130 of 144: Check _WAK (System Wake).
Test _WAK(1) System Wake, State S1.
PASSED: Test 130, \_WAK correctly returned a sane looking package.

Test _WAK(2) System Wake, State S2.
PASSED: Test 130, \_WAK correctly returned a sane looking package.

Test _WAK(3) System Wake, State S3.
PASSED: Test 130, \_WAK correctly returned a sane looking package.

Test _WAK(4) System Wake, State S4.
PASSED: Test 130, \_WAK correctly returned a sane looking package.

Test _WAK(5) System Wake, State S5.
PASSED: Test 130, \_WAK correctly returned a sane looking package.


Test 131 of 144: Check _ADR (Return Unique ID for Device).
PASSED: Test 131, \_SB_.PCI0._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.GFX0._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.GFX0.DD01._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.GFX0.DD02._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.GFX0.DD03._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.GFX0.DD04._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.GFX0.DD05._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.GFX0.DD06._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.GFX0.DD07._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.GFX0.DD08._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.P0P2._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.P0P2.PEGP._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.P0P1._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.LPCB._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.EHC1._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.EHC1.RHUB._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.EHC1.RHUB.IHUB._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.EHC1.RHUB.IHUB.PRT1._ADR correctly returned an
integer.
PASSED: Test 131, \_SB_.PCI0.EHC1.RHUB.IHUB.PRT2._ADR correctly returned an
integer.
PASSED: Test 131, \_SB_.PCI0.EHC1.RHUB.IHUB.PRT3._ADR correctly returned an
integer.
PASSED: Test 131, \_SB_.PCI0.EHC1.RHUB.IHUB.PRT4._ADR correctly returned an
integer.
PASSED: Test 131, \_SB_.PCI0.EHC1.RHUB.IHUB.PRT5._ADR correctly returned an
integer.
PASSED: Test 131, \_SB_.PCI0.EHC1.RHUB.IHUB.PRT6._ADR correctly returned an
integer.
PASSED: Test 131, \_SB_.PCI0.EHC1.RHUB.IHUB.PRT7._ADR correctly returned an
integer.
PASSED: Test 131, \_SB_.PCI0.EHC1.RHUB.IHUB.PRT8._ADR correctly returned an
integer.
PASSED: Test 131, \_SB_.PCI0.USB1._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.USB2._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.USB3._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.USB4._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.HDEF._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.RP01._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.RP01.PXSX._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.RP02._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.RP02.PXS1._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.IO10._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.IO1X._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.IIO0._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.IIOX._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.PEG3._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.PEG3.VGA_._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.PEG3.VGA_.CRT_._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.PEG3.VGA_.LCD_._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.PEG3.VGA_.HDMI._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.PEG3.VGA_.LCD1._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.PEG3.VGA_.HDM1._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.SBUS._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.SATA._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.SATA.PRID._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.SATA.PRID.MAST._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.SATA.PRID.SLAV._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.SATA.SECD._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.SATA.SECD.MAST._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.SATA.SECD.SLAV._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.SAT2._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.SAT2.PRID._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.SAT2.PRID.MAST._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.PCI0.SAT2.PRID.SLAV._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.CPBG._ADR correctly returned an integer.
PASSED: Test 131, \_SB_.CPBG.IMCH._ADR correctly returned an integer.

Test 132 of 144: Check _BCL (Query List of Brightness Control Levels Supported).
Brightness levels for \_SB_.PCI0.GFX0.DD02._BCL:
  Level on full power   : 80
  Level on battery power: 50
  Brightness Levels     : 0, 5, 10, 15, 20, 25, 30, 35, 40, 45, 50, 55, 60, 65, 70, 75, 80, 85, 90, 95, 100
PASSED: Test 132, \_SB_.PCI0.GFX0.DD02._BCL returned a sane package of 23
integers.
Brightness levels for \_SB_.PCI0.PEG3.VGA_.LCD_._BCL:
  Level on full power   : 100
  Level on battery power: 50
  Brightness Levels     : 5, 10, 20, 30, 40, 50, 60, 70, 80, 90, 100
PASSED: Test 132, \_SB_.PCI0.PEG3.VGA_.LCD_._BCL returned a sane package of 13
integers.
Brightness levels for \_SB_.PCI0.PEG3.VGA_.LCD1._BCL:
  Level on full power   : 100
  Level on battery power: 50
  Brightness Levels     : 5, 10, 20, 30, 40, 50, 60, 70, 80, 90, 100
PASSED: Test 132, \_SB_.PCI0.PEG3.VGA_.LCD1._BCL returned a sane package of 13
integers.

Test 133 of 144: Check _BCM (Set Brightness Level).
PASSED: Test 133, \_SB_.PCI0.GFX0.DD02._BCM returned no values as expected.
PASSED: Test 133, \_SB_.PCI0.PEG3.VGA_.LCD_._BCM returned no values as expected.
PASSED: Test 133, \_SB_.PCI0.PEG3.VGA_.LCD1._BCM returned no values as expected.

Test 134 of 144: Check _BQC (Brightness Query Current Level).
PASSED: Test 134, \_SB_.PCI0.GFX0.DD02._BQC correctly returned an integer.
ACPICA Exception AE_AML_UNINITIALIZED_LOCAL during execution of method GBQC
FAILED [HIGH] AEAMLUninitLocal: Test 134, Detected error 'Uninitialized local
variable' when evaluating '\_SB_.PCI0.PEG3.VGA_.LCD_._BQC'.
ACPICA Exception AE_AML_UNINITIALIZED_LOCAL during execution of method GBQC
FAILED [HIGH] AEAMLUninitLocal: Test 134, Detected error 'Uninitialized local
variable' when evaluating '\_SB_.PCI0.PEG3.VGA_.LCD1._BQC'.

Test 135 of 144: Check _DCS (Return the Status of Output Device).
PASSED: Test 135, \_SB_.PCI0.GFX0.DD01._DCS correctly returned an integer.
PASSED: Test 135, \_SB_.PCI0.GFX0.DD02._DCS correctly returned an integer.
PASSED: Test 135, \_SB_.PCI0.GFX0.DD03._DCS correctly returned an integer.
PASSED: Test 135, \_SB_.PCI0.GFX0.DD04._DCS correctly returned an integer.
PASSED: Test 135, \_SB_.PCI0.GFX0.DD05._DCS correctly returned an integer.
PASSED: Test 135, \_SB_.PCI0.GFX0.DD06._DCS correctly returned an integer.
PASSED: Test 135, \_SB_.PCI0.GFX0.DD07._DCS correctly returned an integer.
PASSED: Test 135, \_SB_.PCI0.GFX0.DD08._DCS correctly returned an integer.
PASSED: Test 135, \_SB_.PCI0.PEG3.VGA_.CRT_._DCS correctly returned an integer.
PASSED: Test 135, \_SB_.PCI0.PEG3.VGA_.LCD_._DCS correctly returned an integer.
PASSED: Test 135, \_SB_.PCI0.PEG3.VGA_.HDMI._DCS correctly returned an integer.
PASSED: Test 135, \_SB_.PCI0.PEG3.VGA_.LCD1._DCS correctly returned an integer.
PASSED: Test 135, \_SB_.PCI0.PEG3.VGA_.HDM1._DCS correctly returned an integer.

Test 136 of 144: Check _DDC (Return the EDID for this Device).
SKIPPED: Test 136, Skipping test for non-existant object _DDC.

Test 137 of 144: Check _DSS (Device Set State).
PASSED: Test 137, \_SB_.PCI0.GFX0.DD01._DSS returned no values as expected.
PASSED: Test 137, \_SB_.PCI0.GFX0.DD02._DSS returned no values as expected.
PASSED: Test 137, \_SB_.PCI0.GFX0.DD03._DSS returned no values as expected.
PASSED: Test 137, \_SB_.PCI0.GFX0.DD04._DSS returned no values as expected.
PASSED: Test 137, \_SB_.PCI0.GFX0.DD05._DSS returned no values as expected.
PASSED: Test 137, \_SB_.PCI0.GFX0.DD06._DSS returned no values as expected.
PASSED: Test 137, \_SB_.PCI0.GFX0.DD07._DSS returned no values as expected.
PASSED: Test 137, \_SB_.PCI0.GFX0.DD08._DSS returned no values as expected.
PASSED: Test 137, \_SB_.PCI0.PEG3.VGA_.CRT_._DSS returned no values as expected.
PASSED: Test 137, \_SB_.PCI0.PEG3.VGA_.LCD_._DSS returned no values as expected.
PASSED: Test 137, \_SB_.PCI0.PEG3.VGA_.HDMI._DSS returned no values as expected.
PASSED: Test 137, \_SB_.PCI0.PEG3.VGA_.LCD1._DSS returned no values as expected.
PASSED: Test 137, \_SB_.PCI0.PEG3.VGA_.HDM1._DSS returned no values as expected.

Test 138 of 144: Check _DGS (Query Graphics State).
PASSED: Test 138, \_SB_.PCI0.GFX0.DD01._DGS correctly returned an integer.
PASSED: Test 138, \_SB_.PCI0.GFX0.DD02._DGS correctly returned an integer.
PASSED: Test 138, \_SB_.PCI0.GFX0.DD03._DGS correctly returned an integer.
PASSED: Test 138, \_SB_.PCI0.GFX0.DD04._DGS correctly returned an integer.
PASSED: Test 138, \_SB_.PCI0.GFX0.DD05._DGS correctly returned an integer.
PASSED: Test 138, \_SB_.PCI0.GFX0.DD06._DGS correctly returned an integer.
PASSED: Test 138, \_SB_.PCI0.GFX0.DD07._DGS correctly returned an integer.
PASSED: Test 138, \_SB_.PCI0.GFX0.DD08._DGS correctly returned an integer.
PASSED: Test 138, \_SB_.PCI0.PEG3.VGA_.CRT_._DGS correctly returned an integer.
PASSED: Test 138, \_SB_.PCI0.PEG3.VGA_.LCD_._DGS correctly returned an integer.
PASSED: Test 138, \_SB_.PCI0.PEG3.VGA_.HDMI._DGS correctly returned an integer.
PASSED: Test 138, \_SB_.PCI0.PEG3.VGA_.LCD1._DGS correctly returned an integer.
PASSED: Test 138, \_SB_.PCI0.PEG3.VGA_.HDM1._DGS correctly returned an integer.

Test 139 of 144: Check _DOD (Enumerate All Devices Attached to Display Adapter).
Device 0:
  Instance:                0
  Display port attachment: 0
  Type of display:         4 (Internal/Integrated Digital Flat Panel)
  BIOS can detect device:  0
  Non-VGA device:          0
  Head or pipe ID:         0
PASSED: Test 139, \_SB_.PCI0.GFX0._DOD correctly returned a sane looking
package.
Device 0:
  Instance:                0
  Display port attachment: 1
  Type of display:         1 (VGA, CRT or VESA Compatible Analog Monitor)
  BIOS can detect device:  1
  Non-VGA device:          0
  Head or pipe ID:         0
Device 1:
  Instance:                0
  Display port attachment: 1
  Type of display:         2 (TV/HDTV or other Analog-Video Monitor)
  BIOS can detect device:  1
  Non-VGA device:          0
  Head or pipe ID:         0
Device 2:
  Instance:                0
  Display port attachment: 0
  Type of display:         1 (VGA, CRT or VESA Compatible Analog Monitor)
  BIOS can detect device:  1
  Non-VGA device:          0
  Head or pipe ID:         0
Device 3:
  Instance:                8
  Display port attachment: 1
  Type of display:         1 (VGA, CRT or VESA Compatible Analog Monitor)
  BIOS can detect device:  1
  Non-VGA device:          0
  Head or pipe ID:         0
Device 4:
  Instance:                1
  Display port attachment: 2
  Type of display:         1 (VGA, CRT or VESA Compatible Analog Monitor)
  BIOS can detect device:  1
  Non-VGA device:          0
  Head or pipe ID:         0
PASSED: Test 139, \_SB_.PCI0.PEG3.VGA_._DOD correctly returned a sane looking
package.

Test 140 of 144: Check _DOS (Enable/Disable Output Switching).
PASSED: Test 140, \_SB_.PCI0.GFX0._DOS returned no values as expected.
PASSED: Test 140, \_SB_.PCI0.PEG3.VGA_._DOS returned no values as expected.

Test 141 of 144: Check _GPD (Get POST Device).
SKIPPED: Test 141, Skipping test for non-existant object _GPD.

Test 142 of 144: Check _ROM (Get ROM Data).
SKIPPED: Test 142, Skipping test for non-existant object _ROM.

Test 143 of 144: Check _SPD (Set POST Device).
SKIPPED: Test 143, Skipping test for non-existant object _SPD.

Test 144 of 144: Check _VPO (Video POST Options).
SKIPPED: Test 144, Skipping test for non-existant object _VPO.

================================================================================
281 passed, 8 failed, 5 warnings, 0 aborted, 106 skipped, 0 info only.
================================================================================

mcfg: MCFG PCI Express* memory mapped config space.
--------------------------------------------------------------------------------
Test 1 of 2: Validate MCFG table.
This test tries to validate the MCFG table by comparing the first 16 bytes in
the MMIO mapped config space with the 'traditional' config space of the first
PCI device (root bridge). The MCFG data is only trusted if it is marked reserved
in the Int 15 AX=E820 BIOS memory map

Memory Map Layout
-----------------
0x0000000000000000 - 0x000000000009bbff (System RAM)
0x000000000009bc00 - 0x000000000009ffff (reserved)
0x00000000000e0000 - 0x00000000000fffff (reserved)
0x0000000000100000 - 0x00000000bf681fff (System RAM)
0x00000000bf682000 - 0x00000000bf6befff (reserved)
0x00000000bf6bf000 - 0x00000000bf75afff (System RAM)
0x00000000bf75b000 - 0x00000000bf7befff (ACPI Non-volatile Storage)
0x00000000bf7bf000 - 0x00000000bf7e2fff (System RAM)
0x00000000bf7e3000 - 0x00000000bf7fefff (ACPI Non-volatile Storage)
0x00000000bf7ff000 - 0x00000000bf7fffff (System RAM)
0x00000000bf800000 - 0x00000000bfffffff (reserved)
0x00000000e0000000 - 0x00000000efffffff (reserved)
0x00000000feb00000 - 0x00000000feb03fff (reserved)
0x00000000fec00000 - 0x00000000fec00fff (reserved)
0x00000000fed10000 - 0x00000000fed13fff (reserved)
0x00000000fed18000 - 0x00000000fed19fff (reserved)
0x00000000fed1b000 - 0x00000000fed1ffff (reserved)
0x00000000fee00000 - 0x00000000fee00fff (reserved)
0x00000000ffe80000 - 0x00000000ffffffff (reserved)
0x0000000100000000 - 0x000000023fffffff (System RAM)

MCFG table found, size is 16 bytes (excluding header) (1 entries).
Configuration Entry #0:
  Base Address  : 0xe0000000
  Segment       : 0
  Start bus     : 0
  End bus       : 255
PASSED: Test 1, MCFG mmio config space is reserved in memory map table.

Test 2 of 2: Validate MCFG PCI config space.
PASSED: Test 2, PCI config space verified.

================================================================================
2 passed, 0 failed, 0 warnings, 0 aborted, 0 skipped, 0 info only.
================================================================================

fan: Simple Fan Tests.
--------------------------------------------------------------------------------
Test 1 of 2: Check fan status.
Test how many fans there are in the system. Check for the current status of the
fan(s).
PASSED: Test 1, Fan cooling_device0 of type Processor has max cooling state 10
and current cooling state 0.
PASSED: Test 1, Fan cooling_device1 of type Processor has max cooling state 10
and current cooling state 0.
PASSED: Test 1, Fan cooling_device2 of type Processor has max cooling state 10
and current cooling state 0.
PASSED: Test 1, Fan cooling_device3 of type Processor has max cooling state 10
and current cooling state 0.
PASSED: Test 1, Fan cooling_device4 of type Processor has max cooling state 10
and current cooling state 0.
PASSED: Test 1, Fan cooling_device5 of type Processor has max cooling state 10
and current cooling state 0.
PASSED: Test 1, Fan cooling_device6 of type Processor has max cooling state 10
and current cooling state 0.
PASSED: Test 1, Fan cooling_device7 of type Processor has max cooling state 10
and current cooling state 0.
PASSED: Test 1, Fan cooling_device8 of type LCD has max cooling state 10 and
current cooling state 0.
PASSED: Test 1, Fan cooling_device9 of type LCD has max cooling state 10 and
current cooling state 0.

Test 2 of 2: Load system, check CPU fan status.
Test how many fans there are in the system. Check for the current status of the
fan(s).
Loading CPUs for 20 seconds to try and get fan speeds to change.
Fan cooling_device0 current state did not change from value 0 while CPUs were
busy.
Fan cooling_device1 current state did not change from value 0 while CPUs were
busy.
Fan cooling_device2 current state did not change from value 0 while CPUs were
busy.
Fan cooling_device3 current state did not change from value 0 while CPUs were
busy.
Fan cooling_device4 current state did not change from value 0 while CPUs were
busy.
Fan cooling_device5 current state did not change from value 0 while CPUs were
busy.
Fan cooling_device6 current state did not change from value 0 while CPUs were
busy.
Fan cooling_device7 current state did not change from value 0 while CPUs were
busy.

ADVICE: Did not detect any change in the CPU related thermal cooling device
states. It could be that the devices are returning static information back to
the driver and/or the fan speed is automatically being controlled by firmware
using System Management Mode in which case the kernel interfaces being examined
may not work anyway.


================================================================================
10 passed, 0 failed, 0 warnings, 0 aborted, 0 skipped, 0 info only.
================================================================================

fadt: FADT SCI_EN enabled check.
--------------------------------------------------------------------------------
Test 1 of 1: Check FADT SCI_EN bit is enabled.
FADT Preferred PM Profile: 2 (Mobile) 
FADT is greater than ACPI version 1.0
FAILED [MEDIUM] FADTPM1CNTAddrMismatch: Test 1, 32 and 64 bit versions of FADT
pm1_cnt address do not match (0x00000404 vs 0x0000000000000000).
FAILED [MEDIUM] FADTPM1CNTSizeMismatch: Test 1, 32 and 64 bit versions of FADT
pm1_cnt size do not match (0x10 vs 0x0).
FAILED [HIGH] FADTPM1AInvalidWidth: Test 1, FADT pm1a register has invalid bit
width of 0.

================================================================================
0 passed, 3 failed, 0 warnings, 0 aborted, 0 skipped, 0 info only.
================================================================================

dmar: Check sane DMA Remapping (VT-d).
--------------------------------------------------------------------------------
Test 1 of 1: Check DMA Remapping.
PASSED: Test 1, DMAR ACPI table has passed test.
PASSED: Test 1, Found no DMAR errors in kernel log.

================================================================================
2 passed, 0 failed, 0 warnings, 0 aborted, 0 skipped, 0 info only.
================================================================================

cstates: Check processor C state support.
--------------------------------------------------------------------------------
Test 1 of 1: Check all CPUs C-states.
This test checks if all processors have the same number of C-states, if the
C-state counter works and if C-state transitions happen.
PASSED: Test 1, Processor 0 has reached all C-states: 
PASSED: Test 1, Processor 1 has reached all C-states: 
PASSED: Test 1, Processor 1 has the same number of C-states as processor 0
PASSED: Test 1, Processor 2 has reached all C-states: 
PASSED: Test 1, Processor 2 has the same number of C-states as processor 0
PASSED: Test 1, Processor 3 has reached all C-states: 
PASSED: Test 1, Processor 3 has the same number of C-states as processor 0
PASSED: Test 1, Processor 4 has reached all C-states: 
PASSED: Test 1, Processor 4 has the same number of C-states as processor 0
PASSED: Test 1, Processor 5 has reached all C-states: 
PASSED: Test 1, Processor 5 has the same number of C-states as processor 0
PASSED: Test 1, Processor 6 has reached all C-states: 
PASSED: Test 1, Processor 6 has the same number of C-states as processor 0
PASSED: Test 1, Processor 7 has reached all C-states: 
PASSED: Test 1, Processor 7 has the same number of C-states as processor 0

================================================================================
15 passed, 0 failed, 0 warnings, 0 aborted, 0 skipped, 0 info only.
================================================================================

checksum: Check ACPI table checksum.
--------------------------------------------------------------------------------
Test 1 of 1: Check ACPI table checksums.
PASSED: Test 1, Table RSDP has correct checksum 0xfd.
PASSED: Test 1, Table RSDP has correct extended checksum 0x9d.
PASSED: Test 1, Table RSDT has correct checksum 0x13.
PASSED: Test 1, Table DSDT has correct checksum 0xd8.
PASSED: Test 1, Table FACP has correct checksum 0x81.
PASSED: Test 1, Table ASF! has correct checksum 0x7f.
PASSED: Test 1, Table HPET has correct checksum 0x4e.
PASSED: Test 1, Table APIC has correct checksum 0x97.
PASSED: Test 1, Table MCFG has correct checksum 0x76.
PASSED: Test 1, Table SLIC has correct checksum 0x67.
PASSED: Test 1, Table SSDT has correct checksum 0x33.
PASSED: Test 1, Table SSDT has correct checksum 0x58.
PASSED: Test 1, Table BOOT has correct checksum 0xe.
PASSED: Test 1, Table SSDT has correct checksum 0xce.
PASSED: Test 1, Table SSDT has correct checksum 0xb3.
PASSED: Test 1, Table SPCR has correct checksum 0x12.
PASSED: Test 1, Table ASPT has correct checksum 0x3f.
PASSED: Test 1, Table DMAR has correct checksum 0xb0.
PASSED: Test 1, Table SSDT has correct checksum 0x22.
PASSED: Test 1, Table XSDT has correct checksum 0xd1.

================================================================================
20 passed, 0 failed, 0 warnings, 0 aborted, 0 skipped, 0 info only.
================================================================================

apicinstance: Check for single instance of APIC/MADT table.
--------------------------------------------------------------------------------
Test 1 of 1: Check single instance of APIC/MADT table.
Found APIC/MADT table APIC @ bf7fa000, length 0x140 
PASSED: Test 1, Found 1 APIC/MADT table(s), as expected.

================================================================================
1 passed, 0 failed, 0 warnings, 0 aborted, 0 skipped, 0 info only.
================================================================================

acpitables: ACPI table settings sanity checks.
--------------------------------------------------------------------------------
Test 1 of 1: Check ACPI tables.
PASSED: Test 1, Table APIC passed.
Table ECDT not present to check.
FAILED [MEDIUM] FADT32And64BothDefined: Test 1, FADT 32 bit FIRMWARE_CONTROL is
non-zero, and X_FIRMWARE_CONTROL is also non-zero. Section 5.2.9 of the ACPI
specification states that if the FIRMWARE_CONTROL is non-zero then
X_FIRMWARE_CONTROL must be set to zero.

ADVICE: The FADT FIRMWARE_CTRL is a 32 bit pointer that points to the physical
memory address of the Firmware ACPI Control Structure (FACS). There is also an
extended 64 bit version of this, the X_FIRMWARE_CTRL pointer that also can point
to the FACS. Section 5.2.9 of the ACPI specification states that if the
X_FIRMWARE_CTRL field contains a non zero value then the FIRMWARE_CTRL field
*must* be zero. This error is also detected by the Linux kernel. If
FIRMWARE_CTRL and X_FIRMWARE_CTRL are defined, then the kernel just uses the 64
bit version of the pointer.

PASSED: Test 1, Table HPET passed.
PASSED: Test 1, Table MCFG passed.
PASSED: Test 1, Table RSDT passed.
PASSED: Test 1, Table RSDP passed.
Table SBST not present to check.
PASSED: Test 1, Table XSDT passed.

================================================================================
6 passed, 1 failed, 0 warnings, 0 aborted, 0 skipped, 0 info only.
================================================================================


501 passed, 245 failed, 9 warnings, 1 aborted, 116 skipped, 10 info only.

Test Failure Summary
================================================================================

Critical failures: NONE

High failures: 190
 klog: HIGH Kernel message: [    0.731759] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20130517/hwxface-571)
 klog: HIGH Kernel message: [    0.732048] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20130517/hwxface-571)
 klog: HIGH Kernel message: [    0.744087] \_SB_.PCI0:_OSC invalid UUID
 syntaxcheck: Assembler error in line 2637
 syntaxcheck: Assembler error in line 2735
 syntaxcheck: Assembler error in line 2795
 syntaxcheck: Assembler error in line 2816
 syntaxcheck: Assembler error in line 2837
 syntaxcheck: Assembler error in line 2856
 syntaxcheck: Assembler error in line 2872
 syntaxcheck: Assembler error in line 2874
 syntaxcheck: Assembler error in line 2875
 syntaxcheck: Assembler error in line 2907
 syntaxcheck: Assembler error in line 2914
 syntaxcheck: Assembler error in line 2917
 syntaxcheck: Assembler error in line 2922
 syntaxcheck: Assembler error in line 2927
 syntaxcheck: Assembler error in line 2928
 syntaxcheck: Assembler error in line 2991
 syntaxcheck: Assembler error in line 3012
 syntaxcheck: Assembler error in line 3033
 syntaxcheck: Assembler error in line 3052
 syntaxcheck: Assembler error in line 3068
 syntaxcheck: Assembler error in line 3069
 syntaxcheck: Assembler error in line 3098
 syntaxcheck: Assembler error in line 3105
 syntaxcheck: Assembler error in line 3108
 syntaxcheck: Assembler error in line 3113
 syntaxcheck: Assembler error in line 3118
 syntaxcheck: Assembler error in line 3119
 syntaxcheck: Assembler error in line 3161
 syntaxcheck: Assembler error in line 3349
 syntaxcheck: Assembler error in line 3356
 syntaxcheck: Assembler error in line 3361
 syntaxcheck: Assembler error in line 3367
 syntaxcheck: Assembler error in line 3373
 syntaxcheck: Assembler error in line 3379
 syntaxcheck: Assembler error in line 3385
 syntaxcheck: Assembler error in line 3391
 syntaxcheck: Assembler error in line 3397
 syntaxcheck: Assembler error in line 3403
 syntaxcheck: Assembler error in line 3409
 syntaxcheck: Assembler error in line 3415
 syntaxcheck: Assembler error in line 3421
 syntaxcheck: Assembler error in line 3427
 syntaxcheck: Assembler error in line 3433
 syntaxcheck: Assembler error in line 3439
 syntaxcheck: Assembler error in line 3445
 syntaxcheck: Assembler error in line 3451
 syntaxcheck: Assembler error in line 3457
 syntaxcheck: Assembler error in line 3463
 syntaxcheck: Assembler error in line 3469
 syntaxcheck: Assembler error in line 3475
 syntaxcheck: Assembler error in line 3481
 syntaxcheck: Assembler error in line 3487
 syntaxcheck: Assembler error in line 3493
 syntaxcheck: Assembler error in line 3499
 syntaxcheck: Assembler error in line 3505
 syntaxcheck: Assembler error in line 3511
 syntaxcheck: Assembler error in line 3525
 syntaxcheck: Assembler error in line 3530
 syntaxcheck: Assembler error in line 3564
 syntaxcheck: Assembler error in line 3569
 syntaxcheck: Assembler error in line 4381
 syntaxcheck: Assembler error in line 4450
 syntaxcheck: Assembler error in line 4452
 syntaxcheck: Assembler error in line 4453
 syntaxcheck: Assembler error in line 4457
 syntaxcheck: Assembler error in line 4459
 syntaxcheck: Assembler error in line 4460
 syntaxcheck: Assembler error in line 4464
 syntaxcheck: Assembler error in line 4466
 syntaxcheck: Assembler error in line 4467
 syntaxcheck: Assembler error in line 4468
 syntaxcheck: Assembler error in line 4469
 syntaxcheck: Assembler error in line 4470
 syntaxcheck: Assembler error in line 4474
 syntaxcheck: Assembler error in line 4476
 syntaxcheck: Assembler error in line 4477
 syntaxcheck: Assembler error in line 4478
 syntaxcheck: Assembler error in line 4479
 syntaxcheck: Assembler error in line 4480
 syntaxcheck: Assembler error in line 4481
 syntaxcheck: Assembler error in line 4482
 syntaxcheck: Assembler error in line 4486
 syntaxcheck: Assembler error in line 4488
 syntaxcheck: Assembler error in line 4489
 syntaxcheck: Assembler error in line 4490
 syntaxcheck: Assembler error in line 4494
 syntaxcheck: Assembler error in line 4496
 syntaxcheck: Assembler error in line 4497
 syntaxcheck: Assembler error in line 4498
 syntaxcheck: Assembler error in line 4499
 syntaxcheck: Assembler error in line 4500
 syntaxcheck: Assembler error in line 4501
 syntaxcheck: Assembler error in line 4502
 syntaxcheck: Assembler error in line 4503
 syntaxcheck: Assembler error in line 4507
 syntaxcheck: Assembler error in line 4509
 syntaxcheck: Assembler error in line 4512
 syntaxcheck: Assembler error in line 4515
 syntaxcheck: Assembler error in line 4519
 syntaxcheck: Assembler error in line 4521
 syntaxcheck: Assembler error in line 4522
 syntaxcheck: Assembler error in line 4526
 syntaxcheck: Assembler error in line 4532
 syntaxcheck: Assembler error in line 4534
 syntaxcheck: Assembler error in line 4535
 syntaxcheck: Assembler error in line 4536
 syntaxcheck: Assembler error in line 4540
 syntaxcheck: Assembler error in line 4542
 syntaxcheck: Assembler error in line 4543
 syntaxcheck: Assembler error in line 4547
 syntaxcheck: Assembler error in line 4549
 syntaxcheck: Assembler error in line 4550
 syntaxcheck: Assembler error in line 4554
 syntaxcheck: Assembler error in line 4556
 syntaxcheck: Assembler error in line 4557
 syntaxcheck: Assembler error in line 4561
 syntaxcheck: Assembler error in line 4563
 syntaxcheck: Assembler error in line 4564
 syntaxcheck: Assembler error in line 4568
 syntaxcheck: Assembler error in line 4570
 syntaxcheck: Assembler error in line 4571
 syntaxcheck: Assembler error in line 4572
 syntaxcheck: Assembler error in line 4573
 syntaxcheck: Assembler error in line 4577
 syntaxcheck: Assembler error in line 4579
 syntaxcheck: Assembler error in line 4581
 syntaxcheck: Assembler error in line 4584
 syntaxcheck: Assembler error in line 4585
 syntaxcheck: Assembler error in line 4589
 syntaxcheck: Assembler error in line 4590
 syntaxcheck: Assembler error in line 4594
 syntaxcheck: Assembler error in line 4596
 syntaxcheck: Assembler error in line 4597
 syntaxcheck: Assembler error in line 4601
 syntaxcheck: Assembler error in line 4603
 syntaxcheck: Assembler error in line 4604
 syntaxcheck: Assembler error in line 4605
 syntaxcheck: Assembler error in line 4609
 syntaxcheck: Assembler error in line 4611
 syntaxcheck: Assembler error in line 4612
 syntaxcheck: Assembler error in line 4614
 syntaxcheck: Assembler error in line 4618
 syntaxcheck: Assembler error in line 4619
 syntaxcheck: Assembler error in line 4620
 syntaxcheck: Assembler error in line 4624
 syntaxcheck: Assembler error in line 4626
 syntaxcheck: Assembler error in line 4627
 syntaxcheck: Assembler error in line 4629
 syntaxcheck: Assembler error in line 4633
 syntaxcheck: Assembler error in line 4636
 syntaxcheck: Assembler error in line 4637
 syntaxcheck: Assembler error in line 4641
 syntaxcheck: Assembler error in line 4643
 syntaxcheck: Assembler error in line 4644
 syntaxcheck: Assembler error in line 4648
 syntaxcheck: Assembler error in line 4650
 syntaxcheck: Assembler error in line 4651
 syntaxcheck: Assembler error in line 4652
 syntaxcheck: Assembler error in line 4656
 syntaxcheck: Assembler error in line 4658
 syntaxcheck: Assembler error in line 4660
 syntaxcheck: Assembler error in line 4666
 syntaxcheck: Assembler error in line 4675
 syntaxcheck: Assembler error in line 4676
 syntaxcheck: Assembler error in line 4680
 syntaxcheck: Assembler error in line 4682
 syntaxcheck: Assembler error in line 4683
 syntaxcheck: Assembler error in line 4687
 syntaxcheck: Assembler error in line 4689
 syntaxcheck: Assembler error in line 4690
 syntaxcheck: Assembler error in line 4691
 syntaxcheck: Assembler error in line 4695
 syntaxcheck: Assembler error in line 4699
 syntaxcheck: Assembler error in line 4701
 syntaxcheck: Assembler error in line 4704
 syntaxcheck: Assembler error in line 4706
 syntaxcheck: Assembler error in line 4709
 syntaxcheck: Assembler error in line 4710
 syntaxcheck: Assembler error in line 4711
 syntaxcheck: Assembler error in line 4712
 syntaxcheck: Assembler error in line 4718
 syntaxcheck: Assembler error in line 4720
 syntaxcheck: Assembler error in line 10258
 method: Detected error 'Uninitialized local variable' when evaluating '\_TZ_.TZ01._TMP'.
 method: Detected error 'Uninitialized local variable' when evaluating '\_SB_.PCI0.PEG3.VGA_.LCD_._BQC'.
 method: Detected error 'Uninitialized local variable' when evaluating '\_SB_.PCI0.PEG3.VGA_.LCD1._BQC'.
 fadt: FADT pm1a register has invalid bit width of 0.

Medium failures: 29
 klog: MEDIUM Kernel message: [    0.682731] mtrr: your CPUs had inconsistent variable MTRR settings
 mtrr: It is probable that the BIOS does not set up all the CPUs correctly and the kernel has now corrected this misconfiguration.
 aspm: PCIe ASPM setting was not matched.
 microcode: The kernel did not report that CPU 0 has had a microcode update. The current firmware is revision 0x4 and probably has not been updated.
 microcode: The kernel did not report that CPU 1 has had a microcode update. The current firmware is revision 0x4 and probably has not been updated.
 microcode: The kernel did not report that CPU 2 has had a microcode update. The current firmware is revision 0x4 and probably has not been updated.
 microcode: The kernel did not report that CPU 3 has had a microcode update. The current firmware is revision 0x4 and probably has not been updated.
 microcode: The kernel did not report that CPU 4 has had a microcode update. The current firmware is revision 0x4 and probably has not been updated.
 microcode: The kernel did not report that CPU 5 has had a microcode update. The current firmware is revision 0x4 and probably has not been updated.
 microcode: The kernel did not report that CPU 6 has had a microcode update. The current firmware is revision 0x4 and probably has not been updated.
 microcode: The kernel did not report that CPU 7 has had a microcode update. The current firmware is revision 0x4 and probably has not been updated.
 msr: MSR CLOCK_MODULATION (0x19a) has 7 inconsistent values across 8 CPUs for (shift: 0 mask: 0x1f).
 cpufreq: Processors are set to SW_ANY.
 syntaxcheck: Assembler warning in line 68
 syntaxcheck: Assembler warning in line 182
 syntaxcheck: Assembler warning in line 252
 syntaxcheck: Assembler warning in line 298
 syntaxcheck: Assembler warning in line 344
 syntaxcheck: Assembler warning in line 390
 syntaxcheck: Assembler warning in line 436
 syntaxcheck: Assembler warning in line 482
 method: \_SB_.PCI0.DOCK._HID returned a string 'ABCDEFGH' but it was not a valid PNP ID or a valid ACPI ID.
 method: \_SB_.PCI0.DOCK._EJ0 returned values, but was expected to return nothing.
 method: \_TZ_.TZ01._CRT returned a NULL object, and did not return ACPI_TYPE_INTEGER.
 method: \_TZ_.TZ01._HOT returned a NULL object, and did not return ACPI_TYPE_INTEGER.
 method: \_TZ_.TZ01._PSV returned a NULL object, and did not return ACPI_TYPE_INTEGER.
 fadt: 32 and 64 bit versions of FADT pm1_cnt address do not match (0x00000404 vs 0x0000000000000000).
 fadt: 32 and 64 bit versions of FADT pm1_cnt size do not match (0x10 vs 0x0).
 acpitables: FADT 32 bit FIRMWARE_CONTROL is non-zero, and X_FIRMWARE_CONTROL is also non-zero. Section 5.2.9 of the ACPI specification states that if the FIRMWARE_CONTROL is non-zero then X_FIRMWARE_CONTROL must be set to zero.

Low failures: 7
 klog: LOW Kernel message: [   14.720143] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20130517/utaddress-251)
 klog: LOW Kernel message: [   14.720154] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \_SB_.PCI0.IEIT.SGPE 2 (20130517/utaddress-251)
 klog: LOW Kernel message: [   14.720170] ACPI Warning: 0x0000000000000540-0x000000000000054f SystemIO conflicts with Region \GPIO 1 (20130517/utaddress-251)
 klog: LOW Kernel message: [   14.720179] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20130517/utaddress-251)
 klog: LOW Kernel message: [   14.720187] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20130517/utaddress-251)
 klog: LOW Kernel message: [   14.720196] lpc_ich: Resource conflict(s) found affecting gpio_ich
 maxreadreq: 2 devices have low MaxReadReq settings. Firmware may have configured these too low.

Other failures: NONE

Test           |Pass |Fail |Abort|Warn |Skip |Info |
---------------+-----+-----+-----+-----+-----+-----+
acpiinfo       |     |     |     |     |     |    3|
acpitables     |    6|    1|     |     |     |     |
apicedge       |    1|     |     |     |     |     |
apicinstance   |    1|     |     |     |     |     |
aspm           |    2|    1|     |    3|     |     |
bios32         |     |     |     |     |     |     |
bios_info      |     |     |     |     |     |    1|
checksum       |   20|     |     |     |     |     |
cpufreq        |     |    1|     |     |     |     |
crs            |    1|     |     |     |     |     |
csm            |     |     |     |     |     |    1|
cstates        |   15|     |     |     |     |     |
dmar           |    2|     |     |     |     |     |
dmicheck       |   38|     |     |     |     |     |
ebda           |    1|     |     |     |     |     |
fadt           |     |    3|     |     |     |     |
fan            |   10|     |     |     |     |     |
hda_audio      |    1|     |     |     |     |     |
hpet_check     |    5|     |     |     |     |     |
klog           |     |   10|     |     |     |     |
maxfreq        |    1|     |     |     |     |     |
maxreadreq     |     |    1|     |     |     |     |
mcfg           |    2|     |     |     |     |     |
method         |  281|    8|     |    5|  106|     |
microcode      |     |    8|     |     |     |     |
mpcheck        |     |     |     |     |    9|     |
msr            |   94|    2|     |     |     |     |
mtrr           |    1|    1|     |     |    1|     |
nx             |    3|     |     |     |     |     |
oops           |    2|     |     |     |     |     |
os2gap         |    1|     |     |     |     |     |
osilinux       |     |     |     |    1|     |     |
pcc            |     |     |     |     |     |    1|
pciirq         |     |     |     |     |     |     |
pnp            |    2|     |     |     |     |     |
securebootcert |     |     |    1|     |     |     |
syntaxcheck    |    4|  209|     |     |     |     |
version        |     |     |     |     |     |    4|
virt           |    1|     |     |     |     |     |
wakealarm      |    4|     |     |     |     |     |
wmi            |    2|     |     |     |     |     |
---------------+-----+-----+-----+-----+-----+-----+
Total:         |  501|  245|    1|    9|  116|   10|
---------------+-----+-----+-----+-----+-----+-----+

```

dmesg -k
```

[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Initializing cgroup subsys cpuacct
[    0.000000] Linux version 3.11.0-24-generic (buildd@toyol) (gcc version 4.8.1 (Ubuntu/Linaro 4.8.1-10ubuntu8) ) #41-Ubuntu SMP Mon Jun 9 20:36:00 UTC 2014 (Ubuntu 3.11.0-24.41-generic 3.11.10.11)
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-24-generic root=UUID=52423430-ed6f-46b2-b259-60ddc64c17d0 ro
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000009bbff] usable
[    0.000000] BIOS-e820: [mem 0x000000000009bc00-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000bf681fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bf682000-0x00000000bf6befff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000bf6bf000-0x00000000bf75afff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bf75b000-0x00000000bf7befff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000bf7bf000-0x00000000bf7e2fff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bf7e3000-0x00000000bf7fefff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000bf7ff000-0x00000000bf7fffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000bf800000-0x00000000bfffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000e0000000-0x00000000efffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000feb00000-0x00000000feb03fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fec00000-0x00000000fec00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed10000-0x00000000fed13fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed18000-0x00000000fed19fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fed1b000-0x00000000fed1ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000ffe80000-0x00000000ffffffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000023fffffff] usable
[    0.000000] NX (Execute Disable) protection: active
[    0.000000] SMBIOS 2.6 present.
[    0.000000] DMI: Hewlett-Packard HP Envy 15 Notebook PC/7009, BIOS F.2C 18/02/2011
[    0.000000] e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
[    0.000000] e820: remove [mem 0x000a0000-0x000fffff] usable
[    0.000000] No AGP bridge found
[    0.000000] e820: last_pfn = 0x240000 max_arch_pfn = 0x400000000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF write-combining
[    0.000000]   C0000-EFFFF write-through
[    0.000000]   F0000-FFFFF write-combining
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask F80000000 write-back
[    0.000000]   1 base 0FFE00000 mask FFFE00000 write-protect
[    0.000000]   2 base 080000000 mask FC0000000 write-back
[    0.000000]   3 base 0BF800000 mask FFF800000 uncachable
[    0.000000]   4 base 100000000 mask F00000000 write-back
[    0.000000]   5 base 200000000 mask FC0000000 write-back
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] x86 PAT enabled: cpu 0, old 0x7040600070406, new 0x7010600070106
[    0.000000] e820: last_pfn = 0xbf800 max_arch_pfn = 0x400000000
[    0.000000] Scanning 1 areas for low memory corruption
[    0.000000] Base memory trampoline at [ffff880000095000] 95000 size 24576
[    0.000000] init_memory_mapping: [mem 0x00000000-0x000fffff]
[    0.000000]  [mem 0x00000000-0x000fffff] page 4k
[    0.000000] BRK [0x01fd1000, 0x01fd1fff] PGTABLE
[    0.000000] BRK [0x01fd2000, 0x01fd2fff] PGTABLE
[    0.000000] BRK [0x01fd3000, 0x01fd3fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x23fe00000-0x23fffffff]
[    0.000000]  [mem 0x23fe00000-0x23fffffff] page 2M
[    0.000000] BRK [0x01fd4000, 0x01fd4fff] PGTABLE
[    0.000000] init_memory_mapping: [mem 0x23c000000-0x23fdfffff]
[    0.000000]  [mem 0x23c000000-0x23fdfffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x200000000-0x23bffffff]
[    0.000000]  [mem 0x200000000-0x23bffffff] page 2M
[    0.000000] init_memory_mapping: [mem 0x00100000-0xbf681fff]
[    0.000000]  [mem 0x00100000-0x001fffff] page 4k
[    0.000000]  [mem 0x00200000-0xbf5fffff] page 2M
[    0.000000]  [mem 0xbf600000-0xbf681fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xbf6bf000-0xbf75afff]
[    0.000000]  [mem 0xbf6bf000-0xbf75afff] page 4k
[    0.000000] init_memory_mapping: [mem 0xbf7bf000-0xbf7e2fff]
[    0.000000]  [mem 0xbf7bf000-0xbf7e2fff] page 4k
[    0.000000] init_memory_mapping: [mem 0xbf7ff000-0xbf7fffff]
[    0.000000]  [mem 0xbf7ff000-0xbf7fffff] page 4k
[    0.000000] init_memory_mapping: [mem 0x100000000-0x1ffffffff]
[    0.000000]  [mem 0x100000000-0x1ffffffff] page 2M
[    0.000000] BRK [0x01fd5000, 0x01fd5fff] PGTABLE
[    0.000000] BRK [0x01fd6000, 0x01fd6fff] PGTABLE
[    0.000000] RAMDISK: [mem 0x35eac000-0x36f4dfff]
[    0.000000] ACPI: RSDP 00000000000fe020 00024 (v02 HP    )
[    0.000000] ACPI: XSDT 00000000bf7fe120 0009C (v01 HPQOEM SLIC-MPC 00000001      01000013)
[    0.000000] ACPI: FACP 00000000bf7fc000 000F4 (v04 HP     SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: DSDT 00000000bf7ed000 0B1C0 (v02 HP     SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: FACS 00000000bf76e000 00040
[    0.000000] ACPI: ASF! 00000000bf7fd000 000A5 (v32 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: HPET 00000000bf7fb000 00038 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: APIC 00000000bf7fa000 0008C (v02 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: MCFG 00000000bf7f9000 0003C (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: SLIC 00000000bf7ec000 00176 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: SSDT 00000000bf7eb000 0073D (v01 TrmRef PtidDevc 00001000 INTL 20051117)
[    0.000000] ACPI: SSDT 00000000bf7ea000 00172 (v01  VaRef  Va_Acpi 00003000 INTL 20051117)
[    0.000000] ACPI: BOOT 00000000bf7e9000 00028 (v01 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: SSDT 00000000bf7e8000 00C39 (v01 INTEL   SataPri 00001000 INTL 20051117)
[    0.000000] ACPI: SSDT 00000000bf7e7000 006C5 (v01 INTEL   SataSec 00001000 INTL 20051117)
[    0.000000] ACPI: SPCR 00000000bf7e6000 00050 (v01 HPQOEM SLIC-MPC 00000000 MSFT 01000013)
[    0.000000] ACPI: ASPT 00000000bf7e5000 00034 (v04 HPQOEM SLIC-MPC 00000001 MSFT 01000013)
[    0.000000] ACPI: DMAR 00000000bf7e4000 00060 (v01 INTEL  CP_FIELD 00000001 INTL 00000001)
[    0.000000] ACPI: SSDT 00000000bf7e3000 009F1 (v01  PmRef    CpuPm 00003000 INTL 20051117)
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] No NUMA configuration found
[    0.000000] Faking a node at [mem 0x0000000000000000-0x000000023fffffff]
[    0.000000] Initmem setup node 0 [mem 0x00000000-0x23fffffff]
[    0.000000]   NODE_DATA [mem 0x23fff6000-0x23fffafff]
[    0.000000]  [ffffea0000000000-ffffea0008ffffff] PMD -> [ffff880237600000-ffff88023f5fffff] on node 0
[    0.000000] Zone ranges:
[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
[    0.000000]   Normal   [mem 0x100000000-0x23fffffff]
[    0.000000] Movable zone start for each node
[    0.000000] Early memory node ranges
[    0.000000]   node   0: [mem 0x00001000-0x0009afff]
[    0.000000]   node   0: [mem 0x00100000-0xbf681fff]
[    0.000000]   node   0: [mem 0xbf6bf000-0xbf75afff]
[    0.000000]   node   0: [mem 0xbf7bf000-0xbf7e2fff]
[    0.000000]   node   0: [mem 0xbf7ff000-0xbf7fffff]
[    0.000000]   node   0: [mem 0x100000000-0x23fffffff]
[    0.000000] On node 0 totalpages: 2094813
[    0.000000]   DMA zone: 64 pages used for memmap
[    0.000000]   DMA zone: 21 pages reserved
[    0.000000]   DMA zone: 3994 pages, LIFO batch:0
[    0.000000]   DMA32 zone: 12190 pages used for memmap
[    0.000000]   DMA32 zone: 780099 pages, LIFO batch:31
[    0.000000]   Normal zone: 20480 pages used for memmap
[    0.000000]   Normal zone: 1310720 pages, LIFO batch:31
[    0.000000] ACPI: PM-Timer IO Port: 0x408
[    0.000000] ACPI: Local APIC address 0xfee00000
[    0.000000] ACPI: LAPIC (acpi_id[0x01] lapic_id[0x00] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x02] lapic_id[0x01] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x03] lapic_id[0x02] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x04] lapic_id[0x03] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x05] lapic_id[0x04] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x06] lapic_id[0x05] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x07] lapic_id[0x06] enabled)
[    0.000000] ACPI: LAPIC (acpi_id[0x08] lapic_id[0x07] enabled)
[    0.000000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[    0.000000] IOAPIC[0]: apic_id 2, version 32, address 0xfec00000, GSI 0-23
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[    0.000000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[    0.000000] ACPI: IRQ0 used by override.
[    0.000000] ACPI: IRQ2 used by override.
[    0.000000] ACPI: IRQ9 used by override.
[    0.000000] Using ACPI (MADT) for SMP configuration information
[    0.000000] ACPI: HPET id: 0x8086a201 base: 0xfed00000
[    0.000000] smpboot: Allowing 8 CPUs, 0 hotplug CPUs
[    0.000000] nr_irqs_gsi: 40
[    0.000000] PM: Registered nosave memory: [mem 0x0009b000-0x0009bfff]
[    0.000000] PM: Registered nosave memory: [mem 0x0009c000-0x0009ffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000a0000-0x000dffff]
[    0.000000] PM: Registered nosave memory: [mem 0x000e0000-0x000fffff]
[    0.000000] PM: Registered nosave memory: [mem 0xbf682000-0xbf6befff]
[    0.000000] PM: Registered nosave memory: [mem 0xbf75b000-0xbf7befff]
[    0.000000] PM: Registered nosave memory: [mem 0xbf7e3000-0xbf7fefff]
[    0.000000] PM: Registered nosave memory: [mem 0xbf800000-0xbfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xc0000000-0xdfffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xe0000000-0xefffffff]
[    0.000000] PM: Registered nosave memory: [mem 0xf0000000-0xfeafffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfeb00000-0xfeb03fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfeb04000-0xfebfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec00000-0xfec00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfec01000-0xfed0ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed10000-0xfed13fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed14000-0xfed17fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed18000-0xfed19fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1a000-0xfed1afff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed1b000-0xfed1ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfed20000-0xfedfffff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee00000-0xfee00fff]
[    0.000000] PM: Registered nosave memory: [mem 0xfee01000-0xffe7ffff]
[    0.000000] PM: Registered nosave memory: [mem 0xffe80000-0xffffffff]
[    0.000000] e820: [mem 0xc0000000-0xdfffffff] available for PCI devices
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:256 nr_cpumask_bits:256 nr_cpu_ids:8 nr_node_ids:1
[    0.000000] PERCPU: Embedded 29 pages/cpu @ffff88023fc00000 s86720 r8192 d23872 u262144
[    0.000000] pcpu-alloc: s86720 r8192 d23872 u262144 alloc=1*2097152
[    0.000000] pcpu-alloc: [0] 0 1 2 3 4 5 6 7 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2062058
[    0.000000] Policy zone: Normal
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-24-generic root=UUID=52423430-ed6f-46b2-b259-60ddc64c17d0 ro
[    0.000000] PID hash table entries: 4096 (order: 3, 32768 bytes)
[    0.000000] Checking aperture...
[    0.000000] No AGP bridge found
[    0.000000] Calgary: detecting Calgary via BIOS EBDA area
[    0.000000] Calgary: Unable to locate Rio Grande table in EBDA - bailing!
[    0.000000] Memory: 8147572K/8379252K available (7160K kernel code, 1083K rwdata, 3312K rodata, 1364K init, 1420K bss, 231680K reserved)
[    0.000000] SLUB: HWalign=64, Order=0-3, MinObjects=0, CPUs=8, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000]     RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000]     RCU restricting CPUs from NR_CPUS=256 to nr_cpu_ids=8.
[    0.000000]     Offload RCU callbacks from all CPUs
[    0.000000]     Offload RCU callbacks from CPUs: 0-255.
[    0.000000] NR_IRQS:16640 nr_irqs:744 16
[    0.000000] Console: colour VGA+ 80x25
[    0.000000] console [tty0] enabled
[    0.000000] allocated 33554432 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] hpet clockevent registered
[    0.000000] tsc: Fast TSC calibration using PIT
[    0.004000] tsc: Detected 1728.925 MHz processor
[    0.000003] Calibrating delay loop (skipped), value calculated using timer frequency.. 3457.85 BogoMIPS (lpj=6915700)
[    0.000185] pid_max: default: 32768 minimum: 301
[    0.000315] Security Framework initialized
[    0.000430] AppArmor: AppArmor initialized
[    0.000519] Yama: becoming mindful.
[    0.001322] Dentry cache hash table entries: 1048576 (order: 11, 8388608 bytes)
[    0.003736] Inode-cache hash table entries: 524288 (order: 10, 4194304 bytes)
[    0.004815] Mount-cache hash table entries: 256
[    0.005132] Initializing cgroup subsys memory
[    0.005244] Initializing cgroup subsys devices
[    0.005335] Initializing cgroup subsys freezer
[    0.005431] Initializing cgroup subsys blkio
[    0.005523] Initializing cgroup subsys perf_event
[    0.005616] Initializing cgroup subsys hugetlb
[    0.005731] CPU: Physical Processor ID: 0
[    0.005824] CPU: Processor Core ID: 0
[    0.005924] mce: CPU supports 9 MCE banks
[    0.006026] CPU0: Thermal monitoring enabled (TM1)
[    0.006125] Last level iTLB entries: 4KB 512, 2MB 7, 4MB 7
[    0.006125] Last level dTLB entries: 4KB 512, 2MB 32, 4MB 32
[    0.006125] tlb_flushall_shift: 6
[    0.006338] Freeing SMP alternatives memory: 28K (ffffffff81e65000 - ffffffff81e6c000)
[    0.009122] ACPI: Core revision 20130517
[    0.022497] ACPI: All ACPI Tables successfully acquired
[    0.036577] ftrace: allocating 27874 entries in 109 pages
[    0.054203] dmar: Host address width 36
[    0.054301] dmar: DRHD base: 0x000000fed90000 flags: 0x1
[    0.054406] dmar: IOMMU 0: reg_base_addr fed90000 ver 1:0 cap c90780106f0462 ecap f020a2
[    0.055080] dmar: RMRR base: 0x000000bde20000 end: 0x000000bde40fff
[    0.055712] ..TIMER: vector=0x30 apic1=0 pin1=2 apic2=-1 pin2=-1
[    0.095469] smpboot: CPU0: Intel(R) Core(TM) i7 CPU       Q 740  @ 1.73GHz (fam: 06, model: 1e, stepping: 05)
[    0.548345] APIC calibration not consistent with PM-Timer: 447ms instead of 100ms
[    0.548438] APIC delta adjusted to PM-Timer: 831249 (3723954)
[    0.548548] Performance Events: PEBS fmt1+, 16-deep LBR, Nehalem events, Intel PMU driver.
[    0.549011] perf_event_intel: CPU erratum AAJ80 worked around
[    0.549106] perf_event_intel: CPUID marked event: 'bus cycles' unavailable
[    0.549202] ... version:                3
[    0.549293] ... bit width:              48
[    0.549383] ... generic registers:      4
[    0.549478] ... value mask:             0000ffffffffffff
[    0.549577] ... max period:             000000007fffffff
[    0.549675] ... fixed-purpose events:   3
[    0.549770] ... event mask:             000000070000000f
[    0.565366] NMI watchdog: enabled on all CPUs, permanently consumes one hw-PMU counter.
[    0.551855] smpboot: Booting Node   0, Processors  #1 #2 #3 #4 #5 #6 #7 OK
[    0.645576] Brought up 8 CPUs
[    0.645676] smpboot: Total of 8 processors activated (27662.80 BogoMIPS)
[    0.651870] devtmpfs: initialized
[    0.653685] EVM: security.selinux
[    0.653782] EVM: security.SMACK64
[    0.653873] EVM: security.capability
[    0.654013] PM: Registering ACPI NVS region [mem 0xbf75b000-0xbf7befff] (409600 bytes)
[    0.655342] regulator-dummy: no parameters
[    0.655465] RTC time: 21:25:49, date: 06/24/14
[    0.655598] NET: Registered protocol family 16
[    0.655839] ACPI FADT declares the system doesn't support PCIe ASPM, so disable it
[    0.655937] ACPI: bus type PCI registered
[    0.656032] acpiphp: ACPI Hot Plug PCI Controller Driver version: 0.5
[    0.656207] PCI: MMCONFIG for domain 0000 [bus 00-ff] at [mem 0xe0000000-0xefffffff] (base 0xe0000000)
[    0.656306] PCI: MMCONFIG at [mem 0xe0000000-0xefffffff] reserved in E820
[    0.682330] PCI: Using configuration type 1 for base access
[    0.682731] mtrr: your CPUs had inconsistent variable MTRR settings
[    0.682823] mtrr: probably your BIOS does not setup all CPUs.
[    0.682918] mtrr: corrected configuration.
[    0.683913] bio: create slab <bio-0> at 0
[    0.684241] ACPI: Added _OSI(Module Device)
[    0.684334] ACPI: Added _OSI(Processor Device)
[    0.684430] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.684526] ACPI: Added _OSI(Processor Aggregator Device)
[    0.686933] ACPI: EC: Look up EC in DSDT
[    0.689233] ACPI: Executed 2 blocks of module-level executable AML code
[    0.698891] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.704937] ACPI: SSDT 00000000bf691a98 0031C (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.705782] ACPI: Dynamic OEM Table Load:
[    0.706050] ACPI: SSDT           (null) 0031C (v01  PmRef  Cpu0Ist 00003000 INTL 20051117)
[    0.706507] ACPI: SSDT 00000000bf690618 005CD (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.707332] ACPI: Dynamic OEM Table Load:
[    0.707602] ACPI: SSDT           (null) 005CD (v01  PmRef  Cpu0Cst 00003001 INTL 20051117)
[    0.715192] ACPI: SSDT 00000000bf691718 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.716077] ACPI: Dynamic OEM Table Load:
[    0.716353] ACPI: SSDT           (null) 00303 (v01  PmRef    ApIst 00003000 INTL 20051117)
[    0.723008] ACPI: SSDT 00000000bf68fd98 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.723858] ACPI: Dynamic OEM Table Load:
[    0.724126] ACPI: SSDT           (null) 00119 (v01  PmRef    ApCst 00003000 INTL 20051117)
[    0.731653] ACPI: Interpreter enabled
[    0.731759] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20130517/hwxface-571)
[    0.732048] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20130517/hwxface-571)
[    0.732355] ACPI: (supports S0 S3 S4 S5)
[    0.732450] ACPI: Using IOAPIC for interrupt routing
[    0.732594] PCI: Using host bridge windows from ACPI; if necessary, use "pci=nocrs" and report a bug
[    0.733039] ACPI: ACPI Dock Station Driver: 1 docks/bays found
[    0.743942] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-fe])
[    0.744087] \_SB_.PCI0:_OSC invalid UUID
[    0.744089] _OSC request data:1 8 0 
[    0.744133] \_SB_.PCI0:_OSC invalid UUID
[    0.744135] _OSC request data:1 1f 0 
[    0.744139] acpi PNP0A08:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.744246] acpi PNP0A08:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    0.745246] acpiphp_glue: can't evaluate _ADR (0x5)
[    0.745357] PCI host bridge to bus 0000:00
[    0.745453] pci_bus 0000:00: root bus resource [bus 00-fe]
[    0.745542] pci_bus 0000:00: root bus resource [io  0x0000-0x0cf7]
[    0.745638] pci_bus 0000:00: root bus resource [io  0x0d00-0xffff]
[    0.745734] pci_bus 0000:00: root bus resource [mem 0x000a0000-0x000bffff]
[    0.745831] pci_bus 0000:00: root bus resource [mem 0xc0000000-0xfebfffff]
[    0.745929] pci 0000:00:00.0: [8086:d132] type 00 class 0x060000
[    0.746048] pci 0000:00:03.0: [8086:d138] type 01 class 0x060400
[    0.746106] pci 0000:00:03.0: PME# supported from D0 D3hot D3cold
[    0.746197] pci 0000:00:08.0: [8086:d155] type 00 class 0x088000
[    0.746321] pci 0000:00:08.1: [8086:d156] type 00 class 0x088000
[    0.746445] pci 0000:00:08.2: [8086:d157] type 00 class 0x088000
[    0.746564] pci 0000:00:08.3: [8086:d158] type 00 class 0x088000
[    0.746684] pci 0000:00:10.0: [8086:d150] type 00 class 0x088000
[    0.746791] pci 0000:00:10.1: [8086:d151] type 00 class 0x088000
[    0.746943] pci 0000:00:1b.0: [8086:3b56] type 00 class 0x040300
[    0.746974] pci 0000:00:1b.0: reg 0x10: [mem 0xd4100000-0xd4103fff 64bit]
[    0.747056] pci 0000:00:1b.0: PME# supported from D0 D3hot D3cold
[    0.747160] pci 0000:00:1c.0: [8086:3b42] type 01 class 0x060400
[    0.747243] pci 0000:00:1c.0: PME# supported from D0 D3hot D3cold
[    0.747299] pci 0000:00:1c.0: System wakeup disabled by ACPI
[    0.747436] pci 0000:00:1c.1: [8086:3b44] type 01 class 0x060400
[    0.747528] pci 0000:00:1c.1: PME# supported from D0 D3hot D3cold
[    0.747587] pci 0000:00:1c.1: System wakeup disabled by ACPI
[    0.747738] pci 0000:00:1d.0: [8086:3b34] type 00 class 0x0c0320
[    0.748108] pci 0000:00:1d.0: reg 0x10: [mem 0xd4105800-0xd4105bff]
[    0.750173] pci 0000:00:1d.0: PME# supported from D0 D3hot D3cold
[    0.750253] pci 0000:00:1d.0: System wakeup disabled by ACPI
[    0.750399] pci 0000:00:1e.0: [8086:2448] type 01 class 0x060401
[    0.750510] pci 0000:00:1e.0: System wakeup disabled by ACPI
[    0.750663] pci 0000:00:1f.0: [8086:3b03] type 00 class 0x060100
[    0.750869] pci 0000:00:1f.2: [8086:282a] type 00 class 0x010400
[    0.750908] pci 0000:00:1f.2: reg 0x10: [io  0x5048-0x504f]
[    0.750922] pci 0000:00:1f.2: reg 0x14: [io  0x5054-0x5057]
[    0.750935] pci 0000:00:1f.2: reg 0x18: [io  0x5040-0x5047]
[    0.750948] pci 0000:00:1f.2: reg 0x1c: [io  0x5050-0x5053]
[    0.750962] pci 0000:00:1f.2: reg 0x20: [io  0x5020-0x503f]
[    0.750975] pci 0000:00:1f.2: reg 0x24: [mem 0xd4105000-0xd41057ff]
[    0.751034] pci 0000:00:1f.2: PME# supported from D3hot
[    0.751127] pci 0000:00:1f.3: [8086:3b30] type 00 class 0x0c0500
[    0.751153] pci 0000:00:1f.3: reg 0x10: [mem 0xd4105c00-0xd4105cff 64bit]
[    0.751180] pci 0000:00:1f.3: reg 0x20: [io  0x5000-0x501f]
[    0.751304] pci 0000:00:1f.6: [8086:3b32] type 00 class 0x118000
[    0.751338] pci 0000:00:1f.6: reg 0x10: [mem 0xd4104000-0xd4104fff 64bit]
[    0.751561] pci 0000:01:00.0: [1002:94a0] type 00 class 0x030000
[    0.751574] pci 0000:01:00.0: reg 0x10: [mem 0xc0000000-0xcfffffff pref]
[    0.751583] pci 0000:01:00.0: reg 0x14: [io  0x4000-0x40ff]
[    0.751592] pci 0000:01:00.0: reg 0x18: [mem 0xd4000000-0xd400ffff]
[    0.751621] pci 0000:01:00.0: reg 0x30: [mem 0xfffe0000-0xffffffff pref]
[    0.751659] pci 0000:01:00.0: supports D1 D2
[    0.751711] pci 0000:01:00.1: [1002:aa38] type 00 class 0x040300
[    0.751724] pci 0000:01:00.1: reg 0x10: [mem 0xd4010000-0xd4013fff]
[    0.751802] pci 0000:01:00.1: supports D1 D2
[    0.760245] pci 0000:00:03.0: PCI bridge to [bus 01]
[    0.760356] pci 0000:00:03.0:   bridge window [io  0x4000-0x4fff]
[    0.760360] pci 0000:00:03.0:   bridge window [mem 0xd4000000-0xd40fffff]
[    0.760365] pci 0000:00:03.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.760670] pci 0000:02:00.0: [8086:4237] type 00 class 0x028000
[    0.760945] pci 0000:02:00.0: reg 0x10: [mem 0xd3000000-0xd3001fff 64bit]
[    0.762274] pci 0000:02:00.0: PME# supported from D0 D3hot D3cold
[    0.762494] pci 0000:02:00.0: System wakeup disabled by ACPI
[    0.772369] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.772472] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.772481] pci 0000:00:1c.0:   bridge window [mem 0xd3000000-0xd3ffffff]
[    0.772487] pci 0000:00:1c.0:   bridge window [mem 0xd0000000-0xd0ffffff 64bit pref]
[    0.772595] pci 0000:03:00.0: [1969:1063] type 00 class 0x020000
[    0.772627] pci 0000:03:00.0: reg 0x10: [mem 0xd2000000-0xd203ffff 64bit]
[    0.772644] pci 0000:03:00.0: reg 0x18: [io  0x2000-0x207f]
[    0.772766] pci 0000:03:00.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.772816] pci 0000:03:00.0: System wakeup disabled by ACPI
[    0.784271] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.784372] pci 0000:00:1c.1:   bridge window [io  0x2000-0x2fff]
[    0.784381] pci 0000:00:1c.1:   bridge window [mem 0xd2000000-0xd2ffffff]
[    0.784392] pci 0000:00:1c.1:   bridge window [mem 0xd1000000-0xd1ffffff 64bit pref]
[    0.784484] pci 0000:00:1e.0: PCI bridge to [bus 04] (subtractive decode)
[    0.784593] pci 0000:00:1e.0:   bridge window [io  0x0000-0x0cf7] (subtractive decode)
[    0.784595] pci 0000:00:1e.0:   bridge window [io  0x0d00-0xffff] (subtractive decode)
[    0.784598] pci 0000:00:1e.0:   bridge window [mem 0x000a0000-0x000bffff] (subtractive decode)
[    0.784600] pci 0000:00:1e.0:   bridge window [mem 0xc0000000-0xfebfffff] (subtractive decode)
[    0.785480] ACPI: PCI Interrupt Link [LNKA] (IRQs 1 3 4 5 6 7 *10 12 14 15)
[    0.786762] ACPI: PCI Interrupt Link [LNKB] (IRQs 1 3 4 5 6 7 11 12 14 15) *10
[    0.788103] ACPI: PCI Interrupt Link [LNKC] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[    0.789576] ACPI: PCI Interrupt Link [LNKD] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.790856] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.792215] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 *11 12 14 15)
[    0.793465] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *11
[    0.794822] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[    0.796335] ACPI: PCI Root Bridge [CPBG] (domain 0000 [bus ff])
[    0.796434] acpi PNP0A03:00: ACPI _OSC support notification failed, disabling PCIe ASPM
[    0.796527] acpi PNP0A03:00: Unable to request _OSC control (_OSC support mask: 0x08)
[    0.796671] PCI host bridge to bus 0000:ff
[    0.796767] pci_bus 0000:ff: root bus resource [bus ff]
[    0.796863] pci 0000:ff:00.0: [8086:2c52] type 00 class 0x060000
[    0.796913] pci 0000:ff:00.1: [8086:2c81] type 00 class 0x060000
[    0.796966] pci 0000:ff:02.0: [8086:2c90] type 00 class 0x060000
[    0.797014] pci 0000:ff:02.1: [8086:2c91] type 00 class 0x060000
[    0.797063] pci 0000:ff:03.0: [8086:2c98] type 00 class 0x060000
[    0.797109] pci 0000:ff:03.1: [8086:2c99] type 00 class 0x060000
[    0.797158] pci 0000:ff:03.4: [8086:2c9c] type 00 class 0x060000
[    0.797206] pci 0000:ff:04.0: [8086:2ca0] type 00 class 0x060000
[    0.797252] pci 0000:ff:04.1: [8086:2ca1] type 00 class 0x060000
[    0.797298] pci 0000:ff:04.2: [8086:2ca2] type 00 class 0x060000
[    0.797344] pci 0000:ff:04.3: [8086:2ca3] type 00 class 0x060000
[    0.797393] pci 0000:ff:05.0: [8086:2ca8] type 00 class 0x060000
[    0.797438] pci 0000:ff:05.1: [8086:2ca9] type 00 class 0x060000
[    0.797485] pci 0000:ff:05.2: [8086:2caa] type 00 class 0x060000
[    0.797531] pci 0000:ff:05.3: [8086:2cab] type 00 class 0x060000
[    0.797996] ACPI: \_SB_.PCI0: notify handler is installed
[    0.798048] ACPI: \_SB_.CPBG: notify handler is installed
[    0.798061] Found 2 acpi root devices
[    0.798107] ACPI: EC: GPE = 0x16, I/O: command/status = 0x66, data = 0x62
[    0.798309] vgaarb: device added: PCI:0000:01:00.0,decodes=io+mem,owns=io+mem,locks=none
[    0.798405] vgaarb: loaded
[    0.798495] vgaarb: bridge control possible 0000:01:00.0
[    0.798779] SCSI subsystem initialized
[    0.798867] ACPI: bus type ATA registered
[    0.799019] libata version 3.00 loaded.
[    0.799039] ACPI: bus type USB registered
[    0.799150] usbcore: registered new interface driver usbfs
[    0.799245] usbcore: registered new interface driver hub
[    0.799366] usbcore: registered new device driver usb
[    0.799594] PCI: Using ACPI for IRQ routing
[    0.806365] PCI: pci_cache_line_size set to 64 bytes
[    0.806505] e820: reserve RAM buffer [mem 0x0009bc00-0x0009ffff]
[    0.806507] e820: reserve RAM buffer [mem 0xbf682000-0xbfffffff]
[    0.806509] e820: reserve RAM buffer [mem 0xbf75b000-0xbfffffff]
[    0.806511] e820: reserve RAM buffer [mem 0xbf7e3000-0xbfffffff]
[    0.806513] e820: reserve RAM buffer [mem 0xbf800000-0xbfffffff]
[    0.806608] NetLabel: Initializing
[    0.806708] NetLabel:  domain hash size = 128
[    0.806798] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.806894] NetLabel:  unlabeled traffic allowed by default
[    0.807081] HPET: 8 timers in total, 5 timers will be used for per-cpu timer
[    0.807175] hpet0: at MMIO 0xfed00000, IRQs 2, 8, 40, 41, 42, 43, 44, 0
[    0.808090] hpet0: 8 comparators, 64-bit 14.318180 MHz counter
[    0.811238] hpet: hpet2 irq 40 for MSI
[    0.811300] hpet: hpet3 irq 41 for MSI
[    0.811358] hpet: hpet4 irq 42 for MSI
[    0.811414] hpet: hpet5 irq 43 for MSI
[    0.811491] hpet: hpet6 irq 44 for MSI
[    0.811628] Switched to clocksource hpet
[    0.817306] AppArmor: AppArmor Filesystem Enabled
[    0.817433] pnp: PnP ACPI init
[    0.817547] ACPI: bus type PNP registered
[    0.818620] pnp 00:00: [dma 4]
[    0.818668] pnp 00:00: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.818697] pnp 00:01: Plug and Play ACPI device, IDs INT0800 (active)
[    0.818853] pnp 00:02: Plug and Play ACPI device, IDs PNP0103 (active)
[    0.818896] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.818956] system 00:04: [io  0x0680-0x069f] has been reserved
[    0.819051] system 00:04: [io  0x0800-0x080f] has been reserved
[    0.819143] system 00:04: [io  0xffff] has been reserved
[    0.819231] system 00:04: [io  0xffff] has been reserved
[    0.819332] system 00:04: [io  0x0400-0x047f] could not be reserved
[    0.819424] system 00:04: [io  0x0500-0x057f] has been reserved
[    0.819516] system 00:04: [io  0x164e-0x164f] has been reserved
[    0.819604] system 00:04: [io  0x0380-0x038e] has been reserved
[    0.819701] system 00:04: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.819744] pnp 00:05: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.819790] pnp 00:06: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.819838] pnp 00:07: Plug and Play ACPI device, IDs SYN1e0d SYN1e00 SYN0002 PNP0f13 (active)
[    0.819969] pnp 00:08: Plug and Play ACPI device, IDs HPQ0004 (active)
[    0.820243] system 00:09: [mem 0xfed1c000-0xfed1ffff] has been reserved
[    0.820343] system 00:09: [mem 0xfed1b000-0xfed1bfff] has been reserved
[    0.820440] system 00:09: [mem 0xe0000000-0xefffffff] has been reserved
[    0.820532] system 00:09: [mem 0xfed20000-0xfed3ffff] has been reserved
[    0.820627] system 00:09: [mem 0xfed90000-0xfed93fff] could not be reserved
[    0.820715] system 00:09: [mem 0xfed45000-0xfed8ffff] has been reserved
[    0.820816] system 00:09: [mem 0xff000000-0xffffffff] could not be reserved
[    0.820912] system 00:09: [mem 0xfee00000-0xfeefffff] could not be reserved
[    0.821013] system 00:09: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.821340] pnp: PnP ACPI: found 10 devices
[    0.821442] ACPI: bus type PNP unregistered
[    0.828876] pci 0000:01:00.0: no compatible bridge window for [mem 0xfffe0000-0xffffffff pref]
[    0.829021] pci 0000:01:00.0: BAR 6: assigned [mem 0xd4020000-0xd403ffff pref]
[    0.829117] pci 0000:00:03.0: PCI bridge to [bus 01]
[    0.829212] pci 0000:00:03.0:   bridge window [io  0x4000-0x4fff]
[    0.829309] pci 0000:00:03.0:   bridge window [mem 0xd4000000-0xd40fffff]
[    0.829399] pci 0000:00:03.0:   bridge window [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.829492] pci 0000:00:1c.0: PCI bridge to [bus 02]
[    0.829586] pci 0000:00:1c.0:   bridge window [io  0x3000-0x3fff]
[    0.829677] pci 0000:00:1c.0:   bridge window [mem 0xd3000000-0xd3ffffff]
[    0.829775] pci 0000:00:1c.0:   bridge window [mem 0xd0000000-0xd0ffffff 64bit pref]
[    0.829876] pci 0000:00:1c.1: PCI bridge to [bus 03]
[    0.829973] pci 0000:00:1c.1:   bridge window [io  0x2000-0x2fff]
[    0.830067] pci 0000:00:1c.1:   bridge window [mem 0xd2000000-0xd2ffffff]
[    0.830730] pci 0000:00:1c.1:   bridge window [mem 0xd1000000-0xd1ffffff 64bit pref]
[    0.830831] pci 0000:00:1e.0: PCI bridge to [bus 04]
[    0.831288] pci 0000:00:1e.0: setting latency timer to 64
[    0.831298] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.831300] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.831303] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.831305] pci_bus 0000:00: resource 7 [mem 0xc0000000-0xfebfffff]
[    0.831308] pci_bus 0000:01: resource 0 [io  0x4000-0x4fff]
[    0.831310] pci_bus 0000:01: resource 1 [mem 0xd4000000-0xd40fffff]
[    0.831312] pci_bus 0000:01: resource 2 [mem 0xc0000000-0xcfffffff 64bit pref]
[    0.831315] pci_bus 0000:02: resource 0 [io  0x3000-0x3fff]
[    0.831317] pci_bus 0000:02: resource 1 [mem 0xd3000000-0xd3ffffff]
[    0.831319] pci_bus 0000:02: resource 2 [mem 0xd0000000-0xd0ffffff 64bit pref]
[    0.831322] pci_bus 0000:03: resource 0 [io  0x2000-0x2fff]
[    0.831324] pci_bus 0000:03: resource 1 [mem 0xd2000000-0xd2ffffff]
[    0.831326] pci_bus 0000:03: resource 2 [mem 0xd1000000-0xd1ffffff 64bit pref]
[    0.831329] pci_bus 0000:04: resource 4 [io  0x0000-0x0cf7]
[    0.831331] pci_bus 0000:04: resource 5 [io  0x0d00-0xffff]
[    0.831333] pci_bus 0000:04: resource 6 [mem 0x000a0000-0x000bffff]
[    0.831335] pci_bus 0000:04: resource 7 [mem 0xc0000000-0xfebfffff]
[    0.831377] NET: Registered protocol family 2
[    0.831718] TCP established hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.832292] TCP bind hash table entries: 65536 (order: 8, 1048576 bytes)
[    0.832785] TCP: Hash tables configured (established 65536 bind 65536)
[    0.832903] TCP: reno registered
[    0.833003] UDP hash table entries: 4096 (order: 5, 131072 bytes)
[    0.833175] UDP-Lite hash table entries: 4096 (order: 5, 131072 bytes)
[    0.833408] NET: Registered protocol family 1
[    0.847833] pci 0000:01:00.0: Boot video device
[    0.847896] PCI: CLS 64 bytes, default 64
[    0.847949] Trying to unpack rootfs image as initramfs...
[    1.230494] Freeing initrd memory: 17032K (ffff880035eac000 - ffff880036f4e000)
[    1.230611] PCI-DMA: Using software bounce buffering for IO (SWIOTLB)
[    1.230717] software IO TLB [mem 0xbb682000-0xbf682000] (64MB) mapped at [ffff8800bb682000-ffff8800bf681fff]
[    1.230857] Simple Boot Flag at 0x44 set to 0x1
[    1.231290] Scanning for low memory corruption every 60 seconds
[    1.231831] Initialise module verification
[    1.231975] audit: initializing netlink socket (disabled)
[    1.232086] type=2000 audit(1403645149.768:1): initialized
[    1.268558] bounce pool size: 64 pages
[    1.268666] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.270270] zbud: loaded
[    1.270546] VFS: Disk quotas dquot_6.5.2
[    1.270690] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
[    1.271385] fuse init (API version 7.22)
[    1.271583] msgmni has been set to 15946
[    1.272532] Key type asymmetric registered
[    1.272632] Asymmetric key parser 'x509' registered
[    1.272765] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.272919] io scheduler noop registered
[    1.272999] io scheduler deadline registered (default)
[    1.273125] io scheduler cfq registered
[    1.273455] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.273568] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.273724] intel_idle: MWAIT substates: 0x1120
[    1.273746] intel_idle: v0.4 model 0x1E
[    1.273748] intel_idle: lapic_timer_reliable_states 0x2
[    1.274484] ACPI: AC Adapter [ACAD] (on-line)
[    1.274699] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0
[    1.274800] ACPI: Power Button [PWRB]
[    1.275024] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    1.275537] ACPI: Lid Switch [LID0]
[    1.275680] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    1.275783] ACPI: Power Button [PWRF]
[    1.275956] ACPI: Requesting acpi_cpufreq
[    1.294342] thermal LNXTHERM:00: registered as thermal_zone0
[    1.294440] ACPI: Thermal Zone [TZ01] (63 C)
[    1.294569] GHES: HEST is not enabled!
[    1.294776] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.294929] ACPI: Battery Slot [BAT0] (battery absent)
[    1.295299] ACPI: Battery Slot [BAT1] (battery absent)
[    1.296919] Linux agpgart interface v0.103
[    1.298534] brd: module loaded
[    1.299504] loop: module loaded
[    1.299974] libphy: Fixed MDIO Bus: probed
[    1.300155] tun: Universal TUN/TAP device driver, 1.6
[    1.300256] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.300407] PPP generic driver version 2.4.2
[    1.300555] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.300644] ehci-pci: EHCI PCI platform driver
[    1.300905] ehci-pci 0000:00:1d.0: setting latency timer to 64
[    1.300920] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    1.301025] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    1.301143] ehci-pci 0000:00:1d.0: debug port 2
[    1.305156] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    1.305183] ehci-pci 0000:00:1d.0: irq 20, io mem 0xd4105800
[    1.315441] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    1.315570] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.315667] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.315760] usb usb1: Product: EHCI Host Controller
[    1.315855] usb usb1: Manufacturer: Linux 3.11.0-24-generic ehci_hcd
[    1.315955] usb usb1: SerialNumber: 0000:00:1d.0
[    1.316164] hub 1-0:1.0: USB hub found
[    1.316268] hub 1-0:1.0: 2 ports detected
[    1.316477] ehci-platform: EHCI generic platform driver
[    1.316583] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.316682] ohci-pci: OHCI PCI platform driver
[    1.316787] ohci-platform: OHCI generic platform driver
[    1.316889] uhci_hcd: USB Universal Host Controller Interface driver
[    1.317052] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.333161] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.333265] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.333486] mousedev: PS/2 mouse device common for all mice
[    1.334421] rtc_cmos 00:05: RTC can wake from S4
[    1.334669] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.334803] rtc_cmos 00:05: alarms up to one year, y3k, 242 bytes nvram, hpet irqs
[    1.334965] device-mapper: uevent: version 1.0.3
[    1.335139] device-mapper: ioctl: 4.25.0-ioctl (2013-06-26) initialised: dm-devel@redhat.com
[    1.335396] cpuidle: using governor ladder
[    1.335680] cpuidle: using governor menu
[    1.335785] ledtrig-cpu: registered to indicate activity on CPUs
[    1.335971] TCP: cubic registered
[    1.336161] NET: Registered protocol family 10
[    1.336477] NET: Registered protocol family 17
[    1.336585] Key type dns_resolver registered
[    1.337004] PM: Hibernation image not present or could not be loaded.
[    1.337008] Loading module verification certificates
[    1.338392] MODSIGN: Loaded cert 'Magrathea: Glacier signing key: 1bd3600f2d18ce5a330956c843185cbf76fa7082'
[    1.338502] registered taskstats version 1
[    1.341205] Key type trusted registered
[    1.344463] Key type encrypted registered
[    1.348734] AppArmor: AppArmor sha1 policy hashing enabled
[    1.349136] regulator-dummy: disabling
[    1.349649]   Magic number: 2:407:450
[    1.349761]  machinecheck: hash matches
[    1.350008] rtc_cmos 00:05: setting system clock to 2014-06-24 21:25:50 UTC (1403645150)
[    1.352109] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.352202] EDD information not available.
[    1.353368] Freeing unused kernel memory: 1364K (ffffffff81d10000 - ffffffff81e65000)
[    1.353466] Write protecting the kernel read-only data: 12288k
[    1.353947] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.356075] Freeing unused kernel memory: 1020K (ffff880001701000 - ffff880001800000)
[    1.357649] Freeing unused kernel memory: 784K (ffff880001b3c000 - ffff880001c00000)
[    1.398087] ahci 0000:00:1f.2: version 3.0
[    1.398276] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    1.398359] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 3 Gbps 0x23 impl RAID mode
[    1.398430] ahci 0000:00:1f.2: flags: 64bit ncq sntf ilck pm led clo pio slum part ems sxs apst 
[    1.398501] ahci 0000:00:1f.2: setting latency timer to 64
[    1.412054] scsi0 : ahci
[    1.412325] scsi1 : ahci
[    1.412582] scsi2 : ahci
[    1.412789] scsi3 : ahci
[    1.412987] scsi4 : ahci
[    1.413193] scsi5 : ahci
[    1.413360] ata1: SATA max UDMA/133 abar m2048@0xd4105000 port 0xd4105100 irq 45
[    1.413454] ata2: SATA max UDMA/133 abar m2048@0xd4105000 port 0xd4105180 irq 45
[    1.413547] ata3: DUMMY
[    1.413627] ata4: DUMMY
[    1.413714] ata5: DUMMY
[    1.413784] ata6: SATA max UDMA/133 abar m2048@0xd4105000 port 0xd4105380 irq 45
[    1.423853] atl1c 0000:03:00.0: version 1.0.1.1-NAPI
[    1.627597] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    1.731498] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.733349] ata1.00: ATA-8: ST9320423AS, 0006HPM1, max UDMA/100
[    1.733461] ata1.00: 625142448 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.735491] ata2: SATA link down (SStatus 0 SControl 300)
[    1.735622] ata6: SATA link down (SStatus 0 SControl 300)
[    1.735794] ata1.00: configured for UDMA/100
[    1.736308] scsi 0:0:0:0: Direct-Access     ATA      ST9320423AS      0006 PQ: 0 ANSI: 5
[    1.736724] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.736769] sd 0:0:0:0: [sda] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[    1.737102] sd 0:0:0:0: [sda] Write Protect is off
[    1.737216] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.737419] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.760153] usb 1-1: New USB device found, idVendor=8087, idProduct=0020
[    1.760219] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.760716] hub 1-1:1.0: USB hub found
[    1.761050] hub 1-1:1.0: 8 ports detected
[    1.787552]  sda: sda1 sda2 < sda5 >
[    1.789982] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.031298] usb 1-1.5: new high-speed USB device number 3 using ehci-pci
[    2.126995] usb 1-1.5: New USB device found, idVendor=04f2, idProduct=b16c
[    2.127065] usb 1-1.5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.127136] usb 1-1.5: Product: HP Webcam
[    2.127194] usb 1-1.5: Manufacturer: Chicony Electronics Co., Ltd.
[    2.169825] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.199338] usb 1-1.6: new full-speed USB device number 4 using ehci-pci
[    2.227187] tsc: Refined TSC clocksource calibration: 1728.999 MHz
[    2.295576] usb 1-1.6: New USB device found, idVendor=03f0, idProduct=231d
[    2.295649] usb 1-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.295730] usb 1-1.6: Product: HP Integrated Module
[    2.295792] usb 1-1.6: Manufacturer: Broadcom Corp
[    2.367352] usb 1-1.7: new low-speed USB device number 5 using ehci-pci
[    2.465938] usb 1-1.7: New USB device found, idVendor=045e, idProduct=00cb
[    2.466007] usb 1-1.7: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.466138] usb 1-1.7: Product: Microsoft Basic Optical Mouse v2.0 
[    2.466210] usb 1-1.7: Manufacturer: Microsoft 
[    3.227341] Switched to clocksource tsc
[   14.456091] Adding 16766972k swap on /dev/sda5.  Priority:-1 extents:1 across:16766972k FS
[   14.592649] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.705913] hp_accel: laptop model unknown, using default axes configuration
[   14.707208] lis3lv02d: 8 bits sensor found
[   14.707428] wmi: Mapper loaded
[   14.720143] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20130517/utaddress-251)
[   14.720154] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \_SB_.PCI0.IEIT.SGPE 2 (20130517/utaddress-251)
[   14.720160] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.720170] ACPI Warning: 0x0000000000000540-0x000000000000054f SystemIO conflicts with Region \GPIO 1 (20130517/utaddress-251)
[   14.720176] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.720179] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20130517/utaddress-251)
[   14.720185] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.720187] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20130517/utaddress-251)
[   14.720194] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   14.720196] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   14.721677] [drm] Initialized drm 1.1.0 20060810
[   14.722449] acpi device:27: registered as cooling_device8
[   14.724720] intel ips 0000:00:1f.6: Non-IPS CPU detected.
[   14.724725] intel ips 0000:00:1f.6: IPS not supported on this CPU
[   14.732126] EDAC MC: Ver: 3.0.0
[   14.732358] acpi device:29: registered as cooling_device9
[   14.732403] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   14.732475] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:25/LNXVIDEO:01/input/input4
[   14.734513] EDAC i7core: Device not found: dev 00.0 PCI ID 8086:2c50
[   14.746462] cfg80211: Calling CRDA to update world regulatory domain
[   14.753284] microcode: CPU0 sig=0x106e5, pf=0x10, revision=0x4
[   14.753892] input: ST LIS3LV02DL Accelerometer as /devices/platform/lis3lv02d/input/input5
[   14.756736] Intel(R) Wireless WiFi driver for Linux, in-tree:
[   14.756740] Copyright(c) 2003-2013 Intel Corporation
[   14.756963] iwlwifi 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[   14.757204] iwlwifi 0000:02:00.0: irq 46 for MSI/MSI-X
[   14.771006] lp: driver loaded but no devices found
[   14.779835] [drm] radeon kernel modesetting enabled.
[   14.782025] [drm] initializing kernel modesetting (RV740 0x1002:0x94A0 0x103C:0x7009).
[   14.782054] [drm] register mmio base: 0xD4000000
[   14.782057] [drm] register mmio size: 65536
[   14.782169] ATOM BIOS: BR35781.001
[   14.782244] radeon 0000:01:00.0: VRAM: 1024M 0x0000000000000000 - 0x000000003FFFFFFF (1024M used)
[   14.782248] radeon 0000:01:00.0: GTT: 512M 0x0000000040000000 - 0x000000005FFFFFFF
[   14.782252] [drm] Detected VRAM RAM=1024M, BAR=256M
[   14.782254] [drm] RAM width 128bits DDR
[   14.782332] [TTM] Zone  kernel: Available graphics memory: 4083900 kiB
[   14.782334] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[   14.782337] [TTM] Initializing pool allocator
[   14.782345] [TTM] Initializing DMA pool allocator
[   14.782371] [drm] radeon: 1024M of VRAM memory ready
[   14.782373] [drm] radeon: 512M of GTT memory ready.
[   14.782389] [drm] Loading RV730 Microcode
[   14.809557] type=1400 audit(1403645163.958:2): apparmor="STATUS" operation="profile_load" parent=426 profile="unconfined" name="/sbin/dhclient" pid=490 comm="apparmor_parser"
[   14.809566] type=1400 audit(1403645163.958:3): apparmor="STATUS" operation="profile_load" parent=426 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=490 comm="apparmor_parser"
[   14.809571] type=1400 audit(1403645163.958:4): apparmor="STATUS" operation="profile_load" parent=426 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=490 comm="apparmor_parser"
[   14.810318] type=1400 audit(1403645163.962:5): apparmor="STATUS" operation="profile_replace" parent=426 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=490 comm="apparmor_parser"
[   14.810326] type=1400 audit(1403645163.962:6): apparmor="STATUS" operation="profile_replace" parent=426 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=490 comm="apparmor_parser"
[   14.810711] type=1400 audit(1403645163.962:7): apparmor="STATUS" operation="profile_replace" parent=426 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=490 comm="apparmor_parser"
[   14.818173] snd_hda_intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[   14.830246] mute LED gpio 8 polarity 1
[   14.830466] autoconfig: line_outs=1 (0xd/0x0/0x0/0x0/0x0) type:speaker
[   14.830468]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   14.830470]    hp_outs=1 (0xa/0x0/0x0/0x0/0x0)
[   14.830471]    mono: mono_out=0x0
[   14.830472]    inputs:
[   14.830474]      Internal Mic=0x18
[   14.830476]      Mic=0xb
[   14.849993] input: HDA Intel MID Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   14.850118] input: HDA Intel MID Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   14.940987] input: HP WMI hotkeys as /devices/virtual/input/input8
[   14.970763] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   14.971635] [drm] enabling PCIE gen 2 link speeds, disable with radeon.pcie_gen2=0
[   14.990289] [drm] PCIE GART of 512M enabled (table at 0x000000000025D000).
[   14.990372] radeon 0000:01:00.0: WB enabled
[   14.990377] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000040000c00 and cpu addr 0xffff88021f7d1c00
[   14.990379] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000040000c0c and cpu addr 0xffff88021f7d1c0c
[   14.991943] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x000000000005c598 and cpu addr 0xffffc9001151c598
[   14.991946] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   14.991947] [drm] Driver supports precise vblank timestamp query.
[   14.991969] radeon 0000:01:00.0: irq 48 for MSI/MSI-X
[   14.991982] radeon 0000:01:00.0: radeon: using MSI.
[   14.992011] [drm] radeon: irq initialized.
[   15.038606] [drm] ring test on 0 succeeded in 1 usecs
[   15.038666] [drm] ring test on 3 succeeded in 1 usecs
[   15.042546] iwlwifi 0000:02:00.0: loaded firmware version 8.83.5.1 build 33692 op_mode iwldvm
[   15.061566] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   15.061570] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   15.061572] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   15.061574] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_P2P disabled
[   15.061577] iwlwifi 0000:02:00.0: Detected Intel(R) WiFi Link 5100 AGN, REV=0x54
[   15.061792] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   15.100094] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   15.224232] [drm] ring test on 5 succeeded in 1 usecs
[   15.224236] [drm] UVD initialized successfully.
[   15.224535] [drm] ib test on ring 0 succeeded in 0 usecs
[   15.224558] [drm] ib test on ring 3 succeeded in 0 usecs
[   15.296420] Linux video capture interface: v2.00
[   15.304842] uvcvideo: Found UVC 1.00 device HP Webcam (04f2:b16c)
[   15.306176] input: HP Webcam as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.5/1-1.5:1.0/input/input9
[   15.306256] usbcore: registered new interface driver uvcvideo
[   15.306258] USB Video Class driver (1.1.1)
[   15.354516] hidraw: raw HID events driver (C) Jiri Kosina
[   15.373225] usbcore: registered new interface driver usbhid
[   15.373228] usbhid: USB HID core driver
[   15.374755] [drm] ib test on ring 5 succeeded
[   15.375015] [drm] Radeon Display Connectors
[   15.375018] [drm] Connector 0:
[   15.375019] [drm]   LVDS-1
[   15.375022] [drm]   DDC: 0x7f68 0x7f68 0x7f6c 0x7f6c 0x7f70 0x7f70 0x7f74 0x7f74
[   15.375023] [drm]   Encoders:
[   15.375024] [drm]     LCD1: INTERNAL_UNIPHY2
[   15.375025] [drm] Connector 1:
[   15.375027] [drm]   HDMI-A-1
[   15.375028] [drm]   HPD1
[   15.375030] [drm]   DDC: 0x7e40 0x7e40 0x7e44 0x7e44 0x7e48 0x7e48 0x7e4c 0x7e4c
[   15.375031] [drm]   Encoders:
[   15.375033] [drm]     DFP1: INTERNAL_UNIPHY
[   15.375055] [drm] Internal thermal controller with fan control
[   15.375090] [drm] radeon: power management initialized
[   15.383029] microcode: CPU1 sig=0x106e5, pf=0x10, revision=0x4
[   15.432723] cfg80211: World regulatory domain updated:
[   15.432727] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   15.432730] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.432732] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.432734] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   15.432736] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.432738] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   15.434041] microcode: CPU2 sig=0x106e5, pf=0x10, revision=0x4
[   15.434683] microcode: CPU3 sig=0x106e5, pf=0x10, revision=0x4
[   15.435289] microcode: CPU4 sig=0x106e5, pf=0x10, revision=0x4
[   15.435890] microcode: CPU5 sig=0x106e5, pf=0x10, revision=0x4
[   15.436485] microcode: CPU6 sig=0x106e5, pf=0x10, revision=0x4
[   15.437057] microcode: CPU7 sig=0x106e5, pf=0x10, revision=0x4
[   15.437739] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   15.458129] input: Microsoft  Microsoft Basic Optical Mouse v2.0  as /devices/pci0000:00/0000:00:1d.0/usb1/1-1/1-1.7/1-1.7:1.0/input/input10
[   15.458187] kvm: VM_EXIT_LOAD_IA32_PERF_GLOBAL_CTRL does not work properly. Using workaround
[   15.459046] hid-generic 0003:045E:00CB.0001: input,hidraw0: USB HID v1.11 Mouse [Microsoft  Microsoft Basic Optical Mouse v2.0 ] on usb-0000:00:1d.0-1.7/input0
[   16.338177] [drm] fb mappable at 0xC035F000
[   16.338180] [drm] vram apper at 0xC0000000
[   16.338181] [drm] size 4325376
[   16.338182] [drm] fb depth is 24
[   16.338183] [drm]    pitch is 5632
[   16.338415] fbcon: radeondrmfb (fb0) is primary device
[   16.813228] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   16.996554] Console: switching to colour frame buffer device 170x48
[   17.000066] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
[   17.000067] radeon 0000:01:00.0: registered panic notifier
[   17.000080] [drm] Initialized radeon 2.34.0 20080528 for 0000:01:00.0 on minor 0
[   17.000267] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   17.000271] hda-intel 0000:01:00.1: Using LPIB position fix
[   17.000315] snd_hda_intel 0000:01:00.1: irq 49 for MSI/MSI-X
[   17.002780] hda-intel 0000:01:00.1: Enable sync_write for stable communication
[   17.007107] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/0000:01:00.1/sound/card1/input11
[   17.791380] Bluetooth: Core ver 2.16
[   17.791401] NET: Registered protocol family 31
[   17.791408] Bluetooth: HCI device and connection manager initialized
[   17.791418] Bluetooth: HCI socket layer initialized
[   17.791421] Bluetooth: L2CAP socket layer initialized
[   17.791437] Bluetooth: SCO socket layer initialized
[   17.795169] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   17.795174] Bluetooth: BNEP filters: protocol multicast
[   17.795182] Bluetooth: BNEP socket layer initialized
[   17.796140] Bluetooth: RFCOMM TTY layer initialized
[   17.796149] Bluetooth: RFCOMM socket layer initialized
[   17.796151] Bluetooth: RFCOMM ver 1.11
[   17.965272] WARNING! power/level is deprecated; use power/control instead
[   17.969233] usbcore: registered new interface driver btusb
[   18.433098] type=1400 audit(1403645167.586:8): apparmor="STATUS" operation="profile_load" parent=976 profile="unconfined" name="/usr/lib/libvirt/virt-aa-helper" pid=987 comm="apparmor_parser"
[   18.434829] type=1400 audit(1403645167.586:9): apparmor="STATUS" operation="profile_replace" parent=976 profile="unconfined" name="/sbin/dhclient" pid=984 comm="apparmor_parser"
[   18.434838] type=1400 audit(1403645167.586:10): apparmor="STATUS" operation="profile_replace" parent=976 profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=984 comm="apparmor_parser"
[   18.434844] type=1400 audit(1403645167.586:11): apparmor="STATUS" operation="profile_replace" parent=976 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=984 comm="apparmor_parser"
[   18.502761] ppdev: user-space parallel port driver
[   19.077587] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   19.080695] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[   19.180475] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   19.183537] iwlwifi 0000:02:00.0: Radio type=0x1-0x2-0x0
[   19.213382] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.214102] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   19.218396] atl1c 0000:03:00.0: irq 50 for MSI/MSI-X
[   19.233390] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.237647] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.466379] vboxdrv: module verification failed: signature and/or required key missing - tainting kernel
[   19.469551] vboxdrv: Found 8 processor cores.
[   19.469795] vboxdrv: fAsync=0 offMin=0xdf offMax=0x1d77
[   19.469884] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   19.469886] vboxdrv: Successfully loaded version 4.2.16_Ubuntu (interface 0x001a0005).
[   19.499599] vboxpci: IOMMU not found (not registered)
[   22.205690] Ebtables v2.0 registered
[   22.593511] ip_tables: (C) 2000-2006 Netfilter Core Team
[   22.601986] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   25.338841] wlan0: authenticate with 30:46:9a:8a:03:2e
[   25.341708] wlan0: send auth to 30:46:9a:8a:03:2e (try 1/3)
[   25.352050] wlan0: authenticated
[   25.353292] wlan0: associate with 30:46:9a:8a:03:2e (try 1/3)
[   25.358232] wlan0: RX AssocResp from 30:46:9a:8a:03:2e (capab=0x411 status=0 aid=5)
[   25.362561] wlan0: associated
[   25.362604] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   29.788610] Bridge firewalling registered
[   29.879830] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   29.906160] IPv6: ADDRCONF(NETDEV_UP): virbr0: link is not ready
[  309.783764] wlan0: deauthenticating from 30:46:9a:8a:03:2e by local choice (reason=3)
[  309.798066] cfg80211: Calling CRDA to update world regulatory domain
[  309.803748] cfg80211: World regulatory domain updated:
[  309.803755] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  309.803760] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  309.803765] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  309.803769] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  309.803772] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  309.803776] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  312.963433] wlan0: authenticate with a0:f3:c1:74:a6:27
[  312.969241] wlan0: send auth to a0:f3:c1:74:a6:27 (try 1/3)
[  312.971809] wlan0: authenticated
[  312.975963] wlan0: associate with a0:f3:c1:74:a6:27 (try 1/3)
[  312.979981] wlan0: RX AssocResp from a0:f3:c1:74:a6:27 (capab=0x431 status=0 aid=3)
[  312.982631] wlan0: associated
[ 1826.977770] wlan0: AP a0:f3:c1:74:a6:27 changed bandwidth, new config is 2462 MHz, width 1 (2462/0 MHz)
[ 1827.903877] wlan0: AP a0:f3:c1:74:a6:27 changed bandwidth, new config is 2462 MHz, width 2 (2452/0 MHz)
[ 1834.543932] wlan0: AP a0:f3:c1:74:a6:27 changed bandwidth, new config is 2462 MHz, width 1 (2462/0 MHz)
[ 1834.544105] wlan0: AP a0:f3:c1:74:a6:27 changed bandwidth, new config is 2462 MHz, width 2 (2452/0 MHz)
[ 1887.947343] wlan0: AP a0:f3:c1:74:a6:27 changed bandwidth, new config is 2462 MHz, width 1 (2462/0 MHz)
[ 1888.879139] wlan0: AP a0:f3:c1:74:a6:27 changed bandwidth, new config is 2462 MHz, width 2 (2452/0 MHz)
[ 2468.693104] wlan0: AP a0:f3:c1:74:a6:27 changed bandwidth, new config is 2462 MHz, width 1 (2462/0 MHz)
[ 2469.716016] wlan0: AP a0:f3:c1:74:a6:27 changed bandwidth, new config is 2462 MHz, width 2 (2452/0 MHz)
[ 3865.350534] perf samples too long (2501 > 2500), lowering kernel.perf_event_max_sample_rate to 50000
[ 4370.875872] atl1c 0000:03:00.0: vpd r/w failed.  This is likely a firmware bug on this device.  Contact the card vendor for a firmware update.

```

At some point doing my attempt to diagnose the problem, I removed the "quiet splash" from the entry from the /etc/default/grub file to:
GRUB_CMDLINE_LINUX_DEFAULT=

This gave me the output just before the computer stuck.
```

[     0.559738] perf_event_intel: CPUID marked event: 'bus cycles' unavailable
[     0.XXXXXX] ... version:                       3
[     0.XXXXXX] ... bit widh:                      48
[     0.XXXXXX] ... generic_registers:             4
[     0.XXXXXX] ... value mask:                    0000ffffffffffff
[     0.XXXXXX] ... max period:                    000000007fffffff
[     0.XXXXXX] ... fixed-purpose events:          3
[     0.XXXXXX] ... event mask:                    000000007000000f
[     0.XXXXXX] smpboot: Booting Node    0, Processors #1

```
very similar to the attached image in this bug: [https://bugzilla.kernel.org/show_bug.cgi?id=60635](https://bugzilla.kernel.org/show_bug.cgi?id=60635)

Image: (not mine!)
[https://launchpadlibrarian.net/145295798/3.11-rc1_boot_stuck.jpg](https://launchpadlibrarian.net/145295798/3.11-rc1_boot_stuck.jpg)

This occurence have since (after Boot-Repair) ceased. Instead the system goes black on un-successfull boot attempts.

[B]#2 - Black screen after closing/re-opening lid and suspension.

[/B]As fwts requires the closing of the lid in order to perform interactive tests, I have not been able to generate a log file yet. 
I will try to come up with a solution.

It is probably worth to mention that the computer have been subject to some overheating, as HP apperently figured it was a great idea
to lead the hot air out through the bottom of the computer. The computer have never had a working alt(@) or alt gr button.
II suspect that might be a worn cable, and not a kernel related issue though.

---

