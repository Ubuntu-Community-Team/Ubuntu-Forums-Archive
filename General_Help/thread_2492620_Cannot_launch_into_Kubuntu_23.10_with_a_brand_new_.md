---
title: "Cannot launch into Kubuntu 23.10 with a brand new install"
date: 2023-11-17
forum: General Help
---

### Post by thespoonman on 2023-11-17
I've been having an issue with my Kubuntu install after I replaced my old one that wound up broken. It hangs whenever I try to launch Ubuntu normally through GRUB. I can only launch Kubuntu at the moment through safe mode and this is after installing all third-party drivers and updates. If I try to launch it through the default GRUB option, it simply hangs on a black screen that displays this text:

[TABLE="width: 500"]
[TR]
[TD][    4.059403] iwlwifi 0000:00:14.3: WRT: Invalid buffer destination[/TD]
[/TR]
[TR]
[TD][    5.415909] Bluetooth: hci0: Malformed MSFT vendor event: 0x02[/TD]
[/TR]
[/TABLE]

EDIT: It turns out that my graphics driver wasn't set properly during the installation. Setting it to the Nouveau driver and back to the tested Nvidia driver in Software Sources fixed the issue for me.

---

### Post by TheFu on 2023-11-17
What hardware? People need details to provide any guesses.
The system-info script is a good way to provide that, as is the boot-info (from boot-repair).

Lacking any details, nobody can guess except to ask if you have read the Kubuntu 23.10 release notes AND the Ubuntu 23.10 release notes?  Some hardware doesn't work well (or at all) for some installs.  Claiming you have installed "all third-party drivers" is unlikely. I don't think I've ever been able to do that in 30 yrs of Linux. Be specific and provide proof, please.

Also, those log entries seem related to wifi stuff. Plug in an ethernet cable, does that help?

---

### Post by thespoonman on 2023-11-17
My motherboard is a MSI PRO Z790-P and my CPU is an Intel i7-13700K. I have my computer hooked up with an Ethernet connection, but my motherboard does have built-in wi-fi and bluetooth. I meant to say that I checked the option to install third-party drivers while installing Kubuntu onto my machine. I was in a rush during the morning, so I didn't have time to proof-read my post. This was the report that I got from system-info: [FONT=monospace][[COLOR=#000000]https://paste.ubuntu.com/p/7ZZzRXHHWv/[/COLOR]]("https://paste.ubuntu.com/p/7ZZzRXHHWv/")
[/FONT]

---

### Post by MAFoElffen on 2023-11-18
```

  *-display UNCLAIMED
       description: VGA compatible controller
       product: AD103 [GeForce RTX 4080]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller cap_list
       configuration: latency=0
       resources: 
           iomemory:600-5ff 
           iomemory:640-63f 
           memory:81000000-81ffffff 
           memory:6000000000-63ffffffff 
           memory:6400000000-6401ffffff 
           ioport:4000(size=128) 
           memory:82000000-8207ffff
  *-display UNCLAIMED
       description: Display controller
       product: Raptor Lake-S GT1 [UHD Graphics 770]
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm bus_master cap_list
       configuration: latency=0
       resources: 
           iomemory:640-63f 
           iomemory:400-3ff 
           memory:6403000000-6403ffffff 
           memory:4000000000-400fffffff 
           ioport:5000(size=64) 
           memory:4010000000-4016ffffff 
           memory:4020000000-40ffffffff

```
```

   --- User Installed Package List:
audacity
brave-browser
calibre
curl
deadbeef-static
discord
flatpak
gnome-disk-utility
gnome-software-plugin-flatpak
google-chrome-stable
keepassxc
libc6:i386
libegl1:i386
libgbm1:i386
libgl1-mesa-dri:i386
libgl1:i386
mainline
mpv
neofetch
pipx
plasma-discover-backend-flatpak
python3-pip
sox
steam-launcher
steam-libs-amd64
steam-libs-i386:i386
transmission-gtk
xterm
zenity

```
Okay... Didn't you say you installed third party drivers??? What, where and how? I see none installed and everything is unclaimed. I need to know what you did, so we know what we need to do to get you going...

