---
title: "trust spacecam 320 not working"
date: 2006-11-29
forum: General Help
---

### Post by feest on 2006-11-29
hi i have a trust spacecam 320 but it doesn't work, the sound device (microphone gets detected so i think its not broke or something and its in the usb devices list, however it's not in the webcam list (amsn) so i can't use it. how can i fix this?

---

### Post by teaker1s on 2006-11-29
**lsusb** in terminal
look for something like this
Bus 001 Device 002: ID 046d:08f0 Logitech, Inc. QuickCam Messenger
now you know who really make your webcam you can start looking for a kernel module and driver **046d:08f0****** is the manufacturer and model

---

### Post by feest on 2006-11-29
well it's isn't in the list...

---

### Post by teaker1s on 2006-12-01
> **feest said:**
> well it's isn't in the list... thats possibly because most of trust's products are not their own eg trust 514 dx soundcard is in fact a c-media card

run this in terminal
** hal-device-manager** and look under usb section

---

### Post by feest on 2006-12-02
there's not really a clear usb section, and the only 2 things that do have something with usb, but that are my usb controllers. does anybody else have a 320 spacecam working?

---

### Post by teaker1s on 2006-12-02
> **feest said:**
> there's not really a clear usb section, and the only 2 things that do have something with usb, but that are my usb controllers. does anybody else have a 320 spacecam working?

look [here]("http://ovcam.org/ov511/cameras.html")

---

### Post by feest on 2006-12-03
it says that is should work with the driver, but i don't have a linux driver and on the site it's not available for linux.

---

### Post by teaker1s on 2006-12-03
have you looked [here]("http://ovcam.org/ov511/") for driver

---

### Post by zebzeb on 2006-12-20
I know nothing about anything but my 320 doesn't work either 

Bus 001 Device 002: ID 05a9:a518 OmniVision Technologies, Inc.

shows up in device manager as video4linux device 
\dev\video0

some snippets from dmesg

drivers/media/video/ov511/ov511.c: Sensor is an OV7620
[17179617.368000] drivers/media/video/ov511/ov511.c: Device at usb-0000:00:04.2-1 registered to minor 0
[17179617.368000] usbcore: registered new driver ov511
[17179617.368000] drivers/media/video/ov511/ov511.c: v1.64 for Linux 2.5 : ov511 USB Camera Driver


[17179919.556000] drivers/media/video/ov511/ov511.c: No decompressor available
[17179976.212000] drivers/media/video/ov511/ov511.c: No decompressor available
[17180251.032000] drivers/media/video/ov511/ov511.c: No decompressor available

When I try Camorama webcam viewer I get - could not connect to device \dev\video0

Tried also \dev\video0 in KMPlayer but nothing happens.

I ain't got no clue!!

---

### Post by teaker1s on 2006-12-20
the forums are to point you in the right direction, if you read through this thread I have posted a link to a website that caters for your camera and will have instructions on how to install the driver

---

### Post by zebzeb on 2006-12-21
I had been to the site you reommended and dowloaded the stabe1.x release and I thought I instlled it correctly??

I've just  had my second go at installing a ov511 driver 2.x, I really am new and have not used linux at all before last week but I think it worked (once I put sudo before the make install command)

dmesg now says

[17179599.712000] /home/paul/Desktop/ov511-2.32/ov511_core.c: USB OV518+ video device found
[17179599.712000] /home/paul/Desktop/ov511-2.32/ov511_core.c: Device revision 2
[17179599.724000] /home/paul/Desktop/ov511-2.32/ov511_core.c: Compression required with OV518...enabling
[17179599.780000] /home/paul/Desktop/ov511-2.32/ov511_core.c: Device at usb-0000:00:04.2-1 registered to minor 0
[17179599.780000] usbcore: registered new driver ov511
[17179599.780000] /home/paul/Desktop/ov511-2.32/ov511_core.c: v2.32 : ov511 USB Camera Driver (V4L2 disabled)

