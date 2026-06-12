---
title: "Hangs on Purple Scrren when powering up"
date: 2014-12-13
forum: General Help
---

### Post by feartheterrapin on 2014-12-13
After shutting down my PC for long periods (12 hours plus), it will hang on the purple screen when booting.  When I reset the power from the purple screen, the PC boots to the GRUB.  I have found by repeating this step a few times, the boot cycle will eventually get past the purple screen.  Once booted, I have no issue re-starting PC or powering down for short duration.  I only seem to have this problem after a long period of being shutdown.  Any suggestions how to trouble shoot would be appreciated.  Below are the specifics of my build:

 

 Release 12.04 (precise) 64-bit
 Kernel Linux 3.13.0-41-generic
 GNOME 3.4.2
 Memory:  7.7 GiB
 Processor:  AMD FX(tm)-6300 Six-Core Processor × 6  
 $ lspci | grep -i vga 
 01:00.0 VGA compatible controller: NVIDIA Corporation G94 [GeForce 9600 GSO 512] (rev a1)

---

### Post by schragge on 2014-12-13
We will need to examine contents of log files in the */var/log* directory for anything suspicious or unusual. Let's start with */var/log/Xorg.0.log* and */var/log/Xorg.0.log.old*. They contain log messages from your graphical interface for the current session and the previous one. The lines starting with (EE) are errors, with (WW) — warnings. Type these commands:
```

grep '^(EE)' /var/log/Xorg.0.log
grep '^(EE)' /var/log/Xorg.0.log.old
grep '^(WW)' /var/log/Xorg.0.log
grep '^(WW)' /var/log/Xorg.0.log.old

```
Another interesting output would be
```

dmesg -r | grep '^<[0-4]>'

```
These are kernel messages where <N> is log level: <0>=emergency, <1>=alert, <2>=critical, <3>=error, <4>=warning. See [syslog(2)]("http://manpages.ubuntu.com/manpages/utopic/en/man2/syslog.2.html").

This will show lines in the kernel log where large delays (more than 0.3 s) occured during boot:
```

 awk -F'[][] *' '$2-ts>0.3{printf "%s\n%s\n---\n",l,$0}{ts=$2;l=$0}' /var/log/dmesg

```

---

### Post by feartheterrapin on 2014-12-14
> **schragge said:**
> We will need to examine contents of log files in the */var/log* directory for anything suspicious or unusual. Let's start with */var/log/Xorg.0.log* and */var/log/Xorg.0.log.old*. They contain log messages from your graphical interface for the current session and the previous one. The lines starting with (EE) are errors, with (WW) — warnings. Type these commands:
```

grep '^(EE)' /var/log/Xorg.0.log
grep '^(EE)' /var/log/Xorg.0.log.old
grep '^(WW)' /var/log/Xorg.0.log
grep '^(WW)' /var/log/Xorg.0.log.old
awk -F'[][] *' '$2-ts>0.3{printf "%s\n%s\n---\n",l,$0}{ts=$2;l=$0}' /var/log/dmesg

dmesg -r | grep '^<[0-4]>'

```


All came up empty except  dmesg:

```

$ dmesg -r | grep '^<[0-4]>'
<4>[    0.000000] ACPI: RSDP 000000009aca6000 000024 (v02 ALASKA)
<4>[    0.000000] ACPI: XSDT 000000009aca6070 00005C (v01 ALASKA    A M I 01072009 AMI  00010013)
<4>[    0.000000] ACPI: FACP 000000009acaceb8 00010C (v05 ALASKA    A M I 01072009 AMI  00010013)
<4>[    0.000000] ACPI BIOS Warning (bug): Optional FADT field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20131115/tbfadt-603)
<4>[    0.000000] ACPI: DSDT 000000009aca6168 006D50 (v02 ALASKA    A M I 00000000 INTL 20051117)
<4>[    0.000000] ACPI: FACS 000000009ba07f80 000040
<4>[    0.000000] ACPI: APIC 000000009acacfc8 00008E (v03 ALASKA    A M I 01072009 AMI  00010013)
<4>[    0.000000] ACPI: FPDT 000000009acad058 000044 (v01 ALASKA    A M I 01072009 AMI  00010013)
<4>[    0.000000] ACPI: MCFG 000000009acad0a0 00003C (v01 ALASKA    A M I 01072009 MSFT 00010013)
<4>[    0.000000] ACPI: HPET 000000009acad0e0 000038 (v01 ALASKA    A M I 01072009 AMI  00000005)
<4>[    0.000000] ACPI: SSDT 000000009acad1a8 001158 (v01 AMD    POWERNOW 00000001 AMD  00000001)
<4>[    0.000000] ACPI: BGRT 000000009acad170 000038 (v00 ALASKA    A M I 01072009 AMI  00010013)
<4>[    0.000000] Zone ranges:
<4>[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
<4>[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
<4>[    0.000000]   Normal   [mem 0x100000000-0x25effffff]
<4>[    0.000000] Movable zone start for each node
<4>[    0.000000] Early memory node ranges
<4>[    0.000000]   node   0: [mem 0x00001000-0x0009ffff]
<4>[    0.000000]   node   0: [mem 0x00100000-0x9ab1afff]
<4>[    0.000000]   node   0: [mem 0x9ca51000-0x9ca51fff]
<4>[    0.000000]   node   0: [mem 0x9cc58000-0x9d082fff]
<4>[    0.000000]   node   0: [mem 0x9d7f4000-0x9d7fffff]
<4>[    0.000000]   node   0: [mem 0x100001000-0x25effffff]
<4>[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2039899
<4>[    0.000000] Policy zone: Normal
<4>[    0.000000] Memory: 7779372K/8289220K available (7623K kernel code, 1139K rwdata, 3488K rodata, 1356K init, 1444K bss, 509848K reserved)
<4>[    0.008354] ACPI: All ACPI Tables successfully acquired
<4>[    0.453446] ACPI: Executed 2 blocks of module-level executable AML code
<4>[    0.460837] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
<4>[    0.460841] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
<4>[    1.101762] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
<4>[    1.521389] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
<4>[    1.574000] r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
<4>[    2.099270] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
<4>[    2.557847] nvidia: module license 'NVIDIA' taints kernel.
<4>[    2.557850] Disabling lock debugging due to kernel taint
<4>[    2.571027] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
<4>[    2.600259] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  304.125  Mon Dec  1 19:58:28 PST 2014
<4>[    2.677143] hda-intel 0000:00:14.2: Using LPIB position fix
<4>[    2.680226] hda-intel 0000:00:14.2: Enable sync_write for stable communication
<4>[    2.688828] SKU: Nid=0x1d sku_cfg=0x4004c601
<4>[    2.688831] SKU: port_connectivity=0x1
<4>[    2.688833] SKU: enable_pcbeep=0x0
<4>[    2.688834] SKU: check_sum=0x00000004
<4>[    2.688835] SKU: customization=0x000000c6
<4>[    2.688837] SKU: external_amp=0x0
<4>[    2.688838] SKU: platform_type=0x0
<4>[    2.688839] SKU: swap=0x0
<4>[    2.688840] SKU: override=0x1
<4>[    2.689094] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:line
<4>[    2.689097]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
<4>[    2.689098]    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
<4>[    2.689100]    mono: mono_out=0x0
<4>[    2.689101]    dig-out=0x11/0x0
<4>[    2.689102]    inputs:
<4>[    2.689104]      Front Mic=0x19
<4>[    2.689106]      Rear Mic=0x18
<4>[    2.689107]      Line=0x1a
<4>[    2.689109] realtek: No valid SSID, checking pincfg 0x4004c601 for NID 0x1d
<4>[    2.689111] realtek: Enabling init ASM_ID=0xc601 CODEC_ID=10ec0887
<3>[    3.732458] sd 6:0:0:0: [sdd] No Caching mode page found
<3>[    3.732459] sd 6:0:0:0: [sdd] Assuming drive cache: write through
<3>[    3.738203] sd 6:0:0:0: [sdd] No Caching mode page found
<3>[    3.738206] sd 6:0:0:0: [sdd] Assuming drive cache: write through
<3>[    3.752319] sd 6:0:0:0: [sdd] No Caching mode page found
<3>[    3.752321] sd 6:0:0:0: [sdd] Assuming drive cache: write through
<4>[    4.137885] vboxdrv: fAsync=0 offMin=0x2de offMax=0x17d36
<4>[    4.249162] NVRM: Your system is not currently configured to drive a VGA console
<4>[    4.249164] NVRM: on the primary VGA device. The NVIDIA Linux graphics driver
<4>[    4.249166] NVRM: requires the use of a text-mode VGA console. Use of other console
<4>[    4.249168] NVRM: drivers including, but not limited to, vesafb, may result in
<4>[    4.249169] NVRM: corruption and stability problems, and is not supported.
$ 

```

I am not sure what this means.  Different drivers required or failing video card?

---

### Post by schragge on 2014-12-15
Have you tried to upgrade your NVIDIA driver to *nvidia-331*? It's in precise repository. The official NVIDIA site [lists](http://www.nvidia.com/Download/driverResults.aspx/80533) your card as supported for this version.

