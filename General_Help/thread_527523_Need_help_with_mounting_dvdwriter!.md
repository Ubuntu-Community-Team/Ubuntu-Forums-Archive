---
title: "Need help with mounting dvdwriter!"
date: 2007-08-16
forum: General Help
---

### Post by boom2k1 on 2007-08-16
Hello all,
I just got my new computer and I am having trouble using my LG 18x dvdrw. I used this drive to install Ubuntu, but after Ubuntu is installed, the drive won't work in Linux! (I found out as my dad was trying to test my Linux!!!! --How pissed off he can say again that a lot of things doesn't work in LInux!) A strange thing is I do see the CD-Rom Disc icon on the desktop. Right click on it brings up the menu where I can press Eject. It doesn't do anything!

I use a Asus M2A-VM motherboard on AMD x2 4000+ with a SATA harddrive and the IDE LG18x dvdrw.

Anyway, I recall as I was starting up Ubuntu, I sometimes see the error log
about IDE fails to boot up. Following some of the diagnosis tool I found from other posts:

dmesg
```
[   67.812000] ide: failed opcode was: unknown
[   67.812000] hda: drive not ready for command
[   67.812000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[   67.812000] ide: failed opcode was: unknown
[   67.812000] hda: drive not ready for command
[   67.812000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[   67.812000] ide: failed opcode was: unknown
[   67.812000] hda: drive not ready for command
[   68.956000] vmnet1: no IPv6 routers present
[   69.084000] vmnet8: no IPv6 routers present
[   69.612000] eth0: no IPv6 routers present
[  129.812000] hda: irq timeout: status=0x50 { DriveReady SeekComplete }
[  129.812000] ide: failed opcode was: unknown
[  189.820000] hda: irq timeout: status=0x50 { DriveReady SeekComplete }
[  189.820000] ide: failed opcode was: unknown
[  249.820000] hda: irq timeout: status=0x50 { DriveReady SeekComplete }
[  249.820000] ide: failed opcode was: unknown
[  309.820000] hda: irq timeout: status=0x50 { DriveReady SeekComplete }
[  309.820000] ide: failed opcode was: unknown
[  369.820000] hda: irq timeout: status=0x50 { DriveReady SeekComplete }
[  369.820000] ide: failed opcode was: unknown
[  374.820000] hda: irq timeout: status=0x58 { DriveReady SeekComplete DataRequest }
[  374.820000] ide: failed opcode was: unknown
[  374.820000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  374.820000] ide: failed opcode was: unknown
[  374.820000] hda: drive not ready for command
[  374.820000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  374.820000] ide: failed opcode was: unknown
[  374.820000] hda: drive not ready for command
[  374.820000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  374.820000] ide: failed opcode was: unknown
[  374.820000] hda: drive not ready for command
[  374.820000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  374.820000] ide: failed opcode was: unknown
[  374.820000] hda: drive not ready for command
[  374.820000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  374.820000] ide: failed opcode was: unknown
[  374.820000] hda: drive not ready for command
[  374.848000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  374.848000] ide: failed opcode was: unknown
[  374.848000] hda: drive not ready for command
[  374.848000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  374.848000] ide: failed opcode was: unknown
[  374.848000] hda: drive not ready for command
[  374.848000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  374.848000] ide: failed opcode was: unknown
[  374.848000] hda: drive not ready for command
[  374.848000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  374.848000] ide: failed opcode was: unknown
[  374.848000] hda: drive not ready for command
[  374.868000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  374.868000] ide: failed opcode was: unknown
[  374.868000] hda: drive not ready for command
[  374.872000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  374.872000] ide: failed opcode was: unknown
[  374.872000] hda: drive not ready for command
[  374.872000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  374.872000] ide: failed opcode was: unknown
[  374.872000] hda: drive not ready for command
[  374.872000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  374.872000] ide: failed opcode was: unknown
[  374.872000] hda: drive not ready for command
[  374.872000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  374.872000] ide: failed opcode was: unknown
[  374.872000] hda: drive not ready for command
[  376.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  376.824000] ide: failed opcode was: unknown
[  376.824000] hda: drive not ready for command
[  376.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  376.824000] ide: failed opcode was: unknown
[  376.824000] hda: drive not ready for command
[  376.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  376.824000] ide: failed opcode was: unknown
[  376.824000] hda: drive not ready for command
[  376.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  376.824000] ide: failed opcode was: unknown
[  376.824000] hda: drive not ready for command
[  378.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  378.824000] ide: failed opcode was: unknown
[  378.824000] hda: drive not ready for command
[  378.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  378.824000] ide: failed opcode was: unknown
[  378.824000] hda: drive not ready for command
[  378.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  378.824000] ide: failed opcode was: unknown
[  378.824000] hda: drive not ready for command
[  378.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  378.824000] ide: failed opcode was: unknown
[  378.824000] hda: drive not ready for command
[  380.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  380.824000] ide: failed opcode was: unknown
[  380.824000] hda: drive not ready for command
[  380.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  380.824000] ide: failed opcode was: unknown
[  380.824000] hda: drive not ready for command
[  380.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  380.824000] ide: failed opcode was: unknown
[  380.824000] hda: drive not ready for command
[  380.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  380.824000] ide: failed opcode was: unknown
[  380.824000] hda: drive not ready for command
[  382.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  382.824000] ide: failed opcode was: unknown
[  382.824000] hda: drive not ready for command
[  382.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  382.824000] ide: failed opcode was: unknown
[  382.824000] hda: drive not ready for command
[  382.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  382.824000] ide: failed opcode was: unknown
[  382.824000] hda: drive not ready for command
[  382.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  382.824000] ide: failed opcode was: unknown
[  382.824000] hda: drive not ready for command
[  384.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  384.824000] ide: failed opcode was: unknown
[  384.824000] hda: drive not ready for command
[  384.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  384.824000] ide: failed opcode was: unknown
[  384.824000] hda: drive not ready for command
[  384.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  384.824000] ide: failed opcode was: unknown
[  384.824000] hda: drive not ready for command
[  384.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  384.824000] ide: failed opcode was: unknown
[  384.824000] hda: drive not ready for command
[  386.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  386.824000] ide: failed opcode was: unknown
[  386.824000] hda: drive not ready for command
[  386.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  386.824000] ide: failed opcode was: unknown
[  386.824000] hda: drive not ready for command
[  386.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  386.824000] ide: failed opcode was: unknown
[  386.824000] hda: drive not ready for command
[  386.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  386.824000] ide: failed opcode was: unknown
[  386.824000] hda: drive not ready for command
[  388.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  388.824000] ide: failed opcode was: unknown
[  388.824000] hda: drive not ready for command
[  388.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  388.824000] ide: failed opcode was: unknown
[  388.824000] hda: drive not ready for command
[  388.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  388.824000] ide: failed opcode was: unknown
[  388.824000] hda: drive not ready for command
[  388.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  388.824000] ide: failed opcode was: unknown
[  388.824000] hda: drive not ready for command
[  390.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  390.824000] ide: failed opcode was: unknown
[  390.824000] hda: drive not ready for command
[  390.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  390.824000] ide: failed opcode was: unknown
[  390.824000] hda: drive not ready for command
[  390.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  390.824000] ide: failed opcode was: unknown
[  390.824000] hda: drive not ready for command
[  390.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  390.824000] ide: failed opcode was: unknown
[  390.824000] hda: drive not ready for command
[  392.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  392.824000] ide: failed opcode was: unknown
[  392.824000] hda: drive not ready for command
[  392.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  392.824000] ide: failed opcode was: unknown
[  392.824000] hda: drive not ready for command
[  392.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  392.824000] ide: failed opcode was: unknown
[  392.824000] hda: drive not ready for command
[  392.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  392.824000] ide: failed opcode was: unknown
[  392.824000] hda: drive not ready for command
[  394.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  394.824000] ide: failed opcode was: unknown
[  394.824000] hda: drive not ready for command
[  394.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  394.824000] ide: failed opcode was: unknown
[  394.824000] hda: drive not ready for command
[  394.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  394.824000] ide: failed opcode was: unknown
[  394.824000] hda: drive not ready for command
[  394.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  394.824000] ide: failed opcode was: unknown
[  394.824000] hda: drive not ready for command
[  396.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  396.824000] ide: failed opcode was: unknown
[  396.824000] hda: drive not ready for command
[  396.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  396.824000] ide: failed opcode was: unknown
[  396.824000] hda: drive not ready for command
[  396.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  396.824000] ide: failed opcode was: unknown
[  396.824000] hda: drive not ready for command
[  396.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  396.824000] ide: failed opcode was: unknown
[  396.824000] hda: drive not ready for command
[  398.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  398.824000] ide: failed opcode was: unknown
[  398.824000] hda: drive not ready for command
[  398.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  398.824000] ide: failed opcode was: unknown
[  398.824000] hda: drive not ready for command
[  398.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  398.824000] ide: failed opcode was: unknown
[  398.824000] hda: drive not ready for command
[  398.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  398.824000] ide: failed opcode was: unknown
[  398.824000] hda: drive not ready for command
[  460.824000] hda: irq timeout: status=0x50 { DriveReady SeekComplete }
[  460.824000] ide: failed opcode was: unknown
[  520.824000] hda: irq timeout: status=0x50 { DriveReady SeekComplete }
[  520.824000] ide: failed opcode was: unknown
[  580.824000] hda: irq timeout: status=0x50 { DriveReady SeekComplete }
[  580.824000] ide: failed opcode was: unknown
[  585.824000] hda: irq timeout: status=0x58 { DriveReady SeekComplete DataRequest }
[  585.824000] ide: failed opcode was: unknown
[  585.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  585.824000] ide: failed opcode was: unknown
[  585.824000] hda: drive not ready for command
[  585.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  585.824000] ide: failed opcode was: unknown
[  585.824000] hda: drive not ready for command
[  585.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  585.824000] ide: failed opcode was: unknown
[  585.824000] hda: drive not ready for command
[  585.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  585.824000] ide: failed opcode was: unknown
[  585.824000] hda: drive not ready for command
[  587.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  587.824000] ide: failed opcode was: unknown
[  587.824000] hda: drive not ready for command
[  587.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  587.824000] ide: failed opcode was: unknown
[  587.824000] hda: drive not ready for command
[  587.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  587.824000] ide: failed opcode was: unknown
[  587.824000] hda: drive not ready for command
[  587.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  587.824000] ide: failed opcode was: unknown
[  587.824000] hda: drive not ready for command
[  589.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  589.824000] ide: failed opcode was: unknown
[  589.824000] hda: drive not ready for command
[  589.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  589.824000] ide: failed opcode was: unknown
[  589.824000] hda: drive not ready for command
[  589.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  589.824000] ide: failed opcode was: unknown
[  589.824000] hda: drive not ready for command
[  589.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  589.824000] ide: failed opcode was: unknown
[  589.824000] hda: drive not ready for command
[  591.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  591.824000] ide: failed opcode was: unknown
[  591.824000] hda: drive not ready for command
[  591.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  591.824000] ide: failed opcode was: unknown
[  591.824000] hda: drive not ready for command
[  591.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  591.824000] ide: failed opcode was: unknown
[  591.824000] hda: drive not ready for command
[  591.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  591.824000] ide: failed opcode was: unknown
[  591.824000] hda: drive not ready for command
[  593.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  593.824000] ide: failed opcode was: unknown
[  593.824000] hda: drive not ready for command
[  593.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  593.824000] ide: failed opcode was: unknown
[  593.824000] hda: drive not ready for command
[  593.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  593.824000] ide: failed opcode was: unknown
[  593.824000] hda: drive not ready for command
[  593.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  593.824000] ide: failed opcode was: unknown
[  593.824000] hda: drive not ready for command
[  595.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  595.824000] ide: failed opcode was: unknown
[  595.824000] hda: drive not ready for command
[  595.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  595.824000] ide: failed opcode was: unknown
[  595.824000] hda: drive not ready for command
[  595.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  595.824000] ide: failed opcode was: unknown
[  595.824000] hda: drive not ready for command
[  595.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  595.824000] ide: failed opcode was: unknown
[  595.824000] hda: drive not ready for command
[  597.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  597.824000] ide: failed opcode was: unknown
[  597.824000] hda: drive not ready for command
[  597.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  597.824000] ide: failed opcode was: unknown
[  597.824000] hda: drive not ready for command
[  597.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  597.824000] ide: failed opcode was: unknown
[  597.824000] hda: drive not ready for command
[  597.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  597.824000] ide: failed opcode was: unknown
[  597.824000] hda: drive not ready for command
[  599.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  599.824000] ide: failed opcode was: unknown
[  599.824000] hda: drive not ready for command
[  599.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  599.824000] ide: failed opcode was: unknown
[  599.824000] hda: drive not ready for command
[  599.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  599.824000] ide: failed opcode was: unknown
[  599.824000] hda: drive not ready for command
[  599.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  599.824000] ide: failed opcode was: unknown
[  599.824000] hda: drive not ready for command
[  601.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  601.824000] ide: failed opcode was: unknown
[  601.824000] hda: drive not ready for command
[  601.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  601.824000] ide: failed opcode was: unknown
[  601.824000] hda: drive not ready for command
[  601.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  601.824000] ide: failed opcode was: unknown
[  601.824000] hda: drive not ready for command
[  601.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  601.824000] ide: failed opcode was: unknown
[  601.824000] hda: drive not ready for command
[  603.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  603.824000] ide: failed opcode was: unknown
[  603.824000] hda: drive not ready for command
[  603.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  603.824000] ide: failed opcode was: unknown
[  603.824000] hda: drive not ready for command
[  603.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  603.824000] ide: failed opcode was: unknown
[  603.824000] hda: drive not ready for command
[  603.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  603.824000] ide: failed opcode was: unknown
[  603.824000] hda: drive not ready for command
[  605.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  605.824000] ide: failed opcode was: unknown
[  605.824000] hda: drive not ready for command
[  605.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  605.824000] ide: failed opcode was: unknown
[  605.824000] hda: drive not ready for command
[  605.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  605.824000] ide: failed opcode was: unknown
[  605.824000] hda: drive not ready for command
[  605.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  605.824000] ide: failed opcode was: unknown
[  605.824000] hda: drive not ready for command
[  607.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  607.824000] ide: failed opcode was: unknown
[  607.824000] hda: drive not ready for command
[  607.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  607.824000] ide: failed opcode was: unknown
[  607.824000] hda: drive not ready for command
[  607.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  607.824000] ide: failed opcode was: unknown
[  607.824000] hda: drive not ready for command
[  607.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  607.824000] ide: failed opcode was: unknown
[  607.824000] hda: drive not ready for command
[  609.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  609.824000] ide: failed opcode was: unknown
[  609.824000] hda: drive not ready for command
[  609.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  609.824000] ide: failed opcode was: unknown
[  609.824000] hda: drive not ready for command
[  609.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  609.824000] ide: failed opcode was: unknown
[  609.824000] hda: drive not ready for command
[  609.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  609.824000] ide: failed opcode was: unknown
[  609.824000] hda: drive not ready for command
[  671.824000] hda: irq timeout: status=0x50 { DriveReady SeekComplete }
[  671.824000] ide: failed opcode was: unknown
[  731.824000] hda: irq timeout: status=0x50 { DriveReady SeekComplete }
[  731.824000] ide: failed opcode was: unknown
[  791.824000] hda: irq timeout: status=0x50 { DriveReady SeekComplete }
[  791.824000] ide: failed opcode was: unknown
[  851.824000] hda: irq timeout: status=0x50 { DriveReady SeekComplete }
[  851.824000] ide: failed opcode was: unknown

```