2.32 was the driver I got and installed

In device manager it says the video part of the camera is a video4linux device but as you can see when I do dmseg it says (V4L2 disabled). I haven't done the thing to ensure compression suggested on the site cause I ran the check like the guy said and as you can see above it says -ompression required with OV518...enabling???? Whatever that means.

On the cameras part of that site it lists 2 chipsets for spacecam 320 and it would seem I have the ov518+ which is not definately supported.

If I'm not using the forum properly please tell me but I'm just just saying what I tried and I don't really understand what I've done, I'm just playing really, trying to get to know the system. Not sure if I'll use ubuntu or xp more in the long term I just installed a dual boot cause I had to reinstall xp anyway and I thought I'd give it a go.

---

### Post by teaker1s on 2006-12-21
your using the forum properly;)  this forum helps those who try to help themselves ie. it's not paid support. Describing your issue and what you have tried so far=more help

I would suggest that if your chipset isn't supported that you enquire politley with the driver developer as sometimes it's possible to work with the developer and tweak configuration files to get it working if a similar model works. I found this with a scanner!!!

ubuntu is a good operation system and unlike vista or xp it only breaks when you break it, I would reccomend you stick with it:mrgreen:

---

### Post by zebzeb on 2006-12-21
just to let you know, I ran easycam2 and now it seems to work (kindof). Looks lovely on XawTV but shows a black screen on Camorama and Kopete (which is more than it did before I ran easycam2). 
It looks like it should work in Camorama as there is a framerate but just that screen is black. I think I'm gonna give it a break for a while as baby is teething but I'm chuffed I've got it to work with 1 app!

---

### Post by zebzeb on 2006-12-22
Ho hum, picture lovely in XawTV, also works with Ekiga, but Camorama and Kopete have black screens. Also I seem to have to run easycam everytime I log in as when I reboot it doesn't work untill I do (says it can't find dev/Video0 - I guess I have to alter modules or something but not sure how, will look for more threads inbetween trying to entertain the baby!

---

### Post by teaker1s on 2006-12-23
terminal
"sudo gedit /etc/modules"

add the module you want run at boot to file and save;) glad your making progress

---

