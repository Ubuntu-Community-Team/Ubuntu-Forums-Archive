---
title: "Wubi boot problems"
date: 2007-06-29
forum: General Help
---

### Post by CAVX on 2007-06-29
Hello there.
I'm new to all of this as of yesterday.
But I stumbled upon Wubi and UbuntuStudio and decided that I really wanted to try them both out.

Anyway, I can only ever get so far. I've reinstalled a few times, and every time I have, Ubuntu has frozen in a different stage.

I also have run chkdsk a lot, and most of the time there are a ton of orphaned files. Is there some sort of safe reboot that I don't know about?

Anyway, after looking around here, I found c:\wubi\boot\grub\menu.lst and removed all instances of "quiet splash".
At this particular moment, it freezes up when it reaches the line "Begin: Waiting for root file system..."

I'd appreciate some help. Thanks in advance.

---

### Post by ago on 2007-06-29
Can you try with a fresh install? In case remove quiet splash from the beginning. If you get stacked use Ctrl+Alt+Del or Alt+SysRq key combinations (see google)

---

### Post by CAVX on 2007-06-29
Okay, so I reinstalled and immediately took out the quiet splash.
The first few times, I couldn't get the blue screen installation to come up, but after a few tries it did.
After everything there went through, I restarted again only to get stacked at this line:
```
*Checking file systems...
fsck 1.40 WIP (14-Nov-2006)
```
I have been stuck there previously also.
Anyway, I couldn't use either method to reboot so I had to manually power off. The system wouldn't let me back on to the boot screen, saying that Windows couldn't start (prior to choosing between Windows and Ubuntu).
I was able to get a chkdsk done, which solved that.

Now what happens is consistent. I like that. Regardless of chkdsk or a reboot, it always stops here (again, not able to reboot):
```
[  22.277652] Compat vDSO mapped to fffe000.
[  22.277706] Remapping vsycall page to fffe000.
[  22.277767] Checking 'hit' instruction...OK.
[  22.281163] SMP alternatives: switching to UP code
[  22.281518] Early unpacking initramfs...done
[  22.655764] ACPI: Core revision 20060707
[  22.658776] ACPI: Looking for DSDT in initramfs... fil /DSDT.aml not found,
using machine DSDT.
[  22.869534] CPU0: AMD Turion (tm) 64 x2 Mobile Technology TL-50 stepping 02
[  22.869691] SMP alternatives: switching to SMP code
[  22.869808] Booting processor 1/1 eip 3000
[  22.880282] Initializing CPU#1
[  22.941076] Calibrating delay using timer specific routine... 3214.67 BogoMPS
(lpj=1607339)
[  22.941091] CPU: L1 I Cache: 64K (64 Bytes/line), D cache 64K (64 Bytes/line)
[  22.941094] CPUL L2 Cache: 256K (64 Bytes/line)
[  22.941097] CPU 1(2) -> Core 1
[  22.941044] CPU1: AMD Turion(tm) 64 x2 Mobile Technology TL-50 stepping 02
[  22.941454] Total of 2 processors activated (6431.63 BogoMIPS)
[  22.941021] ENABLING 10-APIC IRQs
[  22.942127] ..TIMER: vector=0x31 apic1=0 pin1=2 apic2=-1 pin2=-1
[  23.053896] checking TSC synchronization across 2 CPU's:
[   0.000048] CPU#0 had -84 usecs TSC skew, fixed it up.
[   0.000101] CPU #1 has 84 usecs TSC skew, fixed it up.
```

Any ideas?

EDIT - [This bug]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/110396/+viewstatus") may be related to my problem because it stops where mine does now. Also, I have an HP Pavilion Laptop. But I don't really understand anything else about the page.

---

### Post by ago on 2007-07-02
Yep that is quite likely. If standard ubuntu cannot boot, Wubi would fail as well.

---