charles@charles-desktop:~$ sudo lspci -v
```

00:00.0 Host bridge: ATI Technologies Inc Unknown device 7910
        Subsystem: ASUSTeK Computer Inc. Unknown device 826d
        Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc Unknown device 7912 (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 99
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fdb00000-fdcfffff
        Prefetchable memory behind bridge: 00000000f0000000-00000000f7ffffff
        Capabilities: [44] HyperTransport: MSI Mapping
        Capabilities: [b0] Subsystem: ATI Technologies Inc Unknown device 7912

00:07.0 PCI bridge: ATI Technologies Inc Unknown device 7917 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fda00000-fdafffff
        Prefetchable memory behind bridge: 00000000fdf00000-00000000fdffffff
        Capabilities: [50] Power Management version 3
        Capabilities: [58] Express Root Port (Slot-) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [b0] Subsystem: ASUSTeK Computer Inc. Unknown device 826d
        Capabilities: [b8] HyperTransport: MSI Mapping

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01 [AHCI 1.0])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81ef
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 20
        I/O ports at ff00 [size=8]
        I/O ports at fe00 [size=4]
        I/O ports at fd00 [size=8]
        I/O ports at fc00 [size=4]
        I/O ports at fb00 [size=16]
        Memory at fe02f000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [60] Power Management version 2
        Capabilities: [70] #12 [0010]

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81ef
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at fe02e000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81ef
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81ef
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
        Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81ef
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81ef
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
        Memory at fe02a000 (32-bit, non-prefetchable) [size=4K]

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81ef
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        Memory at fe029000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [c0] Power Management version 2
        Capabilities: [e4] Debug port

00:14.0 SMBus: ATI Technologies Inc SB600 SMBus (rev 13)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81ef
        Flags: 66MHz, medium devsel
        I/O ports at 0b00 [size=16]
        Memory at fe028000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [b0] HyperTransport: MSI Mapping

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 82 [Master PriP])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81ef
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at f900 [size=16]
        Capabilities: [70] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

00:14.2 Audio device: ATI Technologies Inc SB600 Azalia
        Subsystem: ASUSTeK Computer Inc. Unknown device 8249
        Flags: bus master, slow devsel, latency 64, IRQ 17
        Memory at fe020000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
        Subsystem: ASUSTeK Computer Inc. Unknown device 81ef
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SB600 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
        Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=64
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fde00000-fdefffff
        Prefetchable memory behind bridge: fdd00000-fddfffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel
        Capabilities: [f0] #0f [0010]

01:05.0 VGA compatible controller: ATI Technologies Inc Unknown device 791e (prog-if 00 [VGA])
        Subsystem: ASUSTeK Computer Inc. Unknown device 826d
        Flags: bus master, fast devsel, latency 64, IRQ 19
        Memory at f0000000 (64-bit, prefetchable) [size=128M]
        Memory at fdcf0000 (64-bit, non-prefetchable) [size=64K]
        I/O ports at de00 [size=256]
        Memory at fdb00000 (32-bit, non-prefetchable) [size=1M]
        Capabilities: [50] Power Management version 2
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81aa
        Flags: bus master, fast devsel, latency 0, IRQ 16
        I/O ports at ee00 [size=256]
        Memory at fdaff000 (64-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at fdf00000 [disabled] [size=128K]
        Capabilities: [40] Power Management version 2
        Capabilities: [48] Vital Product Data
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
        Capabilities: [60] Express Endpoint IRQ 0
        Capabilities: [84] Vendor Specific Information

```

