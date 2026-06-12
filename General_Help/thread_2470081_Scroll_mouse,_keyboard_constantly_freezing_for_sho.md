---
title: "Scroll mouse, keyboard constantly freezing for short time"
date: 2021-12-19
forum: General Help
---

### Post by dean.w.schulze on 2021-12-19
I have Ubuntu 20.04 running on a Dell XPS15-9560.  Graphics card is

NVIDIA Corporation GP107M [GeForce GTX 1050 Mobile]

My scroll mouse and keyboard will freeze every several seconds for a couple of seconds and then resume.  It's happened a few times while typing this message.  When using the scroll mouse the scrolling will freeze and then the page jumps to the new location.  This started happening recently.

The /var/log/syslog is full of these errors (nearly every second):

Dec 19 14:33:18 xps15-9560 kernel: [234236.432123] pcieport 0000:00:1d.0: AER: Corrected error received: 0000:04:00.0
Dec 19 14:33:18 xps15-9560 kernel: [234236.432151] nvme 0000:04:00.0: PCIe Bus Error: severity=Corrected, type=Physical Layer, (Receiver ID)
Dec 19 14:33:18 xps15-9560 kernel: [234236.432161] nvme 0000:04:00.0:   device [144d:a804] error status/mask=00000001/00006000
Dec 19 14:33:18 xps15-9560 kernel: [234236.432172] nvme 0000:04:00.0:    [ 0] RxErr  

Is this an error with the graphics driver or something else?

Thanks.

---

### Post by dean.w.schulze on 2021-12-21
[COLOR=#232629][FONT=-apple-system]The problem was the usb c hub I was using to drive a second external monitor. I was using the `UPGROW 8-in-1 Type C Adapter`. When I swapped it out for the U`techSmart 6 In 1 USB C to HDMI Adapter with 1000M Ethernet` usb hub the problems with the scroll mouse and keyboard freezing stopped.

[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]The errors shown above continue to occur, however, but apparently those errors are not related to the freezing I was seeing.[/FONT][/COLOR]

---

