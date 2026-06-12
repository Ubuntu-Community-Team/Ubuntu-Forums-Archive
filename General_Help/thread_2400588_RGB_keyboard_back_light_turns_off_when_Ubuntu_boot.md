---
title: "RGB keyboard back light turns off when Ubuntu boots (MR X6Ti)"
date: 2018-09-07
forum: General Help
---

### Post by lksjfnvljnfdv on 2018-09-07
Please can someone help me i have been struggling to fix this for months..


[COLOR=#242729][FONT=Arial]I have a laptop custom called a TRACER II built by a company called CyberPowerPC. As I understand it they are just a rebranded version of MR XTi Laptop by [MechRevo]("http://www.mechrevo.com/en/html/shenhaitaitan/x6ti_se/2016/0812/113.html").[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]My laptop is dual-boot. In Windows there is an application to control the RGB keyboard and all is fine. As soon as you boot into the Linux side, the back light turns off and I am unable to get it to turn back on.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Tried all the xset led etc. None of them work. The keyboard shortcut doesn't work.


[/FONT][/COLOR]```

$ sudo hwinfo --short
cpu: 


                       Intel(R) Core(TM) i7-7700HQ CPU @ 2.80GHz, 3404 MHz
                       Intel(R) Core(TM) i7-7700HQ CPU @ 2.80GHz, 3409 MHz
                       Intel(R) Core(TM) i7-7700HQ CPU @ 2.80GHz, 3608 MHz
                       Intel(R) Core(TM) i7-7700HQ CPU @ 2.80GHz, 3400 MHz
                       Intel(R) Core(TM) i7-7700HQ CPU @ 2.80GHz, 3404 MHz
                       Intel(R) Core(TM) i7-7700HQ CPU @ 2.80GHz, 3412 MHz
                       Intel(R) Core(TM) i7-7700HQ CPU @ 2.80GHz, 3650 MHz
                       Intel(R) Core(TM) i7-7700HQ CPU @ 2.80GHz, 3471 MHz


keyboard:
  /dev/input/event7    Trust 2.4G Speed Mouse
                       Integrated Technology Express ITE Device(8291)
  /dev/input/event4    AT Translated Set 2 keyboard


mouse:
  /dev/input/mice      Trust 2.4G Speed Mouse
  /dev/input/mice      SynPS/2 Synaptics TouchPad


monitor:
                       LM156LF1L02


graphics card:
                       Intel VGA compatible controller
                       nVidia GP107M [GeForce GTX 1050 Ti Mobile]


sound:
                       Intel Audio device


storage:
                       Samsung Electronics NVMe SSD Controller SM961/PM961
                       Intel Sunrise Point-H SATA Controller [AHCI mode]


network:
  wlp3s0               Intel WLAN controller
  enp2s0               Realtek RTL8111/8168/8411 PCI Express Gigabit 
Ethernet Controller
network interface:
  lo                   Loopback network interface
  vmnet1               Ethernet network interface
  wlp3s0               Ethernet network interface
  vmnet8               Ethernet network interface
  enp2s0               Ethernet network interface


disk:
  /dev/sda             M4-CT128M4SSD2
  /dev/nvme0n1         Samsung Electronics NVMe SSD Controller SM961/PM961


partition:
  /dev/sda1            Partition
  /dev/sda2            Partition
  /dev/nvme0n1p1       Partition
  /dev/nvme0n1p2       Partition
  /dev/nvme0n1p3       Partition
  /dev/nvme0n1p4       Partition
  /dev/nvme0n1p5       Partition


usb controller:
                       Intel Sunrise Point-H USB 3.0 xHCI Controller


bios:
                       BIOS


bridge:
                       Intel Host bridge
                       Intel Sunrise Point-H PCI Express Root Port #13
                       Intel Sunrise Point-H PCI Express Root Port #5
                       Intel Sunrise Point-H PCI Express Root Port #4
                       Intel Sunrise Point-H LPC Controller
                       Intel Skylake PCIe Controller (x16)


hub:
                       Linux Foundation 2.0 root hub
                       Linux Foundation 3.0 root hub


memory:
                       Main Memory


bluetooth:
                       Intel Bluetooth Device


unknown:
                       FPU
                       DMA controller
                       PIC
                       Keyboard controller
                       PS/2 Controller
                       Intel Sunrise Point-H Thermal subsystem
                       Intel Sunrise Point-H SMBus
                       Intel Sunrise Point-H PMC
                       Intel Skylake Gaussian Mixture Model
                       Intel Sunrise Point-H CSME HECI #1
                       Acer HD Webcam
                       Integrated Technology Express ITE Device(8291)


56: PS/2 00.0: 10800 Keyboard
  [Created at input.226]
  Unique ID: c3zD.+49ps10DtUF
  Hardware Class: keyboard
  Model: "AT Translated Set 2 keyboard"
  Vendor: 0x0001 
  Device: 0x0001 "AT Translated Set 2 keyboard"
  Compatible to: int 0x0211 0x0001
  Device File: /dev/input/event4
  Device Files: /dev/input/event4, /dev/input/by-path/platform-i8042-serio-0-event-kbd
  Device Number: char 13:68
  Driver Info #0:
    XkbRules: xfree86
    XkbModel: pc104
  Config Status: cfg=new, avail=yes, need=no, active=unknown


[COLOR=#242729][FONT=Arial]
[/FONT][/COLOR]
```[COLOR=#242729][FONT=Arial]

When I press the back light button Fn+F7 I get this error in dmesg:[/FONT][/COLOR]
```

[ 1120.866597] atkbd serio0: Unknown key pressed (translated set 2, code 0xf8 on isa0060/serio0).
[ 1120.866599] atkbd serio0: Use 'setkeycodes e078 <keycode>' to make it known.
[ 1122.403795] atkbd serio0: Unknown key released (translated set 2, code 0xf8 on isa0060/serio0).
[ 1122.403798] atkbd serio0: Use 'setkeycodes e078 <keycode>' to make it known.
```



I have no ideas what else to do and struggling to use without backlight.. any help would be really appreciated.

---

### Post by lksjfnvljnfdv on 2018-09-08
any ideas?

---

