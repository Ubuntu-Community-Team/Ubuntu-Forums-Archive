---
title: "upgraded kernal using dist-upgrade getting blackscreen"
date: 2013-11-11
forum: General Help
---

### Post by Psil0cybin on 2013-11-11
```
Current Operating System: Linux 3.2.0-56-generic-pae #86-Ubuntu SMP Wed Oct 23 17:51:27 UTC 2013 i686

```

Hey guys i have a problem i upgraded my kernel and i got a black screen every time i booted into the upgraded kernel, so i typed nomodeset by hitting E within the grub and adding it to the boot options and it worked perfectly. So obviously I set it to make it permanent using sudo nano /etc/default/grub it did not work and every time i boot i either get a console (I can tell that the graphic card is failing or I get a black screen after the Ubuntu splash screen)

After upgrading the grub I did run (of course- in order to save changes to the actual grub menu)
```
sudo update-grub
```

So I am confused, prior to upgrading the kernel everything was working fine. (Never had an issue like this before..)

I am using an Acer Aspire One D270-1628
```
00:02.0 VGA compatible controller: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller (rev 09)
```
my /etc/default/grub
reads
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```
where it needs to be set, maybe someone can help me figure this out..because I am lost and am stuck using an outdated kernel :) in order to boot into my system normally, without issues.
**P.S people on the IRC, are suggesting that nomodeset is a bad fix/some say it is a good fix... I am confused... **what can I do in order to get my Ubuntu machine working as perfectly as it was prior to the new kernel upgrade?

Some other people are suggesting I stick to the old outdated kernel, but I am worried that If I upgraded and this kernel does not work, that perhaps all the newer ones from now one will continue down the same path not working? Does this make sense, or would I need to sit this kernel upgrade out? Sorry I am confused this never has happened to my machine. Usually I can upgrade flawlessly.

More Information:
```

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise

```

Please let me know If I need to provide more information In order to fix or diagnose this issue.

---

### Post by Psil0cybin on 2013-11-11
bump I tried 
```
vesafb.nonsense=1 
```

removed splash and still no luck/

---

### Post by Psil0cybin on 2013-11-11
bump...any one? I have tried reinstalling the graphic drivers via additional drivers but that cause more problems then fixed for previous kernel versions..
anyone know what i can do ?! do I stay away from kernel updates from now on?!

---

### Post by Psil0cybin on 2013-11-11
hey guys updated my kernel using *sudo dist-upgrade *and keep getting a blackscreen (after the grub menu -> right before the login menu should start)
The problematic kernel is 
```
[COLOR=#000000][FONT=Ubuntu Mono]Current Operating System: Linux 3.2.0-56-generic-pae #86-Ubuntu SMP Wed Oct 23 17:51:27 UTC 2013 i686
[/FONT][/COLOR]
```

Looking @ Xorg.org I was able to see that the problem is that the new kernel cannot find any displays ( something wrong with the graphic driver / Process )
While version
***3.2.0-55-generic-pae*** worked perfectly fine!

Someone is suggesting because I am using an Acer Aspire One D270-1628 that intel is not working to support any hardware from kernel versions 3.2.0-56

What would I do if i cannot upgrade my kernel-successfully? I do not want to have an obsolete ubuntu system that is going to be forever out of date. I have tried various boot parameters, without any success such as **nomodeset**.

Is this the case, I just got this laptop a year ago..I cannot imagin that the hardware would be unsupported so quickly.
Here is some more information about the chip set. (graphic display)

```
[COLOR=#000000][FONT=Ubuntu Mono]00:02.0 VGA compatible controller: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller (rev 09)[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Ubuntu Mono]
[FONT=arial]Here is some more information I was able to gather via using a working out of date kernel.
[/FONT][/FONT][/COLOR]
```

[LIST=1]
[*][COLOR=#000000]00:00.0 Host bridge: Intel Corporation Atom Processor D2xxx/N2xxx DRAM Controller (rev 03)[/COLOR]
[*][COLOR=#000000]        Subsystem: Acer Incorporated [ALI] Device 061f[/COLOR]
[*][COLOR=#000000]        Flags: bus master, fast devsel, latency 0[/COLOR]
[*][COLOR=#000000]00:02.0 VGA compatible controller: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])[/COLOR]
[*][COLOR=#000000]        Subsystem: Acer Incorporated [ALI] Device 061f[/COLOR]
[*][COLOR=#000000]        Flags: bus master, fast devsel, latency 0, IRQ 45[/COLOR]
[*][COLOR=#000000]        Memory at 46000000 (32-bit, non-prefetchable) [size=1M][/COLOR]
[*][COLOR=#000000]        I/O ports at 50d0 [size=8][/COLOR]
[*][COLOR=#000000]        Expansion ROM at <unassigned> [disabled][/COLOR]
[*][COLOR=#000000]        Capabilities: <access denied>[/COLOR]
[*][COLOR=#000000]        Kernel driver in use: pvrsrvkm[/COLOR]
[*][COLOR=#000000]        Kernel modules: cedarview_gfx[/COLOR]
[*][COLOR=#000000]00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)[/COLOR]
[*][COLOR=#000000]        Subsystem: Acer Incorporated [ALI] Device 061f[/COLOR]
[*][COLOR=#000000]        Flags: bus master, fast devsel, latency 0, IRQ 46[/COLOR]
[*][COLOR=#000000]        Memory at 46100000 (64-bit, non-prefetchable) [size=16K][/COLOR]
[*][COLOR=#000000]        Capabilities: <access denied>[/COLOR]
[*][COLOR=#000000]        Kernel driver in use: snd_hda_intel[/COLOR]
[*][COLOR=#000000]        Kernel modules: snd-hda-intel[/COLOR]
[*][COLOR=#000000]00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])[/COLOR]
[*][COLOR=#000000]        Flags: bus master, fast devsel, latency 0[/COLOR]
[*][COLOR=#000000]        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0[/COLOR]
[*][COLOR=#000000]        I/O behind bridge: 00004000-00004fff[/COLOR]
[*][COLOR=#000000]        Memory behind bridge: 45000000-45ffffff[/COLOR]
[*][COLOR=#000000]        Prefetchable memory behind bridge: 0000000040000000-0000000040ffffff[/COLOR]
[*][COLOR=#000000]        Capabilities: <access denied>[/COLOR]
[*][COLOR=#000000]        Kernel driver in use: pcieport[/COLOR]
[*][COLOR=#000000]        Kernel modules: shpchp[/COLOR]
[*][COLOR=#000000]00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])[/COLOR]
[*][COLOR=#000000]        Flags: bus master, fast devsel, latency 0[/COLOR]
[*][COLOR=#000000]        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0[/COLOR]
[*][COLOR=#000000]        I/O behind bridge: 00003000-00003fff[/COLOR]
[*][COLOR=#000000]        Memory behind bridge: 44000000-44ffffff[/COLOR]
[*][COLOR=#000000]        Prefetchable memory behind bridge: 0000000041000000-0000000041ffffff[/COLOR]
[*][COLOR=#000000]        Capabilities: <access denied>[/COLOR]
[*][COLOR=#000000]        Kernel driver in use: pcieport[/COLOR]
[*][COLOR=#000000]        Kernel modules: shpchp[/COLOR]
[*][COLOR=#000000]00:1c.2 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])[/COLOR]
[*][COLOR=#000000]        Flags: bus master, fast devsel, latency 0[/COLOR]
[*][COLOR=#000000]        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0[/COLOR]
[*][COLOR=#000000]        I/O behind bridge: 00002000-00002fff[/COLOR]
[*][COLOR=#000000]        Memory behind bridge: 43000000-43ffffff[/COLOR]
[*][COLOR=#000000]        Prefetchable memory behind bridge: 0000000042000000-0000000042ffffff[/COLOR]
[*][COLOR=#000000]        Capabilities: <access denied>[/COLOR]
[*][COLOR=#000000]        Kernel driver in use: pcieport[/COLOR]
[*][COLOR=#000000]        Kernel modules: shpchp[/COLOR]
[*][COLOR=#000000]00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])[/COLOR]
[*][COLOR=#000000]        Subsystem: Acer Incorporated [ALI] Device 061f[/COLOR]
[*][COLOR=#000000]        Flags: bus master, medium devsel, latency 0, IRQ 17[/COLOR]
[*][COLOR=#000000]        I/O ports at 50a0 [size=32][/COLOR]
[*][COLOR=#000000]        Kernel driver in use: uhci_hcd[/COLOR]
[*][COLOR=#000000]00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])[/COLOR]
[*][COLOR=#000000]        Subsystem: Acer Incorporated [ALI] Device 061f[/COLOR]
[*][COLOR=#000000]        Flags: bus master, medium devsel, latency 0, IRQ 19[/COLOR]
[*][COLOR=#000000]        I/O ports at 5080 [size=32][/COLOR]
[*][COLOR=#000000]        Kernel driver in use: uhci_hcd[/COLOR]
[*][COLOR=#000000]00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])[/COLOR]
[*][COLOR=#000000]        Subsystem: Acer Incorporated [ALI] Device 061f[/COLOR]
[*][COLOR=#000000]        Flags: bus master, medium devsel, latency 0, IRQ 18[/COLOR]
[*][COLOR=#000000]        I/O ports at 5060 [size=32][/COLOR]
[*][COLOR=#000000]        Kernel driver in use: uhci_hcd[/COLOR]
[*][COLOR=#000000]00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])[/COLOR]
[*][COLOR=#000000]        Subsystem: Acer Incorporated [ALI] Device 061f[/COLOR]
[*][COLOR=#000000]        Flags: bus master, medium devsel, latency 0, IRQ 16[/COLOR]
[*][COLOR=#000000]        I/O ports at 5040 [size=32][/COLOR]
[*][COLOR=#000000]        Kernel driver in use: uhci_hcd[/COLOR]
[*][COLOR=#000000]00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])[/COLOR]
[*][COLOR=#000000]        Subsystem: Acer Incorporated [ALI] Device 061f[/COLOR]
[*][COLOR=#000000]        Flags: bus master, medium devsel, latency 0, IRQ 17[/COLOR]
[*][COLOR=#000000]        Memory at 46105000 (32-bit, non-prefetchable) [size=1K][/COLOR]
[*][COLOR=#000000]        Capabilities: <access denied>[/COLOR]
[*][COLOR=#000000]        Kernel driver in use: ehci_hcd[/COLOR]
[*][COLOR=#000000]00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])[/COLOR]
[*][COLOR=#000000]        Flags: bus master, fast devsel, latency 0[/COLOR]
[*][COLOR=#000000]        Bus: primary=00, secondary=04, subordinate=04, sec-latency=32[/COLOR]
[*][COLOR=#000000]        Capabilities: <access denied>[/COLOR]
[*][COLOR=#000000]00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)[/COLOR]
[*][COLOR=#000000]        Subsystem: Acer Incorporated [ALI] Device 061f[/COLOR]
[*][COLOR=#000000]        Flags: bus master, medium devsel, latency 0[/COLOR]
[*][COLOR=#000000]        Capabilities: <access denied>[/COLOR]
[*][COLOR=#000000]        Kernel modules: iTCO_wdt[/COLOR]
[*][COLOR=#000000]00:1f.2 SATA controller: Intel Corporation NM10/ICH7 Family SATA Controller [AHCI mode] (rev 02) (prog-if 01 [AHCI 1.0])[/COLOR]
[*][COLOR=#000000]        Subsystem: Acer Incorporated [ALI] Device 061f[/COLOR]
[*][COLOR=#000000]        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 43[/COLOR]
[*][COLOR=#000000]        I/O ports at 50c8 [size=8][/COLOR]
[*][COLOR=#000000]        I/O ports at 50dc [size=4][/COLOR]
[*][COLOR=#000000]        I/O ports at 50c0 [size=8][/COLOR]
[*][COLOR=#000000]        I/O ports at 50d8 [size=4][/COLOR]
[*][COLOR=#000000]        I/O ports at 5020 [size=16][/COLOR]
[*][COLOR=#000000]        Memory at 46104000 (32-bit, non-prefetchable) [size=1K][/COLOR]
[*][COLOR=#000000]        Capabilities: <access denied>[/COLOR]
[*][COLOR=#000000]        Kernel driver in use: ahci[/COLOR]
[*][COLOR=#000000]00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)[/COLOR]
[*][COLOR=#000000]        Subsystem: Acer Incorporated [ALI] Device 061f[/COLOR]
[*][COLOR=#000000]        Flags: medium devsel, IRQ 10[/COLOR]
[*][COLOR=#000000]        I/O ports at 5000 [size=32][/COLOR]
[*][COLOR=#000000]        Kernel modules: i2c-i801[/COLOR]
[*][COLOR=#000000]01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)[/COLOR]
[*][COLOR=#000000]        Subsystem: Acer Incorporated [ALI] Device 061f[/COLOR]
[*][COLOR=#000000]        Flags: bus master, fast devsel, latency 0, IRQ 44[/COLOR]
[*][COLOR=#000000]        I/O ports at 4000 [size=256][/COLOR]
[*][COLOR=#000000]        Memory at 40004000 (64-bit, prefetchable) [size=4K][/COLOR]
[*][COLOR=#000000]        Memory at 40000000 (64-bit, prefetchable) [size=16K][/COLOR]
[*][COLOR=#000000]        Capabilities: <access denied>[/COLOR]
[*][COLOR=#000000]        Kernel driver in use: r8169[/COLOR]
[*][COLOR=#000000]        Kernel modules: r8169[/COLOR]
[*][COLOR=#000000]02:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)[/COLOR]
[*][COLOR=#000000]        Subsystem: Foxconn International, Inc. Device e047[/COLOR]
[*][COLOR=#000000]        Flags: bus master, fast devsel, latency 0, IRQ 17[/COLOR]
[*][COLOR=#000000]        Memory at 44000000 (64-bit, non-prefetchable) [size=512K][/COLOR]
[*][COLOR=#000000]        Expansion ROM at 41000000 [disabled] [size=64K][/COLOR]
[*][COLOR=#000000]        Capabilities: <access denied>[/COLOR]
[*][COLOR=#000000]        Kernel driver in use: ath9k[/COLOR]
[*][COLOR=#000000]        Kernel modules: ath9k[/COLOR]
[*][COLOR=#000000]03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)[/COLOR]
[*][COLOR=#000000]        Subsystem: Acer Incorporated [ALI] Device 061f[/COLOR]
[*][COLOR=#000000]        Flags: bus master, fast devsel, latency 0, IRQ 18[/COLOR]
[*][COLOR=#000000]        Memory at 43001000 (32-bit, non-prefetchable) [size=4K][/COLOR]
[*][COLOR=#000000]        Capabilities: <access denied>[/COLOR]
[*][COLOR=#000000]        Kernel driver in use: rts_pstor[/COLOR]
[*][COLOR=#000000]        Kernel modules: rts_pstor
[/COLOR]
[/LIST]

```
[COLOR=#000000][FONT=Ubuntu Mono][FONT=arial]Please someone let me know what I can do...I am all out of ideas.
Do you think that newer kernels might work for me? Or is this the end of the line for my machine? At the moment I am using an out dated kernel, is that fine for now? What can I do fix this problem for later upgrades? I am using Ubuntu 12.04 LTS Precise Pangolin.
I really hope there is something I can do to fix this problem, I really cannot go back to Windows and need to have my computer stable again.
[/FONT]
[/FONT][/COLOR]

---

### Post by Psil0cybin on 2013-11-11
bump...................anyone have any suggestions please?

---

### Post by QIII on 2013-11-11
Please do not bump so quickly.  Allow the community 24 hours to respond.

Remember that we are a world-wide community of users just like you who may be asleep, at work, eating meals, playing with our grandchildren or working in the garden when you post.

---

### Post by Psil0cybin on 2013-11-12
> **QIII said:**
> Please do not bump so quickly.  Allow the community 24 hours to respond.

Remember that we are a world-wide community of users just like you who may be asleep, at work, eating meals, playing with our grandchildren or working in the garden when you post.

Thank you so much, Just was not sure if this was the right section/category. (It gets confusing sometimes),
but thank you I will wait patiently.

---

### Post by mörgæs on 2013-11-12
Repeat bumping AND double-posting will not earn you friends here. I have merged your threads.

---

### Post by philinux on 2013-11-12
> **Psil0cybin said:**
> bump...any one? I have tried reinstalling the graphic drivers via additional drivers but that cause more problems then fixed for previous kernel versions..
anyone know what i can do ?! do I stay away from kernel updates from now on?!

From grub choose an older kernel for now. See if that works.

---

