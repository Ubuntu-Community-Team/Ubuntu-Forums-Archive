---
title: "Display does not work via USB-C port"
date: 2023-12-02
forum: General Help
---

### Post by jbuon on 2023-12-02
Hello,

I have troubles to use my secondary display via an USB-C hub from HP: [https://support.hp.com/in-en/drivers/hp-usb-c-mini-dock/17859030](https://support.hp.com/in-en/drivers/hp-usb-c-mini-dock/17859030)

It was working fine until last Thursday but sudently it is impossible to get the monitor working through the USB-C port. 
It is working perfectly via the HDMI port but as I need two displays.
And other hub functionalities are working fine (RJ45 conection, other USB inputs, ...)

My laptop is an HP Zbook Studio G5

And my graphical card returns following information when I execute: ```
[FONT=var(--font-family-monospace)]sudo lshw -class display[/FONT]
```[FONT=var(--font-family-monospace)]
[/FONT]
```

[COLOR=#000000][FONT=Arial]  *-display                [/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]       description: VGA compatible controller[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]       product: GP107GLM [Quadro P1000 Mobile][/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]       vendor: NVIDIA Corporation[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]       physical id: 0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]       bus info: pci@0000:01:00.0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]       version: a1[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]       width: 64 bits[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]       clock: 33MHz[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]       configuration: driver=nvidia latency=0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]       resources: irq:152 memory:e8000000-e8ffffff memory:a0000000-afffffff memory:b0000000-b1ffffff ioport:4000(size=128) memory:e9080000-e90fffff[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]  *-graphics[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]       product: EFI VGA[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]       physical id: 2[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]       logical name: /dev/fb0[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]       capabilities: fb[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]       configuration: depth=32 resolution=1920,1080
[/FONT][/COLOR]
```

The driver I have is nvidia-driver-535.

Do you have any idea how I could solve this issue? I tried many things I found on various forums but all solutions failed...

I also reinstalled the complete os (ubuntu 22.04) to make sure it is not an issue with my installation, still not working...

Thank you by advance.

---

