---
title: "Gutsy - won't load/detect second cpu (Athlon MP 1900+)"
date: 2007-10-24
forum: General Help
---

### Post by josephus on 2007-10-24
I'm having trouble with Gutsy loading up the second CPU on my Athlon MP 1900+.  I've been loading up the old kernel from Feisty and things seem to work properly with that.

```
uname -a
Linux desktop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux
```

The grub boot entry looks like:

```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=532f9bf9-f0e9-4021-a654-eb45f8e13834 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic

```

I've looked through the logs, and it appears that the cpu is detected but fails to respond.  Is there some parameters that I should tweak, or is this a bug in the kernel?

/var/log/syslog:


```
Oct 24 17:47:10 desktop kernel: [    0.084000] CPU: After generic identify, caps: 0383fbff c1cbfbff 00000000 00000000 00000000 00000000 00000000
Oct 24 17:47:10 desktop kernel: [    0.084000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
Oct 24 17:47:10 desktop kernel: [    0.084000] CPU: L2 Cache: 256K (64 bytes/line)
Oct 24 17:47:10 desktop kernel: [    0.084000] CPU: After all inits, caps: 0383fbff c1cbfbff 00000000 00000420 00000000 00000000 00000000
Oct 24 17:47:10 desktop kernel: [    0.084000] Compat vDSO mapped to ffffe000.
Oct 24 17:47:10 desktop kernel: [    0.084000] Checking 'hlt' instruction... OK.
Oct 24 17:47:10 desktop kernel: [    0.100000] SMP alternatives: switching to UP code
Oct 24 17:47:10 desktop kernel: [    0.100000] Early unpacking initramfs... done
Oct 24 17:47:10 desktop kernel: [    0.532000] ACPI: Core revision 20070126
Oct 24 17:47:10 desktop kernel: [    0.532000] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
Oct 24 17:47:10 desktop kernel: [    0.532000] CPU0: AMD Athlon(tm) MP 1900+ stepping 02
Oct 24 17:47:10 desktop kernel: [    0.532000] SMP alternatives: switching to SMP code
Oct 24 17:47:10 desktop kernel: [    0.532000] Booting processor 1/1 eip 3000
Oct 24 17:47:10 desktop kernel: [    5.812000] Not responding.
Oct 24 17:47:10 desktop kernel: [    5.812000] Inquiring remote APIC #1...
Oct 24 17:47:10 desktop kernel: [    5.812000] ... APIC #1 ID: 1000000
Oct 24 17:47:10 desktop kernel: [    5.812000] ... APIC #1 VERSION: 40010
Oct 24 17:47:10 desktop kernel: [    5.812000] ... APIC #1 SPIV: ff
Oct 24 17:47:10 desktop kernel: [    5.812000] CPU #1 not responding - cannot use it.
Oct 24 17:47:10 desktop kernel: [    5.812000] Total of 1 processors activated (3204.11 BogoMIPS).
Oct 24 17:47:10 desktop kernel: [    5.812000] ENABLING IO-APIC IRQs
Oct 24 17:47:10 desktop kernel: [    5.812000] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
Oct 24 17:47:10 desktop kernel: [    5.852000] Brought up 1 CPUs
```

---