The message from NVRM is only a warning that things *might* not work properly. Is switching away from proprietary NVIDIA driver to free Nouveau driver an option? Nouveau tends to cooperate better with different framebuffer modes. See [here](http://nouveau.freedesktop.org/wiki/KernelModeSetting).

Also have a look at [this question](http://askubuntu.com/questions/6033). It's not the same problem as yours, but also related to framebuffer configuration that works with NVIDIA driver.

---

### Post by feartheterrapin on 2014-12-15
> **schragge said:**
> Have you tried to upgrade your NVIDIA driver to *nvidia-331*? It's in precise repository. The official NVIDIA site [lists]("http://www.nvidia.com/Download/driverResults.aspx/80533") your card as supported for this version.
The message from NVRM is only a warning that things *might* not work properly. Is switching away from proprietary NVIDIA driver to free Nouveau driver an option? Nouveau tends to cooperate better with different framebuffer modes. See [here]("http://nouveau.freedesktop.org/wiki/KernelModeSetting").Also have a look at [this question]("http://askubuntu.com/questions/6033"). It's not the same problem as yours, but also related to framebuffer configuration that works with NVIDIA driver.

I will update my video drivers and report back.  I assumed the drivers updated automatically as I see NVIDIA during some of the Ubuntu updates.  

But could an outdated driver cause the intermittent purple screen hang?  I am currently afraid to power down.

IRT Nouveau, I believe I started with Nouveau during the initial install of 12.04.  My system failed to boot after kernel update (no display after the grub).  Reading these forums lead me to the NVIDIA drivers I currently have.

So reading instructions on updating video driver, I noticed that a line in the GRUB needs to be:
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
 
My grub shows:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

So I tried installing Nouveau using the following commands:

  $ sudo apt-get auroremove --purge nvidia-*
$ sudo stop lightdm
$ sudo apt-get install xserver-xorg-video-nouveau 

I received errors on on the final command. See attached screen shot.

 I was able to reboot.  Code below is result from “dmesg -r | grep '^<[0-4]>' ”

```
$ dmesg -r | grep '^<[0-4]>'
<4>[    0.000000] ACPI: RSDP 000000009aca6000 000024 (v02 ALASKA)
<4>[    0.000000] ACPI: XSDT 000000009aca6070 00005C (v01 ALASKA    A M I 01072009 AMI  00010013)
<4>[    0.000000] ACPI: FACP 000000009acaceb8 00010C (v05 ALASKA    A M I 01072009 AMI  00010013)
<4>[    0.000000] ACPI BIOS Warning (bug): Optional FADT field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20131115/tbfadt-603)
<4>[    0.000000] ACPI: DSDT 000000009aca6168 006D50 (v02 ALASKA    A M I 00000000 INTL 20051117)
<4>[    0.000000] ACPI: FACS 000000009ba07f80 000040
<4>[    0.000000] ACPI: APIC 000000009acacfc8 00008E (v03 ALASKA    A M I 01072009 AMI  00010013)
<4>[    0.000000] ACPI: FPDT 000000009acad058 000044 (v01 ALASKA    A M I 01072009 AMI  00010013)
<4>[    0.000000] ACPI: MCFG 000000009acad0a0 00003C (v01 ALASKA    A M I 01072009 MSFT 00010013)
<4>[    0.000000] ACPI: HPET 000000009acad0e0 000038 (v01 ALASKA    A M I 01072009 AMI  00000005)
<4>[    0.000000] ACPI: SSDT 000000009acad1a8 001158 (v01 AMD    POWERNOW 00000001 AMD  00000001)
<4>[    0.000000] ACPI: BGRT 000000009acad170 000038 (v00 ALASKA    A M I 01072009 AMI  00010013)
<4>[    0.000000] Zone ranges:
<4>[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
<4>[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
<4>[    0.000000]   Normal   [mem 0x100000000-0x25effffff]
<4>[    0.000000] Movable zone start for each node
<4>[    0.000000] Early memory node ranges
<4>[    0.000000]   node   0: [mem 0x00001000-0x0009ffff]
<4>[    0.000000]   node   0: [mem 0x00100000-0x9ab1afff]
<4>[    0.000000]   node   0: [mem 0x9ca51000-0x9ca51fff]
<4>[    0.000000]   node   0: [mem 0x9cc58000-0x9d082fff]
<4>[    0.000000]   node   0: [mem 0x9d7f4000-0x9d7fffff]
<4>[    0.000000]   node   0: [mem 0x100001000-0x25effffff]
<4>[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2039899
<4>[    0.000000] Policy zone: Normal
<4>[    0.000000] Memory: 7781056K/8289220K available (7623K kernel code, 1139K rwdata, 3488K rodata, 1356K init, 1444K bss, 508164K reserved)
<4>[    0.008362] ACPI: All ACPI Tables successfully acquired
<4>[    0.453454] ACPI: Executed 2 blocks of module-level executable AML code
<4>[    0.460840] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
<4>[    0.460844] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
<4>[    1.100884] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
<4>[    1.524335] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
<4>[    1.581418] r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
<4>[    2.108766] sr0: scsi3-mmc drive: 16x/48x writer dvd-ram cd/rw xa/form2 cdda tray
<4>[    2.507889] MXM: GUID detected in BIOS
<4>[    2.597850] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
<4>[    2.650620] hda-intel 0000:00:14.2: Using LPIB position fix
<4>[    2.655312] hda-intel 0000:00:14.2: Enable sync_write for stable communication
<4>[    2.670346] SKU: Nid=0x1d sku_cfg=0x4004c601
<4>[    2.670349] SKU: port_connectivity=0x1
<4>[    2.670351] SKU: enable_pcbeep=0x0
<4>[    2.670353] SKU: check_sum=0x00000004
<4>[    2.670355] SKU: customization=0x000000c6
<4>[    2.670357] SKU: external_amp=0x0
<4>[    2.670359] SKU: platform_type=0x0
<4>[    2.670361] SKU: swap=0x0
<4>[    2.670361] SKU: override=0x1
<4>[    2.670670] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:line
<4>[    2.670672]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
<4>[    2.670674]    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
<4>[    2.670675]    mono: mono_out=0x0
<4>[    2.670678]    dig-out=0x11/0x0
<4>[    2.670679]    inputs:
<4>[    2.670683]      Front Mic=0x19
<4>[    2.670685]      Rear Mic=0x18
<4>[    2.670687]      Line=0x1a
<4>[    2.670689] realtek: No valid SSID, checking pincfg 0x4004c601 for NID 0x1d
<4>[    2.670691] realtek: Enabling init ASM_ID=0xc601 CODEC_ID=10ec0887
<4>[    2.672031] nouveau W[     DRM] failed to create encoder 0/1/0: -19
<4>[    2.672034] nouveau W[     DRM] TV-1 has no encoders, removing
<3>[    3.694418] sd 6:0:0:0: [sdd] No Caching mode page found
<3>[    3.694421] sd 6:0:0:0: [sdd] Assuming drive cache: write through
<3>[    3.705322] sd 6:0:0:0: [sdd] No Caching mode page found
<3>[    3.705330] sd 6:0:0:0: [sdd] Assuming drive cache: write through
<3>[    3.801114] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 28
<3>[    3.801117] Raw EDID:
<3>[    3.801119]      00 ff ff ff ff ff ff 00 05 e3 30 23 6e 30 00 00
<3>[    3.801120]      15 13 01 03 68 1f ff ff ff ff ff ff ff ff ff ff
<3>[    3.801121]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[    3.801122]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[    3.801123]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[    3.801124]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[    3.801124]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[    3.801125]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<4>[    3.978176] vboxdrv: fAsync=0 offMin=0x34e offMax=0x427d
<3>[    4.118453] sd 6:0:0:0: [sdd] No Caching mode page found
<3>[    4.118456] sd 6:0:0:0: [sdd] Assuming drive cache: write through
<3>[   11.072331] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 232
<3>[   11.072335] Raw EDID:
<3>[   11.072336]      00 ff ff ff ff ff ff 00 05 e3 30 23 6e 30 00 00
<3>[   11.072338]      15 13 01 03 68 2f 1a 78 27 ff ff ff ff ff ff ff
<3>[   11.072339]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   11.072340]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   11.072341]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   11.072341]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   11.072342]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   11.072343]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.274773] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 113
<3>[   26.274776] Raw EDID:
<3>[   26.274778]      00 ff ff ff ff ff ff 00 05 e3 30 23 6e 30 00 00
<3>[   26.274779]      15 13 01 03 68 2f 1a 78 2a 35 85 a6 56 48 9a 24
<3>[   26.274780]      12 50 54 bf ef 00 61 4c 81 80 81 8a 81 8c 95 00
<3>[   26.274781]      81 40 71 4f b3 00 02 3a 80 18 71 38 2d 40 58 2c
<3>[   26.274782]      45 00 dc 0c 10 ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.274783]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.274784]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.274785]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.302123] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 161
<3>[   26.302124] Raw EDID:
<3>[   26.302125]      00 ff ff ff ff ff ff 00 05 e3 30 23 6e 30 00 00
<3>[   26.302126]      15 13 01 03 68 2f 1a 78 2a 35 85 a6 56 48 9a 24
<3>[   26.302127]      12 50 54 bf ef 00 61 4c 81 80 81 8a 81 8c 95 00
<3>[   26.302128]      81 40 71 4f b3 00 02 3a 80 18 71 38 2d 40 58 2c
<3>[   26.302129]      45 00 dc 0c 11 00 00 1e 00 00 00 fd 00 38 4b 18
<3>[   26.302129]      50 11 00 09 ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.302130]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.302131]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.329449] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 98
<3>[   26.329450] Raw EDID:
<3>[   26.329451]      00 ff ff ff ff ff ff 00 05 e3 30 23 6e 30 00 00
<3>[   26.329452]      15 13 01 03 68 2f 1a 78 2a 35 85 a6 56 48 9a 24
<3>[   26.329453]      12 50 4f ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.329454]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.329455]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.329456]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.329456]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.329457]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.356715] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 211
<3>[   26.356716] Raw EDID:
<3>[   26.356717]      00 ff ff ff ff ff ff 00 05 e3 30 23 6e 30 00 00
<3>[   26.356718]      15 13 01 03 3f ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.356719]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.356720]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.356721]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.356722]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.356723]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.356724]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<4>[   26.356727] nouveau 0000:01:00.0: VGA-1: EDID block 0 invalid.
<3>[   26.356729] nouveau E[     DRM] DDC responded, but no EDID for VGA-1
jaybo@UB64:~$  awk -F'[][] *' '$2-ts>0.3{printf "%s\n%s\n---\n",l,$0}{ts=$2;l=$0}' /var/log/dmesg
jaybo@UB64:~$ grep '^(WW)' /var/log/Xorg.0.log.old
jaybo@UB64:~$ dmesg -r | grep '^<[0-4]>'
<4>[    0.000000] ACPI: RSDP 000000009aca6000 000024 (v02 ALASKA)
<4>[    0.000000] ACPI: XSDT 000000009aca6070 00005C (v01 ALASKA    A M I 01072009 AMI  00010013)
<4>[    0.000000] ACPI: FACP 000000009acaceb8 00010C (v05 ALASKA    A M I 01072009 AMI  00010013)
<4>[    0.000000] ACPI BIOS Warning (bug): Optional FADT field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20131115/tbfadt-603)
<4>[    0.000000] ACPI: DSDT 000000009aca6168 006D50 (v02 ALASKA    A M I 00000000 INTL 20051117)
<4>[    0.000000] ACPI: FACS 000000009ba07f80 000040
<4>[    0.000000] ACPI: APIC 000000009acacfc8 00008E (v03 ALASKA    A M I 01072009 AMI  00010013)
<4>[    0.000000] ACPI: FPDT 000000009acad058 000044 (v01 ALASKA    A M I 01072009 AMI  00010013)
<4>[    0.000000] ACPI: MCFG 000000009acad0a0 00003C (v01 ALASKA    A M I 01072009 MSFT 00010013)
<4>[    0.000000] ACPI: HPET 000000009acad0e0 000038 (v01 ALASKA    A M I 01072009 AMI  00000005)
<4>[    0.000000] ACPI: SSDT 000000009acad1a8 001158 (v01 AMD    POWERNOW 00000001 AMD  00000001)
<4>[    0.000000] ACPI: BGRT 000000009acad170 000038 (v00 ALASKA    A M I 01072009 AMI  00010013)
<4>[    0.000000] Zone ranges:
<4>[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
<4>[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
<4>[    0.000000]   Normal   [mem 0x100000000-0x25effffff]
<4>[    0.000000] Movable zone start for each node
<4>[    0.000000] Early memory node ranges
<4>[    0.000000]   node   0: [mem 0x00001000-0x0009ffff]
<4>[    0.000000]   node   0: [mem 0x00100000-0x9ab1afff]
<4>[    0.000000]   node   0: [mem 0x9ca51000-0x9ca51fff]
<4>[    0.000000]   node   0: [mem 0x9cc58000-0x9d082fff]
<4>[    0.000000]   node   0: [mem 0x9d7f4000-0x9d7fffff]
<4>[    0.000000]   node   0: [mem 0x100001000-0x25effffff]
<4>[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2039899
<4>[    0.000000] Policy zone: Normal
<4>[    0.000000] Memory: 7781056K/8289220K available (7623K kernel code, 1139K rwdata, 3488K rodata, 1356K init, 1444K bss, 508164K reserved)
<4>[    0.008362] ACPI: All ACPI Tables successfully acquired
<4>[    0.453454] ACPI: Executed 2 blocks of module-level executable AML code
<4>[    0.460840] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
<4>[    0.460844] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
<4>[    1.100884] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
<4>[    1.524335] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
<4>[    1.581418] r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
<4>[    2.108766] sr0: scsi3-mmc drive: 16x/48x writer dvd-ram cd/rw xa/form2 cdda tray
<4>[    2.507889] MXM: GUID detected in BIOS
<4>[    2.597850] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
<4>[    2.650620] hda-intel 0000:00:14.2: Using LPIB position fix
<4>[    2.655312] hda-intel 0000:00:14.2: Enable sync_write for stable communication
<4>[    2.670346] SKU: Nid=0x1d sku_cfg=0x4004c601
<4>[    2.670349] SKU: port_connectivity=0x1
<4>[    2.670351] SKU: enable_pcbeep=0x0
<4>[    2.670353] SKU: check_sum=0x00000004
<4>[    2.670355] SKU: customization=0x000000c6
<4>[    2.670357] SKU: external_amp=0x0
<4>[    2.670359] SKU: platform_type=0x0
<4>[    2.670361] SKU: swap=0x0
<4>[    2.670361] SKU: override=0x1
<4>[    2.670670] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:line
<4>[    2.670672]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
<4>[    2.670674]    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
<4>[    2.670675]    mono: mono_out=0x0
<4>[    2.670678]    dig-out=0x11/0x0
<4>[    2.670679]    inputs:
<4>[    2.670683]      Front Mic=0x19
<4>[    2.670685]      Rear Mic=0x18
<4>[    2.670687]      Line=0x1a
<4>[    2.670689] realtek: No valid SSID, checking pincfg 0x4004c601 for NID 0x1d
<4>[    2.670691] realtek: Enabling init ASM_ID=0xc601 CODEC_ID=10ec0887
<4>[    2.672031] nouveau W[     DRM] failed to create encoder 0/1/0: -19
<4>[    2.672034] nouveau W[     DRM] TV-1 has no encoders, removing
<3>[    3.694418] sd 6:0:0:0: [sdd] No Caching mode page found
<3>[    3.694421] sd 6:0:0:0: [sdd] Assuming drive cache: write through
<3>[    3.705322] sd 6:0:0:0: [sdd] No Caching mode page found
<3>[    3.705330] sd 6:0:0:0: [sdd] Assuming drive cache: write through
<3>[    3.801114] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 28
<3>[    3.801117] Raw EDID:
<3>[    3.801119]      00 ff ff ff ff ff ff 00 05 e3 30 23 6e 30 00 00
<3>[    3.801120]      15 13 01 03 68 1f ff ff ff ff ff ff ff ff ff ff
<3>[    3.801121]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[    3.801122]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[    3.801123]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[    3.801124]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[    3.801124]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[    3.801125]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<4>[    3.978176] vboxdrv: fAsync=0 offMin=0x34e offMax=0x427d
<3>[    4.118453] sd 6:0:0:0: [sdd] No Caching mode page found
<3>[    4.118456] sd 6:0:0:0: [sdd] Assuming drive cache: write through
<3>[   11.072331] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 232
<3>[   11.072335] Raw EDID:
<3>[   11.072336]      00 ff ff ff ff ff ff 00 05 e3 30 23 6e 30 00 00
<3>[   11.072338]      15 13 01 03 68 2f 1a 78 27 ff ff ff ff ff ff ff
<3>[   11.072339]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   11.072340]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   11.072341]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   11.072341]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   11.072342]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   11.072343]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.274773] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 113
<3>[   26.274776] Raw EDID:
<3>[   26.274778]      00 ff ff ff ff ff ff 00 05 e3 30 23 6e 30 00 00
<3>[   26.274779]      15 13 01 03 68 2f 1a 78 2a 35 85 a6 56 48 9a 24
<3>[   26.274780]      12 50 54 bf ef 00 61 4c 81 80 81 8a 81 8c 95 00
<3>[   26.274781]      81 40 71 4f b3 00 02 3a 80 18 71 38 2d 40 58 2c
<3>[   26.274782]      45 00 dc 0c 10 ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.274783]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.274784]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.274785]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.302123] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 161
<3>[   26.302124] Raw EDID:
<3>[   26.302125]      00 ff ff ff ff ff ff 00 05 e3 30 23 6e 30 00 00
<3>[   26.302126]      15 13 01 03 68 2f 1a 78 2a 35 85 a6 56 48 9a 24
<3>[   26.302127]      12 50 54 bf ef 00 61 4c 81 80 81 8a 81 8c 95 00
<3>[   26.302128]      81 40 71 4f b3 00 02 3a 80 18 71 38 2d 40 58 2c
<3>[   26.302129]      45 00 dc 0c 11 00 00 1e 00 00 00 fd 00 38 4b 18
<3>[   26.302129]      50 11 00 09 ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.302130]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.302131]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.329449] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 98
<3>[   26.329450] Raw EDID:
<3>[   26.329451]      00 ff ff ff ff ff ff 00 05 e3 30 23 6e 30 00 00
<3>[   26.329452]      15 13 01 03 68 2f 1a 78 2a 35 85 a6 56 48 9a 24
<3>[   26.329453]      12 50 4f ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.329454]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.329455]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.329456]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.329456]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.329457]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.356715] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 211
<3>[   26.356716] Raw EDID:
<3>[   26.356717]      00 ff ff ff ff ff ff 00 05 e3 30 23 6e 30 00 00
<3>[   26.356718]      15 13 01 03 3f ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.356719]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.356720]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.356721]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.356722]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.356723]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.356724]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<4>[   26.356727] nouveau 0000:01:00.0: VGA-1: EDID block 0 invalid.
<3>[   26.356729] nouveau E[     DRM] DDC responded, but no EDID for VGA-1

```

Is there a way to correct?

---

### Post by schragge on 2014-12-16
> **feartheterrapin said:**
> So reading instructions on updating video driver, I noticed that a line in the GRUB needs to be:
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"
 
My grub shows:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
Wait. "nomodeset" is only needed by NVIDIA proprietary driver. Nouveau actually uses KMS (kernel mode-setting) and probably won't work properly without it.

BTW, there's a typo in your command:
```
sudo apt-get au[COLOR=red]r[/COLOR]oremove --purge nvidia-*
``` should have been
```
sudo apt-get au[COLOR=green]t[/COLOR]oremove --purge nvidia-[COLOR=blue]\[/COLOR]*
```
But since you managed to remove nvidia nevertheless, I assume you typed it correctly. (The backslash before * protects it from being interpreted by the shell. It may be not always needed, but it's just a safer way to do things.)

Let's tackle the Nouveau installation first. It looks like Nouveau requires a certain version of Xorg that is not available on your system. Could you please post the output of
```
apt-cache policy xserver-xorg-core
```
and contents of */var/log/Xorg.0.log* in full length.

Raw EDID dumps in dmesg output probably mean Nouveau can't read correct data from your monitor, and thus cannot automatically configure display resolution.

---

### Post by feartheterrapin on 2014-12-16
> **schragge said:**
> Wait. "nomodeset" is only needed by NVIDIA proprietary driver. Nouveau actually uses KMS (kernel mode-setting) and probably won't work properly without it.
I originally had NVIDIA.  Just wondering if that created any issues?

> BTW, there's a typo in your command:
I did catch that when executing command.

> Let's tackle the Nouveau installation first. It looks like Nouveau requires a certain version of Xorg that is not available on your system. Could you please post the output of
```
apt-cache policy xserver-xorg-core
```
See below:
```
$ apt-cache policy xserver-xorg-core
xserver-xorg-core:
  Installed: (none)
  Candidate: 2:1.11.4-0ubuntu10.16
  Version table:
     2:1.11.4-0ubuntu10.16 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ precise-security/main amd64 Packages
     2:1.11.4-0ubuntu10 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages

```

> and contents of */var/log/Xorg.0.log* in full length.
See below:
```
[     3.373] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[     3.373] X Protocol Version 11, Revision 0
[     3.373] Build Operating System: Linux 2.6.42-58-generic x86_64 Ubuntu
[     3.373] Current Operating System: Linux UB64 3.13.0-43-generic #72~precise1-Ubuntu SMP Tue Dec 9 12:14:18 UTC 2014 x86_64
[     3.373] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-43-generic root=UUID=4e07c3ef-6b82-4b4d-9dcb-433ab93fd897 ro quiet splash vt.handoff=7
[     3.373] Build Date: 09 December 2014  11:03:52PM
[     3.374] xorg-server 2:1.15.1-0ubuntu2~precise4 (For technical support please see http://www.ubuntu.com/support) 
[     3.374] Current version of pixman: 0.30.2
[     3.374]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[     3.374] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     3.374] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Dec 15 20:55:00 2014
[     3.374] (==) Using config file: "/etc/X11/xorg.conf"
[     3.374] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     3.376] (==) No Layout section.  Using the first Screen section.
[     3.376] (==) No screen section available. Using defaults.
[     3.376] (**) |-->Screen "Default Screen Section" (0)
[     3.376] (**) |   |-->Monitor "<default monitor>"
[     3.377] (==) No device specified for screen "Default Screen Section".
    Using the first device section listed.
[     3.377] (**) |   |-->Device "Default Device"
[     3.377] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[     3.377] (==) Automatically adding devices
[     3.377] (==) Automatically enabling devices
[     3.377] (==) Automatically adding GPU devices
[     3.377] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     3.377]     Entry deleted from font path.
[     3.377] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     3.377]     Entry deleted from font path.
[     3.377] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     3.377]     Entry deleted from font path.
[     3.377] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     3.377]     Entry deleted from font path.
[     3.377] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     3.377]     Entry deleted from font path.
[     3.377] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[     3.377] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     3.377] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[     3.377] (II) Loader magic: 0x7f369b72dc20
[     3.377] (II) Module ABI versions:
[     3.377]     X.Org ANSI C Emulation: 0.4
[     3.377]     X.Org Video Driver: 15.0
[     3.377]     X.Org XInput driver : 20.0
[     3.377]     X.Org Server Extension : 8.0
[     3.378] (II) xfree86: Adding drm device (/dev/dri/card0)
[     3.379] (--) PCI:*(0:1:0:0) 10de:0625:3842:c961 rev 161, Mem @ 0xfc000000/16777216, 0xa0000000/536870912, 0xfa000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[     3.380] Initializing built-in extension Generic Event Extension
[     3.380] Initializing built-in extension SHAPE
[     3.380] Initializing built-in extension MIT-SHM
[     3.380] Initializing built-in extension XInputExtension
[     3.380] Initializing built-in extension XTEST
[     3.380] Initializing built-in extension BIG-REQUESTS
[     3.380] Initializing built-in extension SYNC
[     3.380] Initializing built-in extension XKEYBOARD
[     3.380] Initializing built-in extension XC-MISC
[     3.380] Initializing built-in extension SECURITY
[     3.380] Initializing built-in extension XINERAMA
[     3.380] Initializing built-in extension XFIXES
[     3.380] Initializing built-in extension RENDER
[     3.380] Initializing built-in extension RANDR
[     3.380] Initializing built-in extension COMPOSITE
[     3.380] Initializing built-in extension DAMAGE
[     3.380] Initializing built-in extension MIT-SCREEN-SAVER
[     3.380] Initializing built-in extension DOUBLE-BUFFER
[     3.380] Initializing built-in extension RECORD
[     3.380] Initializing built-in extension DPMS
[     3.380] Initializing built-in extension X-Resource
[     3.380] Initializing built-in extension XVideo
[     3.380] Initializing built-in extension XVideo-MotionCompensation
[     3.380] Initializing built-in extension XFree86-VidModeExtension
[     3.380] Initializing built-in extension XFree86-DGA
[     3.380] Initializing built-in extension XFree86-DRI
[     3.380] Initializing built-in extension DRI2
[     3.380] (II) LoadModule: "glx"
[     3.384] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     3.390] (II) Module glx: vendor="X.Org Foundation"
[     3.390]     compiled for 1.15.1, module version = 1.0.0
[     3.390]     ABI class: X.Org Server Extension, version 8.0
[     3.390] (==) AIGLX enabled
[     3.390] Loading extension GLX
[     3.390] (==) Matched nvidia as autoconfigured driver 0
[     3.390] (==) Matched nouveau as autoconfigured driver 1
[     3.390] (==) Matched nvidia as autoconfigured driver 2
[     3.390] (==) Matched nouveau as autoconfigured driver 3
[     3.390] (==) Matched modesetting as autoconfigured driver 4
[     3.390] (==) Matched fbdev as autoconfigured driver 5
[     3.390] (==) Matched vesa as autoconfigured driver 6
[     3.390] (==) Assigned the driver to the xf86ConfigLayout
[     3.390] (II) LoadModule: "nvidia"
[     3.391] (WW) Warning, couldn't open module nvidia
[     3.391] (II) UnloadModule: "nvidia"
[     3.391] (II) Unloading nvidia
[     3.391] (EE) Failed to load module "nvidia" (module does not exist, 0)
[     3.391] (II) LoadModule: "nouveau"
[     3.392] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[     3.393] (II) Module nouveau: vendor="X.Org Foundation"
[     3.393]     compiled for 1.15.1, module version = 1.0.10
[     3.393]     Module class: X.Org Video Driver
[     3.393]     ABI class: X.Org Video Driver, version 15.0
[     3.393] (II) LoadModule: "modesetting"
[     3.393] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     3.394] (II) Module modesetting: vendor="X.Org Foundation"
[     3.394]     compiled for 1.15.1, module version = 0.8.1
[     3.394]     Module class: X.Org Video Driver
[     3.394]     ABI class: X.Org Video Driver, version 15.0
[     3.394] (II) LoadModule: "fbdev"
[     3.394] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     3.394] (II) Module fbdev: vendor="X.Org Foundation"
[     3.394]     compiled for 1.15.1, module version = 0.4.4
[     3.394]     Module class: X.Org Video Driver
[     3.394]     ABI class: X.Org Video Driver, version 15.0
[     3.394] (II) LoadModule: "vesa"
[     3.395] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     3.395] (II) Module vesa: vendor="X.Org Foundation"
[     3.395]     compiled for 1.15.1, module version = 2.3.3
[     3.395]     Module class: X.Org Video Driver
[     3.395]     ABI class: X.Org Video Driver, version 15.0
[     3.395] (==) Matched nvidia as autoconfigured driver 0
[     3.395] (==) Matched nouveau as autoconfigured driver 1
[     3.395] (==) Matched nvidia as autoconfigured driver 2
[     3.395] (==) Matched nouveau as autoconfigured driver 3
[     3.395] (==) Matched modesetting as autoconfigured driver 4
[     3.395] (==) Matched fbdev as autoconfigured driver 5
[     3.395] (==) Matched vesa as autoconfigured driver 6
[     3.395] (==) Assigned the driver to the xf86ConfigLayout
[     3.395] (II) LoadModule: "nvidia"
[     3.395] (WW) Warning, couldn't open module nvidia
[     3.395] (II) UnloadModule: "nvidia"
[     3.395] (II) Unloading nvidia
[     3.395] (EE) Failed to load module "nvidia" (module does not exist, 0)
[     3.395] (II) LoadModule: "nouveau"
[     3.395] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[     3.395] (II) Module nouveau: vendor="X.Org Foundation"
[     3.395]     compiled for 1.15.1, module version = 1.0.10
[     3.395]     Module class: X.Org Video Driver
[     3.395]     ABI class: X.Org Video Driver, version 15.0
[     3.395] (II) UnloadModule: "nouveau"
[     3.395] (II) Unloading nouveau
[     3.395] (II) Failed to load module "nouveau" (already loaded, 0)
[     3.395] (II) LoadModule: "modesetting"
[     3.396] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     3.396] (II) Module modesetting: vendor="X.Org Foundation"
[     3.396]     compiled for 1.15.1, module version = 0.8.1
[     3.396]     Module class: X.Org Video Driver
[     3.396]     ABI class: X.Org Video Driver, version 15.0
[     3.396] (II) UnloadModule: "modesetting"
[     3.396] (II) Unloading modesetting
[     3.396] (II) Failed to load module "modesetting" (already loaded, 0)
[     3.396] (II) LoadModule: "fbdev"
[     3.396] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     3.396] (II) Module fbdev: vendor="X.Org Foundation"
[     3.396]     compiled for 1.15.1, module version = 0.4.4
[     3.396]     Module class: X.Org Video Driver
[     3.396]     ABI class: X.Org Video Driver, version 15.0
[     3.396] (II) UnloadModule: "fbdev"
[     3.396] (II) Unloading fbdev
[     3.396] (II) Failed to load module "fbdev" (already loaded, 0)
[     3.396] (II) LoadModule: "vesa"
[     3.396] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     3.396] (II) Module vesa: vendor="X.Org Foundation"
[     3.396]     compiled for 1.15.1, module version = 2.3.3
[     3.396]     Module class: X.Org Video Driver
[     3.396]     ABI class: X.Org Video Driver, version 15.0
[     3.396] (II) UnloadModule: "vesa"
[     3.396] (II) Unloading vesa
[     3.396] (II) Failed to load module "vesa" (already loaded, 0)
[     3.396] (II) NOUVEAU driver Date:   Thu Nov 7 14:56:48 2013 +1000
[     3.396] (II) NOUVEAU driver for NVIDIA chipset families :
[     3.396]     RIVA TNT        (NV04)
[     3.396]     RIVA TNT2       (NV05)
[     3.396]     GeForce 256     (NV10)
[     3.396]     GeForce 2       (NV11, NV15)
[     3.396]     GeForce 4MX     (NV17, NV18)
[     3.396]     GeForce 3       (NV20)
[     3.396]     GeForce 4Ti     (NV25, NV28)
[     3.396]     GeForce FX      (NV3x)
[     3.396]     GeForce 6       (NV4x)
[     3.396]     GeForce 7       (G7x)
[     3.396]     GeForce 8       (G8x)
[     3.396]     GeForce GTX 200 (NVA0)
[     3.396]     GeForce GTX 400 (NVC0)
[     3.396] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     3.396] (II) FBDEV: driver for framebuffer: fbdev
[     3.396] (II) VESA: driver for VESA chipsets: vesa
[     3.396] (++) using VT number 7

[     3.396] (II) [drm] nouveau interface version: 1.1.2
[     3.397] (WW) Falling back to old probe method for modesetting
[     3.397] (WW) Falling back to old probe method for fbdev
[     3.397] (II) Loading sub module "fbdevhw"
[     3.397] (II) LoadModule: "fbdevhw"
[     3.397] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     3.397] (II) Module fbdevhw: vendor="X.Org Foundation"
[     3.397]     compiled for 1.15.1, module version = 0.0.2
[     3.397]     ABI class: X.Org Video Driver, version 15.0
[     3.397] (WW) Falling back to old probe method for vesa
[     3.397] (II) Loading sub module "dri2"
[     3.397] (II) LoadModule: "dri2"
[     3.397] (II) Module "dri2" already built-in
[     3.397] (--) NOUVEAU(0): Chipset: "NVIDIA NV94"
[     3.397] (II) NOUVEAU(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[     3.397] (==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
[     3.397] (==) NOUVEAU(0): RGB weight 888
[     3.397] (==) NOUVEAU(0): Default visual is TrueColor
[     3.397] (==) NOUVEAU(0): Using HW cursor
[     3.397] (==) NOUVEAU(0): GLX sync to VBlank enabled.
[     3.397] (==) NOUVEAU(0): Page flipping enabled
[     3.397] (==) NOUVEAU(0): Swap limit set to 2 [Max allowed 2]
[     3.434] (II) NOUVEAU(0): Output VGA-1 has no monitor section
[     3.457] (II) NOUVEAU(0): Output DVI-I-1 has no monitor section
[     3.514] (II) NOUVEAU(0): EDID for output VGA-1
[     3.514] (II) NOUVEAU(0): Manufacturer: AOC  Model: 2330  Serial#: 12398
[     3.514] (II) NOUVEAU(0): Year: 2009  Week: 21
[     3.514] (II) NOUVEAU(0): EDID Version: 1.3
[     3.514] (II) NOUVEAU(0): Analog Display Input,  Input Voltage Level: 0.700/0.700 V
[     3.514] (II) NOUVEAU(0): Sync:  Separate
[     3.514] (II) NOUVEAU(0): Max Image Size [cm]: horiz.: 47  vert.: 26
[     3.514] (II) NOUVEAU(0): Gamma: 2.20
[     3.514] (II) NOUVEAU(0): DPMS capabilities: Off; RGB/Color Display
[     3.514] (II) NOUVEAU(0): First detailed timing is preferred mode
[     3.514] (II) NOUVEAU(0): redX: 0.648 redY: 0.339   greenX: 0.282 greenY: 0.603
[     3.514] (II) NOUVEAU(0): blueX: 0.143 blueY: 0.070   whiteX: 0.313 whiteY: 0.329
[     3.514] (II) NOUVEAU(0): Supported established timings:
[     3.514] (II) NOUVEAU(0): 720x400@70Hz
[     3.514] (II) NOUVEAU(0): 640x480@60Hz
[     3.514] (II) NOUVEAU(0): 640x480@67Hz
[     3.514] (II) NOUVEAU(0): 640x480@72Hz
[     3.514] (II) NOUVEAU(0): 640x480@75Hz
[     3.514] (II) NOUVEAU(0): 800x600@56Hz
[     3.514] (II) NOUVEAU(0): 800x600@60Hz
[     3.514] (II) NOUVEAU(0): 800x600@72Hz
[     3.514] (II) NOUVEAU(0): 800x600@75Hz
[     3.514] (II) NOUVEAU(0): 832x624@75Hz
[     3.514] (II) NOUVEAU(0): 1024x768@60Hz
[     3.514] (II) NOUVEAU(0): 1024x768@70Hz
[     3.514] (II) NOUVEAU(0): 1024x768@75Hz
[     3.514] (II) NOUVEAU(0): 1280x1024@75Hz
[     3.514] (II) NOUVEAU(0): Manufacturer's mask: 0
[     3.514] (II) NOUVEAU(0): Supported standard timings:
[     3.514] (II) NOUVEAU(0): #0: hsize: 1024  vsize 768  refresh: 72  vid: 19553
[     3.514] (II) NOUVEAU(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[     3.514] (II) NOUVEAU(0): #2: hsize: 1280  vsize 1024  refresh: 70  vid: 35457
[     3.514] (II) NOUVEAU(0): #3: hsize: 1280  vsize 1024  refresh: 72  vid: 35969
[     3.514] (II) NOUVEAU(0): #4: hsize: 1440  vsize 900  refresh: 60  vid: 149
[     3.514] (II) NOUVEAU(0): #5: hsize: 1280  vsize 960  refresh: 60  vid: 16513
[     3.514] (II) NOUVEAU(0): #6: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[     3.514] (II) NOUVEAU(0): #7: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[     3.514] (II) NOUVEAU(0): Supported detailed timing:
[     3.514] (II) NOUVEAU(0): clock: 148.5 MHz   Image Size:  476 x 268 mm
[     3.514] (II) NOUVEAU(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[     3.514] (II) NOUVEAU(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[     3.514] (II) NOUVEAU(0): Ranges: V min: 56 V max: 75 Hz, H min: 24 H max: 80 kHz, PixClock max 175 MHz
[     3.514] (II) NOUVEAU(0): Monitor name: 2330V
[     3.514] (II) NOUVEAU(0): Serial No: R4295JA012398
[     3.514] (II) NOUVEAU(0): EDID (in hex):
[     3.514] (II) NOUVEAU(0):     00ffffffffffff0005e330236e300000
[     3.514] (II) NOUVEAU(0):     15130103682f1a782a3585a656489a24
[     3.514] (II) NOUVEAU(0):     125054bfef00614c8180818a818c9500
[     3.514] (II) NOUVEAU(0):     8140714fb300023a801871382d40582c
[     3.514] (II) NOUVEAU(0):     4500dc0c1100001e000000fd00384b18
[     3.514] (II) NOUVEAU(0):     5011000a202020202020000000fc0032
[     3.514] (II) NOUVEAU(0):     333330560a20202020202020000000ff
[     3.514] (II) NOUVEAU(0):     0052343239354a413031323339380087
[     3.514] (II) NOUVEAU(0): Printing probed modes for output VGA-1
[     3.514] (II) NOUVEAU(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[     3.514] (II) NOUVEAU(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[     3.514] (II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[     3.514] (II) NOUVEAU(0): Modeline "1280x1024"x72.0  132.84  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.9 kHz)
[     3.514] (II) NOUVEAU(0): Modeline "1280x1024"x70.0  128.95  1280 1368 1504 1728  1024 1025 1028 1066 -hsync +vsync (74.6 kHz)
[     3.514] (II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     3.514] (II) NOUVEAU(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[     3.514] (II) NOUVEAU(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[     3.514] (II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[     3.514] (II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[     3.514] (II) NOUVEAU(0): Modeline "1024x768"x72.0   78.44  1024 1080 1192 1360  768 769 772 801 -hsync +vsync (57.7 kHz)
[     3.514] (II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[     3.514] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     3.514] (II) NOUVEAU(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[     3.514] (II) NOUVEAU(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[     3.514] (II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[     3.514] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     3.514] (II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[     3.514] (II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[     3.514] (II) NOUVEAU(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz e)
[     3.514] (II) NOUVEAU(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[     3.514] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     3.514] (II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[     3.537] (II) NOUVEAU(0): EDID for output DVI-I-1
[     3.537] (II) NOUVEAU(0): Output VGA-1 connected
[     3.537] (II) NOUVEAU(0): Output DVI-I-1 disconnected
[     3.537] (II) NOUVEAU(0): Using exact sizes for initial modes
[     3.537] (II) NOUVEAU(0): Output VGA-1 using initial mode 1920x1080
[     3.537] (II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[     3.537] (--) NOUVEAU(0): Virtual size is 1920x1080 (pitch 0)
[     3.537] (**) NOUVEAU(0):  Driver mode "1920x1080": 148.5 MHz (scaled from 0.0 MHz), 67.5 kHz, 60.0 Hz
[     3.537] (II) NOUVEAU(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[     3.537] (**) NOUVEAU(0):  Driver mode "1680x1050": 146.2 MHz (scaled from 0.0 MHz), 65.3 kHz, 60.0 Hz
[     3.537] (II) NOUVEAU(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[     3.537] (**) NOUVEAU(0):  Driver mode "1280x1024": 135.0 MHz (scaled from 0.0 MHz), 80.0 kHz, 75.0 Hz
[     3.537] (II) NOUVEAU(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[     3.537] (**) NOUVEAU(0):  Mode "1280x1024": 132.8 MHz (scaled from 0.0 MHz), 76.9 kHz, 72.0 Hz
[     3.537] (II) NOUVEAU(0): Modeline "1280x1024"x72.0  132.84  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.9 kHz)
[     3.537] (**) NOUVEAU(0):  Mode "1280x1024": 128.9 MHz (scaled from 0.0 MHz), 74.6 kHz, 70.0 Hz
[     3.537] (II) NOUVEAU(0): Modeline "1280x1024"x70.0  128.95  1280 1368 1504 1728  1024 1025 1028 1066 -hsync +vsync (74.6 kHz)
[     3.537] (**) NOUVEAU(0):  Driver mode "1280x1024": 108.0 MHz (scaled from 0.0 MHz), 64.0 kHz, 60.0 Hz
[     3.537] (II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     3.537] (**) NOUVEAU(0):  Driver mode "1440x900": 106.5 MHz (scaled from 0.0 MHz), 55.9 kHz, 59.9 Hz
[     3.537] (II) NOUVEAU(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[     3.537] (**) NOUVEAU(0):  Driver mode "1280x960": 108.0 MHz (scaled from 0.0 MHz), 60.0 kHz, 60.0 Hz
[     3.537] (II) NOUVEAU(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[     3.537] (**) NOUVEAU(0):  Driver mode "1152x864": 108.0 MHz (scaled from 0.0 MHz), 67.5 kHz, 75.0 Hz
[     3.537] (II) NOUVEAU(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[     3.537] (**) NOUVEAU(0):  Driver mode "1024x768": 78.8 MHz (scaled from 0.0 MHz), 60.1 kHz, 75.1 Hz
[     3.537] (II) NOUVEAU(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[     3.537] (**) NOUVEAU(0):  Mode "1024x768": 78.4 MHz (scaled from 0.0 MHz), 57.7 kHz, 72.0 Hz
[     3.537] (II) NOUVEAU(0): Modeline "1024x768"x72.0   78.44  1024 1080 1192 1360  768 769 772 801 -hsync +vsync (57.7 kHz)
[     3.537] (**) NOUVEAU(0):  Driver mode "1024x768": 75.0 MHz (scaled from 0.0 MHz), 56.5 kHz, 70.1 Hz
[     3.537] (II) NOUVEAU(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[     3.537] (**) NOUVEAU(0):  Driver mode "1024x768": 65.0 MHz (scaled from 0.0 MHz), 48.4 kHz, 60.0 Hz
[     3.537] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     3.537] (**) NOUVEAU(0):  Driver mode "832x624": 57.3 MHz (scaled from 0.0 MHz), 49.7 kHz, 74.6 Hz
[     3.537] (II) NOUVEAU(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[     3.537] (**) NOUVEAU(0):  Driver mode "800x600": 50.0 MHz (scaled from 0.0 MHz), 48.1 kHz, 72.2 Hz
[     3.537] (II) NOUVEAU(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[     3.537] (**) NOUVEAU(0):  Driver mode "800x600": 49.5 MHz (scaled from 0.0 MHz), 46.9 kHz, 75.0 Hz
[     3.537] (II) NOUVEAU(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[     3.537] (**) NOUVEAU(0):  Driver mode "800x600": 40.0 MHz (scaled from 0.0 MHz), 37.9 kHz, 60.3 Hz
[     3.537] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     3.537] (**) NOUVEAU(0):  Driver mode "800x600": 36.0 MHz (scaled from 0.0 MHz), 35.2 kHz, 56.2 Hz
[     3.537] (II) NOUVEAU(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[     3.537] (**) NOUVEAU(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.5 kHz, 75.0 Hz
[     3.537] (II) NOUVEAU(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[     3.537] (**) NOUVEAU(0):  Driver mode "640x480": 31.5 MHz (scaled from 0.0 MHz), 37.9 kHz, 72.8 Hz
[     3.537] (II) NOUVEAU(0): Modeline "640x480"x72.8   31.50  640 664 704 832  480 489 491 520 -hsync -vsync (37.9 kHz e)
[     3.537] (**) NOUVEAU(0):  Driver mode "640x480": 30.2 MHz (scaled from 0.0 MHz), 35.0 kHz, 66.7 Hz
[     3.537] (II) NOUVEAU(0): Modeline "640x480"x66.7   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[     3.537] (**) NOUVEAU(0):  Driver mode "640x480": 25.2 MHz (scaled from 0.0 MHz), 31.5 kHz, 60.0 Hz
[     3.537] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     3.537] (**) NOUVEAU(0):  Driver mode "720x400": 28.3 MHz (scaled from 0.0 MHz), 31.5 kHz, 70.1 Hz
[     3.537] (II) NOUVEAU(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[     3.537] (==) NOUVEAU(0): DPI set to (96, 96)
[     3.537] (II) Loading sub module "fb"
[     3.537] (II) LoadModule: "fb"
[     3.538] (II) Loading /usr/lib/xorg/modules/libfb.so
[     3.541] (II) Module fb: vendor="X.Org Foundation"
[     3.541]     compiled for 1.15.1, module version = 1.0.0
[     3.541]     ABI class: X.Org ANSI C Emulation, version 0.4
[     3.541] (II) Loading sub module "exa"
[     3.541] (II) LoadModule: "exa"
[     3.541] (II) Loading /usr/lib/xorg/modules/libexa.so
[     3.542] (II) Module exa: vendor="X.Org Foundation"
[     3.542]     compiled for 1.15.1, module version = 2.6.0
[     3.542]     ABI class: X.Org Video Driver, version 15.0
[     3.542] (II) Loading sub module "shadowfb"
[     3.542] (II) LoadModule: "shadowfb"
[     3.542] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[     3.542] (II) Module shadowfb: vendor="X.Org Foundation"
[     3.542]     compiled for 1.15.1, module version = 1.0.0
[     3.543]     ABI class: X.Org ANSI C Emulation, version 0.4
[     3.543] (II) UnloadModule: "modesetting"
[     3.543] (II) Unloading modesetting
[     3.543] (II) UnloadModule: "fbdev"
[     3.543] (II) Unloading fbdev
[     3.543] (II) UnloadSubModule: "fbdevhw"
[     3.543] (II) Unloading fbdevhw
[     3.543] (II) UnloadModule: "vesa"
[     3.543] (II) Unloading vesa
[     3.543] (--) Depth 24 pixmap format is 32 bpp
[     3.543] (II) NOUVEAU(0): Opened GPU channel 0
[     3.547] (II) NOUVEAU(0): [DRI2] Setup complete
[     3.547] (II) NOUVEAU(0): [DRI2]   DRI driver: nouveau
[     3.547] (II) NOUVEAU(0): [DRI2]   VDPAU driver: nouveau
[     3.549] (II) EXA(0): Driver allocated offscreen pixmaps
[     3.549] (II) EXA(0): Driver registered support for the following operations:
[     3.549] (II)         Solid
[     3.549] (II)         Copy
[     3.549] (II)         Composite (RENDER acceleration)
[     3.549] (II)         UploadToScreen
[     3.549] (II)         DownloadFromScreen
[     3.549] (==) NOUVEAU(0): Backing store enabled
[     3.549] (==) NOUVEAU(0): Silken mouse enabled
[     3.549] (II) NOUVEAU(0): [XvMC] Associated with Nouveau GeForce 8/9 Textured Video.
[     3.549] (II) NOUVEAU(0): [XvMC] Extension initialized.
[     3.549] (==) NOUVEAU(0): DPMS enabled
[     3.549] (II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[     3.549] (WW) NOUVEAU(0): Option "NoLogo" is not used
[     3.549] (--) RandR disabled
[     3.624] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[     3.624] (II) AIGLX: enabled GLX_ARB_create_context
[     3.624] (II) AIGLX: enabled GLX_ARB_create_context_profile
[     3.624] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[     3.624] (II) AIGLX: enabled GLX_INTEL_swap_event
[     3.624] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[     3.624] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[     3.624] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[     3.624] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[     3.624] (II) AIGLX: Loaded and initialized nouveau
[     3.624] (II) GLX: Initialized DRI2 GL provider for screen 0
[     3.626] (II) NOUVEAU(0): NVEnterVT is called.
[     3.644] (II) NOUVEAU(0): Setting screen physical size to 508 x 285
[     3.644] resize called 1920 1080
[     3.653] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[     3.657] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     3.657] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     3.657] (II) LoadModule: "evdev"
[     3.657] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[     3.658] (II) Module evdev: vendor="X.Org Foundation"
[     3.658]     compiled for 1.15.1, module version = 2.8.2
[     3.658]     Module class: X.Org XInput Driver
[     3.658]     ABI class: X.Org XInput driver, version 20.0
[     3.658] (II) Using input driver 'evdev' for 'Power Button'
[     3.658] (**) Power Button: always reports core events
[     3.658] (**) evdev: Power Button: Device: "/dev/input/event1"
[     3.658] (--) evdev: Power Button: Vendor 0 Product 0x1
[     3.658] (--) evdev: Power Button: Found keys
[     3.658] (II) evdev: Power Button: Configuring as keyboard
[     3.658] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[     3.658] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     3.658] (**) Option "xkb_rules" "evdev"
[     3.658] (**) Option "xkb_model" "pc105"
[     3.658] (**) Option "xkb_layout" "us"
[     3.659] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[     3.659] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[     3.659] (II) Using input driver 'evdev' for 'Power Button'
[     3.659] (**) Power Button: always reports core events
[     3.659] (**) evdev: Power Button: Device: "/dev/input/event0"
[     3.659] (--) evdev: Power Button: Vendor 0 Product 0x1
[     3.659] (--) evdev: Power Button: Found keys
[     3.659] (II) evdev: Power Button: Configuring as keyboard
[     3.659] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input0/event0"
[     3.659] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[     3.659] (**) Option "xkb_rules" "evdev"
[     3.659] (**) Option "xkb_model" "pc105"
[     3.659] (**) Option "xkb_layout" "us"
[     3.659] (II) config/udev: Adding drm device (/dev/dri/card0)
[     3.659] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[     3.659] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/event3)
[     3.659] (**) Logitech USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[     3.659] (II) Using input driver 'evdev' for 'Logitech USB Optical Mouse'
[     3.659] (**) Logitech USB Optical Mouse: always reports core events
[     3.659] (**) evdev: Logitech USB Optical Mouse: Device: "/dev/input/event3"
[     3.659] (--) evdev: Logitech USB Optical Mouse: Vendor 0x46d Product 0xc00c
[     3.659] (--) evdev: Logitech USB Optical Mouse: Found 3 mouse buttons
[     3.659] (--) evdev: Logitech USB Optical Mouse: Found scroll wheel(s)
[     3.659] (--) evdev: Logitech USB Optical Mouse: Found relative axes
[     3.659] (--) evdev: Logitech USB Optical Mouse: Found x and y relative axes
[     3.659] (II) evdev: Logitech USB Optical Mouse: Configuring as mouse
[     3.659] (II) evdev: Logitech USB Optical Mouse: Adding scrollwheel support
[     3.659] (**) evdev: Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
[     3.659] (**) evdev: Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[     3.659] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:12.0/usb4/4-4/4-4:1.0/input/input3/event3"
[     3.659] (II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE, id 8)
[     3.659] (II) evdev: Logitech USB Optical Mouse: initialized for relative axes.
[     3.659] (**) Logitech USB Optical Mouse: (accel) keeping acceleration scheme 1
[     3.659] (**) Logitech USB Optical Mouse: (accel) acceleration profile 0
[     3.659] (**) Logitech USB Optical Mouse: (accel) acceleration factor: 2.000
[     3.659] (**) Logitech USB Optical Mouse: (accel) acceleration threshold: 4
[     3.660] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/mouse0)
[     3.660] (II) No input driver specified, ignoring this device.
[     3.660] (II) This device may have been added with another device file.
[     3.660] (II) config/udev: Adding input device HDA ATI SB Front Mic (/dev/input/event9)
[     3.660] (II) No input driver specified, ignoring this device.
[     3.660] (II) This device may have been added with another device file.
[     3.660] (II) config/udev: Adding input device HDA ATI SB Rear Mic (/dev/input/event8)
[     3.660] (II) No input driver specified, ignoring this device.
[     3.660] (II) This device may have been added with another device file.
[     3.660] (II) config/udev: Adding input device HDA ATI SB Line (/dev/input/event7)
[     3.660] (II) No input driver specified, ignoring this device.
[     3.660] (II) This device may have been added with another device file.
[     3.660] (II) config/udev: Adding input device HDA ATI SB Line Out (/dev/input/event6)
[     3.660] (II) No input driver specified, ignoring this device.
[     3.660] (II) This device may have been added with another device file.
[     3.661] (II) config/udev: Adding input device HDA ATI SB Front Headphone (/dev/input/event5)
[     3.661] (II) No input driver specified, ignoring this device.
[     3.661] (II) This device may have been added with another device file.
[     3.661] (II) config/udev: Adding input device Eee PC WMI hotkeys (/dev/input/event4)
[     3.661] (**) Eee PC WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[     3.661] (II) Using input driver 'evdev' for 'Eee PC WMI hotkeys'
[     3.661] (**) Eee PC WMI hotkeys: always reports core events
[     3.661] (**) evdev: Eee PC WMI hotkeys: Device: "/dev/input/event4"
[     3.661] (--) evdev: Eee PC WMI hotkeys: Vendor 0 Product 0
[     3.661] (--) evdev: Eee PC WMI hotkeys: Found keys
[     3.661] (II) evdev: Eee PC WMI hotkeys: Configuring as keyboard
[     3.661] (**) Option "config_info" "udev:/sys/devices/platform/eeepc-wmi/input/input4/event4"
[     3.661] (II) XINPUT: Adding extended input device "Eee PC WMI hotkeys" (type: KEYBOARD, id 9)
[     3.661] (**) Option "xkb_rules" "evdev"
[     3.661] (**) Option "xkb_model" "pc105"
[     3.661] (**) Option "xkb_layout" "us"
[     3.661] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[     3.661] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[     3.661] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[     3.661] (**) AT Translated Set 2 keyboard: always reports core events
[     3.661] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[     3.661] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[     3.661] (--) evdev: AT Translated Set 2 keyboard: Found keys
[     3.661] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[     3.661] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[     3.661] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 10)
[     3.661] (**) Option "xkb_rules" "evdev"
[     3.661] (**) Option "xkb_model" "pc105"
[     3.661] (**) Option "xkb_layout" "us"
[     3.990] (II) NOUVEAU(0): EDID vendor "AOC", prod id 9008
[     3.990] (II) NOUVEAU(0): Using EDID range info for horizontal sync
[     3.990] (II) NOUVEAU(0): Using EDID range info for vertical refresh
[     3.990] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[     3.990] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[     3.990] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     3.990] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[     3.990] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[     3.990] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[     3.991] (II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[     3.991] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     3.991] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[     3.991] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[     3.991] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[     3.991] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[     3.991] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[     3.991] (II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[     3.991] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[     3.991] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[     3.991] (II) NOUVEAU(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 -hsync +vsync (57.7 kHz e)
[     3.991] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     3.991] (II) NOUVEAU(0): Modeline "1280x1024"x70.0  128.94  1280 1368 1504 1728  1024 1025 1028 1066 -hsync +vsync (74.6 kHz e)
[     3.991] (II) NOUVEAU(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz e)
[     3.991] (II) NOUVEAU(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[     3.991] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[     3.991] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[     3.991] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    12.347] (II) NOUVEAU(0): EDID vendor "AOC", prod id 9008
[    12.347] (II) NOUVEAU(0): Using hsync ranges from config file
[    12.347] (II) NOUVEAU(0): Using vrefresh ranges from config file
[    12.347] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    12.347] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    12.347] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    12.347] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    12.347] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    12.347] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    12.347] (II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    12.347] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    12.347] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    12.347] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    12.347] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    12.347] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    12.347] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    12.347] (II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    12.347] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    12.347] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    12.347] (II) NOUVEAU(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 -hsync +vsync (57.7 kHz e)
[    12.347] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    12.347] (II) NOUVEAU(0): Modeline "1280x1024"x70.0  128.94  1280 1368 1504 1728  1024 1025 1028 1066 -hsync +vsync (74.6 kHz e)
[    12.347] (II) NOUVEAU(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz e)
[    12.347] (II) NOUVEAU(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[    12.347] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    12.347] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    12.347] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    12.611] (II) XKB: reuse xkmfile /var/lib/xkb/server-06D88AAF5356C6CF875D73CED515513D3FEA00ED.xkm
[    25.529] (II) NOUVEAU(0): EDID vendor "AOC", prod id 9008
[    25.529] (II) NOUVEAU(0): Using hsync ranges from config file
[    25.529] (II) NOUVEAU(0): Using vrefresh ranges from config file
[    25.529] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    25.529] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    25.529] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    25.529] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    25.529] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    25.529] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    25.529] (II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    25.529] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    25.529] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    25.529] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    25.529] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    25.529] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    25.529] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    25.529] (II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    25.529] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    25.529] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    25.529] (II) NOUVEAU(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 -hsync +vsync (57.7 kHz e)
[    25.529] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    25.529] (II) NOUVEAU(0): Modeline "1280x1024"x70.0  128.94  1280 1368 1504 1728  1024 1025 1028 1066 -hsync +vsync (74.6 kHz e)
[    25.529] (II) NOUVEAU(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz e)
[    25.529] (II) NOUVEAU(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[    25.529] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    25.529] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    25.529] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[    33.535] (II) NOUVEAU(0): EDID vendor "AOC", prod id 9008
[    33.535] (II) NOUVEAU(0): Using hsync ranges from config file
[    33.535] (II) NOUVEAU(0): Using vrefresh ranges from config file
[    33.535] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    33.535] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[    33.535] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    33.535] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[    33.535] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    33.535] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[    33.535] (II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[    33.535] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    33.535] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    33.535] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    33.535] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    33.535] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    33.535] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    33.535] (II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[    33.535] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    33.535] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    33.535] (II) NOUVEAU(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 -hsync +vsync (57.7 kHz e)
[    33.535] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    33.535] (II) NOUVEAU(0): Modeline "1280x1024"x70.0  128.94  1280 1368 1504 1728  1024 1025 1028 1066 -hsync +vsync (74.6 kHz e)
[    33.535] (II) NOUVEAU(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz e)
[    33.535] (II) NOUVEAU(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[    33.535] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[    33.535] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    33.535] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[   612.138] (II) NOUVEAU(0): EDID vendor "AOC", prod id 9008
[   612.138] (II) NOUVEAU(0): Using hsync ranges from config file
[   612.138] (II) NOUVEAU(0): Using vrefresh ranges from config file
[   612.138] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[   612.138] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[   612.138] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   612.138] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[   612.138] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   612.138] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[   612.138] (II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[   612.138] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   612.138] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   612.138] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   612.138] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   612.138] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[   612.138] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   612.138] (II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   612.138] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   612.138] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[   612.138] (II) NOUVEAU(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 -hsync +vsync (57.7 kHz e)
[   612.138] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   612.138] (II) NOUVEAU(0): Modeline "1280x1024"x70.0  128.94  1280 1368 1504 1728  1024 1025 1028 1066 -hsync +vsync (74.6 kHz e)
[   612.138] (II) NOUVEAU(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz e)
[   612.138] (II) NOUVEAU(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[   612.138] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[   612.138] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   612.138] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[  1999.558] (II) NOUVEAU(0): EDID vendor "AOC", prod id 9008
[  1999.558] (II) NOUVEAU(0): Using hsync ranges from config file
[  1999.558] (II) NOUVEAU(0): Using vrefresh ranges from config file
[  1999.558] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[  1999.558] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[  1999.558] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  1999.558] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[  1999.558] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  1999.558] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[  1999.558] (II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[  1999.558] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  1999.558] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  1999.558] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  1999.558] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  1999.558] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[  1999.558] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  1999.558] (II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[  1999.558] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  1999.558] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[  1999.558] (II) NOUVEAU(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 -hsync +vsync (57.7 kHz e)
[  1999.558] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  1999.558] (II) NOUVEAU(0): Modeline "1280x1024"x70.0  128.94  1280 1368 1504 1728  1024 1025 1028 1066 -hsync +vsync (74.6 kHz e)
[  1999.559] (II) NOUVEAU(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz e)
[  1999.559] (II) NOUVEAU(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[  1999.559] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[  1999.559] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  1999.559] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[  2263.202] (II) NOUVEAU(0): EDID vendor "AOC", prod id 9008
[  2263.202] (II) NOUVEAU(0): Using hsync ranges from config file
[  2263.202] (II) NOUVEAU(0): Using vrefresh ranges from config file
[  2263.202] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[  2263.202] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[  2263.202] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  2263.202] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[  2263.202] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  2263.202] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[  2263.202] (II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[  2263.202] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  2263.202] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  2263.202] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  2263.202] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  2263.202] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[  2263.202] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  2263.202] (II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[  2263.202] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  2263.202] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[  2263.202] (II) NOUVEAU(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 -hsync +vsync (57.7 kHz e)
[  2263.202] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  2263.202] (II) NOUVEAU(0): Modeline "1280x1024"x70.0  128.94  1280 1368 1504 1728  1024 1025 1028 1066 -hsync +vsync (74.6 kHz e)
[  2263.202] (II) NOUVEAU(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz e)
[  2263.202] (II) NOUVEAU(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[  2263.202] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[  2263.202] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  2263.202] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[  4063.567] (II) NOUVEAU(0): EDID vendor "AOC", prod id 9008
[  4063.567] (II) NOUVEAU(0): Using hsync ranges from config file
[  4063.567] (II) NOUVEAU(0): Using vrefresh ranges from config file
[  4063.567] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[  4063.567] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[  4063.567] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  4063.567] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[  4063.567] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  4063.567] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[  4063.567] (II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[  4063.567] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  4063.567] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  4063.567] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  4063.567] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  4063.567] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[  4063.567] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  4063.567] (II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[  4063.568] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  4063.568] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[  4063.568] (II) NOUVEAU(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 -hsync +vsync (57.7 kHz e)
[  4063.568] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  4063.568] (II) NOUVEAU(0): Modeline "1280x1024"x70.0  128.94  1280 1368 1504 1728  1024 1025 1028 1066 -hsync +vsync (74.6 kHz e)
[  4063.568] (II) NOUVEAU(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz e)
[  4063.568] (II) NOUVEAU(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[  4063.568] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[  4063.568] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  4063.568] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[  5596.309] (II) NOUVEAU(0): EDID vendor "AOC", prod id 9008
[  5596.309] (II) NOUVEAU(0): Using hsync ranges from config file
[  5596.309] (II) NOUVEAU(0): Using vrefresh ranges from config file
[  5596.309] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[  5596.309] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[  5596.309] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  5596.309] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[  5596.309] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  5596.309] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[  5596.309] (II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[  5596.309] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  5596.309] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  5596.309] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  5596.309] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  5596.309] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[  5596.309] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  5596.309] (II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[  5596.309] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  5596.309] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[  5596.309] (II) NOUVEAU(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 -hsync +vsync (57.7 kHz e)
[  5596.309] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  5596.309] (II) NOUVEAU(0): Modeline "1280x1024"x70.0  128.94  1280 1368 1504 1728  1024 1025 1028 1066 -hsync +vsync (74.6 kHz e)
[  5596.309] (II) NOUVEAU(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz e)
[  5596.309] (II) NOUVEAU(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[  5596.309] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[  5596.309] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  5596.309] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[  6966.581] (II) NOUVEAU(0): EDID vendor "AOC", prod id 9008
[  6966.581] (II) NOUVEAU(0): Using hsync ranges from config file
[  6966.581] (II) NOUVEAU(0): Using vrefresh ranges from config file
[  6966.581] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[  6966.581] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[  6966.581] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  6966.581] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[  6966.582] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  6966.582] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[  6966.582] (II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[  6966.582] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  6966.582] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  6966.582] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  6966.582] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  6966.582] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[  6966.582] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  6966.582] (II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[  6966.582] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  6966.582] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[  6966.582] (II) NOUVEAU(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 -hsync +vsync (57.7 kHz e)
[  6966.582] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  6966.582] (II) NOUVEAU(0): Modeline "1280x1024"x70.0  128.94  1280 1368 1504 1728  1024 1025 1028 1066 -hsync +vsync (74.6 kHz e)
[  6966.582] (II) NOUVEAU(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz e)
[  6966.582] (II) NOUVEAU(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[  6966.582] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[  6966.582] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  6966.582] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[ 41004.201] (II) NOUVEAU(0): EDID vendor "AOC", prod id 9008
[ 41004.202] (II) NOUVEAU(0): Using hsync ranges from config file
[ 41004.202] (II) NOUVEAU(0): Using vrefresh ranges from config file
[ 41004.202] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[ 41004.202] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[ 41004.202] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 41004.202] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[ 41004.202] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 41004.202] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[ 41004.202] (II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[ 41004.202] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 41004.202] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 41004.202] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 41004.202] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 41004.202] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[ 41004.202] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 41004.202] (II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[ 41004.202] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 41004.202] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[ 41004.202] (II) NOUVEAU(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 -hsync +vsync (57.7 kHz e)
[ 41004.202] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 41004.202] (II) NOUVEAU(0): Modeline "1280x1024"x70.0  128.94  1280 1368 1504 1728  1024 1025 1028 1066 -hsync +vsync (74.6 kHz e)
[ 41004.202] (II) NOUVEAU(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz e)
[ 41004.202] (II) NOUVEAU(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[ 41004.202] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[ 41004.202] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 41004.202] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[ 43030.302] (II) NOUVEAU(0): EDID vendor "AOC", prod id 9008
[ 43030.302] (II) NOUVEAU(0): Using hsync ranges from config file
[ 43030.302] (II) NOUVEAU(0): Using vrefresh ranges from config file
[ 43030.302] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[ 43030.302] (II) NOUVEAU(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[ 43030.302] (II) NOUVEAU(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[ 43030.302] (II) NOUVEAU(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz e)
[ 43030.302] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[ 43030.302] (II) NOUVEAU(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz e)
[ 43030.303] (II) NOUVEAU(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz e)
[ 43030.303] (II) NOUVEAU(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[ 43030.303] (II) NOUVEAU(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[ 43030.303] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[ 43030.303] (II) NOUVEAU(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[ 43030.303] (II) NOUVEAU(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[ 43030.303] (II) NOUVEAU(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[ 43030.303] (II) NOUVEAU(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[ 43030.303] (II) NOUVEAU(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[ 43030.303] (II) NOUVEAU(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[ 43030.303] (II) NOUVEAU(0): Modeline "1024x768"x72.0   78.43  1024 1080 1192 1360  768 769 772 801 -hsync +vsync (57.7 kHz e)
[ 43030.303] (II) NOUVEAU(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[ 43030.303] (II) NOUVEAU(0): Modeline "1280x1024"x70.0  128.94  1280 1368 1504 1728  1024 1025 1028 1066 -hsync +vsync (74.6 kHz e)
[ 43030.303] (II) NOUVEAU(0): Modeline "1280x1024"x72.0  132.75  1280 1368 1504 1728  1024 1025 1028 1067 -hsync +vsync (76.8 kHz e)
[ 43030.303] (II) NOUVEAU(0): Modeline "1440x900"x0.0  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[ 43030.303] (II) NOUVEAU(0): Modeline "1280x960"x0.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[ 43030.303] (II) NOUVEAU(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[ 43030.303] (II) NOUVEAU(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
```

---

### Post by schragge on 2014-12-16
> **feartheterrapin said:**
> I originally had NVIDIA. Just wondering if that created any issues?Maybe. Booting with *nomodeset* kernel option is often required for the NVIDIA driver to work properly. Conversely, Nouveau doesn't like *nomodeset*. After editing */etc/default/grub* don't forget to run ```
sudo update-grub
``` for changes to take effect on next reboot.

> **feartheterrapin said:**
> ```
$ apt-cache policy xserver-xorg-core
xserver-xorg-core:
   [COLOR=red]Installed: (none)[/COLOR]
  Candidate: 2:1.11.4-0ubuntu10.16
  Version table:
     2:1.11.4-0ubuntu10.16 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ precise-security/main amd64 Packages
     2:1.11.4-0ubuntu10 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages

```
Looks like while uninstalling the NVIDIA driver you also accidentally uninstalled some basic packages. **ubuntu-desktop** depends on **xorg** which depends on **xserver-xorg** which in turn depends on **xserver-xorg-core**. Please do
```
sudo apt-get -f install ubuntu-desktop
```

---

### Post by feartheterrapin on 2014-12-16
Have never changed GRUB (yet)

Executed 

"sudo apt-get -f install ubuntu-desktop" and got 

```
The following package was automatically installed and is no longer required:
  screen-resolution-extra
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  nvidia-common
The following NEW packages will be installed:
  nvidia-common ubuntu-desktop
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 23.0 kB of archives.
After this operation, 213 kB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

I continued with no errors.  Should I try to install nouveau again as listed below?

```
$ sudo stop lightdm
$ sudo apt-get install xserver-xorg-video-nouveau
```

---

### Post by schragge on 2014-12-16
> **feartheterrapin said:**
> Have never changed GRUB (yet)Ah, then your *nomodeset* setting didn't take effect yet.

> **feartheterrapin said:**
> Should I try to install nouveau again as listed below?
I expected Xorg packages to get installed automatically, too. Could you please try to install them by hand before installing Nouveau?
```
sudo apt-get install xorg xserver-xorg xserver-xorg-core
```

---

### Post by feartheterrapin on 2014-12-16
Xorg packages installed with no issues or errors.

---

### Post by schragge on 2014-12-16
Ok. Then proceed to install nouveau.

---

### Post by feartheterrapin on 2014-12-16
So I did the ctrl-alt-f1 and executed:
 
 $ sudo stop lightdm
$ sudo apt-get install xserver-xorg-video-nouveau The result was 0-upgraded, 0 installed, 0 to remove, 0 not upgraded.
 
 I then re-booted and got a purple screen hang.  After several re-boot attempts, I am back in.

The, "dmesg -r | grep '^<[0-4]>'" resulted:

```
$ dmesg -r | grep '^<[0-4]>'
<4>[    0.000000] ACPI: RSDP 000000009aca6000 000024 (v02 ALASKA)
<4>[    0.000000] ACPI: XSDT 000000009aca6070 00005C (v01 ALASKA    A M I 01072009 AMI  00010013)
<4>[    0.000000] ACPI: FACP 000000009acaceb8 00010C (v05 ALASKA    A M I 01072009 AMI  00010013)
<4>[    0.000000] ACPI BIOS Warning (bug): Optional FADT field Pm2ControlBlock has zero address or length: 0x0000000000000000/0x1 (20131115/tbfadt-603)
<4>[    0.000000] ACPI: DSDT 000000009aca6168 006D50 (v02 ALASKA    A M I 00000000 INTL 20051117)
<4>[    0.000000] ACPI: FACS 000000009ba07f80 000040
<4>[    0.000000] ACPI: APIC 000000009acacfc8 00008E (v03 ALASKA    A M I 01072009 AMI  00010013)
<4>[    0.000000] ACPI: FPDT 000000009acad058 000044 (v01 ALASKA    A M I 01072009 AMI  00010013)
<4>[    0.000000] ACPI: MCFG 000000009acad0a0 00003C (v01 ALASKA    A M I 01072009 MSFT 00010013)
<4>[    0.000000] ACPI: HPET 000000009acad0e0 000038 (v01 ALASKA    A M I 01072009 AMI  00000005)
<4>[    0.000000] ACPI: SSDT 000000009acad1a8 001158 (v01 AMD    POWERNOW 00000001 AMD  00000001)
<4>[    0.000000] ACPI: BGRT 000000009acad170 000038 (v00 ALASKA    A M I 01072009 AMI  00010013)
<4>[    0.000000] Zone ranges:
<4>[    0.000000]   DMA      [mem 0x00001000-0x00ffffff]
<4>[    0.000000]   DMA32    [mem 0x01000000-0xffffffff]
<4>[    0.000000]   Normal   [mem 0x100000000-0x25effffff]
<4>[    0.000000] Movable zone start for each node
<4>[    0.000000] Early memory node ranges
<4>[    0.000000]   node   0: [mem 0x00001000-0x0009ffff]
<4>[    0.000000]   node   0: [mem 0x00100000-0x9ab1afff]
<4>[    0.000000]   node   0: [mem 0x9ca51000-0x9ca51fff]
<4>[    0.000000]   node   0: [mem 0x9cc58000-0x9d082fff]
<4>[    0.000000]   node   0: [mem 0x9d7f4000-0x9d7fffff]
<4>[    0.000000]   node   0: [mem 0x100001000-0x25effffff]
<4>[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 2039899
<4>[    0.000000] Policy zone: Normal
<4>[    0.000000] Memory: 7781056K/8289220K available (7623K kernel code, 1139K rwdata, 3488K rodata, 1356K init, 1444K bss, 508164K reserved)
<4>[    0.008469] ACPI: All ACPI Tables successfully acquired
<4>[    0.453374] ACPI: Executed 2 blocks of module-level executable AML code
<4>[    0.460815] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S1_] (20131115/hwxface-580)
<4>[    0.460819] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S2_] (20131115/hwxface-580)
<4>[    1.100952] Dquot-cache hash table entries: 512 (order 0, 4096 bytes)
<4>[    1.520404] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
<4>[    1.578498] r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
<4>[    2.104698] sr0: scsi3-mmc drive: 16x/48x writer dvd-ram cd/rw xa/form2 cdda tray
<4>[    2.581952] usb 9-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
<4>[    2.662320] MXM: GUID detected in BIOS
<4>[    2.758568] hda-intel 0000:00:14.2: Using LPIB position fix
<4>[    2.762030] hda-intel 0000:00:14.2: Enable sync_write for stable communication
<4>[    2.770104] SKU: Nid=0x1d sku_cfg=0x4004c601
<4>[    2.770107] SKU: port_connectivity=0x1
<4>[    2.770108] SKU: enable_pcbeep=0x0
<4>[    2.770110] SKU: check_sum=0x00000004
<4>[    2.770111] SKU: customization=0x000000c6
<4>[    2.770112] SKU: external_amp=0x0
<4>[    2.770113] SKU: platform_type=0x0
<4>[    2.770115] SKU: swap=0x0
<4>[    2.770116] SKU: override=0x1
<4>[    2.770372] autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:line
<4>[    2.770374]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
<4>[    2.770375]    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
<4>[    2.770376]    mono: mono_out=0x0
<4>[    2.770377]    dig-out=0x11/0x0
<4>[    2.770378]    inputs:
<4>[    2.770380]      Front Mic=0x19
<4>[    2.770381]      Rear Mic=0x18
<4>[    2.770383]      Line=0x1a
<4>[    2.770384] realtek: No valid SSID, checking pincfg 0x4004c601 for NID 0x1d
<4>[    2.770385] realtek: Enabling init ASM_ID=0xc601 CODEC_ID=10ec0887
<4>[    2.816354] nouveau W[     DRM] failed to create encoder 0/1/0: -19
<4>[    2.816358] nouveau W[     DRM] TV-1 has no encoders, removing
<3>[    3.104499] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 185
<3>[    3.104505] Raw EDID:
<3>[    3.104508]      00 ff ff ff ff ff ff 00 05 e3 30 23 6e 30 00 00
<3>[    3.104511]      15 13 01 03 68 2f 1a 78 2a 35 85 a6 56 48 9a 24
<3>[    3.104515]      12 50 54 bf ef 00 61 4c 81 80 81 8a 81 8c 95 00
<3>[    3.104518]      81 40 71 4f b3 00 01 ff ff ff ff ff ff ff ff ff
<3>[    3.104521]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[    3.104524]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[    3.104528]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[    3.104531]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[    3.736590] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 210
<3>[    3.736592] Raw EDID:
<3>[    3.736594]      00 ff ff ff ff ff ff 00 05 e3 30 23 6e 30 00 00
<3>[    3.736595]      15 13 01 03 68 2f 1a 78 2a 35 85 a6 56 48 9a 24
<3>[    3.736596]      12 50 54 bf ef 00 61 4c 81 80 81 8a 81 8c 95 00
<3>[    3.736597]      81 40 71 4f b3 00 02 3a 80 18 71 38 2d 40 58 2c
<3>[    3.736598]      45 00 dc 0c 11 00 00 1e 00 00 00 fd 00 38 4b 18
<3>[    3.736599]      50 11 00 0a 20 20 20 20 20 20 00 00 00 fc 00 32
<3>[    3.736600]      33 33 30 56 0a 20 20 20 20 20 20 20 00 00 00 ff
<3>[    3.736601]      00 4f ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[    3.770468] sd 6:0:0:0: [sdd] No Caching mode page found
<3>[    3.770472] sd 6:0:0:0: [sdd] Assuming drive cache: write through
<3>[    3.781678] sd 6:0:0:0: [sdd] No Caching mode page found
<3>[    3.781689] sd 6:0:0:0: [sdd] Assuming drive cache: write through
<4>[    3.976464] vboxdrv: fAsync=0 offMin=0x4c5 offMax=0x3e55
<3>[    4.476156] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 103
<3>[    4.476159] Raw EDID:
<3>[    4.476160]      00 ff ff ff ff ff ff 00 05 e3 30 23 6e 30 00 00
<3>[    4.476162]      15 13 01 03 68 2f 1a 78 2a 35 85 a6 56 48 9a 24
<3>[    4.476163]      12 50 54 bf ef 00 61 4c 81 80 81 8a 81 8c 95 00
<3>[    4.476164]      81 40 71 4f b3 00 02 3a 80 18 71 38 2d 40 58 2c
<3>[    4.476165]      45 00 dc 0c 11 00 00 1e 00 00 00 fd 00 38 4b 18
<3>[    4.476166]      50 11 00 0a 20 20 20 20 20 1f ff ff ff ff ff ff
<3>[    4.476167]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[    4.476168]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[    4.503570] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 139
<3>[    4.503571] Raw EDID:
<3>[    4.503573]      00 ff ff ff ff ff ff 00 05 e3 30 23 6e 30 00 00
<3>[    4.503574]      15 13 01 03 68 2f 1a 78 2a 35 85 a6 56 48 9a 24
<3>[    4.503575]      12 50 54 bf ef 00 61 4c 81 80 81 8a 81 8c 95 00
<3>[    4.503575]      81 40 71 4f b3 00 02 3a 80 18 71 38 2d 40 58 2c
<3>[    4.503576]      45 00 dc 0c 11 00 00 1e 00 00 00 fd 00 38 4b 18
<3>[    4.503577]      50 11 00 0a 20 20 20 20 20 20 00 00 00 fc 00 32
<3>[    4.503578]      33 33 30 56 0a 20 20 20 20 20 20 20 00 00 00 ff
<3>[    4.503579]      00 52 34 32 39 35 4a 41 30 1f ff ff ff ff ff ff
<3>[   17.481507] sd 6:0:0:0: [sdd] No Caching mode page found
<3>[   17.481511] sd 6:0:0:0: [sdd] Assuming drive cache: write through
<3>[   25.983809] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 188
<3>[   25.983812] Raw EDID:
<3>[   25.983814]      00 ff ff ff ff ff ff 00 05 e3 30 23 6e 30 00 00
<3>[   25.983815]      15 13 01 03 68 2f 1a 78 2a 35 85 a6 56 48 9a 24
<3>[   25.983816]      12 50 54 bf ef 00 61 4c 81 80 81 8a 81 8c 95 00
<3>[   25.983817]      81 40 71 4f b3 00 02 3a 80 18 71 38 2d 40 58 2c
<3>[   25.983818]      45 00 dc 0c 11 00 00 1e 00 00 00 fd 00 38 4b 18
<3>[   25.983819]      50 11 00 0a 20 20 20 20 20 20 00 00 00 fc 00 32
<3>[   25.983820]      1f ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   25.983821]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.063840] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 242
<3>[   26.063843] Raw EDID:
<3>[   26.063844]      00 ff ff ff ff ff ff 00 05 e3 30 23 6e 30 00 00
<3>[   26.063845]      15 13 01 03 68 2f 1a 78 2a 35 85 a6 56 48 9a 24
<3>[   26.063846]      12 50 54 bf ef 00 61 4c 81 80 81 8a 81 8c 95 00
<3>[   26.063847]      81 40 71 3f ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.063848]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.063849]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.063850]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.063851]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.091128] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 11
<3>[   26.091129] Raw EDID:
<3>[   26.091130]      00 ff ff ff ff ff ff 00 05 e3 30 23 6e 30 00 00
<3>[   26.091131]      15 13 01 03 68 2f 1a 78 2a 1f ff ff ff ff ff ff
<3>[   26.091132]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.091133]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.091134]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.091135]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.091136]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.091137]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.118443] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 148
<3>[   26.118444] Raw EDID:
<3>[   26.118445]      00 ff ff ff ff ff ff 00 05 e3 30 23 6e 30 00 00
<3>[   26.118446]      15 13 01 03 68 2f 1a 78 2a 35 85 a6 56 48 9a 24
<3>[   26.118447]      12 50 54 bf ef 00 61 4c 81 80 81 8a 81 8c 95 00
<3>[   26.118448]      81 40 71 4f b3 00 02 3a 80 18 71 38 2d 40 58 2c
<3>[   26.118449]      45 00 dc 0c 11 00 00 1e 00 00 00 fd 00 38 4b 18
<3>[   26.118450]      50 0f ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.118451]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
<3>[   26.118452]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
$ 