I did see this:
```

    |__ Port 14: Dev 8, If 0, Class=Wireless, Driver=btusb, 12M
        ID 8087:0033 Intel Corp. 
    |__ Port 14: Dev 8, If 1, Class=Wireless, Driver=btusb, 12M
        ID 8087:0033 Intel Corp. 

```

---

### Post by thespoonman on 2023-11-18
> **MAFoElffen said:**
> 
Okay... Didn't you say you installed third party drivers??? What, where and how? I see none installed and everything is unclaimed. I need to know what you did, so we know what we need to do to get you going...


That's odd, I just checked in Konsole and it says that I already have [FONT=monospace]kubuntu-restricted-addons installed and I have checkmarked "Proprietary drivers for devices (restricted)" in Software Sources.[/FONT]
```
[FONT=monospace][COLOR=#000000]$ sudo apt install kubuntu-restricted-addons[/COLOR]
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
kubuntu-restricted-addons is already the newest version (29).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/FONT]
```

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=293075&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=293076&stc=1[/IMG]

---

### Post by TheFu on 2023-11-18
```
inxi -Gxxz
```
will show the graphics subsystem information and drivers used.  I never believe GUI tools. Too many layers.

Or 
```
inxi -Fxxz
```
will show all the details, with s/n removed for privacy.

---

### Post by MAFoElffen on 2023-11-18
And 
```

apt list nvidia-* --installed

```

---

### Post by deadflowr on 2023-11-18
Is nomodeset really needed for nvidia drivers to work?

Edit:
I asked because I don't know what settings nvidia wants these days.

---

