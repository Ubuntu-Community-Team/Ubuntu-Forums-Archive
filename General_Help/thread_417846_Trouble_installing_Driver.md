---
title: "Trouble installing Driver"
date: 2007-04-21
forum: General Help
---

### Post by FuZ3 on 2007-04-21
Trying to set up a USB MIDI Keyboard. I downloaded I driver that is supposed to work with it but when i compile it i get this.

```
gcc -D__KERNEL__ -DMODULE -DLINUX -DEXPORT_SYMTAB -DREDHAT240FIX=0 -O2 -pipe -Wall -Wstrict-prototypes -fomit-frame-pointer -fno-strict-aliasing -fno-strength-reduce -D__SMP__ -march=i686 -DMODVERSIONS -include /usr/src/linux-headers-2.6.20-15/include/linux/modversions.h -I/usr/src/linux-headers-2.6.20-15/include -c -o usb-midi.o usb-midi.c
cc1: error: /usr/src/linux-headers-2.6.20-15/include/linux/modversions.h: No such file or directory
In file included from /usr/src/linux-headers-2.6.20-15/include/asm/thread_info.h:16,
                 from /usr/src/linux-headers-2.6.20-15/include/linux/thread_info.h:21,
                 from /usr/src/linux-headers-2.6.20-15/include/linux/preempt.h:9,
                 from /usr/src/linux-headers-2.6.20-15/include/linux/spinlock.h:49,
                 from /usr/src/linux-headers-2.6.20-15/include/linux/module.h:9,
                 from usb-midi.c:46:
/usr/src/linux-headers-2.6.20-15/include/asm/processor.h:82: error: ‘CONFIG_X86_L1_CACHE_SHIFT’ undeclared here (not in a function)
/usr/src/linux-headers-2.6.20-15/include/asm/processor.h:82: error: requested alignment is not a constant
/usr/src/linux-headers-2.6.20-15/include/asm/processor.h: In function ‘cpuid_count’:
/usr/src/linux-headers-2.6.20-15/include/asm/processor.h:611: warning: pointer targets in passing argument 1 of ‘native_cpuid’ differ in signedness
/usr/src/linux-headers-2.6.20-15/include/asm/processor.h:611: warning: pointer targets in passing argument 2 of ‘native_cpuid’ differ in signedness
/usr/src/linux-headers-2.6.20-15/include/asm/processor.h:611: warning: pointer targets in passing argument 3 of ‘native_cpuid’ differ in signedness
/usr/src/linux-headers-2.6.20-15/include/asm/processor.h:611: warning: pointer targets in passing argument 4 of ‘native_cpuid’ differ in signedness
In file included from /usr/src/linux-headers-2.6.20-15/include/linux/sched.h:51,
                 from /usr/src/linux-headers-2.6.20-15/include/linux/utsname.h:35,
                 from /usr/src/linux-headers-2.6.20-15/include/asm/elf.h:12,
                 from /usr/src/linux-headers-2.6.20-15/include/linux/elf.h:7,
                 from /usr/src/linux-headers-2.6.20-15/include/linux/module.h:15,
                 from usb-midi.c:46:
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:33:3: error: #error You lose.
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:269:46: error: division by zero in #if
In file included from /usr/src/linux-headers-2.6.20-15/include/linux/sched.h:51,
                 from /usr/src/linux-headers-2.6.20-15/include/linux/utsname.h:35,
                 from /usr/src/linux-headers-2.6.20-15/include/asm/elf.h:12,
                 from /usr/src/linux-headers-2.6.20-15/include/linux/elf.h:7,
                 from /usr/src/linux-headers-2.6.20-15/include/linux/module.h:15,
                 from usb-midi.c:46:
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h: In function ‘jiffies_to_msecs’:
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:274: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:274: error: (Each undeclared identifier is reported only once
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:274: error: for each function it appears in.)
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:280:46: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h: In function ‘jiffies_to_usecs’:
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:285: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:293:46: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h: In function ‘msecs_to_jiffies’:
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:298: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:306:46: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h: In function ‘usecs_to_jiffies’:
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:311: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h: In function ‘timespec_to_jiffies’:
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:330: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:336: error: ‘SHIFT_HZ’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h: In function ‘jiffies_to_timespec’:
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:349: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h: In function ‘timeval_to_jiffies’:
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:371: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:375: error: ‘SHIFT_HZ’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h: In function ‘jiffies_to_timeval’:
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:387: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h: In function ‘jiffies_to_clock_t’:
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:401: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h: In function ‘clock_t_to_jiffies’:
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:412: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h: In function ‘jiffies_64_to_clock_t’:
/usr/src/linux-headers-2.6.20-15/include/linux/jiffies.h:432: error: ‘CONFIG_HZ’ undeclared (first use in this function)
In file included from /usr/src/linux-headers-2.6.20-15/include/linux/utsname.h:35,
                 from /usr/src/linux-headers-2.6.20-15/include/asm/elf.h:12,
                 from /usr/src/linux-headers-2.6.20-15/include/linux/elf.h:7,
                 from /usr/src/linux-headers-2.6.20-15/include/linux/module.h:15,
                 from usb-midi.c:46:
/usr/src/linux-headers-2.6.20-15/include/linux/sched.h: In function ‘dequeue_signal_lock’:
/usr/src/linux-headers-2.6.20-15/include/linux/sched.h:1309: warning: implicit declaration of function ‘local_irq_save’
/usr/src/linux-headers-2.6.20-15/include/linux/sched.h:1311: warning: implicit declaration of function ‘local_irq_restore’
In file included from /usr/src/linux-headers-2.6.20-15/include/linux/module.h:21,
                 from usb-midi.c:46:
/usr/src/linux-headers-2.6.20-15/include/asm/module.h:62:2: error: #error unknown processor family
usb-midi.c:50:42: error: missing binary operator before token "("
usb-midi.c:53:27: error: linux/malloc.h: No such file or directory
usb-midi.c:55:27: error: linux/wrapper.h: No such file or directory
In file included from /usr/src/linux-headers-2.6.20-15/include/linux/irq.h:22,
                 from /usr/src/linux-headers-2.6.20-15/include/asm/hardirq.h:5,
                 from /usr/src/linux-headers-2.6.20-15/include/linux/hardirq.h:7,
                 from /usr/src/linux-headers-2.6.20-15/include/linux/interrupt.h:11,
                 from /usr/src/linux-headers-2.6.20-15/include/linux/usb.h:15,
                 from usb-midi.c:56:
/usr/src/linux-headers-2.6.20-15/include/asm/irq.h:15:25: error: irq_vectors.h: No such file or directory
In file included from /usr/src/linux-headers-2.6.20-15/include/asm/hardirq.h:5,
                 from /usr/src/linux-headers-2.6.20-15/include/linux/hardirq.h:7,
                 from /usr/src/linux-headers-2.6.20-15/include/linux/interrupt.h:11,
                 from /usr/src/linux-headers-2.6.20-15/include/linux/usb.h:15,
                 from usb-midi.c:56:
/usr/src/linux-headers-2.6.20-15/include/linux/irq.h: At top level:
/usr/src/linux-headers-2.6.20-15/include/linux/irq.h:172: error: requested alignment is not a constant
/usr/src/linux-headers-2.6.20-15/include/linux/irq.h:174: error: ‘NR_IRQS’ undeclared here (not in a function)
In file included from /usr/src/linux-headers-2.6.20-15/include/linux/hardirq.h:7,
                 from /usr/src/linux-headers-2.6.20-15/include/linux/interrupt.h:11,
                 from /usr/src/linux-headers-2.6.20-15/include/linux/usb.h:15,
                 from usb-midi.c:56:
/usr/src/linux-headers-2.6.20-15/include/asm/hardirq.h:12: error: requested alignment is not a constant
In file included from /usr/src/linux-headers-2.6.20-15/include/linux/usb.h:15,
                 from usb-midi.c:56:
/usr/src/linux-headers-2.6.20-15/include/linux/interrupt.h: In function ‘cli’:
/usr/src/linux-headers-2.6.20-15/include/linux/interrupt.h:204: warning: implicit declaration of function ‘local_irq_disable’
/usr/src/linux-headers-2.6.20-15/include/linux/interrupt.h: In function ‘sti’:
/usr/src/linux-headers-2.6.20-15/include/linux/interrupt.h:208: warning: implicit declaration of function ‘local_irq_enable’
/usr/src/linux-headers-2.6.20-15/include/linux/interrupt.h: In function ‘save_flags’:
/usr/src/linux-headers-2.6.20-15/include/linux/interrupt.h:212: warning: implicit declaration of function ‘local_save_flags’
In file included from usb-midi.c:65:
usb-midi.h:160:41: error: missing binary operator before token "("
usb-midi.c: At top level:
usb-midi.c:85: error: expected ‘)’ before string constant
usb-midi.c:89: error: expected ‘)’ before string constant
usb-midi.c:93: error: expected ‘)’ before string constant
usb-midi.c:97: error: expected ‘)’ before string constant
usb-midi.c:101: error: expected ‘)’ before string constant
usb-midi.c:105: error: expected ‘)’ before string constant
usb-midi.c:109: error: expected ‘)’ before string constant
usb-midi.c:113: error: expected ‘)’ before string constant
usb-midi.c:117: error: expected ‘)’ before string constant
usb-midi.c:125: error: expected ‘)’ before string constant
usb-midi.c:130:42: error: missing binary operator before token "("
usb-midi.c: In function ‘usb_write’:
usb-midi.c:360: warning: implicit declaration of function ‘FILL_BULK_URB’
usb-midi.c:363: error: too few arguments to function ‘usb_submit_urb’
usb-midi.c:441:41: error: missing binary operator before token "("
usb-midi.c: In function ‘usb_bulk_read’:
usb-midi.c:444: error: too few arguments to function ‘usb_submit_urb’
usb-midi.c: In function ‘usb_midi_open’:
usb-midi.c:936: error: too few arguments to function ‘usb_submit_urb’
usb-midi.c:970: error: ‘MOD_INC_USE_COUNT’ undeclared (first use in this function)
usb-midi.c: In function ‘usb_midi_release’:
usb-midi.c:1028: error: ‘MOD_DEC_USE_COUNT’ undeclared (first use in this function)
usb-midi.c: In function ‘alloc_midi_in_endpoint’:
usb-midi.c:1085: error: too few arguments to function ‘usb_alloc_urb’
usb-midi.c: In function ‘alloc_midi_out_endpoint’:
usb-midi.c:1152: error: too few arguments to function ‘usb_alloc_urb’
usb-midi.c: In function ‘get_alt_setting’:
usb-midi.c:1578: error: request for member ‘num_altsetting’ in something not a structure or union
usb-midi.c:1581: error: request for member ‘altsetting’ in something not a structure or union
usb-midi.c:1586: error: ‘struct usb_interface_descriptor’ has no member named ‘endpoint’
usb-midi.c: In function ‘alloc_usb_midi_device’:
usb-midi.c:1784: error: too few arguments to function ‘usb_submit_urb’
usb-midi.c: In function ‘detect_yamaha_device’:
usb-midi.c:1846: warning: initialization from incompatible pointer type
usb-midi.c:1859: error: ‘struct usb_config_descriptor’ has no member named ‘interface’
usb-midi.c:1860: error: ‘struct usb_config_descriptor’ has no member named ‘interface’
usb-midi.c:1875: warning: comparison of distinct pointer types lacks a cast
usb-midi.c:1885: warning: implicit declaration of function ‘usb_set_configuration’
usb-midi.c: In function ‘detect_midi_subclass’:
usb-midi.c:1960: warning: initialization from incompatible pointer type
usb-midi.c:1969: error: ‘struct usb_config_descriptor’ has no member named ‘interface’
usb-midi.c:1970: error: ‘struct usb_config_descriptor’ has no member named ‘interface’
usb-midi.c:1985: warning: comparison of distinct pointer types lacks a cast
usb-midi.c:2088:42: error: missing binary operator before token "("
usb-midi.c: At top level:
usb-midi.c:2168: warning: initialization from incompatible pointer type
usb-midi.c:2169: warning: initialization from incompatible pointer type
usb-midi.c:2170:42: error: missing binary operator before token "("
usb-midi.c:2173: error: unknown field ‘driver_list’ specified in initializer
usb-midi.c:2173: warning: braces around scalar initializer
usb-midi.c:2173: warning: (near initialization for ‘usb_midi_driver.ioctl’)
usb-midi.c:2173: error: ‘struct usb_driver’ has no member named ‘driver_list’
usb-midi.c:2173: error: ‘struct usb_driver’ has no member named ‘driver_list’
usb-midi.c:2173: warning: excess elements in scalar initializer
usb-midi.c:2173: warning: (near initialization for ‘usb_midi_driver.ioctl’)
make: *** [usb-midi.o] Error 1

```

