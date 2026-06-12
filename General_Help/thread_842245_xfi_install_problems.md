---
title: "xfi install problems"
date: 2008-06-27
forum: General Help
---

### Post by mattysp on 2008-06-27
after some digging and plenty of time searching for the right tool i found my sound drivers ( alto only in beta ) and tried installing them all goes fine until i get error messages ( 2 of them ) i think im missing some crucial packages for the drivers to install.

the install log reads:


make -f /tmp/xfisrc/Makefile.build
make[1]: Entering directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers'
cd /tmp/xfisrc/src/utils/alsaver; make clean
make[2]: Entering directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/utils/alsaver'
rm -f alsaver
make[2]: Leaving directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/utils/alsaver'
rm -f alsaver
cd /tmp/xfisrc/src/ossrv; make clean
make[2]: Entering directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/ossrv'
rm -rf ctossrv_main.o LinuxReg.o LinuxSys.o osutils.o   *.o *.ko *.o_shipped *.mod.c *~ .*cmd .tmp_versions .depend Module.symvers
make[2]: Leaving directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/ossrv'
rm -f ctossrv.ko
cd /tmp/xfisrc/src/emupia; make clean
make[2]: Entering directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/emupia'
rm -rf emupia_guids.o emupia_main.o   *.o *.ko *.o_shipped *.mod.c *~ .*cmd .tmp_versions .depend Module.symvers
make[2]: Leaving directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/emupia'
rm -f emupia.ko
cd /tmp/xfisrc/src/sfman; make clean
make[2]: Entering directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/sfman'
rm -rf ctsfman_main.o   *.o *.ko *.o_shipped *.mod.c *~ .*cmd .tmp_versions .depend Module.symvers
make[2]: Leaving directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/sfman'
rm -f ctsfman.ko
cd /tmp/xfisrc/src/haxfi; make clean
make[2]: Entering directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/haxfi'
rm -rf haxfi_main.o   *.o *.ko *.o_shipped *.mod.c *~ .*cmd .tmp_versions .depend Module.symvers
make[2]: Leaving directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/haxfi'
rm -f haxfi.ko
cd /tmp/xfisrc/src/ctalsa; make clean
make[2]: Entering directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/ctalsa'
rm -rf amixer.o ctalsa_main.o dummy.o pcm.o   *.o *.ko *.o_shipped *.mod.c *~ .*cmd .tmp_versions .depend Module.symvers
make[2]: Leaving directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/ctalsa'
rm -f ctalsa.ko
cd /tmp/xfisrc/src/plugins/ct20xut; make clean
make[2]: Entering directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/plugins/ct20xut'
rm -rf  *.o *.ko *~ *.o_shipped .depend .*cmd *.mod.c .tmp_versions Module.symvers
cd /tmp/xfisrc/src/plugins; make clean
make[3]: Entering directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/plugins'
rm -rf pluginutils.o   *.o *.ko *.o_shipped *.mod.c *~ .*cmd .tmp_versions .depend Module.symvers
make[3]: Leaving directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/plugins'
make[2]: Leaving directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/plugins/ct20xut'
rm -f ct20xut.ko
cd /tmp/xfisrc/src/plugins/ctexfifx; make clean
make[2]: Entering directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/plugins/ctexfifx'
rm -rf  *.o *.ko *.o_shipped *~ *.mod.c .*cmd .tmp_versions .depend Module.symvers
cd /tmp/xfisrc/src/plugins; make clean
make[3]: Entering directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/plugins'
rm -rf pluginutils.o   *.o *.ko *.o_shipped *.mod.c *~ .*cmd .tmp_versions .depend Module.symvers
make[3]: Leaving directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/plugins'
make[2]: Leaving directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/plugins/ctexfifx'
rm -f ctexfifx.ko
cd /tmp/xfisrc/src/plugins/cthwiut; make clean
make[2]: Entering directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/plugins/cthwiut'
rm -rf  *.o *.ko *~ *.o_shipped .depend .*cmd *.mod.c .tmp_versions Module.symvers
cd /tmp/xfisrc/src/plugins; make clean
make[3]: Entering directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/plugins'
rm -rf pluginutils.o   *.o *.ko *.o_shipped *.mod.c *~ .*cmd .tmp_versions .depend Module.symvers
make[3]: Leaving directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/plugins'
make[2]: Leaving directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/plugins/cthwiut'
rm -f cthwiut.ko
cd /tmp/xfisrc/src/utils/alsaver; make
make[2]: Entering directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/utils/alsaver'
gcc -Wall -O  alsaver.c -o alsaver
make[2]: Leaving directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/utils/alsaver'
cp -f /tmp/xfisrc/src/utils/alsaver/alsaver .
cd /tmp/xfisrc/src/ossrv; make
make[2]: Entering directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/ossrv'
gcc -Wall -fomit-frame-pointer -O -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY  -D__KERNEL__ -DMODULE -ffreestanding -fno-stack-protector -mcmodel=kernel -D__x86_64__ -m64 -mno-red-zone -fno-reorder-blocks -Wno-sign-compare -fno-asynchronous-unwind-tables -D__CT_SYS_LINUX_AMD64 -msse -mno-mmx -mno-sse2 -mno-3dnow -D__CT_BOUND_64BIT -I/lib/modules/2.6.24-19-generic/build/include -I/lib/modules/2.6.24-19-generic/build/include/asm/mach-default -I/lib/modules/2.6.24-19-generic/build/include -I/tmp/xfisrc/include -imacros /lib/modules/2.6.24-19-generic/build/include/linux/autoconf.h -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(ctossrv)" -D"KBUILD_MODNAME=KBUILD_STR(ctalsa)" -c ctossrv_main.c
gcc -Wall -fomit-frame-pointer -O -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY  -D__KERNEL__ -DMODULE -ffreestanding -fno-stack-protector -mcmodel=kernel -D__x86_64__ -m64 -mno-red-zone -fno-reorder-blocks -Wno-sign-compare -fno-asynchronous-unwind-tables -D__CT_SYS_LINUX_AMD64 -msse -mno-mmx -mno-sse2 -mno-3dnow -D__CT_BOUND_64BIT -I/lib/modules/2.6.24-19-generic/build/include -I/lib/modules/2.6.24-19-generic/build/include/asm/mach-default -I/lib/modules/2.6.24-19-generic/build/include -I/tmp/xfisrc/include -imacros /lib/modules/2.6.24-19-generic/build/include/linux/autoconf.h -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(ctossrv)" -D"KBUILD_MODNAME=KBUILD_STR(ctalsa)" -c LinuxReg.c
gcc -Wall -fomit-frame-pointer -O -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY  -D__KERNEL__ -DMODULE -ffreestanding -fno-stack-protector -mcmodel=kernel -D__x86_64__ -m64 -mno-red-zone -fno-reorder-blocks -Wno-sign-compare -fno-asynchronous-unwind-tables -D__CT_SYS_LINUX_AMD64 -msse -mno-mmx -mno-sse2 -mno-3dnow -D__CT_BOUND_64BIT -I/lib/modules/2.6.24-19-generic/build/include -I/lib/modules/2.6.24-19-generic/build/include/asm/mach-default -I/lib/modules/2.6.24-19-generic/build/include -I/tmp/xfisrc/include -imacros /lib/modules/2.6.24-19-generic/build/include/linux/autoconf.h -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(ctossrv)" -D"KBUILD_MODNAME=KBUILD_STR(ctalsa)" -c LinuxSys.c
LinuxSys.c: In function ‘sysRegisterInterrupt’:
LinuxSys.c:643: warning: cast from pointer to integer of different size
LinuxSys.c:648: error: ‘SA_SHIRQ’ undeclared (first use in this function)
LinuxSys.c:648: error: (Each undeclared identifier is reported only once
LinuxSys.c:648: error: for each function it appears in.)
LinuxSys.c: In function ‘sysGetPagePhysAddr’:
LinuxSys.c:956: warning: passing argument 1 of ‘kvirt_to_phys’ makes integer from pointer without a cast
LinuxSys.c: In function ‘sysGetPageBusAddr’:
LinuxSys.c:983: warning: passing argument 1 of ‘kvirt_to_bus’ makes integer from pointer without a cast
LinuxSys.c: In function ‘sysWriteFile’:
LinuxSys.c:1635: warning: pointer targets in passing argument 2 of ‘filp->f_op->write’ differ in signedness
LinuxSys.c: In function ‘sysReadFile’:
LinuxSys.c:1684: warning: pointer targets in passing argument 2 of ‘filp->f_op->read’ differ in signedness
make[2]: *** [LinuxSys.o] Error 1
make[2]: Leaving directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/ossrv'
make[1]: *** [ctossrv] Error 2
make[1]: Leaving directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers'

