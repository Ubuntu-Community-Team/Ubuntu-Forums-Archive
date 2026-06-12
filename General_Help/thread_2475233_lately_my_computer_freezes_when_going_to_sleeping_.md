---
title: "lately my computer freezes when going to sleeping mode"
date: 2022-05-20
forum: General Help
---

### Post by ronjjjg8885 on 2022-05-20
when i return i see the screen frozen and i need to shut down and turn on again.

it doesn't happen all the time.

---

### Post by ronjjjg8885 on 2022-05-20
anyone knows what to do? it's awful
do you want to see a list of my hardware?

---

### Post by #&amp;thj^% on 2022-05-20
> **ronjjjg8885 said:**
> 
do you want to see a list of my hardware?
That would be a good start
```
inxi -FM
```
EDIT: Please use[ Code Tags]("https://ubuntuforums.org/misc.php?do=bbcode#code") when pasting back
Also try directly running "**systemctl suspend**" to rule out any interference from the screenlocker.

---

### Post by ronjjjg8885 on 2022-05-22
here is the output
```
inxi -FM
System:
  Host: win Kernel: 5.15.0-30-generic x86_64 bits: 64 Desktop: GNOME 42.0
    Distro: Ubuntu 22.04 LTS (Jammy Jellyfish)
Machine:
  Type: Desktop System: Gigabyte product: H110M-S2H v: N/A
    serial: <superuser required>
  Mobo: Gigabyte model: H110M-S2H-CF v: x.x serial: <superuser required>
    UEFI: American Megatrends v: F25 date: 04/11/2018
CPU:
  Info: dual core model: Intel Core i3-6100 bits: 64 type: MT MCP cache:
    L2: 512 KiB
  Speed (MHz): avg: 800 min/max: 800/3700 cores: 1: 800 2: 800 3: 800
    4: 800
Graphics:
  Device-1: Intel HD Graphics 530 driver: i915 v: kernel
  Display: wayland server: X.Org v: 1.22.1.1 with: Xwayland v: 22.1.1
    compositor: gnome-shell driver: X: loaded: modesetting unloaded: fbdev,vesa
    gpu: i915 resolution: 1920x1080~60Hz
  OpenGL: renderer: Mesa Intel HD Graphics 530 (SKL GT2) v: 4.6 Mesa 22.0.1
Audio:
  Device-1: Intel 100 Series/C230 Series Family HD Audio
    driver: snd_hda_intel
  Device-2: C-Media CM108 Audio Controller type: USB
    driver: hid-generic,snd-usb-audio,usbhid
  Sound Server-1: ALSA v: k5.15.0-30-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    driver: r8169
  IF: enp1s0 state: up speed: 1000 Mbps duplex: full mac: 1c:1b:0d:06:ae:eb
Drives:
  Local Storage: total: 238.47 GiB used: 21.14 GiB (8.9%)
  ID-1: /dev/sda vendor: SanDisk model: SD8SBAT256G1122 size: 238.47 GiB
Partition:
  ID-1: / size: 230.57 GiB used: 20.66 GiB (9.0%) fs: ext4 dev: /dev/dm-1
  ID-2: /boot size: 1.61 GiB used: 251.1 MiB (15.3%) fs: ext4
    dev: /dev/sda2
  ID-3: /boot/efi size: 511 MiB used: 5.2 MiB (1.0%) fs: vfat
    dev: /dev/sda1
Swap:
  ID-1: swap-1 type: partition size: 976 MiB used: 218.3 MiB (22.4%)
    dev: /dev/dm-2
Sensors:
  System Temperatures: cpu: 29.8 C mobo: 27.8 C
  Fan Speeds (RPM): N/A
Info:
  Processes: 260 Uptime: 2d 18m Memory: 7.65 GiB used: 5.95 GiB (77.7%)
  Shell: Bash inxi: 3.3.13


```

let me also try the other thing you asked and return with the results..
tnx

---

### Post by ronjjjg8885 on 2022-05-22
i ran
```
systemctl suspend
```
and it woke ok afterwards

---

### Post by #&amp;thj^% on 2022-05-22
> **ronjjjg8885 said:**
> i ran
```
systemctl suspend
```
and it woke ok afterwards

You may want to create keyboard short cut to use for that then.
See if that's a bit more dependable on wake for a period of time.

---

### Post by ronjjjg8885 on 2022-05-23
i'm not sure that i fully understand..

anyhow. maybe i will leave my computer on all the time until there is some update that fixes that,, not?

---

### Post by #&amp;thj^% on 2022-05-23
On gnome, I assume your using Gnome, Go to settings, Keyboard, down at the bottom,
Keyboard Shortcuts, there you can add the command "**systemctl suspen**d" and assign a key combination. (Screenshots to help)
Take care not to change any defaults already preset.
In the example I've shown you I used just for this purpose The <Insert> key to trigger the suspend.
Or just leave it on as you suggested.
I just don't see a fix for this landing anytime soon. :(

---

### Post by ronjjjg8885 on 2022-05-24
i did it
thanks
i hope it will solve the problem

---

### Post by #&amp;thj^% on 2022-05-24
It's a workaround for the time being.
keep us posted.

---

### Post by ronjjjg8885 on 2022-06-03
for now things are ok with this shortcut for sleep.. thanks

---

### Post by ronjjjg8885 on 2022-06-18
seems like the sleep button that comes in the keyboard is now working ok too.
no freezes lately
perhaps it's because of the ununtu updates fixes?

---

