---
title: "[HELP] Installing Windows XP Home in VMware Server"
date: 2007-07-10
forum: General Help
---

### Post by ElemonGW on 2007-07-10
So, everything went well until it reached the 4th step(Windows installation). The progress bar is almost full but it have stucked @ installing devices. Anybody can give me any suggestions??? Here are my system species
```
cpu: Intel(R) Pentium(R) D CPU 2.80GHz
cpu_ghz: 2.79
memory: 495 (in fact it must be 512 but this is how much the application with which i run the test showed)
videocard_manufacturer: Tungsten Graphics, Inc
videocard_type: Mesa DRI Intel(R) 865G 20061017 x86/MMX/SSE2
videocard_ram: 512
agp_aperture_size: N/A
videocard_driver_version: 1.3 Mesa 6.5.2
soundcard: Intel ICH5 with AD1888 at 0xfbe7b800, irq 2
soundcard_driver: ALSA Version 1.0.13
machine_bitness: 32
kernel: 2.6.20-16-generic
x_version: Xorg Version 7.2.0
distro: Debian 4.0 (in fact it is Ubuntu 7.04 but the application with which i ran the test was again wrong ;-) )
```


and the contents of the Windows XP Home Edition.vmx file
```
#!/usr/bin/vmware
config.version = "8"
virtualHW.version = "4"
scsi0.present = "TRUE"
memsize = "192"
ide0:0.present = "TRUE"
ide0:0.fileName = "Windows XP Home Edition.vmdk"
ide0:0.writeThrough = "TRUE"
ide1:0.present = "FALSE"
ide1:0.fileName = "/dev/scd0"
ide1:0.deviceType = "cdrom-raw"
floppy0.fileName = "/dev/fd0"
Ethernet0.present = "TRUE"
Ethernet0.connectionType = "nat"
displayName = "Windows XP Home Edition"
guestOS = "winxphome"
priority.grabbed = "normal"
priority.ungrabbed = "normal"
powerType.powerOff = "hard"
powerType.powerOn = "hard"
powerType.suspend = "hard"
powerType.reset = "hard"

ide0:0.redo = ""
ethernet0.addressType = "generated"
uuid.location = "56 4d 31 fb 60 66 30 14-94 32 63 ca c5 22 cc d3"
uuid.bios = "56 4d 31 fb 60 66 30 14-94 32 63 ca c5 22 cc d3"
checkpoint.vmState = ""
ethernet0.generatedAddress = "00:0c:29:22:cc:d3"
ethernet0.generatedAddressOffset = "0"

numvcpus = "2"
scsi0:0.present = "FALSE"
scsi0:0.fileName = "/dev/scd0"
scsi0:0.deviceType = "cdrom-raw"
debug = "TRUE"

ide0:1.present = "TRUE"
ide0:1.fileName = "/dev/scd0"
ide0:1.deviceType = "cdrom-raw"
```
in case you find it usefull to help me :) .

---

### Post by ElemonGW on 2007-07-10
Well anybody? I hate dumping my own threads but I really need to find a solution asap.

---

### Post by claudiu-eduard on 2007-07-11
I try to install VWware on Ubuntu 7.04 and I got this message:

Extracting the sources of the vmmon module.

Building the vmmon module.

Using 2.6.x kernel build system.
make: Entering directory `/tmp/vmware-config6/vmmon-only'
make -C /lib/modules/2.6.20-16-generic/build/include/.. SUBDIRS=$PWD SRCROOT=$PWD/. modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-16-generic'
  CC [M]  /tmp/vmware-config6/vmmon-only/linux/driver.o
In file included from /tmp/vmware-config6/vmmon-only/linux/driver.c:80:
/tmp/vmware-config6/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;compat_exit&#8217;
/tmp/vmware-config6/vmmon-only/./include/compat_kernel.h:21: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;exit_code&#8217;
/tmp/vmware-config6/vmmon-only/./include/compat_kernel.h:21: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;_syscall1&#8217;
make[2]: *** [/tmp/vmware-config6/vmmon-only/linux/driver.o] Error 1
make[1]: *** [_module_/tmp/vmware-config6/vmmon-only] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-16-generic'
make: *** [vmmon.ko] Error 2
make: Leaving directory `/tmp/vmware-config6/vmmon-only'
Unable to build the vmmon module.

For more information on how to troubleshoot module-related problems, please 
visit our Web site at "http://www.vmware.com/download/modules/modules.html" and
"http://www.vmware.com/support/reference/linux/prebuilt_modules_linux.html".

Execution aborted.

If somebody,anybody know what to do please post a reply

---

### Post by bsimpson63 on 2008-01-22
If anyone is still struggling with this, the solution can be found here: [http://pieter.wigleven.com/it/archives/11](http://pieter.wigleven.com/it/archives/11)

Basically, keep focus on the Windows installation until you get past the "Installing Devices" step.

---

### Post by rosegarden78 on 2008-01-22
When I was researching way to use Windows and other operating systems with Ubuntu I came across a few alternatives

wine
qemu
bochs
vmware

Of the four alternative I could only manage to get the first two to work.  WINE is like built in to Lindows and Ubuntu too.  QEMU is from the same author as WINE and FFMPEG. QEMU is a virtual PC you can install to a qcow file like a partition.  I've installed Windows XP, Windows 3.1 and possibly 98 in a qcow format.  In fact, I keep a fresh install of activated Windows XP in a QCOW backup.

As far as WINE is concerned, you just need to make a symlink from your Common Files (located in Program Files) to your /home/user/.wine/.../Program\ Files/ directory, replacing the user and ... with the actual path to your .wine directory.  It's hidden so turn on view hidden files if you can't see it. So like for me it's a link to /media/sda1/windows/... ...

---

