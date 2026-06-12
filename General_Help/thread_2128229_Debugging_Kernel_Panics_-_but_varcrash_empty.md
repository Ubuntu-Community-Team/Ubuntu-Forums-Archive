---
title: "Debugging Kernel Panics - but /var/crash empty"
date: 2013-03-22
forum: General Help
---

### Post by sandyd on 2013-03-22
I am currently running Ubuntu 12.10.
Both in 12.04, and 12.10, I have been noticing random Kernel Panics that seem to happen only when I am not using the laptop.

I went to follow the [guide]("https://help.ubuntu.com/12.10/serverguide/kernel-crash-dump.html") for getting the crash dump, but after a simulated crash (using sysreq c), /var/crash is empty. It is also empty after one of those random Kernel Panics.

I have confirmed that crashdump has been added to my grub, and loaded (dmesg)

cat /proc/cmdline
```

BOOT_IMAGE=/vmlinuz-3.5.0-25-generic root=UUID=f84dd846-ad9e-4b58-93dc-8d48020f9089 ro rootflags=subvol=@ crashkernel=384M-2G:64M,2G-:128M quiet splash acpi_osi= vt.handoff=7
```

dmesg -i | grep crash
```

[    0.000000] Command line: BOOT_IMAGE=/vmlinuz-3.5.0-25-generic root=UUID=f84dd846-ad9e-4b58-93dc-8d48020f9089 ro rootflags=subvol=@ crashkernel=384M-2G:64M,2G-:128M quiet splash acpi_osi= vt.handoff=7
[    0.000000] Reserving 128MB of memory at 720MB for crashkernel (System RAM: 5995MB)
[    0.000000] Kernel command line: BOOT_IMAGE=/vmlinuz-3.5.0-25-generic root=UUID=f84dd846-ad9e-4b58-93dc-8d48020f9089 ro rootflags=subvol=@ crashkernel=384M-2G:64M,2G-:128M quiet splash acpi_osi= vt.handoff=7

```
EDIT: it now appears that kexec/kdump is not loading after the crash - system is not restarting


Any ideas?

---

### Post by sanderj on 2013-03-22
I can't help on your question, but: did you run memtest86 to rule out memory problems?

---

### Post by tgalati4 on 2013-03-22
What is the hardware?  Possible power supply issue?  How old is the hardware?

Linux is very good at capturing errors when they are truly software-generated.  Not so good at hardware errors--intermittent disk, bad RAM, wonky power supply.  The fact that the panics are happening during idle periods also points to hardware, as there are fewer processes running to contribute to a crash.  And, you have experienced the issue with both 12.04 and 12.10.  You can possibly rule out the hard disk by running a Live DVD session, and see how much uptime you get before a crash.  That would rule out the hard disk.  If it runs for several days without issue on the Live DVD, then you can start to look at the disk.

What are the SMART parameters of the disk drive?

---

### Post by matt_symes on 2013-03-22
Hi sandyd

Do you have ```
/proc/vmcore
``` ?

That's what it's dumping to the file. 

Take a look at 

```
/usr/share/initramfs-tools/scripts/init-bottom/0_kdump
```
```

KVER="`uname -r`"
CRASHFILE="/var/crash/vmcore"
MAKEDUMPFILE="/usr/bin/makedumpfile"
LOG="$rootmnt/var/crash/vmcore.log"
VMCORE="/proc/vmcore"

<snip>

chroot $rootmnt $MAKEDUMPFILE -E -d 31 $VMCORE $CRASHFILE > $LOG 2>&1
```

Also have a read of this

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/710733](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/710733)

I think that documentation is hopelessly out of date. Surley one should not have to compile a kernel just to get /proc/vmcore support ?

Still, you're doing better than i am.

```
matthew-S206:/home/matthew % cat /sys/kernel/{kexec_loaded,kexec_crash_loaded}
0
0
matthew-S206:/home/matthew % 
```

I'm not using a debug kernel, only a Ubuntu kernel from the ppa.
```

matthew-S206:/home/matthew % uname -r
3.9.0-030900rc3-generic
matthew-S206:/home/matthew % 
```

Kind regards

---

### Post by sandyd on 2013-03-22
> **sanderj said:**
> I can't help on your question, but: did you run memtest86 to rule out memory problems?

yep

---

### Post by sandyd on 2013-03-22
> **matt_symes said:**
> Hi sandyd

Do you have ```
/proc/vmcore
``` ?

That's what it's dumping to the file. 

Take a look at 

```
/usr/share/initramfs-tools/scripts/init-bottom/0_kdump
```
```

KVER="`uname -r`"
CRASHFILE="/var/crash/vmcore"
MAKEDUMPFILE="/usr/bin/makedumpfile"
LOG="$rootmnt/var/crash/vmcore.log"
VMCORE="/proc/vmcore"

<snip>

chroot $rootmnt $MAKEDUMPFILE -E -d 31 $VMCORE $CRASHFILE > $LOG 2>&1
```

Also have a read of this

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/710733](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/710733)

I think that documentation is hopelessly out of date. Surley one should not have to compile a kernel just to get /proc/vmcore support ?

Still, you're doing better than i am.

```
matthew-S206:/home/matthew % cat /sys/kernel/{kexec_loaded,kexec_crash_loaded}
0
0
matthew-S206:/home/matthew % 
```

I'm not using a debug kernel, only a Ubuntu kernel from the ppa.
```

matthew-S206:/home/matthew % uname -r
3.9.0-030900rc3-generic
matthew-S206:/home/matthew % 
```

Kind regards
I am missing a /proc/vmcore as well, but...
```

 cat /sys/kernel/{kexec_loaded,kexec_crash_loaded}
0
1
```

---

### Post by matt_symes on 2013-03-22
Hi

```
cat /sys/kernel/{kexec_loaded,kexec_crash_loaded} 
0 
1
```

You're using a debug kernel ? You compiled it yourself ?
```

matthew-S206:/boot/grub % cat /etc/default/kexec 
# Defaults for kexec initscript
# sourced by /etc/init.d/kexec and /etc/init.d/kexec-load

# Load a kexec kernel (true/false)
LOAD_KEXEC=true

# Kernel and initrd image
KERNEL_IMAGE="/vmlinuz"
INITRD="/initrd.img"

# If empty, use current /proc/cmdline
APPEND=""

# Load the default kernel from grub config (true/false)
USE_GRUB_CONFIG=true
matthew-S206:/boot/grub %
```

Is yours the same ?

Kind regards

---

### Post by sandyd on 2013-03-22
> **matt_symes said:**
> Hi

```
cat /sys/kernel/{kexec_loaded,kexec_crash_loaded} 
0 
1
```

You're using a debug kernel ? You compiled it yourself ?
```

matthew-S206:/boot/grub % cat /etc/default/kexec 
# Defaults for kexec initscript
# sourced by /etc/init.d/kexec and /etc/init.d/kexec-load

# Load a kexec kernel (true/false)
LOAD_KEXEC=true

# Kernel and initrd image
KERNEL_IMAGE="/vmlinuz"
INITRD="/initrd.img"

# If empty, use current /proc/cmdline
APPEND=""

# Load the default kernel from grub config (true/false)
USE_GRUB_CONFIG=true
matthew-S206:/boot/grub %
```

Is yours the same ?

Kind regards
Im using the debug kernels from [http://ddebs.ubuntu.com/pool/main/l/linux/](http://ddebs.ubuntu.com/pool/main/l/linux/)

the config is the same

---

### Post by matt_symes on 2013-03-23
Thanks sandyd. I'll be having a play over the weekend.

---