```

---

### Post by schragge on 2014-12-17
So, changing the driver didn't help. Well, you can try to reconfigure the X server with
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

And remove "quiet splash" from the kernel command line in */etc/default/grub*. This way you'll at least get a wall of text output instead of the purple screen on boot and be able to see at what point it stucks. Don't forget to ```
sudo update-grub
``` after editing */etc/default/grub* for any changes there to take effect.

---

### Post by feartheterrapin on 2014-12-17
X server reconfigured as recommend.
 
 GRUB changed as follows:
 
 ```

 # GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
 GRUB_CMDLINE_LINUX_DEFAULT=
```
 
 ```

 $ sudo update-grub  
 Generating grub.cfg ...  
 Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.  
 Found linux image: /boot/vmlinuz-3.13.0-43-generic  
 Found initrd image: /boot/initrd.img-3.13.0-43-generic  
 Found linux image: /boot/vmlinuz-3.13.0-41-generic  
 Found initrd image: /boot/initrd.img-3.13.0-41-generic  
 Found linux image: /boot/vmlinuz-3.13.0-40-generic  
 Found initrd image: /boot/initrd.img-3.13.0-40-generic  
 Found linux image: /boot/vmlinuz-3.13.0-39-generic  
 Found initrd image: /boot/initrd.img-3.13.0-39-generic  
 Found linux image: /boot/vmlinuz-3.5.0-54-generic  
 Found initrd image: /boot/initrd.img-3.5.0-54-generic  
 Found memtest86+ image: /boot/memtest86+.bin  
 Adding boot menu entry for EFI firmware configuration  
 done  
 $
```
 
 Reboot successful.   
 I will report back on the next boot hang.  I will be securing power for several days this weekend.   
 I really appreciate your assistance [COLOR=#000000]schragge.[/COLOR]

---

### Post by feartheterrapin on 2015-01-11
Just an update:  It has been 3 weeks and no purple screen hangs.   However, on three separate occasions, the screen suddenly changes resolution to 640X480.  When I click on something afterwards, the screen reverts to 1920x1080.    Otherwise, no issues.

---