### Post by thespoonman on 2023-11-18
Here are the results of inxi and the apt list commands:
```
System:
  Kernel: 6.5.0-10-generic arch: x86_64 bits: 64 compiler: N/A
    Desktop: KDE Plasma v: 5.27.8 tk: Qt v: 5.15.10 wm: kwin_x11 dm: SDDM
    Distro: Ubuntu 23.10 (Mantic Minotaur)
Machine:
  Type: Desktop Mobo: Micro-Star model: PRO Z790-P WIFI (MS-7E06) v: 2.0
    serial: <superuser required> UEFI: American Megatrends LLC. v: A.A0
    date: 10/27/2023
CPU:
  Info: 16-core (8-mt/8-st) model: 13th Gen Intel Core i7-13700K bits: 64
    type: MST AMCP arch: Raptor Lake rev: 1 cache: L1: 1.4 MiB L2: 24 MiB
    L3: 30 MiB
  Speed (MHz): avg: 850 high: 1100 min/max: 800/5300:5400:4200 cores:
    1: 1100 2: 800 3: 800 4: 800 5: 800 6: 800 7: 800 8: 800 9: 800 10: 1100
    11: 800 12: 800 13: 800 14: 800 15: 1100 16: 1100 17: 800 18: 800 19: 807
    20: 800 21: 800 22: 800 23: 800 24: 800 bogomips: 164044
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: Intel Raptor Lake-S GT1 [UHD Graphics 770] vendor: Micro-Star MSI
    driver: N/A arch: Gen-13 bus-ID: 00:02.0 chip-ID: 8086:a780
  Device-2: NVIDIA AD103 [GeForce RTX 4080] vendor: ZOTAC driver: N/A
    arch: Lovelace pcie: speed: 16 GT/s lanes: 16 bus-ID: 01:00.0
    chip-ID: 10de:2704
  Device-3: Logitech HD Webcam C525 driver: snd-usb-audio,uvcvideo type: USB
    rev: 2.0 speed: 480 Mb/s lanes: 1 bus-ID: 1-5.1:7 chip-ID: 046d:0826
  Display: x11 server: X.Org v: 1.21.1.7 with: Xwayland v: 23.2.0
    compositor: kwin_x11 driver: X: loaded: nouveau,vesa
    unloaded: fbdev,modesetting dri: swrast gpu: N/A display-ID: :0 screens: 1
  Screen-1: 0 s-res: 2560x1440 s-dpi: 96
  Monitor-1: default res: 2560x1440 size: N/A
  API: OpenGL v: 4.5 Mesa 23.2.1-1ubuntu3 renderer: llvmpipe (LLVM 15.0.7
    256 bits) direct-render: Yes
Audio:
  Device-1: Intel vendor: Micro-Star MSI driver: snd_hda_intel v: kernel
    bus-ID: 00:1f.3 chip-ID: 8086:7a50
  Device-2: NVIDIA vendor: ZOTAC driver: snd_hda_intel v: kernel pcie:
    speed: 16 GT/s lanes: 16 bus-ID: 01:00.1 chip-ID: 10de:22bb
  Device-3: Thesycon System & Consulting GmbH D30 Pro driver: snd-usb-audio
    type: USB rev: 2.0 speed: 480 Mb/s lanes: 1 bus-ID: 1-1:2 chip-ID: 152a:8750
  Device-4: Logitech HD Webcam C525 driver: snd-usb-audio,uvcvideo type: USB
    rev: 2.0 speed: 480 Mb/s lanes: 1 bus-ID: 1-5.1:7 chip-ID: 046d:0826
  Device-5: Focusrite-Novation Focusrite Scarlett 2i2 2nd Gen
    driver: snd-usb-audio type: USB rev: 2.0 speed: 480 Mb/s lanes: 1
    bus-ID: 1-5.4:10 chip-ID: 1235:8202
  API: ALSA v: k6.5.0-10-generic status: kernel-api
  Server-1: PipeWire v: 0.3.79 status: active with: 1: pipewire-pulse
    status: active 2: wireplumber status: active
Network:
  Device-1: Intel driver: iwlwifi v: kernel port: N/A bus-ID: 00:14.3
    chip-ID: 8086:7a70
  IF: wlo1 state: down mac: <filter>
  Device-2: Intel Ethernet I225-V vendor: Micro-Star MSI driver: igc
    v: kernel pcie: speed: 5 GT/s lanes: 1 port: N/A bus-ID: 06:00.0
    chip-ID: 8086:15f3
  IF: enp6s0 state: up speed: 100 Mbps duplex: full mac: <filter>
Bluetooth:
  Device-1: Intel driver: btusb v: 0.8 type: USB rev: 2.0 speed: 12 Mb/s
    lanes: 1 bus-ID: 1-14:8 chip-ID: 8087:0033
  Report: hciconfig ID: hci0 rfk-id: 0 state: up address: <filter> bt-v: 5.3
    lmp-v: 12 sub-v: 32fe
Drives:
  Local Storage: total: 20.01 TiB used: 9.73 TiB (48.6%)
  ID-1: /dev/nvme0n1 vendor: Crucial model: CT2000P5PSSD8 size: 1.82 TiB
    speed: 63.2 Gb/s lanes: 4 serial: <filter> temp: 44.9 C
  ID-2: /dev/nvme1n1 vendor: Crucial model: CT2000P5PSSD8 size: 1.82 TiB
    speed: 63.2 Gb/s lanes: 4 serial: <filter> temp: 42.9 C
  ID-3: /dev/sda vendor: Western Digital model: WD6003FZBX-00K5WB0
    size: 5.46 TiB speed: 6.0 Gb/s serial: <filter>
  ID-4: /dev/sdb vendor: Crucial model: CT4000MX500SSD1 size: 3.64 TiB
    speed: 6.0 Gb/s serial: <filter>
  ID-5: /dev/sdc vendor: Western Digital model: WD8002FZWX-00BKUA0
    size: 7.28 TiB speed: 6.0 Gb/s serial: <filter>
Partition:
  ID-1: / size: 45.53 GiB used: 16.6 GiB (36.4%) fs: ext4 dev: /dev/nvme0n1p6
  ID-2: /boot/efi size: 96 MiB used: 35.7 MiB (37.2%) fs: vfat
    dev: /dev/nvme0n1p1
  ID-3: /home size: 906.99 GiB used: 17.38 GiB (1.9%) fs: ext4
    dev: /dev/nvme0n1p7
Swap:
  ID-1: swap-1 type: partition size: 7.45 GiB used: 0 KiB (0.0%) priority: -2
    dev: /dev/nvme0n1p5
Sensors:
  System Temperatures: cpu: 41.0 C mobo: N/A
  Fan Speeds (rpm): N/A
Info:
  Processes: 458 Uptime: 5m Memory: total: 32 GiB note: est.
  available: 31.11 GiB used: 2.93 GiB (9.4%) Init: systemd v: 253
  target: graphical (5) default: graphical Compilers: gcc: 13.2.0 alt: 12/13
  Packages: 2536 pm: dpkg pkgs: 2517 pm: flatpak pkgs: 8 pm: snap pkgs: 11
  Shell: Bash v: 5.2.15 running-in: konsole inxi: 3.3.29

```