Also I had to change /usr/src/linux to /usr/src/linux-headers-2.6.20-15-generic before it even worked at all.

Any Ideas?

---

### Post by clubsoda on 2007-05-19
>Bump< for a Gotop Super Q2 graphic tablet.:guitar:
[ a.k.a. Lucidity Touchpad
or Junior Penpower Handwriting Pad
or Slim GogoPen
vendor=08f2 ]

[img]http://www.gotop.com.tw/waweb2004/images/super_s.jpg[/img]

Different device, different driver but a near-identical string of errors.
Looking around, it seems the kernel headers have to be "primed" somehow.

As root have tried ```
cd /usr/src/linux-headers-2.6.20-15-generic
cp /boot/config-2.6.20-15-generic .config
```That .config file contains definitions like CONFIG_X86_L1_CACHE_SHIFT so it must be a step in the right direction.  Then ```
make oldconfig
```appears to ask itself 500 questions and answer them automatically (nice!) but the compile errors remain.  What next?```
make mrproper
scripts/Makefile.clean:17: /usr/src/linux-headers-2.6.20-15-generic/drivers/infiniband/hw/amso1100/Makefile: No such file or directory
make[3]: *** No rule to make target `/usr/src/linux-headers-2.6.20-15-generic/drivers/infiniband/hw/amso1100/Makefile'.  Stop.
make[2]: *** [drivers/infiniband/hw/amso1100] Error 2
make[1]: *** [drivers/infiniband] Error 2
make: *** [_clean_drivers] Error 2
``````
make xconfig
  CHECK   qt
