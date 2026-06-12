---
title: "Problems with compiling driver for an I/O card"
date: 2007-06-28
forum: General Help
---

### Post by markusg on 2007-06-28
Hi,
I am trying to compile some experimental drivers for an IO-card i have installed
in a Feisty box. These are the only drivers i have found for the I/O card, DT340.
Found here: [http://sourceforge.net/project/downloading.php?group_id=57794&use_mirror=ovh&filename=dti_dt340.R0.0.tar.bz2&8808805](http://sourceforge.net/project/downloading.php?group_id=57794&use_mirror=ovh&filename=dti_dt340.R0.0.tar.bz2&8808805)

I get a bunch of errors, some i have corrected by specifing correct path to the kernel
directory, but i am stuck with this:

Any help will be appreciated!


> # make
gcc -D__KERNEL__ -DMODULE -Wall -Wstrict-prototypes -O2 -I/usr/src/linux-headers-2.6.20-15-386/include -DMODVERSIONS -include /usr/src/linux-headers-2.6.20-15-386/include/config/modversions.h -c ./dt340.c
In file included from /usr/src/linux-headers-2.6.20-15-386/include/asm/thread_info.h:16,
                 from /usr/src/linux-headers-2.6.20-15-386/include/linux/thread_info.h:21,
                 from /usr/src/linux-headers-2.6.20-15-386/include/linux/preempt.h:9,
                 from /usr/src/linux-headers-2.6.20-15-386/include/linux/spinlock.h:49,
                 from /usr/src/linux-headers-2.6.20-15-386/include/linux/module.h:9,
                 from ./dt340.c:21:
/usr/src/linux-headers-2.6.20-15-386/include/asm/processor.h:82: error: ‘CONFIG_X86_L1_CACHE_SHIFT’ undeclared here (not in a function)
/usr/src/linux-headers-2.6.20-15-386/include/asm/processor.h:82: error: requested alignment is not a constant
/usr/src/linux-headers-2.6.20-15-386/include/asm/processor.h: In function ‘cpuid_count’:
/usr/src/linux-headers-2.6.20-15-386/include/asm/processor.h:611: warning: pointer targets in passing argument 1 of ‘native_cpuid’ differ in signedness
/usr/src/linux-headers-2.6.20-15-386/include/asm/processor.h:611: warning: pointer targets in passing argument 2 of ‘native_cpuid’ differ in signedness
/usr/src/linux-headers-2.6.20-15-386/include/asm/processor.h:611: warning: pointer targets in passing argument 3 of ‘native_cpuid’ differ in signedness
/usr/src/linux-headers-2.6.20-15-386/include/asm/processor.h:611: warning: pointer targets in passing argument 4 of ‘native_cpuid’ differ in signedness
In file included from /usr/src/linux-headers-2.6.20-15-386/include/linux/sched.h:51,
                 from /usr/src/linux-headers-2.6.20-15-386/include/linux/utsname.h:35,
                 from /usr/src/linux-headers-2.6.20-15-386/include/asm/elf.h:12,
                 from /usr/src/linux-headers-2.6.20-15-386/include/linux/elf.h:7,
                 from /usr/src/linux-headers-2.6.20-15-386/include/linux/module.h:15,
                 from ./dt340.c:21:
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:33:3: error: #error You lose.
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:225:31: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:269:46: error: division by zero in #if
In file included from /usr/src/linux-headers-2.6.20-15-386/include/linux/sched.h:51,
                 from /usr/src/linux-headers-2.6.20-15-386/include/linux/utsname.h:35,
                 from /usr/src/linux-headers-2.6.20-15-386/include/asm/elf.h:12,
                 from /usr/src/linux-headers-2.6.20-15-386/include/linux/elf.h:7,
                 from /usr/src/linux-headers-2.6.20-15-386/include/linux/module.h:15,
                 from ./dt340.c:21:
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h: In function ‘jiffies_to_msecs’:
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:274: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:274: error: (Each undeclared identifier is reported only once
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:274: error: for each function it appears in.)
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:280:46: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h: In function ‘jiffies_to_usecs’:
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:285: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:293:46: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h: In function ‘msecs_to_jiffies’:
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:298: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:306:46: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h: In function ‘usecs_to_jiffies’:
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:311: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h: In function ‘timespec_to_jiffies’:
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:330: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:336: error: ‘SHIFT_HZ’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h: In function ‘jiffies_to_timespec’:
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:349: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h: In function ‘timeval_to_jiffies’:
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:371: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:375: error: ‘SHIFT_HZ’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h: In function ‘jiffies_to_timeval’:
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:387: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:400:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h: In function ‘jiffies_to_clock_t’:
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:401: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h: In function ‘clock_t_to_jiffies’:
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:412: error: ‘CONFIG_HZ’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:431:6: error: division by zero in #if
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h: In function ‘jiffies_64_to_clock_t’:
/usr/src/linux-headers-2.6.20-15-386/include/linux/jiffies.h:432: error: ‘CONFIG_HZ’ undeclared (first use in this function)
In file included from /usr/src/linux-headers-2.6.20-15-386/include/linux/aio.h:5,
                 from /usr/src/linux-headers-2.6.20-15-386/include/linux/sched.h:260,
                 from /usr/src/linux-headers-2.6.20-15-386/include/linux/utsname.h:35,
                 from /usr/src/linux-headers-2.6.20-15-386/include/asm/elf.h:12,
                 from /usr/src/linux-headers-2.6.20-15-386/include/linux/elf.h:7,
                 from /usr/src/linux-headers-2.6.20-15-386/include/linux/module.h:15,
                 from ./dt340.c:21:
/usr/src/linux-headers-2.6.20-15-386/include/linux/workqueue.h: In function ‘cancel_delayed_work’:
/usr/src/linux-headers-2.6.20-15-386/include/linux/workqueue.h:203: warning: dereferencing type-punned pointer will break strict-aliasing rules
In file included from /usr/src/linux-headers-2.6.20-15-386/include/linux/utsname.h:35,
                 from /usr/src/linux-headers-2.6.20-15-386/include/asm/elf.h:12,
                 from /usr/src/linux-headers-2.6.20-15-386/include/linux/elf.h:7,
                 from /usr/src/linux-headers-2.6.20-15-386/include/linux/module.h:15,
                 from ./dt340.c:21:
/usr/src/linux-headers-2.6.20-15-386/include/linux/sched.h: In function ‘dequeue_signal_lock’:
/usr/src/linux-headers-2.6.20-15-386/include/linux/sched.h:1309: warning: implicit declaration of function ‘local_irq_save’
/usr/src/linux-headers-2.6.20-15-386/include/linux/sched.h:1311: warning: implicit declaration of function ‘local_irq_restore’
In file included from /usr/src/linux-headers-2.6.20-15-386/include/linux/module.h:21,
                 from ./dt340.c:21:
/usr/src/linux-headers-2.6.20-15-386/include/asm/module.h:62:2: error: #error unknown processor family
In file included from /usr/src/linux-headers-2.6.20-15-386/include/asm/pci.h:6,
                 from /usr/src/linux-headers-2.6.20-15-386/include/linux/pci.h:746,
                 from ./dt340.h:60,
                 from ./dt340.c:28:
/usr/src/linux-headers-2.6.20-15-386/include/linux/mm.h: In function ‘lowmem_page_address’:
/usr/src/linux-headers-2.6.20-15-386/include/linux/mm.h:539: warning: implicit declaration of function ‘__page_to_pfn’
/usr/src/linux-headers-2.6.20-15-386/include/linux/mm.h:539: error: ‘CONFIG_PAGE_OFFSET’ undeclared (first use in this function)
In file included from /usr/src/linux-headers-2.6.20-15-386/include/asm/pci.h:41,
                 from /usr/src/linux-headers-2.6.20-15-386/include/linux/pci.h:746,
                 from ./dt340.h:60,
                 from ./dt340.c:28:
/usr/src/linux-headers-2.6.20-15-386/include/asm/io.h: In function ‘virt_to_phys’:
/usr/src/linux-headers-2.6.20-15-386/include/asm/io.h:77: error: ‘CONFIG_PAGE_OFFSET’ undeclared (first use in this function)
/usr/src/linux-headers-2.6.20-15-386/include/asm/io.h: In function ‘phys_to_virt’:
/usr/src/linux-headers-2.6.20-15-386/include/asm/io.h:95: error: ‘CONFIG_PAGE_OFFSET’ undeclared (first use in this function)
In file included from /usr/src/linux-headers-2.6.20-15-386/include/linux/pci.h:746,
                 from ./dt340.h:60,
                 from ./dt340.c:28:
/usr/src/linux-headers-2.6.20-15-386/include/asm/pci.h: In function ‘pci_dac_dma_to_page’:
/usr/src/linux-headers-2.6.20-15-386/include/asm/pci.h:72: warning: implicit declaration of function ‘__pfn_to_page’
/usr/src/linux-headers-2.6.20-15-386/include/asm/pci.h:72: warning: return makes pointer from integer without a cast
./dt340.c:36:2: error: #error "This driver requires that PCI support be configured in the Kernel"
./dt340.c: In function ‘dt340_init_one’:
./dt340.c:1872: warning: implicit declaration of function ‘request_irq’
./dt340.c:1873: error: ‘SA_SHIRQ’ undeclared (first use in this function)
./dt340.c:1873: error: ‘SA_INTERRUPT’ undeclared (first use in this function)
./dt340.c: In function ‘dt340_remove_one’:
./dt340.c:1923: warning: implicit declaration of function ‘free_irq’
make: *** [dt340.o] Error 1

---

