---
title: "Grub2 doesn't recognise W11"
date: 2024-01-05
forum: General Help
---

### Post by AllanP on 2024-01-05
I've tried this on all my OS's (Ubuntu, Debian and Mint; didn't try it on my Fedora) to recognise and put Windows 11 into Grub. I have searched around and tried different scenarios, but couldn't get any to work. Just wondering if any one here has a sure fire way to go about this. It's no big deal as I go into Windows very rarely and then F12 for boot choice and select Windows.

---

### Post by jeremy31 on 2024-01-05
Post results from terminal for ```
mokutil --sb; sudo parted -l
```

---

### Post by AllanP on 2024-01-05
allan@allanslaptop:~ $ mokutil --sb; sudo parted -l
SecureBoot disabled
[sudo] password for allan:   
Model: ATA CT1000BX500SSD1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name       Flags
 1      1049kB  1075MB  1074MB  fat32           EFI        bios_grub
 2      1075MB  211GB   210GB   ntfs                       msftdata
 3      211GB   221GB   10.5GB  linux-swap(v1)             swap
 4      221GB   326GB   105GB   ext4            Storage
 5      326GB   536GB   210GB   ext4            Timeshift
 6      536GB   594GB   57.7GB  ext4            MintOS
 7      594GB   669GB   74.8GB  ext4
 8      669GB   726GB   57.7GB  ext4            UbuntuOS
 9      726GB   808GB   82.1GB  ext4
10      808GB   840GB   31.5GB  ext4            DebianOS
11      840GB   903GB   62.9GB  ext4            DebHome


Model: Generic- SD/MMC/MS PRO (scsi)
Disk /dev/sdb: 31.9GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  31.9GB  31.9GB  primary  fat32

---

### Post by jeremy31 on 2024-01-05
Results for ```
sudo ls -R /boot/efi
```

---

### Post by AllanP on 2024-01-05
```
allan@allanslaptop:~ $ sudo ls -R /boot/efi
[sudo] password for allan:   
/boot/efi:
 EFI  'System Volume Information'

/boot/efi/EFI:
Boot  Debian  Microsoft  ubuntu

/boot/efi/EFI/Boot:
bootx64.efi  fbx64.efi    mmx64.efi

/boot/efi/EFI/Debian:
BOOTX64.CSV  fbx64.efi    grub.cfg  grubx64.efi  mmx64.efi  shimx64.efi

/boot/efi/EFI/Microsoft:
Boot  Recovery

/boot/efi/EFI/Microsoft/Boot:
BCD          el-GR  ja-JP          kdstub.dll   ru-RU
BCD.LOG       en-GB  kd_02_10df.dll      ko-KR        sk-SK
BCD.LOG1      en-US  kd_02_10ec.dll      lt-LT        sl-SI
BCD.LOG2      es-ES  kd_02_1137.dll      lv-LV        sr-Latn-RS
bg-BG          es-MX  kd_02_14e4.dll      memtest.efi  sv-SE
bootmgfw.efi  et-EE  kd_02_15b3.dll      nb-NO        tr-TR
bootmgr.efi   fi-FI  kd_02_1969.dll      nl-NL        uk-UA
BOOTSTAT.DAT  Fonts  kd_02_19a2.dll      pl-PL        winsipolicy.p7b
boot.stl      fr-CA  kd_02_1af4.dll      pt-BR        zh-CN
CIPolicies    fr-FR  kd_02_8086.dll      pt-PT        zh-TW
cs-CZ          hr-HR  kd_07_1415.dll      qps-ploc
da-DK          hu-HU  kd_0C_8086.dll      Resources
de-DE          it-IT  kdnet_uart16550.dll  ro-RO

/boot/efi/EFI/Microsoft/Boot/bg-BG:
bootmgfw.efi.mui  bootmgr.efi.mui

/boot/efi/EFI/Microsoft/Boot/CIPolicies:
Active

/boot/efi/EFI/Microsoft/Boot/CIPolicies/Active:
{5DAC656C-21AD-4A02-AB49-649917162E70}.cip
{82443e1e-8a39-4b4a-96a8-f40ddc00b9f3}.cip
{CDD5CB55-DB68-4D71-AA38-3DF2B6473A52}.cip

/boot/efi/EFI/Microsoft/Boot/cs-CZ:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/da-DK:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/de-DE:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/el-GR:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/en-GB:
bootmgfw.efi.mui  bootmgr.efi.mui

/boot/efi/EFI/Microsoft/Boot/en-US:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/es-ES:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/es-MX:
bootmgfw.efi.mui  bootmgr.efi.mui

/boot/efi/EFI/Microsoft/Boot/et-EE:
bootmgfw.efi.mui  bootmgr.efi.mui

/boot/efi/EFI/Microsoft/Boot/fi-FI:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/Fonts:
chs_boot.ttf  malgun_boot.ttf    msjh_boot.ttf    segmono_boot.ttf
cht_boot.ttf  malgunn_boot.ttf    msjhn_boot.ttf    segoen_slboot.ttf
jpn_boot.ttf  meiryo_boot.ttf    msyh_boot.ttf    segoe_slboot.ttf
kor_boot.ttf  meiryon_boot.ttf    msyhn_boot.ttf    wgl4_boot.ttf

/boot/efi/EFI/Microsoft/Boot/fr-CA:
bootmgfw.efi.mui  bootmgr.efi.mui

/boot/efi/EFI/Microsoft/Boot/fr-FR:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/hr-HR:
bootmgfw.efi.mui  bootmgr.efi.mui

/boot/efi/EFI/Microsoft/Boot/hu-HU:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/it-IT:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/ja-JP:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/ko-KR:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/lt-LT:
bootmgfw.efi.mui  bootmgr.efi.mui

/boot/efi/EFI/Microsoft/Boot/lv-LV:
bootmgfw.efi.mui  bootmgr.efi.mui

/boot/efi/EFI/Microsoft/Boot/nb-NO:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/nl-NL:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/pl-PL:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/pt-BR:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/pt-PT:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/qps-ploc:
memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/Resources:
bootres.dll  en-US

/boot/efi/EFI/Microsoft/Boot/Resources/en-US:
bootres.dll.mui

/boot/efi/EFI/Microsoft/Boot/ro-RO:
bootmgfw.efi.mui  bootmgr.efi.mui

/boot/efi/EFI/Microsoft/Boot/ru-RU:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/sk-SK:
bootmgfw.efi.mui  bootmgr.efi.mui

/boot/efi/EFI/Microsoft/Boot/sl-SI:
bootmgfw.efi.mui  bootmgr.efi.mui

/boot/efi/EFI/Microsoft/Boot/sr-Latn-RS:
bootmgfw.efi.mui  bootmgr.efi.mui

/boot/efi/EFI/Microsoft/Boot/sv-SE:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/tr-TR:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/uk-UA:
bootmgfw.efi.mui  bootmgr.efi.mui

/boot/efi/EFI/Microsoft/Boot/zh-CN:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

/boot/efi/EFI/Microsoft/Boot/zh-TW:
bootmgfw.efi.mui  bootmgr.efi.mui  memtest.efi.mui

/boot/efi/EFI/Microsoft/Recovery:
BCD  BCD.LOG  BCD.LOG1    BCD.LOG2

/boot/efi/EFI/ubuntu:
BOOTX64.CSV  grub.cfg  grubx64.efi  mmx64.efi  shimx64.efi

'/boot/efi/System Volume Information':
```

---

### Post by oldfred on 2024-01-05
Added code tags, easy to add with Forum's advanced editor & # icon.
Terminal output needs code tags to preserve formatting.

```
1      1049kB  1075MB  1074MB  fat32           EFI        bios_grub
```

A partition cannot be both ESP - efi system partition and bios_grub partition.
The ESP is FAT32 with boot,esp flags (with gparted) or code ef00 with gdisk. Required for UEFI boot.
If UEFI used for Windows all other systems on same drive must in in UEFI mode.
The bios_grub partition must be unformatted an is normally only 1 or 2 MB, only used for BIOS boot on gpt partitioned drives. Do not use on UEFI systems.

Use gparted and change flags on sda1 to esp, boot.

What brand/model system? What video card/chip?
To see UEFI boot order
sudo efibootmgr -v
See also 
man efibootmgr

In Windows make sure fast startup & bitlocker are off. Or always boot Windows from UEFI boot menu, not from grub.

---

### Post by AllanP on 2024-01-05
When I partitioned the drive I did flag sda1 "esp, boot". I'll work on your suggestions tomorrow. Thanks for all your help. Like I said don't do Windows much so no biggy to load from boot menu. Here is my ageing Dell laptop bought in 2017:
allan@allanslaptop:~ $ inxi -Fxz
System:
  Kernel: 6.5.0-14-generic arch: x86_64 bits: 64 compiler: N/A Desktop: MATE
    v: 1.26.2 Distro: Ubuntu 23.10 (Mantic Minotaur)
Machine:
  Type: Laptop System: Dell product: Inspiron 15-5578 v: N/A
    serial: <superuser required>
  Mobo: Dell model: 0H20TW v: A00 serial: <superuser required> UEFI: Dell
    v: 1.36.0 date: 12/15/2021
Battery:
  ID-1: BAT0 charge: 16.6 Wh (40.2%) condition: 41.3/42.0 Wh (98.5%)
    volts: 10.7 min: 11.4 model: SMP DELL 35RH35C status: discharging
  Device-1: hidpp_battery_0 model: Logitech Wireless Mouse M325
    charge: 55% (should be ignored) status: discharging
CPU:
  Info: dual core model: Intel Core i7-7500U bits: 64 type: MT MCP
    arch: Amber/Kaby Lake note: check rev: 9 cache: L1: 128 KiB L2: 512 KiB
    L3: 4 MiB
  Speed (MHz): avg: 1100 min/max: 400/3500 cores: 1: 1100 2: 1100 3: 1100
    4: 1100 bogomips: 23199
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel HD Graphics 620 vendor: Dell driver: i915 v: kernel
    arch: Gen-9.5 bus-ID: 00:02.0
  Device-2: Realtek Integrated_Webcam_HD driver: uvcvideo type: USB
    bus-ID: 1-5:3
  Display: x11 server: X.Org v: 1.21.1.7 driver: X: loaded: modesetting
    unloaded: fbdev,vesa dri: iris gpu: i915 resolution: 1920x1080~60Hz
  API: OpenGL v: 4.6 Mesa 23.2.1-1ubuntu3.1 renderer: Mesa Intel HD
    Graphics 620 (KBL GT2) direct-render: Yes
Audio:
  Device-1: Intel Sunrise Point-LP HD Audio vendor: Dell driver: snd_hda_intel
    v: kernel bus-ID: 00:1f.3
  API: ALSA v: k6.5.0-14-generic status: kernel-api
  Server-1: PipeWire v: 0.3.79 status: active
Network:
  Device-1: Intel Wireless 3165 driver: iwlwifi v: kernel bus-ID: 01:00.0
  IF: wlp1s0 state: up mac: <filter>
Bluetooth:
  Device-1: Intel Bluetooth wireless interface driver: btusb v: 0.8 type: USB
    bus-ID: 1-6:4
  Report: hciconfig ID: hci0 rfk-id: 8 state: up address: <filter> bt-v: 4.2
    lmp-v: 8
Drives:
  Local Storage: total: 961.24 GiB used: 32.77 GiB (3.4%)
  ID-1: /dev/sda vendor: Crucial model: CT1000BX500SSD1 size: 931.51 GiB
  ID-2: /dev/sdb vendor: Generic model: SD MMC MS PRO size: 29.72 GiB
    type: USB
Partition:
  ID-1: / size: 52.57 GiB used: 14.11 GiB (26.8%) fs: ext4 dev: /dev/sda8
  ID-2: /boot/efi size: 1022 MiB used: 38.5 MiB (3.8%) fs: vfat
    dev: /dev/sda1
  ID-3: /home size: 74.99 GiB used: 12.32 GiB (16.4%) fs: ext4
    dev: /dev/sda9
Swap:
  ID-1: swap-1 type: partition size: 9.77 GiB used: 0 KiB (0.0%)
    dev: /dev/sda3
Sensors:
  System Temperatures: cpu: 64.0 C pch: 52.0 C mobo: 52.0 C sodimm: SODIMM C
  Fan Speeds (rpm): cpu: 4647
Info:
  Processes: 262 Uptime: 5h 39m Memory: total: 16 GiB available: 15.48 GiB
  used: 3.11 GiB (20.1%) Init: systemd target: graphical (5) Comp

---

### Post by yancek on 2024-01-06
Making the change suggested in post 6 should enable booting windows from Grub after booting to Ubuntu and running:  sudo update-grub.  Disable Legacy boot in the BIOS firmware.  You have all the correct EFI files on the EFI partition and having a Legacy install of a Linux OS booting with Grub will not boot an EFI install of windows on the same drive.

---

### Post by AllanP on 2024-01-06
Thanks guys; that worked. I never thought to check the flags on sda1. In my defence though after replacing a 500GB ssd with a 1TB and creating the partitions, I did in fact flag sda1 as esp/boot and a 200GB for Windows. I then proceeded to install W11. After W11 install I created the other Linux partitions. I guess on the W11 install it must have changed the flags. So I'll have to remember this for my PC which I have a TPM module coming today so I can pass W11 requirements.
Anyways let me emphasise that I really appreciate your help; so we can mark this as solved.

---