In Device Manager, 
SB600 IDE
   IDE device (master)
       HL-DT-STDVD-RAM GSA-H54A

I do see my drive!!!



and also
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=c7ef857d-0cb7-4fc1-8b7d-2263cd133de4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=f7614a41-5dd2-4d19-8dfe-0c5694c4df2b /storage        ext3    defaults        0       2
# /dev/sda4
UUID=028B-3D8D  /windows        vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=706e1b6c-9ef1-49ff-927b-11725a16605d none            swap    sw              0       0
#/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0


Please help!!!!!!!!! 
Thanks!

---

### Post by UK-Wobbie on 2007-08-16
> **boom2k1 said:**
> Hello all,
I just got my new computer and I am having trouble using my LG 18x dvdrw. I used this drive to install Ubuntu, but after Ubuntu is installed, the drive won't work in Linux! (I found out as my dad was trying to test my Linux!!!! --How pissed off he can say again that a lot of things doesn't work in LInux!) A strange thing is I do see the CD-Rom Disc icon on the desktop. Right click on it brings up the menu where I can press Eject. It doesn't do anything!

I use a Asus M2A-VM motherboard on AMD x2 4000+ with a SATA harddrive and the IDE LG18x dvdrw.

Anyway, I recall as I was starting up Ubuntu, I sometimes see the error log
about IDE fails to boot up. Following some of the diagnosis tool I found from other posts:

dmesg
```
[   67.812000] ide: failed opcode was: unknown
[   67.812000] hda: drive not ready for command
[   67.812000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[   67.812000] ide: failed opcode was: unknown
[   67.812000] hda: drive not ready for command
[   67.812000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[   67.812000] ide: failed opcode was: unknown
[   67.812000] hda: drive not ready for command
[   68.956000] vmnet1: no IPv6 routers present
[   69.084000] vmnet8: no IPv6 routers present
[   69.612000] eth0: no IPv6 routers present
[  129.812000] hda: irq timeout: status=0x50 { DriveReady SeekComplete }
[  129.812000] ide: failed opcode was: unknown
[  189.820000] hda: irq timeout: status=0x50 { DriveReady SeekComplete }
[  189.820000] ide: failed opcode was: unknown
[  249.820000] hda: irq timeout: status=0x50 { DriveReady SeekComplete }
[  249.820000] ide: failed opcode was: unknown
[  309.820000] hda: irq timeout: status=0x50 { DriveReady SeekComplete }
[  309.820000] ide: failed opcode was: unknown
[  369.820000] hda: irq timeout: status=0x50 { DriveReady SeekComplete }
[  369.820000] ide: failed opcode was: unknown
[  374.820000] hda: irq timeout: status=0x58 { DriveReady SeekComplete DataRequest }
[  374.820000] ide: failed opcode was: unknown
[  374.820000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  374.820000] ide: failed opcode was: unknown
[  374.820000] hda: drive not ready for command
[  374.820000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  374.820000] ide: failed opcode was: unknown
[  374.820000] hda: drive not ready for command
[  374.820000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  374.820000] ide: failed opcode was: unknown
[  374.820000] hda: drive not ready for command
[  374.820000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  374.820000] ide: failed opcode was: unknown
[  374.820000] hda: drive not ready for command
[  374.820000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  374.820000] ide: failed opcode was: unknown
[  374.820000] hda: drive not ready for command
[  374.848000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  374.848000] ide: failed opcode was: unknown
[  374.848000] hda: drive not ready for command
[  374.848000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  374.848000] ide: failed opcode was: unknown
[  374.848000] hda: drive not ready for command
[  374.848000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  374.848000] ide: failed opcode was: unknown
[  374.848000] hda: drive not ready for command
[  374.848000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  374.848000] ide: failed opcode was: unknown
[  374.848000] hda: drive not ready for command
[  374.868000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  374.868000] ide: failed opcode was: unknown
[  374.868000] hda: drive not ready for command
[  374.872000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  374.872000] ide: failed opcode was: unknown
[  374.872000] hda: drive not ready for command
[  374.872000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  374.872000] ide: failed opcode was: unknown
[  374.872000] hda: drive not ready for command
[  374.872000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  374.872000] ide: failed opcode was: unknown
[  374.872000] hda: drive not ready for command
[  374.872000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  374.872000] ide: failed opcode was: unknown
[  374.872000] hda: drive not ready for command
[  376.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  376.824000] ide: failed opcode was: unknown
[  376.824000] hda: drive not ready for command
[  376.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  376.824000] ide: failed opcode was: unknown
[  376.824000] hda: drive not ready for command
[  376.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  376.824000] ide: failed opcode was: unknown
[  376.824000] hda: drive not ready for command
[  376.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  376.824000] ide: failed opcode was: unknown
[  376.824000] hda: drive not ready for command
[  378.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  378.824000] ide: failed opcode was: unknown
[  378.824000] hda: drive not ready for command
[  378.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  378.824000] ide: failed opcode was: unknown
[  378.824000] hda: drive not ready for command
[  378.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  378.824000] ide: failed opcode was: unknown
[  378.824000] hda: drive not ready for command
[  378.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  378.824000] ide: failed opcode was: unknown
[  378.824000] hda: drive not ready for command
[  380.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  380.824000] ide: failed opcode was: unknown
[  380.824000] hda: drive not ready for command
[  380.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  380.824000] ide: failed opcode was: unknown
[  380.824000] hda: drive not ready for command
[  380.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  380.824000] ide: failed opcode was: unknown
[  380.824000] hda: drive not ready for command
[  380.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  380.824000] ide: failed opcode was: unknown
[  380.824000] hda: drive not ready for command
[  382.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  382.824000] ide: failed opcode was: unknown
[  382.824000] hda: drive not ready for command
[  382.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  382.824000] ide: failed opcode was: unknown
[  382.824000] hda: drive not ready for command
[  382.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  382.824000] ide: failed opcode was: unknown
[  382.824000] hda: drive not ready for command
[  382.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  382.824000] ide: failed opcode was: unknown
[  382.824000] hda: drive not ready for command
[  384.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  384.824000] ide: failed opcode was: unknown
[  384.824000] hda: drive not ready for command
[  384.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  384.824000] ide: failed opcode was: unknown
[  384.824000] hda: drive not ready for command
[  384.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  384.824000] ide: failed opcode was: unknown
[  384.824000] hda: drive not ready for command
[  384.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  384.824000] ide: failed opcode was: unknown
[  384.824000] hda: drive not ready for command
[  386.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  386.824000] ide: failed opcode was: unknown
[  386.824000] hda: drive not ready for command
[  386.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  386.824000] ide: failed opcode was: unknown
[  386.824000] hda: drive not ready for command
[  386.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  386.824000] ide: failed opcode was: unknown
[  386.824000] hda: drive not ready for command
[  386.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  386.824000] ide: failed opcode was: unknown
[  386.824000] hda: drive not ready for command
[  388.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  388.824000] ide: failed opcode was: unknown
[  388.824000] hda: drive not ready for command
[  388.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  388.824000] ide: failed opcode was: unknown
[  388.824000] hda: drive not ready for command
[  388.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  388.824000] ide: failed opcode was: unknown
[  388.824000] hda: drive not ready for command
[  388.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  388.824000] ide: failed opcode was: unknown
[  388.824000] hda: drive not ready for command
[  390.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  390.824000] ide: failed opcode was: unknown
[  390.824000] hda: drive not ready for command
[  390.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  390.824000] ide: failed opcode was: unknown
[  390.824000] hda: drive not ready for command
[  390.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  390.824000] ide: failed opcode was: unknown
[  390.824000] hda: drive not ready for command
[  390.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  390.824000] ide: failed opcode was: unknown
[  390.824000] hda: drive not ready for command
[  392.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  392.824000] ide: failed opcode was: unknown
[  392.824000] hda: drive not ready for command
[  392.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  392.824000] ide: failed opcode was: unknown
[  392.824000] hda: drive not ready for command
[  392.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  392.824000] ide: failed opcode was: unknown
[  392.824000] hda: drive not ready for command
[  392.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  392.824000] ide: failed opcode was: unknown
[  392.824000] hda: drive not ready for command
[  394.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  394.824000] ide: failed opcode was: unknown
[  394.824000] hda: drive not ready for command
[  394.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  394.824000] ide: failed opcode was: unknown
[  394.824000] hda: drive not ready for command
[  394.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  394.824000] ide: failed opcode was: unknown
[  394.824000] hda: drive not ready for command
[  394.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  394.824000] ide: failed opcode was: unknown
[  394.824000] hda: drive not ready for command
[  396.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  396.824000] ide: failed opcode was: unknown
[  396.824000] hda: drive not ready for command
[  396.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  396.824000] ide: failed opcode was: unknown
[  396.824000] hda: drive not ready for command
[  396.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  396.824000] ide: failed opcode was: unknown
[  396.824000] hda: drive not ready for command
[  396.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  396.824000] ide: failed opcode was: unknown
[  396.824000] hda: drive not ready for command
[  398.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  398.824000] ide: failed opcode was: unknown
[  398.824000] hda: drive not ready for command
[  398.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  398.824000] ide: failed opcode was: unknown
[  398.824000] hda: drive not ready for command
[  398.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  398.824000] ide: failed opcode was: unknown
[  398.824000] hda: drive not ready for command
[  398.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  398.824000] ide: failed opcode was: unknown
[  398.824000] hda: drive not ready for command
[  460.824000] hda: irq timeout: status=0x50 { DriveReady SeekComplete }
[  460.824000] ide: failed opcode was: unknown
[  520.824000] hda: irq timeout: status=0x50 { DriveReady SeekComplete }
[  520.824000] ide: failed opcode was: unknown
[  580.824000] hda: irq timeout: status=0x50 { DriveReady SeekComplete }
[  580.824000] ide: failed opcode was: unknown
[  585.824000] hda: irq timeout: status=0x58 { DriveReady SeekComplete DataRequest }
[  585.824000] ide: failed opcode was: unknown
[  585.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  585.824000] ide: failed opcode was: unknown
[  585.824000] hda: drive not ready for command
[  585.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  585.824000] ide: failed opcode was: unknown
[  585.824000] hda: drive not ready for command
[  585.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  585.824000] ide: failed opcode was: unknown
[  585.824000] hda: drive not ready for command
[  585.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  585.824000] ide: failed opcode was: unknown
[  585.824000] hda: drive not ready for command
[  587.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  587.824000] ide: failed opcode was: unknown
[  587.824000] hda: drive not ready for command
[  587.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  587.824000] ide: failed opcode was: unknown
[  587.824000] hda: drive not ready for command
[  587.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  587.824000] ide: failed opcode was: unknown
[  587.824000] hda: drive not ready for command
[  587.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  587.824000] ide: failed opcode was: unknown
[  587.824000] hda: drive not ready for command
[  589.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  589.824000] ide: failed opcode was: unknown
[  589.824000] hda: drive not ready for command
[  589.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  589.824000] ide: failed opcode was: unknown
[  589.824000] hda: drive not ready for command
[  589.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  589.824000] ide: failed opcode was: unknown
[  589.824000] hda: drive not ready for command
[  589.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  589.824000] ide: failed opcode was: unknown
[  589.824000] hda: drive not ready for command
[  591.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  591.824000] ide: failed opcode was: unknown
[  591.824000] hda: drive not ready for command
[  591.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  591.824000] ide: failed opcode was: unknown
[  591.824000] hda: drive not ready for command
[  591.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  591.824000] ide: failed opcode was: unknown
[  591.824000] hda: drive not ready for command
[  591.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  591.824000] ide: failed opcode was: unknown
[  591.824000] hda: drive not ready for command
[  593.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  593.824000] ide: failed opcode was: unknown
[  593.824000] hda: drive not ready for command
[  593.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  593.824000] ide: failed opcode was: unknown
[  593.824000] hda: drive not ready for command
[  593.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  593.824000] ide: failed opcode was: unknown
[  593.824000] hda: drive not ready for command
[  593.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  593.824000] ide: failed opcode was: unknown
[  593.824000] hda: drive not ready for command
[  595.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  595.824000] ide: failed opcode was: unknown
[  595.824000] hda: drive not ready for command
[  595.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  595.824000] ide: failed opcode was: unknown
[  595.824000] hda: drive not ready for command
[  595.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  595.824000] ide: failed opcode was: unknown
[  595.824000] hda: drive not ready for command
[  595.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  595.824000] ide: failed opcode was: unknown
[  595.824000] hda: drive not ready for command
[  597.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  597.824000] ide: failed opcode was: unknown
[  597.824000] hda: drive not ready for command
[  597.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  597.824000] ide: failed opcode was: unknown
[  597.824000] hda: drive not ready for command
[  597.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  597.824000] ide: failed opcode was: unknown
[  597.824000] hda: drive not ready for command
[  597.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  597.824000] ide: failed opcode was: unknown
[  597.824000] hda: drive not ready for command
[  599.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  599.824000] ide: failed opcode was: unknown
[  599.824000] hda: drive not ready for command
[  599.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  599.824000] ide: failed opcode was: unknown
[  599.824000] hda: drive not ready for command
[  599.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  599.824000] ide: failed opcode was: unknown
[  599.824000] hda: drive not ready for command
[  599.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  599.824000] ide: failed opcode was: unknown
[  599.824000] hda: drive not ready for command
[  601.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  601.824000] ide: failed opcode was: unknown
[  601.824000] hda: drive not ready for command
[  601.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  601.824000] ide: failed opcode was: unknown
[  601.824000] hda: drive not ready for command
[  601.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  601.824000] ide: failed opcode was: unknown
[  601.824000] hda: drive not ready for command
[  601.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  601.824000] ide: failed opcode was: unknown
[  601.824000] hda: drive not ready for command
[  603.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  603.824000] ide: failed opcode was: unknown
[  603.824000] hda: drive not ready for command
[  603.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  603.824000] ide: failed opcode was: unknown
[  603.824000] hda: drive not ready for command
[  603.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  603.824000] ide: failed opcode was: unknown
[  603.824000] hda: drive not ready for command
[  603.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  603.824000] ide: failed opcode was: unknown
[  603.824000] hda: drive not ready for command
[  605.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  605.824000] ide: failed opcode was: unknown
[  605.824000] hda: drive not ready for command
[  605.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  605.824000] ide: failed opcode was: unknown
[  605.824000] hda: drive not ready for command
[  605.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  605.824000] ide: failed opcode was: unknown
[  605.824000] hda: drive not ready for command
[  605.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  605.824000] ide: failed opcode was: unknown
[  605.824000] hda: drive not ready for command
[  607.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  607.824000] ide: failed opcode was: unknown
[  607.824000] hda: drive not ready for command
[  607.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  607.824000] ide: failed opcode was: unknown
[  607.824000] hda: drive not ready for command
[  607.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  607.824000] ide: failed opcode was: unknown
[  607.824000] hda: drive not ready for command
[  607.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  607.824000] ide: failed opcode was: unknown
[  607.824000] hda: drive not ready for command
[  609.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  609.824000] ide: failed opcode was: unknown
[  609.824000] hda: drive not ready for command
[  609.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  609.824000] ide: failed opcode was: unknown
[  609.824000] hda: drive not ready for command
[  609.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  609.824000] ide: failed opcode was: unknown
[  609.824000] hda: drive not ready for command
[  609.824000] hda: status error: status=0x58 { DriveReady SeekComplete DataRequest }
[  609.824000] ide: failed opcode was: unknown
[  609.824000] hda: drive not ready for command
[  671.824000] hda: irq timeout: status=0x50 { DriveReady SeekComplete }
[  671.824000] ide: failed opcode was: unknown
[  731.824000] hda: irq timeout: status=0x50 { DriveReady SeekComplete }
[  731.824000] ide: failed opcode was: unknown
[  791.824000] hda: irq timeout: status=0x50 { DriveReady SeekComplete }
[  791.824000] ide: failed opcode was: unknown
[  851.824000] hda: irq timeout: status=0x50 { DriveReady SeekComplete }
[  851.824000] ide: failed opcode was: unknown

```


