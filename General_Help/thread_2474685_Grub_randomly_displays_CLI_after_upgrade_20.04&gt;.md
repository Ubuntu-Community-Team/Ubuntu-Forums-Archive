---
title: "Grub randomly displays CLI after upgrade 20.04&gt;22.04"
date: 2022-05-05
forum: General Help
---

### Post by linuxtom682 on 2022-05-05
I recently did an in place upgrade from 20.04 to 22.04.  Following the upgrade I noticed that 80% of the time on boot, grub drops to the command line. This is on a Dell Inspiron 3793, the same system that is known to require the grub tpm module to be unloaded in grub.d in order to boot properly (which has been done and is a separate issue). I'm a long time Linux user dating back to '94 and can usually figure out what's going on, but this has me stumped to the point that I just signed up here to see if anyone has experience anything like this. I've checked all the UEFI related settings in the BIOS and OS, nothing seems wonky. I've forcibly purged grub* and shim-signed and then re-installed with no change. When using rEFInd I can boot the kernel directly without issue, and can also load grub's efi and then boot any entry from the menu. I'm attaching some related details, if anyone has any ideas I'd be interested in hearing them.

> System:
  Host: d01774 Kernel: 5.15.0-27-generic x86_64 bits: 64 Desktop: Xfce 4.16.0
    Distro: Ubuntu 22.04 LTS (Jammy Jellyfish)
Machine:
  Type: Laptop System: Dell product: Inspiron 3793 v: N/A
    serial: <superuser required>
  Mobo: Dell model: 01J5TX v: A00 serial: <superuser required> UEFI: Dell
    v: 1.20.0 date: 03/19/2022
Battery:
  ID-1: BAT0 charge: 24.8 Wh (74.9%) condition: 33.1/42.0 Wh (78.8%)
CPU:
  Info: quad core model: Intel Core i5-1035G1 bits: 64 type: MT MCP cache:
    L2: 2 MiB
  Speed (MHz): avg: 2159 min/max: 400/3600 cores: 1: 1400 2: 1354 3: 3300
    4: 2004 5: 3258 6: 1679 7: 2932 8: 1351
Graphics:
  Device-1: Intel Iris Plus Graphics G1 driver: i915 v: kernel
  Device-2: Realtek Integrated_Webcam_HD type: USB driver: uvcvideo
  Display: x11 server: X.Org v: 1.21.1.3 driver: X: loaded: modesetting
    unloaded: fbdev,vesa gpu: i915 resolution: 1920x1080~60Hz
  OpenGL: renderer: Mesa DRI Intel UHD Graphics (ICL GT1)
    v: 4.6 Mesa 21.3.7 Amber
Audio:
  Device-1: Intel Ice Lake-LP Smart Sound Audio driver: snd_hda_intel
  Sound Server-1: ALSA v: k5.15.0-27-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Realtek RTL810xE PCI Express Fast Ethernet driver: r8169
  IF: enp1s0 state: down mac: xxxxxx
  Device-2: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter
    driver: ath10k_pci
  IF: wlp2s0 state: up mac: xxxxxx
Bluetooth:
  Device-1: Qualcomm Atheros type: USB driver: btusb
  Report: hciconfig ID: hci0 state: up address: xxxxxx bt-v: 2.1
Drives:
  Local Storage: total: 1.36 TiB used: 559.77 GiB (40.1%)
  ID-1: /dev/nvme0n1 vendor: Crucial model: CT500P5SSD8 size: 465.76 GiB
  ID-2: /dev/sda vendor: Seagate model: ST1000LM035-1RK172 size: 931.51 GiB
Partition:
  ID-1: / size: 405.11 GiB used: 197.33 GiB (48.7%) fs: ext4 dev: /dev/dm-3
  ID-2: /boot size: 1.91 GiB used: 188.8 MiB (9.7%) fs: ext3 dev: /dev/sda7
  ID-3: /boot/efi size: 146 MiB used: 88.8 MiB (60.8%) fs: vfat
    dev: /dev/sda1
Swap:
  ID-1: swap-1 type: partition size: 12 GiB used: 0 KiB (0.0%) dev: /dev/dm-2
Sensors:
  System Temperatures: cpu: 50.0 C mobo: N/A
  Fan Speeds (RPM): cpu: 0
Info:
  Processes: 283 Uptime: 5m Memory: 15.4 GiB used: 1.34 GiB (8.7%)
  Shell: Bash inxi: 3.3.13
=================================================================================

grub-common/jammy,now 2.06-2ubuntu7 amd64 [installed]
grub-efi-amd64-bin/jammy,now 2.06-2ubuntu7 amd64 [installed]
grub-efi-amd64-signed/jammy,now 1.180+2.06-2ubuntu7 amd64 [installed]
grub-efi-amd64/jammy,now 2.06-2ubuntu7 amd64 [installed]
grub2-common/jammy,now 2.06-2ubuntu7 amd64 [installed]
shim-signed/jammy,now 1.51+15.4-0ubuntu9 amd64 [installed]
=================================================================================

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_TIMEOUT_STYLE=countdown
GRUB_TIMEOUT=25
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false
=================================================================================

