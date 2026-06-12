---
title: "Directories suddenly turned into broken links"
date: 2024-04-16
forum: General Help
---

### Post by accessd on 2024-04-16
A number of directories in my home directory — including Downloads, Desktop, Videos, Templates and Public — suddenly started showing up as broken links. Everything was working fine when I started my work day, but I soon started noticing that I couldn't access my Downloads folder. I didn't make any changes to the system in that time, but the package manager did perform an upgrade. 

Double-clicking on any of the directories in Nautilus gives the following error: "The link 'Videos' is broken. Move it to Trash? This link cannot be used because its target '/home/jesse/Videos' doesn't exist." ls -al displays them as follows:

```
lrwxrwxrwx   1 jesse            jesse               18 Apr 16 15:53  Videos -> /home/jesse/Videos
```

I tried removing the broken link to the Downloads directory and recreating it. I was able to download an image from Firefox and edit it in GIMP, however, when saving it, I was told that its metadata could not be saved. I'm running Ubuntu 22.04.4 LTS, using a solid-state drive. None of the directories in question were symlinks. Does anyone have any idea what might be going on? Is this a sign of more issues to come?

TIA

---

### Post by ajgreeny on 2024-04-17
Very strange!
What hardware are you using?
Please run command **inxi -Fzx** as a start, and post the output using code tags which may give us some clues about where to begin looking for answers.

---

### Post by accessd on 2024-04-17
Thanks for your help. The output is as follows:

```
System:
  Kernel: 5.15.0-102-generic x86_64 bits: 64 compiler: gcc v: 11.4.0
    Desktop: GNOME 42.9 Distro: Ubuntu 22.04.4 LTS (Jammy Jellyfish)
Machine:
  Type: Desktop System: ASUS product: All Series v: N/A
    serial: <superuser required>
  Mobo: ASUSTeK model: H97I-PLUS v: Rev X.0x serial: <superuser required>
    UEFI: American Megatrends v: 3602 date: 04/08/2018
Battery:
  Device-1: apple_mfi_fastcharge model: N/A charge: N/A status: N/A
CPU:
  Info: quad core model: Intel Core i7-4790K bits: 64 type: MT MCP
    arch: Haswell rev: 3 cache: L1: 256 KiB L2: 1024 KiB L3: 8 MiB
  Speed (MHz): avg: 3293 high: 4058 min/max: 800/4400 cores: 1: 2295
    2: 2295 3: 2296 4: 3422 5: 3995 6: 3993 7: 3993 8: 4058 bogomips: 63854
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3
Graphics:
  Device-1: AMD Baffin [Radeon RX 550 640SP / 560/560X]
    vendor: Micro-Star MSI driver: amdgpu v: kernel bus-ID: 01:00.0
  Device-2: Logitech HD Webcam C525 type: USB
    driver: snd-usb-audio,uvcvideo bus-ID: 3-13:3
  Display: wayland server: X.Org v: 1.22.1.1 with: Xwayland v: 22.1.1
    compositor: gnome-shell driver: X: loaded: amdgpu,ati
    unloaded: fbdev,modesetting,radeon,vesa gpu: amdgpu
    resolution: 2560x1440~144Hz
  OpenGL: renderer: AMD Radeon RX 560 Series (polaris11 LLVM 15.0.7 DRM
    3.42 5.15.0-102-generic)
    v: 4.6 Mesa 23.2.1-1ubuntu3.1~22.04.2 direct render: Yes
Audio:
  Device-1: Intel 9 Series Family HD Audio vendor: ASUSTeK
    driver: snd_hda_intel v: kernel bus-ID: 00:1b.0
  Device-2: AMD Baffin HDMI/DP Audio [Radeon RX 550 640SP / 560/560X]
    vendor: Micro-Star MSI driver: snd_hda_intel v: kernel bus-ID: 01:00.1
  Device-3: Logitech HD Webcam C525 type: USB
    driver: snd-usb-audio,uvcvideo bus-ID: 3-13:3
  Sound Server-1: ALSA v: k5.15.0-102-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Intel Ethernet I218-V vendor: ASUSTeK driver: e1000e v: kernel
    port: f040 bus-ID: 00:19.0
  IF: eno1 state: up speed: 1000 Mbps duplex: full mac: <filter>
  IF-ID-1: enxb235b5ecf1ab state: up speed: N/A duplex: N/A mac: <filter>
Drives:
  Local Storage: total: 1.36 TiB used: 253.97 GiB (18.2%)
  ID-1: /dev/sda vendor: Crucial model: CT500BX100SSD1 size: 465.76 GiB
  ID-2: /dev/sdb vendor: Crucial model: CT1000MX500SSD1 size: 931.51 GiB
Partition:
  ID-1: / size: 457.28 GiB used: 41.95 GiB (9.2%) fs: ext4 dev: /dev/sda2
  ID-2: /boot/efi size: 96.5 MiB used: 6 MiB (6.3%) fs: vfat dev: /dev/sda1
  ID-3: /home size: 915.82 GiB used: 212.02 GiB (23.2%) fs: ext4
    dev: /dev/sdb
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 0 KiB (0.0%) file: /swapfile
Sensors:
  System Temperatures: cpu: 29.8 C mobo: 27.8 C gpu: amdgpu temp: 36.0 C
  Fan Speeds (RPM): N/A gpu: amdgpu fan: 1277
Info:
  Processes: 309 Uptime: 17h 3m Memory: 15.56 GiB used: 2.55 GiB (16.4%)
  Init: systemd runlevel: 5 Compilers: gcc: 11.4.0 Packages: 3424 Shell: Bash
  v: 5.1.16 inxi: 3.3.13
```

---

### Post by ajgreeny on 2024-04-17
Hmm?

That didn't help much so let's try something else.

We need to know where those folders are as they would not seem to be where they should be in **home/jesse/Videos** etc, etc.
Let's  start with commands **locate Videos** which will probably show a huge list and **find -iname Vidoes** which might be more useful.

---

### Post by accessd on 2024-04-17
**locate Videos** found /home/jesse/Videos. **find -iname Videos** also found ./Videos. However, when I try to cd into the directory, I get the following error:

```
bash: cd: /home/jesse/Videos: Too many levels of symbolic links
```

---

### Post by dragonfly41 on 2024-04-17
That gives a clue ...

[https://www.reddit.com/r/linuxquestions/comments/e6n110/how_do_i_resolve_a_too_many_levels_of_symbolic/](https://www.reddit.com/r/linuxquestions/comments/e6n110/how_do_i_resolve_a_too_many_levels_of_symbolic/)

"[COLOR=#131313][FONT=-apple-system]Unless you've done something stupid with symbolic links, this is probably a sign of hard drive failure."[/FONT][/COLOR]

---

### Post by accessd on 2024-04-17
That's what I was worried about. Thank you very much for your help with this.

---