```
nvidia-compute-utils-535/mantic-updates,mantic-security,now 535.129.03-0ubuntu0.23.10.1 amd64 [installed,automatic]
nvidia-dkms-535/mantic-updates,mantic-security,now 535.129.03-0ubuntu0.23.10.1 amd64 [installed,automatic]
nvidia-driver-535/mantic-updates,mantic-security,now 535.129.03-0ubuntu0.23.10.1 amd64 [installed]
nvidia-firmware-535-535.129.03/mantic-updates,mantic-security,now 535.129.03-0ubuntu0.23.10.1 amd64 [installed,automatic]
nvidia-kernel-common-535/mantic-updates,mantic-security,now 535.129.03-0ubuntu0.23.10.1 amd64 [installed,automatic]
nvidia-kernel-source-535/mantic-updates,mantic-security,now 535.129.03-0ubuntu0.23.10.1 amd64 [installed,automatic]
nvidia-prime/mantic,mantic,now 0.8.17.2 all [installed]
nvidia-settings/mantic,now 510.47.03-0ubuntu1 amd64 [installed,automatic]
nvidia-utils-535/mantic-updates,mantic-security,now 535.129.03-0ubuntu0.23.10.1 amd64 [installed,automatic]

```

---

### Post by TheFu on 2023-11-18
```
Graphics:
  Device-1: Intel Raptor Lake-S GT1 [UHD Graphics 770] vendor: Micro-Star MSI
    [COLOR="#FF0000"]driver: N/A[/COLOR] arch: Gen-13 bus-ID: 00:02.0 chip-ID: 8086:a780
  Device-2: NVIDIA AD103 [GeForce RTX 4080] vendor: ZOTAC [COLOR="#FF0000"]driver: N/A
[/COLOR]    arch: Lovelace pcie: speed: 16 GT/s lanes: 16 bus-ID: 01:00.0
    chip-ID: 10de:2704
  Device-3: Logitech HD Webcam C525 driver: snd-usb-audio,uvcvideo type: USB
    rev: 2.0 speed: 480 Mb/s lanes: 1 bus-ID: 1-5.1:7 chip-ID: 046d:0826
  Display: x11 server: X.Org v: 1.21.1.7 with: [COLOR="#FF0000"]Xwayland[/COLOR] v: 23.2.0
    compositor: kwin_x11 driver: X: [COLOR="#FF0000"]loaded: nouveau,vesa[/COLOR]
    unloaded: fbdev,modesetting dri: swrast gpu: N/A display-ID: :0 screens: 1
```