### Post by zebzeb on 2006-12-26
haven't managed to fix this problem but have got modem and DVD working! I've found someone having the same problem with a different driver [http://ubuntuforums.org/showthread.php?t=128819](http://ubuntuforums.org/showthread.php?t=128819) 
Having fun with ubuntu, may get DVD rewritable drive??? Thanks for help, If you read this teaker1s, I'm gonna follow what happens in the other query, this really is a small problem as I haven't used it in years, let alone regularly.

---

### Post by teaker1s on 2006-12-27
may I wish you seasons greetings and enjoy ubuntu :mrgreen:

---

### Post by feest on 2007-02-17
> **teaker1s said:**
> look [here]("http://ovcam.org/ov511/cameras.html")

okay i've downloaded that file but when i run MAKE i get this:

```
ity.h:45,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/sched.h:44,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/module.h:9,
                 from ov511.c:53:
/lib/modules/2.6.17-11-generic/build/include/asm/system.h: In function ‘__set_64bit_var’:
/lib/modules/2.6.17-11-generic/build/include/asm/system.h:215: warning: dereferencing type-punned pointer will break strict-aliasing rules
/lib/modules/2.6.17-11-generic/build/include/asm/system.h:215: warning: dereferencing type-punned pointer will break strict-aliasing rules
In file included from /lib/modules/2.6.17-11-generic/build/include/linux/rwsem.h:26,
                 from /lib/modules/2.6.17-11-generic/build/include/asm/semaphore.h:42,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/sched.h:57,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/module.h:9,
                 from ov511.c:53:
/lib/modules/2.6.17-11-generic/build/include/asm/rwsem.h: In function ‘__down_read’:
/lib/modules/2.6.17-11-generic/build/include/asm/rwsem.h:105: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
/lib/modules/2.6.17-11-generic/build/include/asm/rwsem.h: In function ‘__down_write’:
/lib/modules/2.6.17-11-generic/build/include/asm/rwsem.h:157: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
/lib/modules/2.6.17-11-generic/build/include/asm/rwsem.h: In function ‘__up_read’:
/lib/modules/2.6.17-11-generic/build/include/asm/rwsem.h:194: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
/lib/modules/2.6.17-11-generic/build/include/asm/rwsem.h:188: warning: unused variable ‘tmp’
/lib/modules/2.6.17-11-generic/build/include/asm/rwsem.h: In function ‘__up_write’:
/lib/modules/2.6.17-11-generic/build/include/asm/rwsem.h:220: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
/lib/modules/2.6.17-11-generic/build/include/asm/rwsem.h: In function ‘__downgrade_write’:
/lib/modules/2.6.17-11-generic/build/include/asm/rwsem.h:245: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
In file included from /lib/modules/2.6.17-11-generic/build/include/linux/sched.h:57,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/module.h:9,
                 from ov511.c:53:
/lib/modules/2.6.17-11-generic/build/include/asm/semaphore.h: In function ‘down’:
/lib/modules/2.6.17-11-generic/build/include/asm/semaphore.h:105: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
/lib/modules/2.6.17-11-generic/build/include/asm/semaphore.h: In function ‘down_interruptible’:
/lib/modules/2.6.17-11-generic/build/include/asm/semaphore.h:130: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
/lib/modules/2.6.17-11-generic/build/include/asm/semaphore.h: In function ‘down_trylock’:
/lib/modules/2.6.17-11-generic/build/include/asm/semaphore.h:155: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
/lib/modules/2.6.17-11-generic/build/include/asm/semaphore.h: In function ‘up’:
/lib/modules/2.6.17-11-generic/build/include/asm/semaphore.h:179: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
In file included from /lib/modules/2.6.17-11-generic/build/include/asm/smp.h:17,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/smp.h:18,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/sched.h:63,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/module.h:9,
                 from ov511.c:53:
/lib/modules/2.6.17-11-generic/build/include/asm/mpspec.h:6:25: error: mach_mpspec.h: No such file or directory
In file included from /lib/modules/2.6.17-11-generic/build/include/asm/smp.h:17,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/smp.h:18,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/sched.h:63,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/module.h:9,
                 from ov511.c:53:
/lib/modules/2.6.17-11-generic/build/include/asm/mpspec.h: At top level:
/lib/modules/2.6.17-11-generic/build/include/asm/mpspec.h:8: error: ‘MAX_MP_BUSSES’ undeclared here (not in a function)
/lib/modules/2.6.17-11-generic/build/include/asm/mpspec.h:22: error: ‘MAX_IRQ_SOURCES’ undeclared here (not in a function)
In file included from /lib/modules/2.6.17-11-generic/build/include/linux/smp.h:18,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/sched.h:63,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/module.h:9,
                 from ov511.c:53:
/lib/modules/2.6.17-11-generic/build/include/asm/smp.h:76:26: error: mach_apicdef.h: No such file or directory
In file included from /lib/modules/2.6.17-11-generic/build/include/linux/smp.h:18,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/sched.h:63,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/module.h:9,
                 from ov511.c:53:
/lib/modules/2.6.17-11-generic/build/include/asm/smp.h: In function ‘hard_smp_processor_id’:
/lib/modules/2.6.17-11-generic/build/include/asm/smp.h:80: warning: implicit declaration of function ‘GET_APIC_ID’
In file included from /lib/modules/2.6.17-11-generic/build/include/linux/irq.h:21,
                 from /lib/modules/2.6.17-11-generic/build/include/asm/hardirq.h:5,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/hardirq.h:6,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/interrupt.h:10,
                 from /lib/modules/2.6.17-11-generic/build/include/asm/highmem.h:23,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/highmem.h:23,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/pagemap.h:10,
                 from ov511.c:60:
/lib/modules/2.6.17-11-generic/build/include/asm/irq.h:15:25: error: irq_vectors.h: No such file or directory
In file included from /lib/modules/2.6.17-11-generic/build/include/asm/hardirq.h:5,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/hardirq.h:6,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/interrupt.h:10,
                 from /lib/modules/2.6.17-11-generic/build/include/asm/highmem.h:23,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/highmem.h:23,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/pagemap.h:10,
                 from ov511.c:60:
/lib/modules/2.6.17-11-generic/build/include/linux/irq.h: At top level:
/lib/modules/2.6.17-11-generic/build/include/linux/irq.h:84: error: ‘NR_IRQS’ undeclared here (not in a function)
In file included from /lib/modules/2.6.17-11-generic/build/include/linux/irq.h:93,
                 from /lib/modules/2.6.17-11-generic/build/include/asm/hardirq.h:5,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/hardirq.h:6,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/interrupt.h:10,
                 from /lib/modules/2.6.17-11-generic/build/include/asm/highmem.h:23,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/highmem.h:23,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/pagemap.h:10,
                 from ov511.c:60:
/lib/modules/2.6.17-11-generic/build/include/asm/hw_irq.h:29: error: ‘NR_IRQ_VECTORS’ undeclared here (not in a function)
ov511.c:64:27: error: linux/wrapper.h: No such file or directory
ov511.c:189: error: expected ‘)’ before string constant
ov511.c:191: error: expected ‘)’ before string constant
ov511.c:193: error: expected ‘)’ before string constant
ov511.c:195: error: expected ‘)’ before string constant
ov511.c:198: error: expected ‘)’ before string constant
ov511.c:202: error: expected ‘)’ before string constant
ov511.c:205: error: expected ‘)’ before string constant
ov511.c:209: error: expected ‘)’ before string constant
ov511.c:211: error: expected ‘)’ before string constant
ov511.c:213: error: expected ‘)’ before string constant
ov511.c:216: error: expected ‘)’ before string constant
ov511.c:218: error: expected ‘)’ before string constant
ov511.c:221: error: expected ‘)’ before string constant
ov511.c:223: error: expected ‘)’ before string constant
ov511.c:225: error: expected ‘)’ before string constant
ov511.c:227: error: expected ‘)’ before string constant
ov511.c:229: error: expected ‘)’ before string constant
ov511.c:231: error: expected ‘)’ before string constant
ov511.c:233: error: expected ‘)’ before string constant
ov511.c:235: error: expected ‘)’ before string constant
ov511.c:237: error: expected ‘)’ before string constant
ov511.c:239: error: expected ‘)’ before string constant
ov511.c:241: error: expected ‘)’ before string constant
ov511.c:243: error: expected ‘)’ before string constant
ov511.c:246: error: expected ‘)’ before string constant
ov511.c:249: error: expected ‘)’ before string constant
ov511.c:251: error: expected ‘)’ before string constant
ov511.c:253: error: expected ‘)’ before string constant
ov511.c:255: error: expected ‘)’ before string constant
ov511.c:257: error: expected ‘)’ before string constant
ov511.c:259: error: expected ‘)’ before string constant
ov511.c:261: error: expected ‘)’ before string constant
ov511.c:264: error: expected ‘)’ before string constant
ov511.c:267: error: expected ‘)’ before string constant
ov511.c:269: error: expected ‘)’ before string constant
ov511.c: In function ‘rvmalloc’:
ov511.c:448: warning: implicit declaration of function ‘mem_map_reserve’
ov511.c: In function ‘rvfree’:
ov511.c:466: warning: implicit declaration of function ‘mem_map_unreserve’
ov511.c: In function ‘request_decompressor’:
ov511.c:3651: warning: implicit declaration of function ‘__MOD_INC_USE_COUNT’
ov511.c: In function ‘release_decompressor’:
ov511.c:3674: warning: implicit declaration of function ‘__MOD_DEC_USE_COUNT’
ov511.c: In function ‘ov51x_init_isoc’:
ov511.c:4547: warning: assignment from incompatible pointer type
ov511.c: In function ‘ov51x_v4l1_mmap’:
ov511.c:5664: warning: implicit declaration of function ‘remap_page_range’
ov511.c: In function ‘ov518_configure’:
ov511.c:6677: warning: initialization from incompatible pointer type
ov511.c:6678: error: ‘struct usb_host_endpoint’ has no member named ‘wMaxPacketSize’
ov511.c: In function ‘ov51x_probe’:
ov511.c:6782: warning: assignment from incompatible pointer type
ov511.c:7017: error: invalid storage class for function ‘ov51x_disconnect’
ov511.c:7088: error: unknown field ‘owner’ specified in initializer
ov511.c:7088: warning: initialization from incompatible pointer type
ov511.c:7096: error: initializer element is not constant
ov511.c:7096: error: (near initialization for ‘ov511_driver.disconnect’)
ov511.c: In function ‘ov511_register_decomp_module’:
ov511.c:7152: error: ‘MOD_INC_USE_COUNT’ undeclared (first use in this function)
ov511.c:7152: error: (Each undeclared identifier is reported only once
ov511.c:7152: error: for each function it appears in.)
ov511.c: In function ‘ov511_deregister_decomp_module’:
ov511.c:7179: error: ‘MOD_DEC_USE_COUNT’ undeclared (first use in this function)
ov511.c: In function ‘ov51x_probe’:
ov511.c:7186: error: invalid storage class for function ‘usb_ov511_init’
ov511.c:7208: error: invalid storage class for function ‘usb_ov511_exit’
ov511.c:7215: error: invalid storage class for function ‘__inittest’
ov511.c:7215: warning: ‘alias’ attribute ignored
ov511.c:7216: error: invalid storage class for function ‘__exittest’
ov511.c:7216: warning: ‘alias’ attribute ignored
ov511.c:7218: error: non-static declaration of ‘ov511_register_decomp_module’ follows static declaration
ov511.c:7108: error: previous definition of ‘ov511_register_decomp_module’ was here
ov511.c:7219: error: non-static declaration of ‘ov511_deregister_decomp_module’ follows static declaration
ov511.c:7164: error: previous definition of ‘ov511_deregister_decomp_module’ was here
ov511.c:7219: error: expected declaration or statement at end of input
make: *** [ov511.o] Fout 1
sven@sven-desktop:~/Desktop/ov511-1.65$ make help
make: *** Er is geen regel om doel 'help' te maken.  Gestopt.
sven@sven-desktop:~/Desktop/ov511-1.65$ clear

sven@sven-desktop:~/Desktop/ov511-1.65$ nano README
sven@sven-desktop:~/Desktop/ov511-1.65$ make clean
rm -f *.o *~ core *.i
sven@sven-desktop:~/Desktop/ov511-1.65$ make
gcc -c -D__KERNEL__ -DMODULE -DOUTSIDE_KERNEL -O2 -Wall -Wstrict-prototypes -fomit-frame-pointer -I/lib/modules/`uname -r`/build/include -DEXPORT_SYMTAB ov511.c
ov511.c:47:33: error: linux/modversions.h: No such file or directory
In file included from /lib/modules/2.6.17-11-generic/build/include/asm/processor.h:18,
                 from /lib/modules/2.6.17-11-generic/build/include/asm/thread_info.h:16,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/thread_info.h:21,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/preempt.h:9,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/spinlock.h:49,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/capability.h:45,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/sched.h:44,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/module.h:9,
                 from ov511.c:53:
/lib/modules/2.6.17-11-generic/build/include/asm/system.h: In function ‘__set_64bit_var’:
/lib/modules/2.6.17-11-generic/build/include/asm/system.h:215: warning: dereferencing type-punned pointer will break strict-aliasing rules
/lib/modules/2.6.17-11-generic/build/include/asm/system.h:215: warning: dereferencing type-punned pointer will break strict-aliasing rules
In file included from /lib/modules/2.6.17-11-generic/build/include/linux/rwsem.h:26,
                 from /lib/modules/2.6.17-11-generic/build/include/asm/semaphore.h:42,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/sched.h:57,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/module.h:9,
                 from ov511.c:53:
/lib/modules/2.6.17-11-generic/build/include/asm/rwsem.h: In function ‘__down_read’:
/lib/modules/2.6.17-11-generic/build/include/asm/rwsem.h:105: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
/lib/modules/2.6.17-11-generic/build/include/asm/rwsem.h: In function ‘__down_write’:
/lib/modules/2.6.17-11-generic/build/include/asm/rwsem.h:157: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
/lib/modules/2.6.17-11-generic/build/include/asm/rwsem.h: In function ‘__up_read’:
/lib/modules/2.6.17-11-generic/build/include/asm/rwsem.h:194: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
/lib/modules/2.6.17-11-generic/build/include/asm/rwsem.h:188: warning: unused variable ‘tmp’
/lib/modules/2.6.17-11-generic/build/include/asm/rwsem.h: In function ‘__up_write’:
/lib/modules/2.6.17-11-generic/build/include/asm/rwsem.h:220: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
/lib/modules/2.6.17-11-generic/build/include/asm/rwsem.h: In function ‘__downgrade_write’:
/lib/modules/2.6.17-11-generic/build/include/asm/rwsem.h:245: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
In file included from /lib/modules/2.6.17-11-generic/build/include/linux/sched.h:57,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/module.h:9,
                 from ov511.c:53:
/lib/modules/2.6.17-11-generic/build/include/asm/semaphore.h: In function ‘down’:
/lib/modules/2.6.17-11-generic/build/include/asm/semaphore.h:105: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
/lib/modules/2.6.17-11-generic/build/include/asm/semaphore.h: In function ‘down_interruptible’:
/lib/modules/2.6.17-11-generic/build/include/asm/semaphore.h:130: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
/lib/modules/2.6.17-11-generic/build/include/asm/semaphore.h: In function ‘down_trylock’:
/lib/modules/2.6.17-11-generic/build/include/asm/semaphore.h:155: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
/lib/modules/2.6.17-11-generic/build/include/asm/semaphore.h: In function ‘up’:
/lib/modules/2.6.17-11-generic/build/include/asm/semaphore.h:179: error: expected ‘:’ or ‘)’ before ‘KBUILD_BASENAME’
In file included from /lib/modules/2.6.17-11-generic/build/include/asm/smp.h:17,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/smp.h:18,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/sched.h:63,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/module.h:9,
                 from ov511.c:53:
/lib/modules/2.6.17-11-generic/build/include/asm/mpspec.h:6:25: error: mach_mpspec.h: No such file or directory
In file included from /lib/modules/2.6.17-11-generic/build/include/asm/smp.h:17,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/smp.h:18,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/sched.h:63,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/module.h:9,
                 from ov511.c:53:
/lib/modules/2.6.17-11-generic/build/include/asm/mpspec.h: At top level:
/lib/modules/2.6.17-11-generic/build/include/asm/mpspec.h:8: error: ‘MAX_MP_BUSSES’ undeclared here (not in a function)
/lib/modules/2.6.17-11-generic/build/include/asm/mpspec.h:22: error: ‘MAX_IRQ_SOURCES’ undeclared here (not in a function)
In file included from /lib/modules/2.6.17-11-generic/build/include/linux/smp.h:18,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/sched.h:63,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/module.h:9,
                 from ov511.c:53:
/lib/modules/2.6.17-11-generic/build/include/asm/smp.h:76:26: error: mach_apicdef.h: No such file or directory
In file included from /lib/modules/2.6.17-11-generic/build/include/linux/smp.h:18,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/sched.h:63,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/module.h:9,
                 from ov511.c:53:
/lib/modules/2.6.17-11-generic/build/include/asm/smp.h: In function ‘hard_smp_processor_id’:
/lib/modules/2.6.17-11-generic/build/include/asm/smp.h:80: warning: implicit declaration of function ‘GET_APIC_ID’
In file included from /lib/modules/2.6.17-11-generic/build/include/linux/irq.h:21,
                 from /lib/modules/2.6.17-11-generic/build/include/asm/hardirq.h:5,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/hardirq.h:6,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/interrupt.h:10,
                 from /lib/modules/2.6.17-11-generic/build/include/asm/highmem.h:23,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/highmem.h:23,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/pagemap.h:10,
                 from ov511.c:60:
/lib/modules/2.6.17-11-generic/build/include/asm/irq.h:15:25: error: irq_vectors.h: No such file or directory
In file included from /lib/modules/2.6.17-11-generic/build/include/asm/hardirq.h:5,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/hardirq.h:6,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/interrupt.h:10,
                 from /lib/modules/2.6.17-11-generic/build/include/asm/highmem.h:23,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/highmem.h:23,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/pagemap.h:10,
                 from ov511.c:60:
/lib/modules/2.6.17-11-generic/build/include/linux/irq.h: At top level:
/lib/modules/2.6.17-11-generic/build/include/linux/irq.h:84: error: ‘NR_IRQS’ undeclared here (not in a function)
In file included from /lib/modules/2.6.17-11-generic/build/include/linux/irq.h:93,
                 from /lib/modules/2.6.17-11-generic/build/include/asm/hardirq.h:5,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/hardirq.h:6,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/interrupt.h:10,
                 from /lib/modules/2.6.17-11-generic/build/include/asm/highmem.h:23,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/highmem.h:23,
                 from /lib/modules/2.6.17-11-generic/build/include/linux/pagemap.h:10,
                 from ov511.c:60:
/lib/modules/2.6.17-11-generic/build/include/asm/hw_irq.h:29: error: ‘NR_IRQ_VECTORS’ undeclared here (not in a function)
ov511.c:64:27: error: linux/wrapper.h: No such file or directory
ov511.c:189: error: expected ‘)’ before string constant
ov511.c:191: error: expected ‘)’ before string constant
ov511.c:193: error: expected ‘)’ before string constant
ov511.c:195: error: expected ‘)’ before string constant
ov511.c:198: error: expected ‘)’ before string constant
ov511.c:202: error: expected ‘)’ before string constant
ov511.c:205: error: expected ‘)’ before string constant
ov511.c:209: error: expected ‘)’ before string constant
ov511.c:211: error: expected ‘)’ before string constant
ov511.c:213: error: expected ‘)’ before string constant
ov511.c:216: error: expected ‘)’ before string constant
ov511.c:218: error: expected ‘)’ before string constant
ov511.c:221: error: expected ‘)’ before string constant
ov511.c:223: error: expected ‘)’ before string constant
ov511.c:225: error: expected ‘)’ before string constant
ov511.c:227: error: expected ‘)’ before string constant
ov511.c:229: error: expected ‘)’ before string constant
ov511.c:231: error: expected ‘)’ before string constant
ov511.c:233: error: expected ‘)’ before string constant
ov511.c:235: error: expected ‘)’ before string constant
ov511.c:237: error: expected ‘)’ before string constant
ov511.c:239: error: expected ‘)’ before string constant
ov511.c:241: error: expected ‘)’ before string constant
ov511.c:243: error: expected ‘)’ before string constant
ov511.c:246: error: expected ‘)’ before string constant
ov511.c:249: error: expected ‘)’ before string constant
ov511.c:251: error: expected ‘)’ before string constant
ov511.c:253: error: expected ‘)’ before string constant
ov511.c:255: error: expected ‘)’ before string constant
ov511.c:257: error: expected ‘)’ before string constant
ov511.c:259: error: expected ‘)’ before string constant
ov511.c:261: error: expected ‘)’ before string constant
ov511.c:264: error: expected ‘)’ before string constant
ov511.c:267: error: expected ‘)’ before string constant
ov511.c:269: error: expected ‘)’ before string constant
ov511.c: In function ‘rvmalloc’:
ov511.c:448: warning: implicit declaration of function ‘mem_map_reserve’
ov511.c: In function ‘rvfree’:
ov511.c:466: warning: implicit declaration of function ‘mem_map_unreserve’
ov511.c: In function ‘request_decompressor’:
ov511.c:3651: warning: implicit declaration of function ‘__MOD_INC_USE_COUNT’
ov511.c: In function ‘release_decompressor’:
ov511.c:3674: warning: implicit declaration of function ‘__MOD_DEC_USE_COUNT’
ov511.c: In function ‘ov51x_init_isoc’:
ov511.c:4547: warning: assignment from incompatible pointer type
ov511.c: In function ‘ov51x_v4l1_mmap’:
ov511.c:5664: warning: implicit declaration of function ‘remap_page_range’
ov511.c: In function ‘ov518_configure’:
ov511.c:6677: warning: initialization from incompatible pointer type
ov511.c:6678: error: ‘struct usb_host_endpoint’ has no member named ‘wMaxPacketSize’
ov511.c: In function ‘ov51x_probe’:
ov511.c:6782: warning: assignment from incompatible pointer type
ov511.c:7017: error: invalid storage class for function ‘ov51x_disconnect’
ov511.c:7088: error: unknown field ‘owner’ specified in initializer
ov511.c:7088: warning: initialization from incompatible pointer type
ov511.c:7096: error: initializer element is not constant
ov511.c:7096: error: (near initialization for ‘ov511_driver.disconnect’)
ov511.c: In function ‘ov511_register_decomp_module’:
ov511.c:7152: error: ‘MOD_INC_USE_COUNT’ undeclared (first use in this function)
ov511.c:7152: error: (Each undeclared identifier is reported only once
ov511.c:7152: error: for each function it appears in.)
ov511.c: In function ‘ov511_deregister_decomp_module’:
ov511.c:7179: error: ‘MOD_DEC_USE_COUNT’ undeclared (first use in this function)
ov511.c: In function ‘ov51x_probe’:
ov511.c:7186: error: invalid storage class for function ‘usb_ov511_init’
ov511.c:7208: error: invalid storage class for function ‘usb_ov511_exit’
ov511.c:7215: error: invalid storage class for function ‘__inittest’
ov511.c:7215: warning: ‘alias’ attribute ignored
ov511.c:7216: error: invalid storage class for function ‘__exittest’
ov511.c:7216: warning: ‘alias’ attribute ignored
ov511.c:7218: error: non-static declaration of ‘ov511_register_decomp_module’ follows static declaration
ov511.c:7108: error: previous definition of ‘ov511_register_decomp_module’ was here
ov511.c:7219: error: non-static declaration of ‘ov511_deregister_decomp_module’ follows static declaration
ov511.c:7164: error: previous definition of ‘ov511_deregister_decomp_module’ was here
ov511.c:7219: error: expected declaration or statement at end of input
make: *** [ov511.o] Fout 1
sven@sven-desktop:~/Desktop/ov511-1.65$ 
```

any solution?

---

### Post by teaker1s on 2007-02-17
other than you must have [COLOR="Red"]build-essential[/COLOR] installed to compile, I'm not very up on the finer points of compiling. Maybe the driver project people can advise you on the error

---

### Post by feest on 2007-02-18
well i have, build-essential

---

### Post by palimmo on 2007-11-18
i have the same problem with this webcam on ubuntu.
Someone can help us?

---

### Post by palimmo on 2007-12-03
help!:icon_frown:

---

### Post by palimmo on 2007-12-03
is it the right way?
[http://doc.ubuntu-fr.org/trust_320](http://doc.ubuntu-fr.org/trust_320)

---

