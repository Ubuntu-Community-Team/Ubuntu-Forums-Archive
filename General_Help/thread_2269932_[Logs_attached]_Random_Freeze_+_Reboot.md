---
title: "[Logs attached] Random Freeze + Reboot"
date: 2015-03-19
forum: General Help
---

### Post by utkarsh4 on 2015-03-19
Hello everybody,
I am using Ubuntu since a year and a half now.
I use it to compile android ROMs.

About 5 months ago, I built a new machine.
Specs:-
CPU: Intel i5-4690K
RAM: Corsair Vengeance 8GB
GPU: MSI R6950 TwinFrozr III PE/OC
Motherboard: Asus Maximus VII Ranger
PSU: Season S12II Bronze 520W
HDD: Seagate 1TB ST1000DM001
SSD: Samsung 840 EVO 128GB
CPU Cooler: CM Hyper 212X

Only GPU is old (3.5 years now).
With my old PC and this GPU, I had no issues.
I was using Ubuntu 14.04 on it, didn't try it with 14.10
Now, I am using 14.10

My OS is up to date.
I have not installed any drivers myself.

The issue:
Ever since I am using this machine, every now and then it randomly freezes and then automatically reboots.
Once it freezes, frequency of freezes increase until I stop using it for long time. (I mean I use it daily but for short periods).
It's doesn't seem to be a hardware issue.
Whether I am compiling the ROM or just using chrome, it can reboot.
With GPU, my screen would just randomly freeze and stay as it is. 10-15 seconds later, PC will reboot.
Without GPU, my screen would go black. 10-15 seconds later, PC will reboot.

At multiple times, I have tried reinstalling the OS.
But the issue would return 6-7days later.

In Windows 8.1, I have absolutely no issues.
I ran OCCT for >90 minutes (CPU + GPU + RAM).
I have OCed my CPU to 4.6GHz@1.28V and applied XMP profile on my RAM.
I have also changed some other BIOS settings (related and unrelated to CPU).
It also doesn't seem to be a heating issue (It can even crash while using chrome).
So far I haven't been able to isolate the cause/trigger.

Logs: [https://drive.google.com/file/d/0B9H3V_TDVt5vSGRLUjdfc0U2clE/view?usp=sharing](https://drive.google.com/file/d/0B9H3V_TDVt5vSGRLUjdfc0U2clE/view?usp=sharing)
It is copy of /var/log
Before I took the logs:
1. Without GPU installed, my PC randomly rebooted.
2. Before Ubuntu could start loading (i.e. at grub screen), I turned PC off.
3. Installed GPU.
4. Booted PC and copied logs.

If there is something more I can do to help myself, Please tell me.

Regards,
Utkarsh

---

### Post by gordintoronto on 2015-03-19
I suggest you install an "Additional Driver." " You can find additional drivers available for your system in Software & Updates, under Additional Drivers tab..."

---

### Post by utkarsh4 on 2015-03-25
So I got the crash again, but this time I had already logged into console and this was printed:

```

[ 3873.846119] mce: [Hardware Error]: CPU 2: Machine Check Exception: 5 Bank 1: bf80000000000124
[ 3873.846160] mce: [Hardware Error]: RIP !INEXACT! 33:<00007f32309fcb67>
[ 3873.846188] mce: [Hardware Error]: TSC c55c2ce1665 ADDR 399f140 MISC 86
[ 3873.846217] mce: [Hardware Error]: PROCESSOR 0:306c3 TIME 1427271378 SOCKET 0 APIC 4 microcode 19
[ 3873.846253] mce: [Hardware Error]: Run the above through 'mcelog --ascii'
[ 3873.846280] mce: [Hardware Error]: Machine check: Processor context corrupt
[ 3873.846309] Kernel panic - not syncing: Fatal Machine check
[ 3873.846334] Kernel Offset: 0x1000000 from 0xffffffff81000000 (relocation range: 0xffffffff80000000-0xffffffffbfffffff)
[ 3873.846377] drm_kms_belper: panic occurred, switching back to text console
[ 3873.852094] Rebooting in 30 seconds..

```

Output of "sudo mcelog --ascii":
```

Hardware event. This is not a software error.
CPU 2 BANK 1 TSC c55c2ce1665 
RIP !INEXACT! 33:7f32309fcb67
MISC 86 ADDR 399f140 
TIME 1427271378 Wed Mar 25 13:46:18 2015
MCG status:RIPV MCIP 
MCi status:
Uncorrected error
Error enabled
MCi_MISC register valid
MCi_ADDR register valid
Processor context corrupt
SRAR
MCA: Data CACHE Level-0 Write Error
STATUS bf80000000000124 MCGSTATUS 5
CPUID Vendor Intel Family 6 Model 60
SOCKET 0 APIC 4 microcode 19

```

EDIT: Occured again, new log:
```

[ 11125.432434] mce: [Hardware Error]: CPU 2: Machine Check Exception: 5 Bank 1: bf80000000000124
[ 11125.432474] mce: [Hardware Error]: RIP !INEXACT! 10:<ffffffff817897b4> {down_write+0x24/0x40}
[ 11125.432512] mce: [Hardware Error]: TSC 29653c73606d ADDR db9d7c40 MISC 86
[ 11125.432542] mce: [Hardware Error]: PROCESSOR 0:306c3 TIME 1427371828 SOCKET 0 APIC 4 microcode 19
[ 11125.432578] mce: [Hardware Error]: Run the above through 'mcelog --ascii'
[ 11125.432606] mce: [Hardware Error]: Machine check: Processor context corrupt
[ 11125.432634] Kernel panic - not syncing: Fatal Machine check
[ 11125.432660] Kernel Offset: 0x1000000 from 0xffffffff81000000 (relocation range: 0xffffffff80000000-0xffffffffbfffffff)
[ 11125.432702] drm_kms_belper: panic occurred, switching back to text console
[ 11125.432872] Rebooting in 30 seconds..

```

Output of "sudo mcelog --ascii":
```

Hardware event. This is not a software error.
CPU 2 BANK 1 TSC 29653c73606d 
RIP !INEXACT! 10:ffffffff817897b4
MISC 86 ADDR db9d7c40 
TIME 1427371828 Thu Mar 26 17:40:28 2015
MCG status:RIPV MCIP 
MCi status:
Uncorrected error
Error enabled
MCi_MISC register valid
MCi_ADDR register valid
Processor context corrupt
SRAR
MCA: Data CACHE Level-0 Write Error
STATUS bf80000000000124 MCGSTATUS 5
CPUID Vendor Intel Family 6 Model 60
RIP: {down_write+0x24/0x40}
SOCKET 0 APIC 4 microcode 19

```

---

### Post by gordintoronto on 2015-03-25
So it's a hardware problem?

Could you please explain more about "logged into console"?

---

### Post by utkarsh4 on 2015-03-26
Well since windows is absolutely stable for me during stress test, I don't think it's a hardware problem.
Then again, I don't know much.

By logged into console I meant I pressed "ctrl+alt+f1" and then entered username/password.
This time when it crashed, that mce thing was printed. (as mentioned in previous post).
BTW, when it crashed, I was in desktop mode, not terminal mode, and it automatically switched to terminal.

---

### Post by utkarsh4 on 2015-04-01
So I reset my BIOS settings to default and everything seems good now.
I changed quite a bit of settings, but I think CPU/RAM overclock was causing the issue.
Will test different settings over the weekend and see if I can find the real culprit.

---