*
* Unable to find the QT installation. Please make sure that
* the QT development package is correctly installed and
* either install pkg-config or set the QTDIR environment
* variable to the correct location.
*
make[1]: *** No rule to make target `scripts/kconfig/.tmp_qtcheck', needed by `scripts/kconfig/qconf.o'.  Stop.
make: *** [xconfig] Error 2
```Do I install one of the Qt dev packages and proceed along this route?  I'm not looking to compile a kernel...```
make dep
scripts/kconfig/conf -s arch/i386/Kconfig
*** Warning: make dep is unnecessary now.
```Glad to know it!  But it looks like something else is still necessary.  :)

---

### Post by clubsoda on 2007-05-19
Here's how to get "make mrproper" working.
Edit /usr/src/linux-headers-2.6.20-15/drivers/infiniband/Makefile and comment out the indicated lines
```
obj-$(CONFIG_INFINIBAND)                += core/
obj-$(CONFIG_INFINIBAND_MTHCA)          += hw/mthca/
obj-$(CONFIG_INFINIBAND_IPATH)          += hw/ipath/
obj-$(CONFIG_INFINIBAND_EHCA)           += hw/ehca/
# obj-$(CONFIG_INFINIBAND_AMSO1100)     += hw/amso1100/
obj-$(CONFIG_INFINIBAND_IPOIB)          += ulp/ipoib/
# obj-$(CONFIG_INFINIBAND_SRP)          += ulp/srp/
obj-$(CONFIG_INFINIBAND_ISER)           += ulp/iser/
```Next there's a problem with missing DocBook.
Hack /usr/src/linux-headers-2.6.20-15-generic/Makefile and comment out this line```
# mrproper-dirs      := $(addprefix _mrproper_,Documentation/DocBook scripts)
```Then "make mrproper" works.  It removes the .config file too so that must be copied in from /boot again.```
make oldconfig
```However, "make mrproper" seems to have broken more than it fixed.  My modversions.h has been truncated and the compiler complains that it can't find the file.  Reinstall kernel headers?:confused:

---

### Post by clubsoda on 2007-06-05
Since my last post, there have been two other threads in which people have been unable to compile drivers due to this "CONFIG_X86_L1_CACHE_SHIFT undeclared" bug.  I can only speculate:-
1) the 2.6.20-15-generic kernel headers are inconsistent with the kernel OR
2) something in the kernel module compilation process has been streamlined, breaking hundreds (thousands?) of drivers in the process.

Option 2) seems more likely.  For example, these old driver source packages do not support the "./configure" framework.

If hundreds of drivers are indeed broken, why is there not more awareness of this problem and how to fix it?  I've seen references to this error message on Fedora and Gentoo boards dating back to 2003.

---

### Post by clubsoda on 2007-09-17
>Bump<

Can anyone help with updating a (2.4 kernel) USB driver to the 2.6 kernel?  Looks like the USB data structure has changed and some of the function calls need to be modified.

The driver I'm trying to compile is called [gogopen.tar.gz](http://input.foruto.com/IME/Linux/BINARIES/gogopen.tar.gz) from [this page](http://input.foruto.com/IME/Linux/BIG5/HAND_WRITING/index.html).

Cheers.

---

### Post by clubsoda on 2007-11-20
I'm posting this here for the benefit of anyone else who might want to plug a GoTop USB tablet into linux.  The good news is that within a few months it should work "out-of-the-box"(!)  I expect there will be thousands of people out there excited about this development. :rolleyes:  Well, me at least. :D

Basically, I bit the bullet and started looking at some code to see how tablets work under the 2.6 kernel framework.  Following the examples in usbtouchscreen.c and using some specific information about the GoTop protocol contained in one of the Readme files provided by Mr Lam (the guy who coded the driver for the 2.2 kernel and whose page I linked above), I was able to get the tablet going by adding very few lines of code.  These changes have been committed to the official source for kernel modules and should start circulating in bleeding-edge distributions in a matter of weeks/months.

Getting back to the original topic of this thread, if you get the dreaded CONFIG_X86_L1_CACHE_SHIFT error then you can pretty much discard the source code you're trying to compile because the changes to the handling of USB devices run deep.  Fortunately, there is a big pay-off associated with those changes, which is that most of the difficult stuff is now handled automatically.  If you're up for the challenge, you can probably get your device working with some minor changes, starting by adding the vendor and device ID's to the list of recognised devices.  Beyond that you need knowledge of the protocol used by your device, for which you'll want documentation or some reverse engineering of the old driver code.  Good Luck.

---

