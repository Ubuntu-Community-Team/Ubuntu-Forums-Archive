---
title: "Ubuntu 20.04 Bluetooth freezes boot"
date: 2020-10-12
forum: General Help
---

### Post by rs-aleev on 2020-10-12
Hello, 

Recently, after testing ly DM in SDDM session, I receive such strange error, that freezes boot 
```

[FONT=monospace][COLOR=#18B218][    5.070783] [/COLOR][COLOR=#B26818]Bluetooth[/COLOR][COLOR=#000000]: hci0: read Intel version: 370810011003110e00[/COLOR]
[COLOR=#18B218][    5.074728] [/COLOR][COLOR=#B26818]Bluetooth[/COLOR][COLOR=#000000]: hci0: Intel Bluetooth firmware file: intel/ibt-hw-37.8.10-fw-1.10.3.11.e.bseq[/COLOR]
[COLOR=#18B218][    5.207024] [/COLOR][COLOR=#B26818]uvcvideo[/COLOR][COLOR=#000000]: Found UVC 1.00 device Integrated Camera (5986:2113)[/COLOR]
[COLOR=#18B218][    5.225338] [/COLOR][COLOR=#B26818]uvcvideo 1-6:1.0[/COLOR][COLOR=#000000]**: Entity type for entity Extension 4 was not initialized!**[/COLOR]
[COLOR=#18B218][    5.225339] [/COLOR][COLOR=#B26818]uvcvideo 1-6:1.0[/COLOR][COLOR=#000000]**: Entity type for entity Extension 3 was not initialized!**[/COLOR]
[COLOR=#18B218][    5.225340] [/COLOR][COLOR=#B26818]uvcvideo 1-6:1.0[/COLOR][COLOR=#000000]**: Entity **[/COLOR][/FONT] [FONT=monospace][COLOR=#000000]**type for entity Processing 2 was not initialized!**[/COLOR]
[COLOR=#18B218][    5.225341] [/COLOR][COLOR=#B26818]uvcvideo 1-6:1.0[/COLOR][COLOR=#000000]**: Entity type for entity Camera 1 was not initialized!**[/COLOR]
[COLOR=#18B218][    5.225398] [/COLOR][COLOR=#B26818]input[/COLOR][COLOR=#000000]: Integrated Camera: Integrated C as /devices/pci0000:00/0000:00:14.0/usb1/1-6/1-6:1.0/input/input17[/COLOR]
[COLOR=#18B218][    5.225475] [/COLOR][COLOR=#B26818]usbcore[/COLOR][COLOR=#000000]: registered new interface driver uvcvideo[/COLOR]
[COLOR=#18B218][    5.225476] [/COLOR][COLOR=#000000]USB Video Class driver (1.1.1)[/COLOR]
[COLOR=#18B218][    5.253226] [/COLOR][COLOR=#B26818]Generic FE-GE Realtek PHY r8169-300:00[/COLOR][COLOR=#000000]: attached PHY driver [Generic FE-GE Realtek PHY] (mii_bus:phy_addr=r8169-300:00[/COLOR]
, irq=IGNORE)
[COLOR=#18B218][    5.270769] [/COLOR][COLOR=#B26818]Bluetooth[/COLOR][COLOR=#B21818]: hci0: unexpected event for opcode 0xfc2f[/COLOR]
[COLOR=#18B218][    5.270776] [/COLOR][COLOR=#B26818]fbcon[/COLOR][COLOR=#000000]: Taking over console[/COLOR]
[COLOR=#18B218][    5.277138] [/COLOR][COLOR=#B26818]Console[/COLOR][COLOR=#000000]: swi[/COLOR][/FONT] [FONT=monospace][COLOR=#000000]tching to colour frame buffer device 240x67[/COLOR]
[COLOR=#18B218][    5.287780] [/COLOR][COLOR=#B26818]Bluetooth[/COLOR][COLOR=#000000]: hci0: Intel firmware patch completed and activated[/COLOR]
[COLOR=#18B218][    5.374914] [/COLOR][COLOR=#B26818]r8169 0000:03:00.0 enp3s0[/COLOR][COLOR=#000000]: Link is Down[/COLOR]
[/FONT] 
```

As you can see, I had to switch to tty2 to start a session, because tty1 was freezed and SDDM didn't start, also.  How to fix it? What can cause this bug? 
```

[FONT=monospace][COLOR=#000000]Kernel 5.4.0-48-generic [/COLOR]
[/FONT]
```

---

### Post by alexandrerocha on 2021-01-30
I have the same problem after install Pop OS and I fixed  following link -> [https://support.system76.com/articles/bluetooth/](https://support.system76.com/articles/bluetooth/)

---