BootCurrent: 0004
Timeout: 0 seconds
BootOrder: 0004,0002,0005,0003,0000,0001
Boot0000* UEFI CT500P5SSD8 20382ACF34C8 1    PciRoot(0x0)/Pci(0x1d,0x4)/Pci(0x0,0x0)/NVMe(0x1,00-A0-75-01-2A-CF-34-C8)/HD(4,GPT,f34808de-3f01-11eb-902f-98e7432883ea,0x23c90000,0x64000)/File(\EFI\Boot\BootX64.efi)N.....YM....R,Y.
Boot0001* UEFI ST1000LM035-1RK172 ZDEHQMF2    PciRoot(0x0)/Pci(0x17,0x0)/Sata(0,65535,0)/HD(1,GPT,5c92766b-b584-4de1-a875-269e0fa6d3f8,0x800,0x4b000)/File(\EFI\Boot\BootX64.efi)N.....YM....R,Y.
Boot0002* ubuntu    HD(1,GPT,5c92766b-b584-4de1-a875-269e0fa6d3f8,0x800,0x4b000)/File(\EFI\ubuntu\shimx64.efi)
Boot0003* Linux Firmware Updater    HD(1,GPT,5c92766b-b584-4de1-a875-269e0fa6d3f8,0x800,0x4b000)/File(\EFI\ubuntu\fwupdx64.efi)
Boot0004* rEFInd Boot Manager    HD(1,GPT,5c92766b-b584-4de1-a875-269e0fa6d3f8,0x800,0x4b000)/File(\EFI\refind\refind_x64.efi)
Boot0005* Windows Boot Manager    HD(1,GPT,5c92766b-b584-4de1-a875-269e0fa6d3f8,0x800,0x4b000)/File(\EFI\Microsoft\Boot\bootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
=================================================================================

/dev/mapper/cryptdisk: UUID="OFJdrk-zkTL-Bd54-ztjm-CVz2-zPfQ-Fofq92" TYPE="LVM2_member"
/dev/mapper/D01774-LV_root: LABEL="LV_root" UUID="ba20f385-3951-4a54-93c2-39d00c61fc75" BLOCK_SIZE="4096" TYPE="ext4"
/dev/mapper/D01774-LV_swap: UUID="9bc47d78-2bdf-4a2a-b202-059773171fb0" TYPE="swap"
/dev/nvme0n1p1: PARTLABEL="Microsoft reserved partition" PARTUUID="7b3fae11-6ab6-44c2-afed-20b72f859c99"
/dev/nvme0n1p2: LABEL="OS-NVMe" BLOCK_SIZE="512" UUID="01D6C74889426190" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="9a2fe60e-e4fe-4f3a-8737-bf5f282f6226"
/dev/nvme0n1p3: BLOCK_SIZE="512" UUID="6456FF1D56FEEF24" TYPE="ntfs" PARTUUID="9ee82bf6-1243-4f74-a4e4-02b0e05409af"
/dev/nvme0n1p4: SEC_TYPE="msdos" LABEL_FATBOOT="EFISYS" LABEL="EFISYS" UUID="BD41-11EE" BLOCK_SIZE="512" TYPE="vfat" PARTUUID="f34808de-3f01-11eb-902f-98e7432883ea"
/dev/sda1: LABEL_FATBOOT="ESP" LABEL="ESP" UUID="4642-BE4F" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="5c92766b-b584-4de1-a875-269e0fa6d3f8"
/dev/sda2: PARTLABEL="Microsoft reserved partition" PARTUUID="df37c82a-9a8a-4568-8f0e-2f89b1cad59f"
/dev/sda3: LABEL="OS-hdd" BLOCK_SIZE="512" UUID="01D6C74889426191" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="543b817c-4211-4a04-85c0-ace4178954b0"
/dev/sda4: BLOCK_SIZE="512" UUID="8228AEA628AE98A5" TYPE="ntfs" PARTUUID="740073ac-33c1-42bd-9d53-010891fff5db"
/dev/sda5: LABEL="Image" BLOCK_SIZE="512" UUID="BC9C62D79C628BA8" TYPE="ntfs" PARTUUID="9d4ae3d8-65bc-4a34-ab71-d9eeaa6468d3"
/dev/sda6: LABEL="DELLSUPPORT" BLOCK_SIZE="512" UUID="54DE2C99DE2C7580" TYPE="ntfs" PARTUUID="738dce21-ced6-4536-b47a-01ddce4011e4"
/dev/sda7: LABEL="boot" UUID="f13475fe-9ecb-4f2b-8148-6471693eaa45" BLOCK_SIZE="4096" TYPE="ext3" PARTLABEL="boot" PARTUUID="f5989bed-cad9-4329-96f3-66c4edc44795"
/dev/sda8: UUID="41e29537-b9a8-4d5f-af7f-a1c690c9da8b" TYPE="crypto_LUKS" PARTUUID="9f3cf6c9-aa38-4f1e-b6b4-287922eb88e7"
=================================================================================

---

### Post by linuxtom682 on 2022-05-25
Apparently something changed within the grub efi configuration between the 20.04 and 22.04 releases. The issue is caused by the same Dell tpm issue that as has been discussed in detail online. In 20.04 you could simply rmmod the tpm module in "/etc/grub.d/06_notpm" and the system would boot correctly, however in 22.04 you must also insert 'rmmod tpm' as the first un-commented line in the file "/boot/efi/EFI/ubuntu/grub.cfg".

I don't know for certain if the "grub.cfg" was even present in "/boot/efi/EFI/ubuntu" under 20.04, but I'm guessing there was a change in the way grub-install calls grub-mkimage or grub-mkstandalone, in Jammy, which created this preload config to call the main configuration at "/boot/grub/grub.cfg".  Of course, without the early rmmod of tpm the system was back to booting inconsistently.

---

### Post by #&amp;thj^% on 2022-05-25
Same machine for a friend I used:
```
sudo cp /etc/grub.d/40_custom /etc/grub.d/06_notpm
sudo bash -c 'echo "rmmod tpm" >> /etc/grub.d/06_notpm'
sudo update-grub
```
I did notice on his laptop, I had to run **"sudo update-grub"**  twice.
Hope it works for you as well, I had received that, from A Dell Tech.

---

