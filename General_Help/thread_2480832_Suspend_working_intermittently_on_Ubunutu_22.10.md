---
title: "Suspend working intermittently on Ubunutu 22.10"
date: 2022-11-11
forum: General Help
---

### Post by Raging_Cascadoo on 2022-11-11
I had made a post a few months back about a similar issue on Ubuntu 22.04 which was not being able to suspend/resume due to an amdgpu reset issue. This was resolved by moving to a newer kernel version, 5.18 at the time. This worked well but then about a month after I had issues suspending again. I didn't bother to troubleshoot at the time and thought that upgrading to 22.10 with a newer kernel/fixes than 22.04 would have resolved it.

Unfortunately the issue still persists on Ubuntu 22.10 but does not seem to be related to the amdgpu reset issue anymore. From what I can tell, no errors are present when I look at journalctl at the time of performing a suspend. When I compare the output on journalctl from a successful suspend to an unsuccessful one, the outputs look the same to me. What sometime happens is that I can see the system enter sleep state: suspend on the logs, I lose connection to the suspend, no display but the PC is still on and running. Even if I leave it for some time after, it never suspends and at that point it cannot resume as it's basically frozen requiring a hard reboot.

I used a laptop connected to the PC and ran "journalctl -f" to monitor the suspend process. I am not sure how to troubleshoot this or what to check as I don't see any errors via journalctl during suspend well at least until I lose ssh connection.

Extract of logs when suspend does not work:

```
Broadcast message from marlon@MBLPC (Fri 2022-11-11 16:00:10 AST):

The system is going down for suspend NOW!

Nov 11 16:00:10 MBLPC ModemManager[1939]: <info>  [sleep-monitor-systemd] system is about to suspend
Nov 11 16:00:10 MBLPC NetworkManager[1944]: <info>  [1668196810.6292] manager: sleep: sleep requested (sleeping: no  enabled: yes)
Nov 11 16:00:10 MBLPC NetworkManager[1944]: <info>  [1668196810.6293] device (wlp8s0): state change: unavailable -> unmanaged (reason 'sleeping', sys-iface-s
Nov 11 16:00:10 MBLPC NetworkManager[1944]: <info>  [1668196810.6298] manager: NetworkManager state is now ASLEEP
Nov 11 16:00:10 MBLPC gnome-shell[3137]: Timelines with detached actors are not supported. <unnamed>[<Gjs_ui_panel_QuickSettings>:0x55c2eabbe5e0] in animatio
Nov 11 16:00:13 MBLPC systemd[1]: Reached target Sleep.
Nov 11 16:00:13 MBLPC systemd[1]: Starting Record successful boot for GRUB...
Nov 11 16:00:13 MBLPC systemd[1]: Starting System Suspend...
Nov 11 16:00:13 MBLPC systemd-sleep[16953]: Entering sleep state 'suspend'...
Nov 11 16:00:13 MBLPC kernel: PM: suspend entry (deep)
Nov 11 16:00:13 MBLPC systemd[1]: grub-common.service: Deactivated successfully.
Nov 11 16:00:13 MBLPC systemd[1]: Finished Record successful boot for GRUB.
Nov 11 16:00:13 MBLPC systemd[1]: Starting GRUB failed boot detection...
Nov 11 16:00:13 MBLPC systemd[1]: grub-initrd-fallback.service: Deactivated successfully.
Nov 11 16:00:13 MBLPC systemd[1]: Finished GRUB failed boot detection.
```

Looking at journalctl for the same time stamp, after a hard shutdown, then reboot of system.

