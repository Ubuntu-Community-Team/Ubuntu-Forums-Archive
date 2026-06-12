---
title: "&quot;Hello world&quot; module make problems"
date: 2006-11-08
forum: General Help
---

### Post by GunnarK on 2006-11-08
Hello

I am trying to compile a kernel module. 
kernel_module_test.c

************* the file ****************************
#include <linux/init.h>
#include <linux/module.h>

MODULE_LICENSE("Dual BSD/GPL");

static int module_test_init( void ){
	printk(KERN_ALERT" module_test_init \n");
	return 0;
}

static void module_test_exit( void ){
	printk(KERN_ALERT" module_test_exit \n");
}
module_init(module_test_init);
module_exit(module_test_exit);

***********end File*******************************

Makefile
*************************************************
ifneq ($(KERNELRELEASE),) 
obj-m := kernel_module_test.o
else
KERNELDIR := /usr/src/`uname -r`
PWN:= $(shell pwd)
default: $(MAKE) -C $(KERNELDIR) M=$(PWD) module
endif
**************************************************

I got the following make error
make: *** No rule to make target `make', needed by `default'. Stop.

can anyone help me with this ?

---

### Post by GunnarK on 2006-11-09
When I change 
default: $(MAKE).......
to
default: kernel_module_test ...................
I`ve got the following error

**********************************************************************

cc     kernel_module_test.c   -o kernel_module_test
In file included from /usr/include/linux/sched.h:16,
                 from /usr/include/linux/module.h:9,
                 from kernel_module_test.c:2:
/usr/include/linux/signal.h:2:2: warning: #warning "You should include <signal.h>. This time I will do it for you."
In file included from /usr/include/linux/resource.h:4,
                 from /usr/include/linux/sched.h:79,
                 from /usr/include/linux/module.h:9,
                 from kernel_module_test.c:2:
/usr/include/linux/time.h:9: error: redefinition of ‘struct timespec’
/usr/include/linux/time.h:15: error: redefinition of ‘struct timeval’
/usr/include/linux/time.h:20: error: redefinition of ‘struct timezone’
/usr/include/linux/time.h:47: error: redefinition of ‘struct itimerval’
In file included from kernel_module_test.c:2:
/usr/include/linux/module.h:41: error: field ‘attr’ has incomplete type
/usr/include/linux/module.h:49: error: field ‘kobj’ has incomplete type
kernel_module_test.c: In function ‘module_test_init’:
kernel_module_test.c:7: error: ‘KERN_ALERT’ undeclared (first use in this function)
kernel_module_test.c:7: error: (Each undeclared identifier is reported only oncekernel_module_test.c:7: error: for each function it appears in.)
kernel_module_test.c:7: error: syntax error before string constant
kernel_module_test.c: In function ‘module_test_exit’:
kernel_module_test.c:12: error: ‘KERN_ALERT’ undeclared (first use in this function)
kernel_module_test.c:12: error: syntax error before string constant
make: *** [kernel_module_test] Error 1

*************************************************************************

---