make -f /tmp/xfisrc/Makefile.build install
make[1]: Entering directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers'
Copy module files...
cp: cannot stat `ctossrv.ko': No such file or directory
cp: cannot stat `emupia.ko': No such file or directory
cp: cannot stat `ctsfman.ko': No such file or directory
cp: cannot stat `haxfi.ko': No such file or directory
cp: cannot stat `ctalsa.ko': No such file or directory
cp: cannot stat `ct20xut.ko': No such file or directory
cp: cannot stat `ctexfifx.ko': No such file or directory
cp: cannot stat `cthwiut.ko': No such file or directory
make[1]: *** [copy_modules] Error 1
make[1]: Leaving directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers'

make -f /tmp/xfisrc/Makefile.build
make[1]: Entering directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers'
cd /tmp/xfisrc/src/utils/alsaver; make clean
make[2]: Entering directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/utils/alsaver'
rm -f alsaver
make[2]: Leaving directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/utils/alsaver'
rm -f alsaver
cd /tmp/xfisrc/src/ossrv; make clean
make[2]: Entering directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/ossrv'
rm -rf ctossrv_main.o LinuxReg.o LinuxSys.o osutils.o   *.o *.ko *.o_shipped *.mod.c *~ .*cmd .tmp_versions .depend Module.symvers
make[2]: Leaving directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/ossrv'
rm -f ctossrv.ko
cd /tmp/xfisrc/src/emupia; make clean
make[2]: Entering directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/emupia'
rm -rf emupia_guids.o emupia_main.o   *.o *.ko *.o_shipped *.mod.c *~ .*cmd .tmp_versions .depend Module.symvers
make[2]: Leaving directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/emupia'
rm -f emupia.ko
cd /tmp/xfisrc/src/sfman; make clean
make[2]: Entering directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/sfman'
rm -rf ctsfman_main.o   *.o *.ko *.o_shipped *.mod.c *~ .*cmd .tmp_versions .depend Module.symvers
make[2]: Leaving directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/sfman'
rm -f ctsfman.ko
cd /tmp/xfisrc/src/haxfi; make clean
make[2]: Entering directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/haxfi'
rm -rf haxfi_main.o   *.o *.ko *.o_shipped *.mod.c *~ .*cmd .tmp_versions .depend Module.symvers
make[2]: Leaving directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/haxfi'
rm -f haxfi.ko
cd /tmp/xfisrc/src/ctalsa; make clean
make[2]: Entering directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/ctalsa'
rm -rf amixer.o ctalsa_main.o dummy.o pcm.o   *.o *.ko *.o_shipped *.mod.c *~ .*cmd .tmp_versions .depend Module.symvers
make[2]: Leaving directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/ctalsa'
rm -f ctalsa.ko
cd /tmp/xfisrc/src/plugins/ct20xut; make clean
make[2]: Entering directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/plugins/ct20xut'
rm -rf  *.o *.ko *~ *.o_shipped .depend .*cmd *.mod.c .tmp_versions Module.symvers
cd /tmp/xfisrc/src/plugins; make clean
make[3]: Entering directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/plugins'
rm -rf pluginutils.o   *.o *.ko *.o_shipped *.mod.c *~ .*cmd .tmp_versions .depend Module.symvers
make[3]: Leaving directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/plugins'
make[2]: Leaving directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/plugins/ct20xut'
rm -f ct20xut.ko
cd /tmp/xfisrc/src/plugins/ctexfifx; make clean
make[2]: Entering directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/plugins/ctexfifx'
rm -rf  *.o *.ko *.o_shipped *~ *.mod.c .*cmd .tmp_versions .depend Module.symvers
cd /tmp/xfisrc/src/plugins; make clean
make[3]: Entering directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/plugins'
rm -rf pluginutils.o   *.o *.ko *.o_shipped *.mod.c *~ .*cmd .tmp_versions .depend Module.symvers
make[3]: Leaving directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/plugins'
make[2]: Leaving directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/plugins/ctexfifx'
rm -f ctexfifx.ko
cd /tmp/xfisrc/src/plugins/cthwiut; make clean
make[2]: Entering directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/plugins/cthwiut'
rm -rf  *.o *.ko *~ *.o_shipped .depend .*cmd *.mod.c .tmp_versions Module.symvers
cd /tmp/xfisrc/src/plugins; make clean
make[3]: Entering directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/plugins'
rm -rf pluginutils.o   *.o *.ko *.o_shipped *.mod.c *~ .*cmd .tmp_versions .depend Module.symvers
make[3]: Leaving directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/plugins'
make[2]: Leaving directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/plugins/cthwiut'
rm -f cthwiut.ko
cd /tmp/xfisrc/src/utils/alsaver; make
make[2]: Entering directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/utils/alsaver'
gcc -Wall -O  alsaver.c -o alsaver
make[2]: Leaving directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/utils/alsaver'
cp -f /tmp/xfisrc/src/utils/alsaver/alsaver .
cd /tmp/xfisrc/src/ossrv; make
make[2]: Entering directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/ossrv'
gcc -Wall -fomit-frame-pointer -O -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY  -D__KERNEL__ -DMODULE -ffreestanding -fno-stack-protector -mcmodel=kernel -D__x86_64__ -m64 -mno-red-zone -fno-reorder-blocks -Wno-sign-compare -fno-asynchronous-unwind-tables -D__CT_SYS_LINUX_AMD64 -msse -mno-mmx -mno-sse2 -mno-3dnow -D__CT_BOUND_64BIT -I/lib/modules/2.6.24-19-generic/build/include -I/lib/modules/2.6.24-19-generic/build/include/asm/mach-default -I/lib/modules/2.6.24-19-generic/build/include -I/tmp/xfisrc/include -imacros /lib/modules/2.6.24-19-generic/build/include/linux/autoconf.h -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(ctossrv)" -D"KBUILD_MODNAME=KBUILD_STR(ctalsa)" -c ctossrv_main.c
gcc -Wall -fomit-frame-pointer -O -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY  -D__KERNEL__ -DMODULE -ffreestanding -fno-stack-protector -mcmodel=kernel -D__x86_64__ -m64 -mno-red-zone -fno-reorder-blocks -Wno-sign-compare -fno-asynchronous-unwind-tables -D__CT_SYS_LINUX_AMD64 -msse -mno-mmx -mno-sse2 -mno-3dnow -D__CT_BOUND_64BIT -I/lib/modules/2.6.24-19-generic/build/include -I/lib/modules/2.6.24-19-generic/build/include/asm/mach-default -I/lib/modules/2.6.24-19-generic/build/include -I/tmp/xfisrc/include -imacros /lib/modules/2.6.24-19-generic/build/include/linux/autoconf.h -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(ctossrv)" -D"KBUILD_MODNAME=KBUILD_STR(ctalsa)" -c LinuxReg.c
gcc -Wall -fomit-frame-pointer -O -fno-strict-aliasing -pipe -D__CT_SYS_LINUX -DNO_SWSYNTH -D__CT_LITTLE_ENDIAN -DNO_NEWDELETE_OVERLOAD -DUSE_CALLBACKS_EX -DNATIVE_OPENAL -DCTAUDBINARY  -D__KERNEL__ -DMODULE -ffreestanding -fno-stack-protector -mcmodel=kernel -D__x86_64__ -m64 -mno-red-zone -fno-reorder-blocks -Wno-sign-compare -fno-asynchronous-unwind-tables -D__CT_SYS_LINUX_AMD64 -msse -mno-mmx -mno-sse2 -mno-3dnow -D__CT_BOUND_64BIT -I/lib/modules/2.6.24-19-generic/build/include -I/lib/modules/2.6.24-19-generic/build/include/asm/mach-default -I/lib/modules/2.6.24-19-generic/build/include -I/tmp/xfisrc/include -imacros /lib/modules/2.6.24-19-generic/build/include/linux/autoconf.h -D"KBUILD_STR(s)=#s" -D"KBUILD_BASENAME=KBUILD_STR(ctossrv)" -D"KBUILD_MODNAME=KBUILD_STR(ctalsa)" -c LinuxSys.c
LinuxSys.c: In function ‘sysRegisterInterrupt’:
LinuxSys.c:643: warning: cast from pointer to integer of different size
LinuxSys.c:648: error: ‘SA_SHIRQ’ undeclared (first use in this function)
LinuxSys.c:648: error: (Each undeclared identifier is reported only once
LinuxSys.c:648: error: for each function it appears in.)
LinuxSys.c: In function ‘sysGetPagePhysAddr’:
LinuxSys.c:956: warning: passing argument 1 of ‘kvirt_to_phys’ makes integer from pointer without a cast
LinuxSys.c: In function ‘sysGetPageBusAddr’:
LinuxSys.c:983: warning: passing argument 1 of ‘kvirt_to_bus’ makes integer from pointer without a cast
LinuxSys.c: In function ‘sysWriteFile’:
LinuxSys.c:1635: warning: pointer targets in passing argument 2 of ‘filp->f_op->write’ differ in signedness
LinuxSys.c: In function ‘sysReadFile’:
LinuxSys.c:1684: warning: pointer targets in passing argument 2 of ‘filp->f_op->read’ differ in signedness
make[2]: *** [LinuxSys.o] Error 1
make[2]: Leaving directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers/src/ossrv'
make[1]: *** [ctossrv] Error 2
make[1]: Leaving directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers'

make -f /tmp/xfisrc/Makefile.build install
make[1]: Entering directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers'
Copy module files...
cp: cannot stat `ctossrv.ko': No such file or directory
cp: cannot stat `emupia.ko': No such file or directory
cp: cannot stat `ctsfman.ko': No such file or directory
cp: cannot stat `haxfi.ko': No such file or directory
cp: cannot stat `ctalsa.ko': No such file or directory
cp: cannot stat `ct20xut.ko': No such file or directory
cp: cannot stat `ctexfifx.ko': No such file or directory
cp: cannot stat `cthwiut.ko': No such file or directory
make[1]: *** [copy_modules] Error 1
make[1]: Leaving directory `/opt/Creative/XFiDrv_Linux_US-1.18/drivers'
--------------------END--------------------------------------------------

The only reason im looking into the drivers for my XFI sound card is when i use teamspeak and try to browse the internet i get no sound from the explorer window in fact i can only have one application using the sound at once media player teamspeak explorer window even system sounds stop when using teamspeak.

is this down to a bug or is there a easey fix to get sound out of all my applications.

will installing my XFI sound card improve the situation.

audio drivers XFI drivers 1.18

ubuntu 8.04

kernel version 2.6.24.19

---