```
Nov 11 16:00:13 MBLPC kernel: PM: suspend entry (deep)
Nov 11 16:00:13 MBLPC systemd-sleep[16953]: Entering sleep state 'suspend'...
Nov 11 16:00:13 MBLPC systemd[1]: Starting System Suspend...
Nov 11 16:00:13 MBLPC systemd[1]: Starting Record successful boot for GRUB...
Nov 11 16:00:13 MBLPC systemd[1]: Reached target Sleep.
Nov 11 16:00:10 MBLPC gnome-shell[3137]: Timelines with detached actors are not supported. <unnamed>[<Gjs_ui_panel_QuickSettings>:0x55c2eabbe5e0] in animation of duration 150ms but not on stage.
Nov 11 16:00:10 MBLPC NetworkManager[1944]: <info>  [1668196810.6298] manager: NetworkManager state is now ASLEEP
Nov 11 16:00:10 MBLPC NetworkManager[1944]: <info>  [1668196810.6293] device (wlp8s0): state change: unavailable -> unmanaged (reason 'sleeping', sys-iface-state: 'managed')
Nov 11 16:00:10 MBLPC NetworkManager[1944]: <info>  [1668196810.6292] manager: sleep: sleep requested (sleeping: no  enabled: yes)
Nov 11 16:00:10 MBLPC ModemManager[1939]: <info>  [sleep-monitor-systemd] system is about to suspend
```

Entries after this is for when I power the machine on after the hard shutdown.
[I]
*Currently using liquorix kernel for ACS patch but the same issue happens with stock 22.10 kernel[/I]

Machine Specs via inxi:

```

  Host: MBLPC Kernel: 6.0.0-8.1-liquorix-amd64 arch: x86_64 bits: 64
    Desktop: GNOME v: 43.0 Distro: Ubuntu 22.10 (Kinetic Kudu)
Machine:
  Type: Desktop Mobo: ASRock model: X370 Taichi serial: <superuser required>
    UEFI: American Megatrends v: P7.00 date: 01/15/2022
CPU:
  Info: 8-core model: AMD Ryzen 7 3800X bits: 64 type: MT MCP cache:
    L2: 4 MiB
  Speed (MHz): avg: 3979 min/max: 2200/4559 cores: 1: 3862 2: 3900 3: 4447
    4: 4434 5: 3619 6: 4438 7: 3675 8: 4062 9: 3707 10: 3900 11: 3900 12: 3900
    13: 3900 14: 3900 15: 4133 16: 3900
Graphics:
  Device-1: AMD Navi 23 [Radeon RX 6600/6600 XT/6600M] driver: amdgpu
    v: kernel
  Device-2: AMD Hawaii PRO [Radeon R9 290/390] driver: vfio-pci v: N/A
  Display: x11 server: X.Org v: 1.21.1.4 with: Xwayland v: 22.1.3 driver:
    X: loaded: amdgpu unloaded: fbdev,modesetting,radeon,vesa gpu: amdgpu
    resolution: 1: 1920x1080~60Hz 2: 2560x1440~60Hz
  OpenGL: renderer: AMD Radeon RX 6600 XT (navi23 LLVM 15.0.2 DRM 3.48
    6.0.0-8.1-liquorix-amd64) v: 4.6 Mesa 22.2.1
Audio:
  Device-1: C-Media CMI8788 [Oxygen HD Audio] driver: snd_oxygen
  Device-2: AMD Navi 21/23 HDMI/DP Audio driver: vfio-pci
  Device-3: AMD Hawaii HDMI Audio [Radeon R9 290/290X / 390/390X]
    driver: vfio-pci
  Device-4: AMD Starship/Matisse HD Audio driver: snd_hda_intel
  Sound Server-1: ALSA v: k6.0.0-8.1-liquorix-amd64 running: yes
  Sound Server-2: PipeWire v: 0.3.58 running: yes
Network:
  Device-1: Intel Dual Band Wireless-AC 3168NGW [Stone Peak] driver: iwlwifi
  IF: wlp8s0 state: down mac: a0:d3:7a:cb:a1:60
  Device-2: Intel I211 Gigabit Network driver: igb
  IF: enp10s0 state: up speed: 1000 Mbps duplex: full
    mac: 70:85:c2:71:42:c9
  IF-ID-1: br0 state: up speed: 1000 Mbps duplex: unknown
    mac: fa:58:42:ba:08:d4
  IF-ID-2: virbr0 state: down mac: 52:54:00:ba:f1:fb
  IF-ID-3: virbr1 state: down mac: 52:54:00:ba:c2:6e
Bluetooth:
  Device-1: Intel Wireless-AC 3168 Bluetooth type: USB driver: btusb
  Report: hciconfig ID: hci0 state: up address: A0:D3:7A:CB:A1:64 bt-v: 2.1
Drives:
  Local Storage: total: 13.41 TiB used: 2.5 TiB (18.7%)
  ID-1: /dev/nvme0n1 vendor: Western Digital model: WD Green SN350 2TB
    size: 1.82 TiB
  ID-2: /dev/sda vendor: Seagate model: ST4000DM004-2CV104 size: 3.64 TiB
  ID-3: /dev/sdb vendor: Seagate model: ST4000DM004-2CV104 size: 3.64 TiB
  ID-4: /dev/sdc vendor: Smart Modular Tech. model: SHGS31-500GS-2
    size: 465.76 GiB
  ID-5: /dev/sdd vendor: Seagate model: ST4000DM004-2CV104 size: 3.64 TiB
  ID-6: /dev/sde vendor: TeamGroup model: L5Lite3D240G size: 223.57 GiB
Partition:
  ID-1: / size: 1.58 TiB used: 197.11 GiB (12.2%) fs: ext4 dev: /dev/dm-0
  ID-2: /boot/efi size: 2 GiB used: 5.2 MiB (0.3%) fs: vfat
    dev: /dev/nvme0n1p1
Swap:
  ID-1: swap-1 type: partition size: 64 GiB used: 0 KiB (0.0%)
    dev: /dev/nvme0n1p2
Sensors:
  System Temperatures: cpu: 51.1 C mobo: N/A gpu: amdgpu temp: 40.0 C
  Fan Speeds (RPM): N/A gpu: amdgpu fan: 0
Info:
  Processes: 425 Uptime: 41m Memory: 62.73 GiB used: 6.08 GiB (9.7%)
  Shell: Bash inxi: 3.3.21
```
[I]
*I wanted to mention that I actually did not have any issues suspending with Ubuntu 20.04. Other things I tried where switching from wayland to xorg and also testing with the the different ACPI power settings in the BIOS.[/I]

