---
title: "Frequent power-on of discrete graphics card when laptop work on battery"
date: 2022-05-30
forum: General Help
---

### Post by matadrox on 2022-05-30
Hello! I generally don't use nvidia on my laptop (540M driver 390), and use bbswitch to limit it. However, something is not right. The bbswitch module is loaded on startup, but the card is still active. I'm manually turning it off with tee /acpi/proc/bbswitch<<OFF and it's working, but after a while the card is back to ON position, so I have to repeat the turn off command several times. On power supply it happens similarly but less often. What am I doing wrong, someone may know?
```

marekania@marekania:~$ sudo tee /proc/acpi/bbswitch<<<OFF
[sudo] has&#322;o u&#380;ytkownika marekania: 
OFF
marekania@marekania:~$ cat /proc/acpi/bbswitch
0000:01:00.0 OFF
marekania@marekania:~$ cat /proc/acpi/bbswitch
0000:01:00.0 ON
marekania@marekania:~$ sudo tee /proc/acpi/bbswitch<<<OFF
OFF
marekania@marekania:~$ cat /proc/acpi/bbswitch
0000:01:00.0 ON
marekania@marekania:~$ sudo tee /proc/acpi/bbswitch<<<OFF
OFF
marekania@marekania:~$ cat /proc/acpi/bbswitch
0000:01:00.0 OFF
marekania@marekania:~$ cat /proc/acpi/bbswitch
0000:01:00.0 OFF
marekania@marekania:~$ cat /proc/acpi/bbswitch
0000:01:00.0 ON
marekania@marekania:~$ sudo tee /proc/acpi/bbswitch<<<OFF
OFF

```
output dmesg
```

[    4.109878] bbswitch: loading out-of-tree module taints kernel.
[    4.109913] bbswitch: module verification failed: signature and/or required key missing - tainting kernel
[    4.110182] bbswitch: version 0.8
[    4.110191] bbswitch: Found integrated VGA device 0000:00:02.0: \_SB_.PCI0.GFX0
[    4.110197] bbswitch: Found discrete VGA device 0000:01:00.0: \_SB_.PCI0.PEG0.PEGP
[    4.110413] bbswitch: detected an Optimus _DSM function
[    4.110506] bbswitch: disabling discrete graphics
[    4.148825] bbswitch: Succesfully loaded. Discrete card 0000:01:00.0 is off
[    6.963114] bbswitch: disabling discrete graphics
[    6.964678]  msr parport_pc ppdev lp parport drm bbswitch(OE) ip_tables x_tables autofs4 btrfs blake2b_generic xor zstd_compress raid6_pq libcrc32c hid_generic usbhid hid crc32_pclmul psmouse ahci i2c_i801 lpc_ich i2c_smbus libahci wmi video
[    6.964732]  bbswitch_off.part.0+0xf0/0x1e3 [bbswitch]
[    6.964737]  bbswitch_proc_write.cold+0x5/0x22 [bbswitch]
[  230.353363] bbswitch: disabling discrete graphics

```

Everything is solved by a simple installation of bumblebee, plus even the system now boots much faster. Until now I have not encountered such a situation. Regards!

---

