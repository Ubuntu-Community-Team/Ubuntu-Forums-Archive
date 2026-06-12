---
title: "Crash after wake up computer"
date: 2024-08-22
forum: General Help
---

### Post by pritel on 2024-08-22
After sleep of computer is not possible wake up computer. If I try wake up, it fully restart computer. 
(I use HDD, not SSD).

Can you me help, please?

More information about my OS and hardware my computer is here
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/2076536](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/2076536)

---

### Post by currentshaft on 2024-08-22
>,

---

### Post by pritel on 2024-08-22
[**[COLOR=#000000]currentshaft[/COLOR]**]("https://ubuntuforums.org/member.php?u=2187870")**[COLOR=#000000]: thank you very much for answer.[/COLOR]**[B][COLOR=#000000] I try send you more information.
[/COLOR]I send video for you about crash here: [https://youtu.be/ygt6BYrwRTE?si=ccQN6Dg_WhhkL7VJ](https://youtu.be/ygt6BYrwRTE?si=ccQN6Dg_WhhkL7VJ)[/B]
[B]

Hardware and OS info
[/B]```
hostnamectl
 Static hostname: uzivatel
       Icon name: computer-laptop
         Chassis: laptop &#128187;
      Machine ID: d5011fe0ec914e429e6cdb40885d15f6
         Boot ID: 8890eb6439c640cf94d4e2ff137b972f
Operating System: Ubuntu 24.04 LTS                
          Kernel: Linux 6.8.0-41-generic
    Architecture: x86-64
 Hardware Vendor: Hewlett-Packard
  Hardware Model: HP ProBook 6450b
Firmware Version: 68CDE Ver. F.06
   Firmware Date: Tue 2011-01-11
    Firmware Age: 13y 7month 1w 4d  
```[B]

Hardware info[/B]
```
System:
  Host: uzivatel Kernel: 6.8.0-41-generic arch: x86_64 bits: 64
  Desktop: GNOME v: 46.0 Distro: Ubuntu 24.04 LTS (Noble Numbat)
Machine:
  Type: Laptop System: Hewlett-Packard product: HP ProBook 6450b v: N/A
    serial: <superuser required>
  Mobo: Hewlett-Packard model: 146D v: KBC Version 73.13
    serial: <superuser required> BIOS: Hewlett-Packard v: 68CDE Ver. F.06
    date: 01/11/2011
Battery:
  ID-1: BAT0 charge: 25.8 Wh (100.0%) condition: 25.8/51.0 Wh (50.6%)
CPU:
  Info: dual core model: Intel Core i5 M 540 bits: 64 type: MT MCP cache:
    L2: 512 KiB
  Speed (MHz): avg: 1264 min/max: 1199/2534 cores: 1: 1197 2: 1199 3: 1463
    4: 1199
Graphics:
  Device-1: Intel Core Processor Integrated Graphics driver: i915 v: kernel
  Device-2: Chicony HP Laptop Integrated Webcam [2 MP Fixed]
    driver: uvcvideo type: USB
  Display: x11 server: X.Org v: 21.1.11 with: Xwayland v: 23.2.6 driver: X:
    loaded: modesetting unloaded: fbdev,vesa dri: crocus gpu: i915
    resolution: 1600x900~60Hz
  API: EGL v: 1.5 drivers: crocus,swrast platforms: x11,surfaceless,device
  API: OpenGL v: 4.5 compat-v: 2.1 vendor: intel mesa v: 24.0.9-0ubuntu0.1
    renderer: Mesa Intel HD Graphics (ILK)
Audio:
  Device-1: Intel 5 Series/3400 Series High Definition Audio
    driver: snd_hda_intel
  API: ALSA v: k6.8.0-41-generic status: kernel-api
  Server-1: PipeWire v: 1.0.5 status: active
Network:
  Device-1: Intel 82577LC Gigabit Network driver: e1000e
  IF: enp0s25 state: up speed: 100 Mbps duplex: full mac: 2c:41:38:02:87:0a
  Device-2: Intel Centrino Advanced-N 6200 driver: iwlwifi
  IF: wlo1 state: down mac: 18:3d:a2:8b:be:28
Drives:
  Local Storage: total: 931.51 GiB used: 71.02 GiB (7.6%)
  ID-1: /dev/sda vendor: Toshiba model: MQ02ABD100H size: 931.51 GiB
Partition:
  ID-1: / size: 114.98 GiB used: 33.78 GiB (29.4%) fs: ext4 dev: /dev/sda3
  ID-2: /home size: 626.76 GiB used: 37.24 GiB (5.9%) fs: ext4
    dev: /dev/sda5
Swap:
  ID-1: swap-1 type: file size: 4 GiB used: 0 KiB (0.0%) file: /swap.img
Sensors:
  System Temperatures: cpu: 52.0 C mobo: N/A
  Fan Speeds (rpm): N/A
Info:
  Memory: total: 8 GiB available: 7.55 GiB used: 2.43 GiB (32.2%)
  Processes: 256 Uptime: 4m Shell: Bash inxi: 3.3.34
```

** RAM info**
```
sudo dmidecode --type memory
# dmidecode 3.5
Getting SMBIOS data from sysfs.
SMBIOS 2.6 present.

Handle 0x0003, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 8 GB
    Error Information Handle: Not Provided
    Number Of Devices: 2

Handle 0x0004, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0003
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 4 GB
    Form Factor: SODIMM
    Set: None
    Locator: Top
    Bank Locator: BANK 0
    Type: DDR3
    Type Detail: Synchronous
    Speed: 1333 MT/s
    Manufacturer: 0000
    Serial Number: 54578546
    Asset Tag: Unknown
    Part Number: MLLSE 1333 4GB    

Handle 0x0006, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x0003
    Error Information Handle: Not Provided
    Total Width: 64 bits
    Data Width: 64 bits
    Size: 4 GB
    Form Factor: SODIMM
    Set: None
    Locator: Bottom
    Bank Locator: BANK 2
    Type: DDR3
    Type Detail: Synchronous
    Speed: 1333 MT/s
    Manufacturer: 0000
    Serial Number: 54578546
    Asset Tag: Unknown
    Part Number: MLLSE 1333 4GB    

```

**BIOS**
```
sudo dmidecode -s bios-version
68CDE Ver. F.06
```

**BIOS**
```
sudo dmidecode --type bios
# dmidecode 3.5
Getting SMBIOS data from sysfs.
SMBIOS 2.6 present.

Handle 0x0009, DMI type 0, 24 bytes
BIOS Information
    Vendor: Hewlett-Packard
    Version: 68CDE Ver. F.06
    Release Date: 01/11/2011
    Address: 0xF0000
    Runtime Size: 64 kB
    ROM Size: 2560 kB
    Characteristics:
        PCI is supported
        PC Card (PCMCIA) is supported
        BIOS is upgradeable
        BIOS shadowing is allowed
        Boot from CD is supported
        Selectable boot is supported
        EDD is supported
        Print screen service is supported (int 5h)
        8042 keyboard services are supported (int 9h)
        Serial services are supported (int 14h)
        Printer services are supported (int 17h)
        ACPI is supported
        USB legacy is supported
        Smart battery is supported
        BIOS boot specification is supported
        Function key-initiated network boot is supported
        Targeted content distribution is supported
    BIOS Revision: 15.6
    Firmware Revision: 115.19

Handle 0x0017, DMI type 13, 22 bytes
BIOS Language Information
    Language Description Format: Abbreviated
    Installable Languages: 12
        enUS
        daDK
        nlNL
        fiFI
        frFR
        deDE
        itIT
        jaJP
        noNO
        ptPT
        esES
        svSE
    Currently Installed Language: enUS


```

---