So, this tells me that your system isn't using the proprietary nvidia driver.  You are using the F/LOSS nouveau driver.  I'm guessing that the Intel iGPU is getting in the way. I have no idea how to pick between the Intel iGPU and the nvidia GPU. Sorry.
I think you are also using Wayland which is known to be a problem for nvidia GPUs, so you should look up how to ensure Wayland + XWayland aren't used.

I could be misreading the output, but for reference, here's mine for a Ryzen iGPU on a 20.04 system:
```
$ inxi -Gxxz
Graphics:  Device-1: AMD vendor: ASUSTeK driver: amdgpu v: kernel bus ID: 09:00.0 
           chip ID: 1002:1638 
           Display: x11 server: X.Org 1.20.13 [COLOR="#00FF00"]driver: amdgpu[/COLOR],ati unloaded: fbdev,modesetting,vesa 
           resolution: 1920x1200~60Hz 
           OpenGL: renderer: AMD RENOIR (DRM 3.42.0 5.15.0-88-generic LLVM 12.0.0) 
           v: 4.6 Mesa 21.2.6 direct render: Yes 

```

---

### Post by thespoonman on 2023-11-18
Thanks for posting that! I wound up selecting the Nouveau driver in the Additional Drivers tab, then switching back to the recommended NVIDIA driver, and then I reset my system. After I did all of that, I was able to launch my system normally again! I guess that the graphics driver wasn't set up properly during the install process.

```
$ inxi -GxxzGraphics:
  Device-1: Intel Raptor Lake-S GT1 [UHD Graphics 770] vendor: Micro-Star MSI
    driver: i915 v: kernel arch: Gen-13 ports: active: none empty: DP-1, DP-2,
    HDMI-A-1, HDMI-A-2, HDMI-A-3, HDMI-A-4 bus-ID: 00:02.0 chip-ID: 8086:a780
  Device-2: NVIDIA AD103 [GeForce RTX 4080] vendor: ZOTAC driver: nvidia
    v: 535.129.03 arch: Lovelace pcie: speed: 2.5 GT/s lanes: 16 ports:
    active: none off: DP-3 empty: DP-4,DP-5,HDMI-A-5 bus-ID: 01:00.0
    chip-ID: 10de:2704
  Device-3: Logitech HD Webcam C525 driver: snd-usb-audio,uvcvideo type: USB
    rev: 2.0 speed: 480 Mb/s lanes: 1 bus-ID: 1-5.1:7 chip-ID: 046d:0826
  Display: x11 server: X.Org v: 1.21.1.7 with: Xwayland v: 23.2.0
    compositor: kwin_x11 driver: X: loaded: modesetting,nvidia
    unloaded: fbdev,nouveau,vesa dri: iris gpu: nvidia,nvidia-nvswitch
    display-ID: :0 screens: 1
  Screen-1: 0 s-res: 2560x1440 s-dpi: 108
  Monitor-1: DP-3 mapped: DP-0 note: disabled model: Dell G2724D
    res: 2560x1440 dpi: 109 diag: 684mm (26.9")
  API: OpenGL v: 4.6.0 NVIDIA 535.129.03 renderer: NVIDIA GeForce RTX
    4080/PCIe/SSE2 direct-render: Yes

```

---

### Post by TheFu on 2023-11-18
```
Display: x11 server: X.Org v: 1.21.1.7 with: Xwayland v: 23.2.0
    compositor: kwin_x11 driver: X: loaded: modesetting,nvidia
```

I still think you need to 
a) switch from Wayland to Xorg as the display driver
b) use the nomemset kernel boot parameter so nvidia's driver is first in the list.


There shouldn't be any mention of Xwayland in that output.

---

### Post by thespoonman on 2023-11-19
I just tried doing both of those things you mentioned, but the output of inxi -Gxxz was the exact same. The odd thing is that I always selected "Desktop Session: Plasma (X11)" from the login screen. The output stayed the same when I switched to Wayland and then back to X11 before running the command again. Also, if I try checking with echo $XDG_SESSION_TYPE, it returns x11.

---

