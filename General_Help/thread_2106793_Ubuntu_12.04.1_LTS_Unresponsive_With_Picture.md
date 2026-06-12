---
title: "Ubuntu 12.04.1 LTS Unresponsive With Picture"
date: 2013-01-20
forum: General Help
---

### Post by copan on 2013-01-20
This issue was reposted in the proper forum after concluding what the problem must be.  You can find the new post here:

[http://ubuntuforums.org/showthread.php?p=12465408#post12465408](http://ubuntuforums.org/showthread.php?p=12465408#post12465408)

Okay here's a strange one for you.  I've used Ubuntu for about 2 years now and haven't had any problems with freezing, but lately here's what been happening.

Ubuntu randomly becomes unresponsive, and displays a cancel or don't sign (not sure what the actual symbol is called, which is why I uploaded screeny).  This has happened about 3 times now and seems to happen after I switch my TV input from ubuntu (HDMI 1) to XBOX 360 (ColorStream) and back again.  It does not happen every time but happens sometimes.

I have a 42" Toshiba running on Ubuntu 12.04.1 LTS 64-bit version
Processor: AMD Phenom II X6 1055T
Graphics: VESA: Redwood

Anyway, my machine does not respond to anything, including:

[LIST]
[*]mouse
[*]keyboard
[*]ssh
[*]http
[*]ftp
[/LIST]

If I could even login using ssh or use the terminal I would at least try restarting lightdm or something.

Please look at my screenshot to see the symbol I get when the machine freezes.  Has anyone else had this happen to them?  Am I being hacked or something?  Seems like the machine is running but no longer accepts incoming connections or devices.

Since the keyboard was frozen the "screenshot" is actually a digital photo of the screen.

Thank you for your time.

** EDIT: after further investigation I figured out how to locate and copy the latest from ubuntu's kernel log report - which occurred around the time of the crash:

Jan 20 01:39:49 prissy-TA785G3 kernel: [   14.665958] [fglrx] Maximum main memory to use for locked dma buf$
Jan 20 01:39:49 prissy-TA785G3 kernel: [   14.666051] [fglrx]   vendor: 1002 device: 68d8 count: 1
Jan 20 01:39:49 prissy-TA785G3 kernel: [   14.666438] [fglrx] ioport: bar 4, base 0xd000, size: 0x100
Jan 20 01:39:49 prissy-TA785G3 kernel: [   14.666450] pci 0000:01:00.0: PCI INT A -> GSI 18 (level, low) ->$
Jan 20 01:39:49 prissy-TA785G3 kernel: [   14.666453] pci 0000:01:00.0: setting latency timer to 64
Jan 20 01:39:49 prissy-TA785G3 kernel: [   14.666732] [fglrx] Kernel PAT support is enabled
Jan 20 01:39:49 prissy-TA785G3 kernel: [   14.666747] [fglrx] module loaded - fglrx 8.96.4 [Mar 12 2012] wi$
Jan 20 01:39:49 prissy-TA785G3 kernel: [   15.005604] logitech-djreceiver 0003:046D:C52B.0006: hiddev0,hidr$
Jan 20 01:39:49 prissy-TA785G3 kernel: [   15.010722] input: Logitech Unifying Device. Wireless PID:1025 as$
Jan 20 01:39:49 prissy-TA785G3 kernel: [   15.010888] logitech-djdevice 0003:046D:C52B.0007: input,hidraw4:$
Jan 20 01:39:49 prissy-TA785G3 kernel: [   15.250858] type=1400 audit(1358674789.912:8): apparmor="STATUS" $
Jan 20 01:39:49 prissy-TA785G3 kernel: [   15.251269] type=1400 audit(1358674789.912:9): apparmor="STATUS" $
Jan 20 01:39:50 prissy-TA785G3 kernel: [   15.578359] init: failsafe main process (760) killed by TERM sign$
Jan 20 01:39:51 prissy-TA785G3 kernel: [   16.917664] Bluetooth: Core ver 2.16
Jan 20 01:39:51 prissy-TA785G3 kernel: [   16.917684] NET: Registered protocol family 31
Jan 20 01:39:51 prissy-TA785G3 kernel: [   16.917686] Bluetooth: HCI device and connection manager initiali$
Jan 20 01:39:51 prissy-TA785G3 kernel: [   16.917689] Bluetooth: HCI socket layer initialized
Jan 20 01:39:51 prissy-TA785G3 kernel: [   16.917691] Bluetooth: L2CAP socket layer initialized
Jan 20 01:39:51 prissy-TA785G3 kernel: [   16.917695] Bluetooth: SCO socket layer initialized
Jan 20 01:39:51 prissy-TA785G3 kernel: [   16.935434] Bluetooth: RFCOMM TTY layer initialized
Jan 20 01:39:51 prissy-TA785G3 kernel: [   16.935438] Bluetooth: RFCOMM socket layer initialized
Jan 20 01:39:51 prissy-TA785G3 kernel: [   16.935439] Bluetooth: RFCOMM ver 1.11
Jan 20 01:39:51 prissy-TA785G3 kernel: [   17.076942] snd_hda_intel 0000:00:14.2: PCI INT A -> GSI 16 (leve$
Jan 20 01:39:51 prissy-TA785G3 kernel: [ * 17.106776] input: HDA ATI SB Line as /devices/pci0000:00/0000:00$
Jan 20 01:39:51 prissy-TA785G3 kernel: [ * 17.106899] input: HDA ATI SB Rear Mic as /devices/pci0000:00/000$
Jan 20 01:39:51 prissy-TA785G3 kernel: [ * 17.106962] input: HDA ATI SB Front Mic as /devices/pci0000:00/00$
Jan 20 01:39:51 prissy-TA785G3 kernel: [ * 17.107017] input: HDA ATI SB Front Headphone as /devices/pci0000$
Jan 20 01:39:51 prissy-TA785G3 kernel: [ * 17.107069] input: HDA ATI SB Line Out as /devices/pci0000:00/000$
Jan 20 01:39:51 prissy-TA785G3 kernel: [ * 17.107324] snd_hda_intel 0000:01:00.1: PCI INT B -> GSI 19 (leve$
Jan 20 01:39:51 prissy-TA785G3 kernel: [ * 17.107390] snd_hda_intel 0000:01:00.1: irq 43 for MSI/MSI-X
Jan 20 01:39:51 prissy-TA785G3 kernel: [ * 17.107408] snd_hda_intel 0000:01:00.1: setting latency timer to $
Jan 20 01:39:51 prissy-TA785G3 kernel: [ * 17.164970] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
Jan 20 01:39:51 prissy-TA785G3 kernel: [ * 17.164973] Bluetooth: BNEP filters: protocol multicast
Jan 20 01:39:52 prissy-TA785G3 kernel: [ * 17.333713] type=1400 audit(1358674791.996:10): apparmor="STATUS"$
Jan 20 01:39:52 prissy-TA785G3 kernel: [ * 17.334073] type=1400 audit(1358674791.996:11): apparmor="STATUS"$
Jan 20 01:39:52 prissy-TA785G3 kernel: [ * 17.346756] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci$
Jan 20 01:39:52 prissy-TA785G3 kernel: [ * 18.029552] r8169 0000:02:00.0: eth0: link down
Jan 20 01:39:52 prissy-TA785G3 kernel: [ * 18.029565] r8169 0000:02:00.0: eth0: link down
Jan 20 01:39:52 prissy-TA785G3 kernel: [ * 18.030275] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan 20 01:39:52 prissy-TA785G3 kernel: [ * 18.030508] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jan 20 01:39:52 prissy-TA785G3 kernel: [   18.283789] vesafb: mode is 1400x1050x32, linelength=5632, pages=0
Jan 20 01:39:52 prissy-TA785G3 kernel: [   18.283792] vesafb: scrolling: redraw
Jan 20 01:39:52 prissy-TA785G3 kernel: [   18.283795] vesafb: Truecolor: size=0:8:8:8, shift=0:16:8:0
Jan 20 01:39:52 prissy-TA785G3 kernel: [   18.291762] vesafb: framebuffer at 0xd0000000, mapped to 0xffffc9$
Jan 20 01:39:52 prissy-TA785G3 kernel: [   18.291982] Console: switching to colour frame buffer device 175x$
Jan 20 01:39:52 prissy-TA785G3 kernel: [   18.292025] fb0: VESA VGA frame buffer device
Jan 20 01:39:53 prissy-TA785G3 kernel: [   19.122272] audit_printk_skb: 48 callbacks suppressed
Jan 20 01:39:53 prissy-TA785G3 kernel: [   19.122275] type=1400 audit(1358674793.784:28): apparmor="STATUS"$
Jan 20 01:39:54 prissy-TA785G3 kernel: [   20.183367] r8169 0000:02:00.0: eth0: link up
Jan 20 01:39:54 prissy-TA785G3 kernel: [   20.184160] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Jan 20 01:40:01 prissy-TA785G3 kernel: [   26.340660] fglrx_pci 0000:01:00.0: irq 44 for MSI/MSI-X
Jan 20 01:40:01 prissy-TA785G3 kernel: [   26.341323] [fglrx] Firegl kernel thread PID: 1265
Jan 20 01:40:01 prissy-TA785G3 kernel: [   26.341389] [fglrx] Firegl kernel thread PID: 1266
Jan 20 01:40:01 prissy-TA785G3 kernel: [   26.341454] [fglrx] Firegl kernel thread PID: 1267
Jan 20 01:40:01 prissy-TA785G3 kernel: [   26.341539] [fglrx] IRQ 44 Enabled
Jan 20 01:40:04 prissy-TA785G3 kernel: [   29.374825] [fglrx] Gart USWC size:1280 M.
Jan 20 01:40:04 prissy-TA785G3 kernel: [   29.374828] [fglrx] Gart cacheable size:508 M.
Jan 20 01:40:04 prissy-TA785G3 kernel: [   29.374831] [fglrx] Reserved FB block: Shared offset:0, size:1000$
Jan 20 01:40:04 prissy-TA785G3 kernel: [   29.374833] [fglrx] Reserved FB block: Unshared offset:f8fd000, s$
Jan 20 01:40:04 prissy-TA785G3 kernel: [   29.374835] [fglrx] Reserved FB block: Unshared offset:3fff4000, $
Jan 20 01:40:06 prissy-TA785G3 kernel: [   31.488061] eth0: no IPv6 routers present

---

### Post by rrich1974 on 2013-01-20
i think that is something to do with the video driver. i see that you are using vesa but see some instances of fglrx. 
put the output of:
> lspci
> glxinfo
> fglrxinfo

---

### Post by copan on 2013-01-20
> **rrich1974 said:**
> i think that is something to do with the video driver. i see that you are using vesa but see some instances of fglrx. 
put the output of:


I've posted the output you requested in a post I created last night because I also figured it must be a graphics driver issue.

The post is here: 

[http://ubuntuforums.org/showthread.php?p=12465408#post12465408](http://ubuntuforums.org/showthread.php?p=12465408#post12465408)

---

### Post by tgalati4 on 2013-01-20
Is it possible that your TV is going to sleep when you switch away from it?  Go into the menu/settings on the TV and turn power-savings off.  Then see if the behavior changes.

---