---

### Post by Raging_Cascadoo on 2022-11-13
I found some helpful information to aid with troubleshooting via [https://01.org/blogs/rzhang/2015/best-practice-debug-linux-suspend/hibernate-issues](https://01.org/blogs/rzhang/2015/best-practice-debug-linux-suspend/hibernate-issues) but I think it would prove more useful if troubleshooting via serial as I lose ssh connection almost immediately after suspend. I do have a serial breakout connector but don't have the appropriate gender cable to connect to it.

What I ended trying instead was to enable hibernate. I used the guide at [https://ubuntuhandbook.org/index.php/2021/08/enable-hibernate-ubuntu-21-10/](https://ubuntuhandbook.org/index.php/2021/08/enable-hibernate-ubuntu-21-10/) to specify the swap partition used for hibernate and this worked! So far I have been able to hibernate and resume without issue...crossing fingers and hoping that I don't encounter issues in the future. Hibernating does seem to take a little longer than the regular suspend to memory even with my swap partition residing on a nvme drive. Resume from hibernation definitely takes longer than suspend as it goes through post and kernel boot up. I came across [https://www.kernel.org/doc/html/v4.18/admin-guide/pm/sleep-states.html](https://www.kernel.org/doc/html/v4.18/admin-guide/pm/sleep-states.html) and upon reading the hibernation section, the post and bootup on resume from hibernate can probably be referenced to this extract:

***[COLOR=#FF8C00]"After wakeup, control goes to the platform firmware that runs a boot loader which boots a fresh instance of the kernel (control may also go directly to the boot loader, depending on the system configuration, but anyway it causes a fresh instance of the kernel to be booted).  That new instance of the kernel (referred to as the restore kernel) looks for a hibernation image in persistent storage and if one is found, it is loaded into memory.  Next, all activity in the system is stopped and the restore kernel overwrites itself with the image contents and jumps into a special trampoline area in the original kernel stored in the image (referred to as the image kernel), which is where the special architecture-specific low-level code is needed.  Finally, the image kernel restores the system to the pre-hibernation state and allows user space to run again.[/COLOR]"***

From what I understand, suspend is S3 state while hibernate is S4. As for the issues I am having with suspend and no errors being represented via logs, I assume it is related to this extract found from same kernal.org guide under suspend to ram section:

[COLOR=#FF8C00]***"In particular, on ACPI-based systems the kernel passes control to the platform firmware (BIOS) as the last step during S2RAM transitions and that usually results in powering down some more low-level components that are not directly controlled by the kernel."***[/COLOR]

Maybe if I was connected via serial with the appropriate console parameters I may be able to see some output at this point but I probably would not have the knowledge or skill set required to resolve the issue. While more of a work around instead of a fix, I am glad that I can at least hibernate instead of having to power off and on and the extra time to hibernate/resume compared to suspend doesn't affect me.  

So if you having suspend issues, maybe you can try to enable hibernate and see if that works for you.

---

### Post by Raging_Cascadoo on 2022-11-14
Unfortunately, I encountered the same error when hibernating which is the system remains on and no errors are present on the logs :confused:

Extract from logs:

```
Nov 13 20:48:54 MBLPC kernel: PM: hibernation: hibernation entry
Nov 13 20:48:54 MBLPC systemd-sleep[71729]: Entering sleep state 'hibernate'...
Nov 13 20:48:54 MBLPC systemd[1]: Finished GRUB failed boot detection.
Nov 13 20:48:54 MBLPC systemd[1]: grub-initrd-fallback.service: Deactivated successfully.
Nov 13 20:48:54 MBLPC systemd[1]: Starting GRUB failed boot detection...
Nov 13 20:48:54 MBLPC systemd[1]: Finished Record successful boot for GRUB.
Nov 13 20:48:54 MBLPC systemd[1]: grub-common.service: Deactivated successfully.
Nov 13 20:48:54 MBLPC systemd[1]: Starting Hibernate...
Nov 13 20:48:54 MBLPC systemd[1]: Starting Record successful boot for GRUB...
Nov 13 20:48:54 MBLPC systemd[1]: Reached target Sleep.
Nov 13 20:48:51 MBLPC NetworkManager[1706]: <info>  [1668386931.1487] manager: NetworkManager state is now ASLEEP
Nov 13 20:48:51 MBLPC NetworkManager[1706]: <info>  [1668386931.1482] device (wlp8s0): state change: unavailable -> unmanaged (reason 'sleeping', sys-iface-state: 'managed')
Nov 13 20:48:51 MBLPC sudo[71703]: pam_unix(sudo:session): session closed for user root
Nov 13 20:48:51 MBLPC NetworkManager[1706]: <info>  [1668386931.1480] manager: sleep: sleep requested (sleeping: no  enabled: yes)
Nov 13 20:48:51 MBLPC ModemManager[1715]: <info>  [sleep-monitor-systemd] system is about to suspend
Nov 13 20:48:51 MBLPC sudo[71703]: pam_unix(sudo:session): session opened for user root(uid=0) by (uid=1000)
Nov 13 20:48:51 MBLPC sudo[71703]:   marlon : TTY=pts/0 ; PWD=/home/marlon ; USER=root ; COMMAND=/usr/bin/systemctl hibernate
```

I am beginning to wonder if this could possibly be related to BIOS firmware or possibly a board issue.

---

### Post by Raging_Cascadoo on 2022-11-26
Ok, so I managed to get this "resolved" by 2 methods, one a workaround I guess and the other a proper fix.

Workaround:

I mentioned that the biggest issue I had when looking at journalctl is that after entering the sleep state there was no more information printed to the logs so I could not tell what happened after this point when the machine hanged. Initially I was using the "no_console_suspend initcall_debug" parameters which did actually provide more information after entering the sleep state but only on a successful suspend. What made a big difference was the "ignore_loglevel" which would print output to the display after the machine entered the sleep state. Thinking for sure that I would now be able to catch whatever error caused the machine to hang on suspend I realized that the machine stopped hanging once I added the ignore_loglevel parameter. I don't exactly understand why but this works.

** With the ignore_loglevel parameter you will actually be able to see the suspend process explained at [https://wiki.ubuntu.com/UnderstandingSuspend](https://wiki.ubuntu.com/UnderstandingSuspend)*

Problem & Fix:

I came across a forum post with similar issues that mentioned their problem was related to a  nvme drive. Thinking back on it the only difference in hardware I had since experiencing the  suspend issue was the installation of a nvme drive. I expected to see some nvme related error via the logs but as mentioned before after using the ignore_loglevel parameter the machine stopped hanging and no errors or delays were present on the logs. I decided to just go ahead and test disabling the wakeup of the nvme hdd.

The forum post and guides I mentioned before recommended disabling and testing pci devices via /proc/acpi/wakeup.I found the pcie id of the nvme via the logs and lshw. 

lshw -short:
```

H/W path                      Device          Class          Description
========================================================================
                                              system         To Be Filled By O.E.M. (To Be Filled By O.E.M.)
/0                                            bus            X370 Taichi
/0/0                                          memory         64KiB BIOS
/0/e                                          memory         64GiB System Memory
/0/e/0                                        memory         16GiB DIMM DDR4 Synchronous Unbuffered (Unregistered) 2133 MHz (0.5 ns)
/0/e/1                                        memory         16GiB DIMM DDR4 Synchronous Unbuffered (Unregistered) 2133 MHz (0.5 ns)
/0/e/2                                        memory         16GiB DIMM DDR4 Synchronous Unbuffered (Unregistered) 2133 MHz (0.5 ns)
/0/e/3                                        memory         16GiB DIMM DDR4 Synchronous Unbuffered (Unregistered) 2133 MHz (0.5 ns)
/0/11                                         memory         512KiB L1 cache
/0/12                                         memory         4MiB L2 cache
/0/13                                         memory         32MiB L3 cache
/0/14                                         processor      AMD Ryzen 7 3800X 8-Core Processor
/0/100                                        bridge         Starship/Matisse Root Complex
/0/100/0.2                                    generic        Starship/Matisse IOMMU
/0/100/1.1                                    bridge         Starship/Matisse GPP Bridge
/0/100/1.1/0                  /dev/nvme0      storage        WD Green SN350 2TB
/0/100/1.1/0/0                hwmon0          disk           NVMe disk
/0/100/1.1/0/2                /dev/ng0n1      disk           NVMe disk
/0/100/1.1/0/1                /dev/nvme0n1    disk           2TB NVMe disk
/0/100/1.1/0/1/1              /dev/nvme0n1p1  volume         2047MiB Windows FAT volume
/0/100/1.1/0/1/2              /dev/nvme0n1p2  volume         63GiB Linux swap volume
/0/100/1.1/0/1/3              /dev/nvme0n1p3  volume         150GiB LVM Physical Volume
/0/100/1.1/0/1/4              /dev/nvme0n1p4  volume         1647GiB LVM Physical Volume
/0/100/1.3                                    bridge         Starship/Matisse GPP Bridge
/0/100/1.3/0                                  bus            X370 Series Chipset USB 3.1 xHCI Controller
/0/100/1.3/0/0                usb1            bus            xHCI Host Controller
/0/100/1.3/0/0/2                              bus            USB2.0 Hub
/0/100/1.3/0/0/2/1                            bus            USB2.0 Hub
/0/100/1.3/0/0/2/1/1                          bus            USB2.1 Hub
/0/100/1.3/0/0/2/1/3                          generic        Xbox 360 Wireless Receiver for Windows
/0/100/1.3/0/0/2/3            input62         input          EVGA Corporation EVGA Z15 RGB Gaming Keyboard
/0/100/1.3/0/0/2/4                            bus            USB2.0 Hub
/0/100/1.3/0/0/2/4/1          scsi12          storage        Flash Card Reader/Writer
/0/100/1.3/0/0/2/4/1/0.0.0    /dev/sdf        disk           Card  Reader
/0/100/1.3/0/0/2/4/1/0.0.0/0  /dev/sdf        disk           
/0/100/1.3/0/0/6                              bus            USB2.1 Hub
/0/100/1.3/0/0/6/1                            bus            USB2.1 Hub
/0/100/1.3/0/0/6/3            input75         input          Sony Computer Entertainment Wireless Controller Motion Sensors
/0/100/1.3/0/0/9                              communication  Wireless-AC 3168 Bluetooth
/0/100/1.3/0/1                usb2            bus            xHCI Host Controller
/0/100/1.3/0/1/2                              bus            USB3.0 Hub
/0/100/1.3/0/1/2/1                            bus            USB3.0 Hub
/0/100/1.3/0/1/2/1/1                          bus            USB3.1 Hub
/0/100/1.3/0/1/2/4                            bus            USB3.0 Hub
/0/100/1.3/0/1/6                              bus            USB3.2 Hub
/0/100/1.3/0/1/6/1                            bus            USB3.2 Hub
/0/100/1.3/0.1                scsi0           storage        X370 Series Chipset SATA Controller
/0/100/1.3/0.1/0              /dev/sda        volume         3726GiB ST4000DM004-2CV1
/0/100/1.3/0.1/1              /dev/sdb        disk           4TB ST4000DM004-2CV1
/0/100/1.3/0.1/1/1                            volume         3726GiB EFI partition
/0/100/1.3/0.1/0.0.0          /dev/sdc        disk           500GB SHGS31-500GS-2
/0/100/1.3/0.1/0.0.0/1        /dev/sdc1       volume         465GiB EXT4 volume
/0/100/1.3/0.2                                bridge         X370 Series Chipset PCIe Upstream Port
/0/100/1.3/0.2/0                              bridge         300 Series Chipset PCIe Port
/0/100/1.3/0.2/2                              bridge         300 Series Chipset PCIe Port
/0/100/1.3/0.2/2/0            scsi8           storage        ASM1062 Serial ATA Controller
/0/100/1.3/0.2/2/0/0          /dev/sdd        disk           4TB ST4000DM004-2CV1
/0/100/1.3/0.2/2/0/0/1        /dev/sdd1       volume         15MiB reserved partition
/0/100/1.3/0.2/2/0/0/2        /dev/sdd2       volume         3726GiB Windows NTFS volume
/0/100/1.3/0.2/2/0/1          /dev/sde        disk           240GB TEAML5Lite3D240G
/0/100/1.3/0.2/2/0/1/1        /dev/sde1       volume         499MiB Windows NTFS volume
/0/100/1.3/0.2/2/0/1/2        /dev/sde2       volume         222GiB Windows NTFS volume
/0/100/1.3/0.2/2/0/1/3        /dev/sde3       volume         99MiB Windows FAT volume
/0/100/1.3/0.2/2/0/1/4        /dev/sde4       volume         827MiB Windows NTFS volume
/0/100/1.3/0.2/3                              bridge         300 Series Chipset PCIe Port
/0/100/1.3/0.2/3/0                            bridge         ASM1184e 4-Port PCIe x1 Gen2 Packet Switch
/0/100/1.3/0.2/3/0/1                          bridge         ASM1184e 4-Port PCIe x1 Gen2 Packet Switch
/0/100/1.3/0.2/3/0/1/0        wlp8s0          network        Dual Band Wireless-AC 3168NGW [Stone Peak]
/0/100/1.3/0.2/3/0/3                          bridge         ASM1184e 4-Port PCIe x1 Gen2 Packet Switch
/0/100/1.3/0.2/3/0/5                          bridge         ASM1184e 4-Port PCIe x1 Gen2 Packet Switch
/0/100/1.3/0.2/3/0/5/0        enp10s0         network        I211 Gigabit Network Connection
/0/100/1.3/0.2/3/0/7                          bridge         ASM1184e 4-Port PCIe x1 Gen2 Packet Switch
/0/100/1.3/0.2/4                              bridge         300 Series Chipset PCIe Port
/0/100/1.3/0.2/4/0            /dev/fb0        bridge         ASM1083/1085 PCIe to PCI Bridge
/0/100/1.3/0.2/4/0/4          card0           multimedia     CMI8788 [Oxygen HD Audio]
/0/100/3.1                                    bridge         Starship/Matisse GPP Bridge
/0/100/3.1/0                                  bridge         Navi 10 XL Upstream Port of PCI Express Switch
/0/100/3.1/0/0                                bridge         Navi 10 XL Downstream Port of PCI Express Switch
/0/100/3.1/0/0/0              /dev/fb0        display        Navi 23 [Radeon RX 6600/6600 XT/6600M]
/0/100/3.1/0/0/0.1                            multimedia     Navi 21/23 HDMI/DP Audio Controller
/0/100/3.2                                    bridge         Starship/Matisse GPP Bridge
/0/100/3.2/0                                  display        Hawaii PRO [Radeon R9 290/390]
/0/100/3.2/0.1                                multimedia     Hawaii HDMI Audio [Radeon R9 290/290X / 390/390X]
/0/100/7.1                                    bridge         Starship/Matisse Internal PCIe GPP Bridge 0 to bus[E:B]
/0/100/7.1/0                                  generic        Starship/Matisse PCIe Dummy Function
/0/100/8.1                                    bridge         Starship/Matisse Internal PCIe GPP Bridge 0 to bus[E:B]
/0/100/8.1/0                                  generic        Starship/Matisse Reserved SPP
/0/100/8.1/0.1                                generic        Starship/Matisse Cryptographic Coprocessor PSPCPP
/0/100/8.1/0.3                                bus            Matisse USB 3.0 Host Controller
/0/100/8.1/0.3/0              usb3            bus            xHCI Host Controller
/0/100/8.1/0.3/0/3            input2          input          USB Laser Game Mouse
/0/100/8.1/0.3/1              usb4            bus            xHCI Host Controller
/0/100/8.1/0.4                card1           multimedia     Starship/Matisse HD Audio Controller
/0/100/8.1/0.4/0              input13         input          HD-Audio Generic Front Mic
/0/100/8.1/0.4/1              input14         input          HD-Audio Generic Rear Mic
/0/100/8.1/0.4/2              input15         input          HD-Audio Generic Line
/0/100/8.1/0.4/3              input16         input          HD-Audio Generic Line Out Front
/0/100/8.1/0.4/4              input17         input          HD-Audio Generic Line Out Surround
/0/100/8.1/0.4/5              input18         input          HD-Audio Generic Line Out CLFE
/0/100/8.1/0.4/6              input19         input          HD-Audio Generic Front Headphone
/0/100/8.2                                    bridge         Starship/Matisse Internal PCIe GPP Bridge 0 to bus[E:B]
/0/100/8.2/0                                  storage        FCH SATA Controller [AHCI mode]
/0/100/8.3                                    bridge         Starship/Matisse Internal PCIe GPP Bridge 0 to bus[E:B]
/0/100/8.3/0                                  storage        FCH SATA Controller [AHCI mode]
/0/100/14                                     bus            FCH SMBus Controller
/0/100/14.3                                   bridge         FCH LPC Bridge
/0/100/14.3/0                                 system         PnP device PNP0c01
/0/100/14.3/1                                 system         PnP device PNP0c02
/0/100/14.3/2                                 system         PnP device PNP0b00
/0/100/14.3/3                                 system         PnP device PNP0c02
/0/100/14.3/4                                 system         PnP device PNP0c02
/0/101                                        bridge         Starship/Matisse PCIe Dummy Host Bridge
/0/102                                        bridge         Starship/Matisse PCIe Dummy Host Bridge
/0/103                                        bridge         Starship/Matisse PCIe Dummy Host Bridge
/0/104                                        bridge         Starship/Matisse PCIe Dummy Host Bridge
/0/105                                        bridge         Starship/Matisse PCIe Dummy Host Bridge
/0/106                                        bridge         Starship/Matisse PCIe Dummy Host Bridge
/0/107                                        bridge         Starship/Matisse PCIe Dummy Host Bridge
/0/108                                        bridge         Matisse/Vermeer Data Fabric: Device 18h; Function 0
/0/109                                        bridge         Matisse/Vermeer Data Fabric: Device 18h; Function 1
/0/10a                                        bridge         Matisse/Vermeer Data Fabric: Device 18h; Function 2
/0/10b                                        bridge         Matisse/Vermeer Data Fabric: Device 18h; Function 3
/0/10c                                        bridge         Matisse/Vermeer Data Fabric: Device 18h; Function 4
/0/10d                                        bridge         Matisse/Vermeer Data Fabric: Device 18h; Function 5
/0/10e                                        bridge         Matisse/Vermeer Data Fabric: Device 18h; Function 6
/0/10f                                        bridge         Matisse/Vermeer Data Fabric: Device 18h; Function 7
/1                            input0          input          Power Button
/2                            input1          input          Power Button

```


/proc/acpi/wakeup

```

Device    S-state      Status   Sysfs node
GPP0      S4    *enabled   pci:0000:00:01.1
GPP1      S4    *disabled
GPP3      S4    *disabled
GPP4      S4    *disabled
GPP5      S4    *disabled
GPP6      S4    *disabled
GPP7      S4    *disabled
GPP8      S4    *enabled   pci:0000:00:03.1
GPP9      S4    *enabled   pci:0000:00:03.2
GPPA      S4    *disabled
GPPB      S4    *disabled
GPPC      S4    *disabled
GPPD      S4    *disabled
GPPE      S4    *disabled
GPPF      S4    *disabled
GP10      S4    *disabled
GP11      S4    *disabled
GP12      S4    *enabled   pci:0000:00:07.1
GP13      S4    *enabled   pci:0000:00:08.1
XHC0      S4    *enabled   pci:0000:13:00.3
GP30      S4    *enabled   pci:0000:00:08.2
GP31      S4    *enabled   pci:0000:00:08.3
PS2K      S3    *disabled
PS2M      S3    *disabled
GPP2      S4    *enabled   pci:0000:00:01.3
PTXH      S4    *enabled   pci:0000:02:00.0

```

GPP0 was the nvme device in my case. I removed all the boot parameters I had set, update grub, restarted then attempted then following the guides, I used "echo GPP0 > /proc/acpi/wakeup to disable the nvme temporarily. I then performed numerous suspend and hibernate cycles without any encountering any hangs.

I understand that a script is necessary to make this change permanent which I found via [https://unix.stackexchange.com/questions/417956/make-changes-to-proc-acpi-wakeup-permanent](https://unix.stackexchange.com/questions/417956/make-changes-to-proc-acpi-wakeup-permanent). I have not done this yet and just kept "ignore_loglevel no_console_suspend initcall_debug" paramteters active instead. I prefer this, as I can see at which point the suspend, hibernate and resume has reached for those instances were it takes longer than normal which is much better than staring at a blank screen.

Hopefully this can provide some assistance for those with similar suspend issues.

---