### Post by TheFu on 2023-11-19
I don't have 23.10 on real hardware nor do I use KDE. Perhaps things have changed in newer releases. 

Hopefully, someone else can help.

---

### Post by MAFoElffen on 2023-11-19
For Kubuntu 23.10, 
```

apt list plasma-workspace-wayland --installed

```
If that is not there, install it...

Then do this to fix a Scaling rendering bug with KDE Plasma, for 23.10:
```

sudoedit /usr/share/xdg-desktop-portal/kde-portals.conf

```
Add this line at the end
```

org.freedesktop.impl.portal.Settings=kde;gtk;

```
Reboot to pick up that change...

At the SDDM Graphical login panel... Look at the bottom left of the screen, where it says "Desktop Session". Choose "Plasma X11". Enter your password and login.

---

### Post by Yellow Pasque on 2023-11-19
> **TheFu said:**
> There shouldn't be any mention of Xwayland in that output.

No, that's just how inxi works nowadays. If the xwayland package is installed, it reports the version, even if Wayland isn't being used. It doesn't make sense to me either..

> use the nomemset kernel boot parameter so nvidia's driver is first in the list.

If you're referring to 'nomodeset', that is not a good idea. That will disable any accelerated graphics kernel modules/drivers from loading. It is okay for the 'modesetting' (aka GLAMOR) X driver to be present/loaded on a system with an Intel GPU. That is what Intel GPU's use for 2D acceleration.
If OP is really worried about the Intel GPU interfering and wants to disable it, that can be done in the BIOS: [https://www.technewstoday.com/msi-integrated-graphics/](https://www.technewstoday.com/msi-integrated-graphics/)

EDIT: Actually, I'm confused about whether the OP is still having any issues. "I was able to launch my system normally again!" sounds like problem solved to me.

---

### Post by thespoonman on 2023-11-19
Sorry if I wasn't clear about it before, but my issue was resolved after switching between the Nouveau and Nvidia drivers in safe mode. Should I also ignore editing kde-portals.conf if inxi always reports Wayland in it's output?

---

### Post by MAFoElffen on 2023-11-20
```

printenv | grep 'XDG_SESSION_TYPE'

```
That will tell you whether Wayland or X11 is running. At this point you could mark the thread as "Solved". It probably doesn't matter which graphics engine is running, as now you are doing well. You know how to see what it running, and how to change it now, if you do need to.

I would still do the edit to /usr/share/xdg-desktop-portal/kde-portals.conf... That corrects a bug that affected the font scaling, that isn't backported to Kubuntu 23.10 yet. It will hit the updates eventually.

---

### Post by Yellow Pasque on 2023-11-20
We already know OP is running X.
```
Display: x11 server: X.Org v: 1.21.1.7 with: Xwayland v: 23.2.0
    compositor: kwin_x11
```

---

### Post by TheFu on 2023-11-20
> **MAFoElffen said:**
> ```

printevn | grep 'XDG_SESSION_TYPE'

```

That's just painful and printevn doesn't exist. Shorter is:

```
echo $XDG_SESSION_TYPE
```

So, 
```
$ echo $XDG_SESSION_TYPE
tty

```

```
$ echo $XDG_SESSION_TYPE
x11
```
is what I see.

---

### Post by Yellow Pasque on 2023-11-20
It was a typo. It should have been print**env**.

---

### Post by TheFu on 2023-11-20
> **Yellow Pasque said:**
> It was a typo. It should have been print**env**.

I've always used 'env' instead.  I'm lazy. Don't want to waste extra characters. ;)    Feels a little like the MS-PowerShell command names which are really-long-to-be-descriptive-but-unnecessary-if-you-know-the-shorter-version-already.

In complex programs, I prefer long-descriptive-names.  Not so much for 1-line commands.

---

### Post by Yellow Pasque on 2023-11-20
We are getting way off topic here. The problem is solved. And the user is running X, no matter how many similar commands s/he runs to tell us that.

---

