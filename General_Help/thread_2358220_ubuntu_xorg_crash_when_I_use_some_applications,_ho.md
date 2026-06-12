---
title: "ubuntu xorg crash when I use some applications, how to troubleshoot ?"
date: 2017-04-10
forum: General Help
---

### Post by tuxmobil on 2017-04-10
hi

When I share my screen through skype (v4.3.0.37) I always have a crash, this happens also when I use the IDE webstorm used to write js code (v2016.3).
This is probably driver issue but how to troubleshoot that ?

this is the output of uname -a command:
```
Linux vegito 3.19.0-33-generic #38~14.04.1-Ubuntu SMP Fri Nov 6 18:17:28 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```
This version of ubuntu has been presintalled by dell when I purchased my laptop, the driver used for the graphcal card is the proprietary one provided by nvidia.

```
 cat /var/log/Xorg.0.log | grep EE
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     5.759] (EE) AIGLX error: Calling driver entry point failed
[     5.759] (EE) AIGLX: reverting to software rendering
[     5.785] (EE) BUG: triggered 'if (axnum >= dev->valuator->numAxes)'
[     5.786] (EE) BUG: ../../Xi/exevents.c:2086 in InitValuatorAxisStruct()
[     5.786] (EE) 
[     5.786] (EE) Backtrace:
[     5.786] (EE) 0: /usr/bin/X (xorg_backtrace+0x48) [0x7f828255ded8]
[     5.786] (EE) 1: /usr/bin/X (InitValuatorAxisStruct+0x68) [0x7f82824f0398]
[     5.786] (EE) 2: /usr/lib/xorg/modules/input/evdev_drv.so (0x7f82721f4000+0x4e70) [0x7f82721f8e70]
[     5.786] (EE) 3: /usr/lib/xorg/modules/input/evdev_drv.so (0x7f82721f4000+0x5326) [0x7f82721f9326]
[     5.786] (EE) 4: /usr/lib/xorg/modules/input/evdev_drv.so (0x7f82721f4000+0x6f90) [0x7f82721faf90]
[     5.786] (EE) 5: /usr/bin/X (ActivateDevice+0x37) [0x7f8282402257]
[     5.786] (EE) 6: /usr/bin/X (0x7f82823b9000+0x9f5c6) [0x7f82824585c6]
[     5.786] (EE) 7: /usr/bin/X (0x7f82823b9000+0xb580b) [0x7f828246e80b]
[     5.786] (EE) 8: /usr/bin/X (0x7f82823b9000+0xb5d83) [0x7f828246ed83]
[     5.786] (EE) 9: /usr/bin/X (config_init+0x9) [0x7f828246d8c9]
[     5.786] (EE) 10: /usr/bin/X (InitInput+0xab) [0x7f828244c2ab]
[     5.786] (EE) 11: /usr/bin/X (0x7f82823b9000+0x574a9) [0x7f82824104a9]
[     5.786] (EE) 12: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xf5) [0x7f8280559f45]
[     5.786] (EE) 13: /usr/bin/X (0x7f82823b9000+0x42a5e) [0x7f82823fba5e]
[     5.786] (EE) 
```

I added few screen shots below, may be it can help, can you please let me know how I can troubleshoot such issue ?

thanks

[ATTACH=CONFIG]274510[/ATTACH]
[ATTACH=CONFIG]274511[/ATTACH][ATTACH=CONFIG]274512[/ATTACH]

---