charles@charles-desktop:~$ sudo lspci -v
```

00:00.0 Host bridge: ATI Technologies Inc Unknown device 7910
        Subsystem: ASUSTeK Computer Inc. Unknown device 826d
        Flags: bus master, 66MHz, medium devsel, latency 64

00:01.0 PCI bridge: ATI Technologies Inc Unknown device 7912 (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 99
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=68
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fdb00000-fdcfffff
        Prefetchable memory behind bridge: 00000000f0000000-00000000f7ffffff
        Capabilities: [44] HyperTransport: MSI Mapping
        Capabilities: [b0] Subsystem: ATI Technologies Inc Unknown device 7912

00:07.0 PCI bridge: ATI Technologies Inc Unknown device 7917 (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        I/O behind bridge: 0000e000-0000efff
        Memory behind bridge: fda00000-fdafffff
        Prefetchable memory behind bridge: 00000000fdf00000-00000000fdffffff
        Capabilities: [50] Power Management version 3
        Capabilities: [58] Express Root Port (Slot-) IRQ 0
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
        Capabilities: [b0] Subsystem: ASUSTeK Computer Inc. Unknown device 826d
        Capabilities: [b8] HyperTransport: MSI Mapping

00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA (prog-if 01 [AHCI 1.0])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81ef
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 20
        I/O ports at ff00 [size=8]
        I/O ports at fe00 [size=4]
        I/O ports at fd00 [size=8]
        I/O ports at fc00 [size=4]
        I/O ports at fb00 [size=16]
        Memory at fe02f000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [60] Power Management version 2
        Capabilities: [70] #12 [0010]

00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81ef
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        Memory at fe02e000 (32-bit, non-prefetchable) [size=4K]

00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81ef
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at fe02d000 (32-bit, non-prefetchable) [size=4K]

00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81ef
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
        Memory at fe02c000 (32-bit, non-prefetchable) [size=4K]

00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81ef
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
        Memory at fe02b000 (32-bit, non-prefetchable) [size=4K]

00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4) (prog-if 10 [OHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81ef
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
        Memory at fe02a000 (32-bit, non-prefetchable) [size=4K]

00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI) (prog-if 20 [EHCI])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81ef
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 16
        Memory at fe029000 (32-bit, non-prefetchable) [size=256]
        Capabilities: [c0] Power Management version 2
        Capabilities: [e4] Debug port

00:14.0 SMBus: ATI Technologies Inc SB600 SMBus (rev 13)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81ef
        Flags: 66MHz, medium devsel
        I/O ports at 0b00 [size=16]
        Memory at fe028000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: [b0] HyperTransport: MSI Mapping

00:14.1 IDE interface: ATI Technologies Inc SB600 IDE (prog-if 82 [Master PriP])
        Subsystem: ASUSTeK Computer Inc. Unknown device 81ef
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 17
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at f900 [size=16]
        Capabilities: [70] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-

00:14.2 Audio device: ATI Technologies Inc SB600 Azalia
        Subsystem: ASUSTeK Computer Inc. Unknown device 8249
        Flags: bus master, slow devsel, latency 64, IRQ 17
        Memory at fe020000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
        Subsystem: ASUSTeK Computer Inc. Unknown device 81ef
        Flags: bus master, 66MHz, medium devsel, latency 0

00:14.4 PCI bridge: ATI Technologies Inc SB600 PCI to PCI Bridge (prog-if 01 [Subtractive decode])
        Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=64
        I/O behind bridge: 0000c000-0000cfff
        Memory behind bridge: fde00000-fdefffff
        Prefetchable memory behind bridge: fdd00000-fddfffff

00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
        Flags: fast devsel
        Capabilities: [80] HyperTransport: Host or Secondary Interface

00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
        Flags: fast devsel

00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
        Flags: fast devsel

00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
        Flags: fast devsel
        Capabilities: [f0] #0f [0010]

01:05.0 VGA compatible controller: ATI Technologies Inc Unknown device 791e (prog-if 00 [VGA])
        Subsystem: ASUSTeK Computer Inc. Unknown device 826d
        Flags: bus master, fast devsel, latency 64, IRQ 19
        Memory at f0000000 (64-bit, prefetchable) [size=128M]
        Memory at fdcf0000 (64-bit, non-prefetchable) [size=64K]
        I/O ports at de00 [size=256]
        Memory at fdb00000 (32-bit, non-prefetchable) [size=1M]
        Capabilities: [50] Power Management version 2
        Capabilities: [80] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 01)
        Subsystem: ASUSTeK Computer Inc. Unknown device 81aa
        Flags: bus master, fast devsel, latency 0, IRQ 16
        I/O ports at ee00 [size=256]
        Memory at fdaff000 (64-bit, non-prefetchable) [size=4K]
        [virtual] Expansion ROM at fdf00000 [disabled] [size=128K]
        Capabilities: [40] Power Management version 2
        Capabilities: [48] Vital Product Data
        Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable-
        Capabilities: [60] Express Endpoint IRQ 0
        Capabilities: [84] Vendor Specific Information

```

In Device Manager, 
SB600 IDE
   IDE device (master)
       HL-DT-STDVD-RAM GSA-H54A

I do see my drive!!!



and also
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=c7ef857d-0cb7-4fc1-8b7d-2263cd133de4 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=f7614a41-5dd2-4d19-8dfe-0c5694c4df2b /storage        ext3    defaults        0       2
# /dev/sda4
UUID=028B-3D8D  /windows        vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=706e1b6c-9ef1-49ff-927b-11725a16605d none            swap    sw              0       0
#/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0


Please help!!!!!!!!! 
Thanks!

It sounds mad :lolflag: If i was you i will restill Ubuntu.
It may be that the CD drive as not been install right when Ubuntu was getting instilled lol
Or that Ubuntu as not got the right pluggings for the drive :confused:

I will still go for restill Ubuntu. :) And hope for the best!

---

### Post by boom2k1 on 2007-08-16
thanks.. are there any other ideas?

---

