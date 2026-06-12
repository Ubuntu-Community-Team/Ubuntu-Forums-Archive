---
title: "please help enabling rtc"
date: 2006-12-28
forum: General Help
---

### Post by albesan on 2006-12-28
Hello team,

Does anybody know how to enable the real time clock in ubuntu?

I keep reading that it is there by defult but I keep getting this error:

open /dev/rtc: No such file or directory
open /dev/misc/rtc: No such file or directory

any ideas?

thanks

a.

---

### Post by beow on 2006-12-28
Exactly what do you want to do? The "real time clock" usually refers to the hw clock built in to your computer. If you in a terminal window types 'date' and you get something like ' Thu Dec 28 22:04:10 CET 2006' in return your hw or real time clock proibably works.

If you want to synchronize your computer clock to a network time server, it is done from the System > Administration > Time and Date menu item.

---

### Post by albesan on 2006-12-28
hello, thanks for the reply.

ok, I tried "date" and I got this:

 date
Fri Dec 29 00:46:02 GMT 2006

So I assume the clock is working.

What I am trying to do is compile a program called QLC, which deals with lighting.

After make it and installing it when I try to run it I get this output:

qlc
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
open /dev/rtc: No such file or directory
open /dev/misc/rtc: No such file or directory

So I did a search for rtc and got something like this:

/lib/modules/2.6.15-26-powerpc/kernel/drivers/i2c/chips/rtc8564.ko
/lib/modules/2.6.15-27-powerpc/kernel/drivers/i2c/chips/rtc8564.ko
/usr/include/linux/rtc.h
/usr/src/linux-headers-2.6.15-26-powerpc/include/linux/rtc.h
/usr/src/linux-headers-2.6.15-26-powerpc/include/config/gen/rtc
/usr/src/linux-headers-2.6.15-26-powerpc/include/config/gen/rtc/module.h
/usr/src/linux-headers-2.6.15-26-powerpc/include/config/gen/rtc/x.h
/usr/src/linux-headers-2.6.15-26-powerpc/include/config/sensors/rtc8564
/usr/src/linux-headers-2.6.15-26-powerpc/include/config/sensors/rtc8564/module.h/usr/src/linux-headers-2.6.15-26-powerpc/include/config/rtc
/usr/src/linux-headers-2.6.15-26-powerpc/include/config/rtc/x1205
/usr/src/linux-headers-2.6.15-26-powerpc/include/config/rtc/x1205/i2c
/usr/src/linux-headers-2.6.15-26-powerpc/include/config/rtc/x1205/i2c/module.h
/usr/src/linux-headers-2.6.15-26/include/asm-alpha/rtc.h
/usr/src/linux-headers-2.6.15-26/include/asm-arm/rtc.h
/usr/src/linux-headers-2.6.15-26/include/asm-cris/rtc.h
/usr/src/linux-headers-2.6.15-26/include/asm-generic/rtc.h
/usr/src/linux-headers-2.6.15-26/include/asm-i386/rtc.h
/usr/src/linux-headers-2.6.15-26/include/asm-m32r/rtc.h
/usr/src/linux-headers-2.6.15-26/include/asm-m68k/rtc.h
/usr/src/linux-headers-2.6.15-26/include/asm-mips/rtc.h
/usr/src/linux-headers-2.6.15-26/include/asm-parisc/rtc.h
/usr/src/linux-headers-2.6.15-26/include/asm-powerpc/rtc.h
/usr/src/linux-headers-2.6.15-26/include/asm-ppc/rtc.h
/usr/src/linux-headers-2.6.15-26/include/asm-sh/cpu-sh3/rtc.h
/usr/src/linux-headers-2.6.15-26/include/asm-sh/cpu-sh4/rtc.h
/usr/src/linux-headers-2.6.15-26/include/asm-sh/rtc.h
/usr/src/linux-headers-2.6.15-26/include/asm-sparc/rtc.h
/usr/src/linux-headers-2.6.15-26/include/asm-sparc64/rtc.h
/usr/src/linux-headers-2.6.15-26/include/asm-x86_64/rtc.h
/usr/src/linux-headers-2.6.15-26/include/linux/rtc.h
/usr/src/linux-headers-2.6.15-26/include/config/gen/rtc.h
/usr/src/linux-headers-2.6.15-26/include/config/gen/rtc
/usr/src/linux-headers-2.6.15-26/include/config/gen/rtc/x.h
/usr/src/linux-headers-2.6.15-26/include/config/sensors/rtc8564.h
/usr/src/linux-headers-2.6.15-26/include/config/rtc
/usr/src/linux-headers-2.6.15-26/include/config/rtc/x1205
/usr/src/linux-headers-2.6.15-26/include/config/rtc/x1205/i2c.h
/usr/src/linux-headers-2.6.15-27-powerpc/include/linux/rtc.h
/usr/src/linux-headers-2.6.15-27-powerpc/include/config/gen/rtc
/usr/src/linux-headers-2.6.15-27-powerpc/include/config/gen/rtc/module.h
/usr/src/linux-headers-2.6.15-27-powerpc/include/config/gen/rtc/x.h
/usr/src/linux-headers-2.6.15-27-powerpc/include/config/sensors/rtc8564
/usr/src/linux-headers-2.6.15-27-powerpc/include/config/sensors/rtc8564/module.h/usr/src/linux-headers-2.6.15-27-powerpc/include/config/rtc
/usr/src/linux-headers-2.6.15-27-powerpc/include/config/rtc/x1205
/usr/src/linux-headers-2.6.15-27-powerpc/include/config/rtc/x1205/i2c
/usr/src/linux-headers-2.6.15-27-powerpc/include/config/rtc/x1205/i2c/module.h
/usr/src/linux-headers-2.6.15-27/include/asm-alpha/rtc.h
/usr/src/linux-headers-2.6.15-27/include/asm-arm/rtc.h
/usr/src/linux-headers-2.6.15-27/include/asm-cris/rtc.h
/usr/src/linux-headers-2.6.15-27/include/asm-generic/rtc.h
/usr/src/linux-headers-2.6.15-27/include/asm-i386/rtc.h
/usr/src/linux-headers-2.6.15-27/include/asm-m32r/rtc.h
/usr/src/linux-headers-2.6.15-27/include/asm-m68k/rtc.h
/usr/src/linux-headers-2.6.15-27/include/asm-mips/rtc.h
/usr/src/linux-headers-2.6.15-27/include/asm-parisc/rtc.h
/usr/src/linux-headers-2.6.15-27/include/asm-powerpc/rtc.h
/usr/src/linux-headers-2.6.15-27/include/asm-ppc/rtc.h
/usr/src/linux-headers-2.6.15-27/include/asm-sh/cpu-sh3/rtc.h
/usr/src/linux-headers-2.6.15-27/include/asm-sh/cpu-sh4/rtc.h
/usr/src/linux-headers-2.6.15-27/include/asm-sh/rtc.h
/usr/src/linux-headers-2.6.15-27/include/asm-sparc/rtc.h
/usr/src/linux-headers-2.6.15-27/include/asm-sparc64/rtc.h
/usr/src/linux-headers-2.6.15-27/include/asm-x86_64/rtc.h
/usr/src/linux-headers-2.6.15-27/include/linux/rtc.h
/usr/src/linux-headers-2.6.15-27/include/config/gen/rtc.h
/usr/src/linux-headers-2.6.15-27/include/config/gen/rtc
/usr/src/linux-headers-2.6.15-27/include/config/gen/rtc/x.h
/usr/src/linux-headers-2.6.15-27/include/config/sensors/rtc8564.h
/usr/src/linux-headers-2.6.15-27/include/config/rtc
/usr/src/linux-headers-2.6.15-27/include/config/rtc/x1205
/usr/src/linux-headers-2.6.15-27/include/config/rtc/x1205/i2c.h


Now, what I don't know how to do is how to make that /dev/rtc and /dev/misc/rtc exist on my system. This might be really obvious for some of the advanced user but I'm quite new to linux and totally lost.

Thanks again for your help.

a.

---

