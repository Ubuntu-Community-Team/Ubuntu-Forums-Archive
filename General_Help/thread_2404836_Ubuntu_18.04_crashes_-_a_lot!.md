---
title: "Ubuntu 18.04 crashes - a lot!"
date: 2018-10-29
forum: General Help
---

### Post by naomibrown on 2018-10-29
Hi,

I've never had this happen before, until about a week ago. My computer crashes, seemingly randomly, regularly. Sometimes up to four times a day. Sometimes not at all. I've tried key combinations suggested by others: 

Ctrl+Alt+F3 and Alt+SysRq+R - to kill the XServer.
I don't have another computer to use, so couldn't try SSHing in. 
Alt+SysRq+REISUB - to restart

None of those work. So I've been powering off the machine. When it reboots it seems fine! It has crashed twice this morning now in less than an hour so now I'm getting irritated. 

I looked up the crash reports (never really looked at these before!) but it doesn't make a lot of sense to me. I've tried to attach it to see if it makes more sense to someone else ... but it says that it's an invalid file?

Thanks,
Naomi

---

### Post by georgit1 on 2018-10-29
Hi,
Ive been using Linux (Ubuntu, Arch etc) for more than 10 years now. 
I got this bug too. On my pc and on my laptop. On the laptop it is worst as it happens a lot more often. 
What I found was that this only happens if I'm using kernel 4.10 or newer. With kernel 4.9 my system does not freeze. I tryed Ubuntu, Antergos, Deepin. Also KDE, GNOME, UNITY and other DE, but as long as the system uses kernel 4.10 or newer - it freezes.
On my laptop it usually happens when I play big video file, but most of the time it is completely random. I would really like to know what causes this bug and I hope that it will be fixed in future.

---

### Post by HermanAB on 2018-10-29
OK, thanks very much for the report about kernel 4.9 working reliably.  I have also seen weirdness with 18.04 and my solution was to go back to the previous LTS version.

---

### Post by georgit1 on 2018-10-29
Yes. 
What I found was that with kernel 4.18 and 4.19 system was more stable - freezing less often. The web is full of such complains, but seems like most users havent noticed that it is kernel related. Hope it will be fixed soon.

---

### Post by dino99 on 2018-10-29
If you are affected, then use the log to find the reason:
'journalctl -b' for the present session
'journalctl -b -1' for the previous one, and so on
Scroll down the log where you got the crash.

If the system is instable, that can mean:
- system needs some clean up: use autoremove, gtkorphan, bleachbit (as root, select carefully settings)
- some partition(s) are too full: free space might be at least 10 to 15 % to let temp activity working.

---

### Post by naomibrown on 2018-11-01
Hi,

I've just run autoremove and gtkorphan. 

If I've got this right, these are the last two times that it froze. 

```
-- Logs begin at Mon 2018-10-01 17:28:20 BST, end at Thu 2018-11-01 17:26:57 GMT
Nov 01 09:23:21 Tigger kernel: microcode: microcode updated early to revision 0x
Nov 01 09:23:21 Tigger kernel: Linux version 4.15.0-38-generic (buildd@lcy01-amd
Nov 01 09:23:21 Tigger kernel: Command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-38-
Nov 01 09:23:21 Tigger kernel: KERNEL supported cpus:
Nov 01 09:23:21 Tigger kernel:   Intel GenuineIntel
Nov 01 09:23:21 Tigger kernel:   AMD AuthenticAMD
Nov 01 09:23:21 Tigger kernel:   Centaur CentaurHauls
Nov 01 09:23:21 Tigger kernel: x86/fpu: Supporting XSAVE feature 0x001: 'x87 flo
Nov 01 09:23:21 Tigger kernel: x86/fpu: Supporting XSAVE feature 0x002: 'SSE reg
Nov 01 09:23:21 Tigger kernel: x86/fpu: Supporting XSAVE feature 0x004: 'AVX reg
Nov 01 09:23:21 Tigger kernel: x86/fpu: xstate_offset[2]:  576, xstate_sizes[2]:
Nov 01 09:23:21 Tigger kernel: x86/fpu: Enabled xstate features 0x7, context siz
Nov 01 09:23:21 Tigger kernel: e820: BIOS-provided physical RAM map:
Nov 01 09:23:21 Tigger kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009
Nov 01 09:23:21 Tigger kernel: BIOS-e820: [mem 0x000000000009d800-0x000000000009
Nov 01 09:23:21 Tigger kernel: BIOS-e820: [mem 0x00000000000e0000-0x00000000000f
Nov 01 09:23:21 Tigger kernel: BIOS-e820: [mem 0x0000000000100000-0x00000000cf58
Nov 01 09:23:21 Tigger kernel: BIOS-e820: [mem 0x00000000cf585000-0x00000000cf5d
Nov 01 09:23:21 Tigger kernel: BIOS-e820: [mem 0x00000000cf5d8000-0x00000000cf5f
Nov 01 09:23:21 Tigger kernel: BIOS-e820: [mem 0x00000000cf5fd000-0x00000000cf5f
Nov 01 09:23:21 Tigger kernel: BIOS-e820: [mem 0x00000000cf5fe000-0x00000000cf60
Nov 01 09:23:21 Tigger kernel: BIOS-e820: [mem 0x00000000cf60e000-0x00000000cf61
lines 1-23...skipping...
-- Logs begin at Mon 2018-10-01 17:28:20 BST, end at Thu 2018-11-01 17:26:57 GMT. --
Nov 01 09:23:21 Tigger kernel: microcode: microcode updated early to revision 0x2e, date = 2018-04-10
Nov 01 09:23:21 Tigger kernel: Linux version 4.15.0-38-generic (buildd@lcy01-amd64-023) (gcc version 7.3.0 (Ubuntu 7.3.0-16ubuntu3)) 
Nov 01 09:23:21 Tigger kernel: Command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-38-generic root=UUID=63cde20a-e93c-4472-83ce-154c0e7047f
Nov 01 09:23:21 Tigger kernel: KERNEL supported cpus:
Nov 01 09:23:21 Tigger kernel:   Intel GenuineIntel
Nov 01 09:23:21 Tigger kernel:   AMD AuthenticAMD
Nov 01 09:23:21 Tigger kernel:   Centaur CentaurHauls
Nov 01 09:23:21 Tigger kernel: x86/fpu: Supporting XSAVE feature 0x001: 'x87 floating point registers'
Nov 01 09:23:21 Tigger kernel: x86/fpu: Supporting XSAVE feature 0x002: 'SSE registers'
Nov 01 09:23:21 Tigger kernel: x86/fpu: Supporting XSAVE feature 0x004: 'AVX registers'
Nov 01 09:23:21 Tigger kernel: x86/fpu: xstate_offset[2]:  576, xstate_sizes[2]:  256
Nov 01 09:23:21 Tigger kernel: x86/fpu: Enabled xstate features 0x7, context size is 832 bytes, using 'standard' format.
Nov 01 09:23:21 Tigger kernel: e820: BIOS-provided physical RAM map:
Nov 01 09:23:21 Tigger kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009d7ff] usable
Nov 01 09:23:21 Tigger kernel: BIOS-e820: [mem 0x000000000009d800-0x000000000009ffff] reserved
Nov 01 09:23:21 Tigger kernel: BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
Nov 01 09:23:21 Tigger kernel: BIOS-e820: [mem 0x0000000000100000-0x00000000cf584fff] usable
Nov 01 09:23:21 Tigger kernel: BIOS-e820: [mem 0x00000000cf585000-0x00000000cf5d7fff] ACPI NVS
Nov 01 09:23:21 Tigger kernel: BIOS-e820: [mem 0x00000000cf5d8000-0x00000000cf5fcfff] reserved
Nov 01 09:23:21 Tigger kernel: BIOS-e820: [mem 0x00000000cf5fd000-0x00000000cf5fdfff] usable
Nov 01 09:23:21 Tigger kernel: BIOS-e820: [mem 0x00000000cf5fe000-0x00000000cf60dfff] reserved
Nov 01 09:23:21 Tigger kernel: BIOS-e820: [mem 0x00000000cf60e000-0x00000000cf615fff] ACPI NVS
Nov 01 09:23:21 Tigger kernel: BIOS-e820: [mem 0x00000000cf616000-0x00000000cf618fff] reserved
Nov 01 09:23:21 Tigger kernel: BIOS-e820: [mem 0x00000000cf619000-0x00000000cf61cfff] ACPI NVS
Nov 01 09:23:21 Tigger kernel: BIOS-e820: [mem 0x00000000cf61d000-0x00000000cf63cfff] reserved
Nov 01 09:23:21 Tigger kernel: BIOS-e820: [mem 0x00000000cf63d000-0x00000000cf67ffff] ACPI NVS
Nov 01 09:23:21 Tigger kernel: BIOS-e820: [mem 0x00000000cf680000-0x00000000cf7fffff] usable
Nov 01 09:23:21 Tigger kernel: BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
Nov 01 09:23:21 Tigger kernel: BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
Nov 01 09:23:21 Tigger kernel: BIOS-e820: [mem 0x0000000100000000-0x000000022f7fffff] usable
Nov 01 09:23:21 Tigger kernel: NX (Execute Disable) protection: active
Nov 01 09:23:21 Tigger kernel: SMBIOS 2.6 present.
Nov 01 09:23:21 Tigger kernel: DMI: Dell Inc. XPS 8300  /002RX9, BIOS A01 12/21/2010
Nov 01 09:23:21 Tigger kernel: e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Nov 01 09:23:21 Tigger kernel: e820: remove [mem 0x000a0000-0x000fffff] usable
Nov 01 09:23:21 Tigger kernel: e820: last_pfn = 0x22f800 max_arch_pfn = 0x400000000
Nov 01 09:23:21 Tigger kernel: MTRR default type: uncachable
Nov 01 09:23:21 Tigger kernel: MTRR fixed ranges enabled:
Nov 01 09:23:21 Tigger kernel:   00000-9FFFF write-back
Nov 01 09:23:21 Tigger kernel:   A0000-BFFFF uncachable
Nov 01 09:23:21 Tigger kernel:   C0000-CFFFF write-protect
Nov 01 09:23:21 Tigger kernel:   D0000-E7FFF uncachable
Nov 01 09:23:21 Tigger kernel:   E8000-FFFFF write-protect
Nov 01 09:23:21 Tigger kernel: MTRR variable ranges enabled:
Nov 01 09:23:21 Tigger kernel:   0 base 000000000 mask E00000000 write-back
Nov 01 09:23:21 Tigger kernel:   1 base 200000000 mask FC0000000 write-back
Nov 01 09:23:21 Tigger kernel:   2 base 0D0000000 mask FF0000000 uncachable
Nov 01 09:23:21 Tigger kernel:   3 base 0E0000000 mask FE0000000 uncachable
Nov 01 09:23:21 Tigger kernel:   4 base 22F800000 mask FFF800000 uncachable
Nov 01 09:23:21 Tigger kernel:   5 base 230000000 mask FF0000000 uncachable

Then before that:

-- Logs begin at Mon 2018-10-01 17:28:20 BST, end at Thu 2018-11-01 17:23:08 GMT
Nov 01 09:13:58 Tigger kernel: microcode: microcode updated early to revision 0x
Nov 01 09:13:58 Tigger kernel: Linux version 4.15.0-38-generic (buildd@lcy01-amd
Nov 01 09:13:58 Tigger kernel: Command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-38-
Nov 01 09:13:58 Tigger kernel: KERNEL supported cpus:
Nov 01 09:13:58 Tigger kernel:   Intel GenuineIntel
Nov 01 09:13:58 Tigger kernel:   AMD AuthenticAMD
Nov 01 09:13:58 Tigger kernel:   Centaur CentaurHauls
Nov 01 09:13:58 Tigger kernel: x86/fpu: Supporting XSAVE feature 0x001: 'x87 flo
Nov 01 09:13:58 Tigger kernel: x86/fpu: Supporting XSAVE feature 0x002: 'SSE reg
Nov 01 09:13:58 Tigger kernel: x86/fpu: Supporting XSAVE feature 0x004: 'AVX reg
Nov 01 09:13:58 Tigger kernel: x86/fpu: xstate_offset[2]:  576, xstate_sizes[2]:
Nov 01 09:13:58 Tigger kernel: x86/fpu: Enabled xstate features 0x7, context siz
Nov 01 09:13:58 Tigger kernel: e820: BIOS-provided physical RAM map:
Nov 01 09:13:58 Tigger kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009
Nov 01 09:13:58 Tigger kernel: BIOS-e820: [mem 0x000000000009d800-0x000000000009
Nov 01 09:13:58 Tigger kernel: BIOS-e820: [mem 0x00000000000e0000-0x00000000000f
Nov 01 09:13:58 Tigger kernel: BIOS-e820: [mem 0x0000000000100000-0x00000000cf58
Nov 01 09:13:58 Tigger kernel: BIOS-e820: [mem 0x00000000cf585000-0x00000000cf5d
Nov 01 09:13:58 Tigger kernel: BIOS-e820: [mem 0x00000000cf5d8000-0x00000000cf5f
Nov 01 09:13:58 Tigger kernel: BIOS-e820: [mem 0x00000000cf5fd000-0x00000000cf5f
Nov 01 09:13:58 Tigger kernel: BIOS-e820: [mem 0x00000000cf5fe000-0x00000000cf60
Nov 01 09:13:58 Tigger kernel: BIOS-e820: [mem 0x00000000cf60e000-0x00000000cf61
lines 1-23...skipping...
-- Logs begin at Mon 2018-10-01 17:28:20 BST, end at Thu 2018-11-01 17:23:08 GMT. --
Nov 01 09:13:58 Tigger kernel: microcode: microcode updated early to revision 0x2e, date = 2018-04-10
Nov 01 09:13:58 Tigger kernel: Linux version 4.15.0-38-generic (buildd@lcy01-amd64-023) (gcc version 7.3.0 (Ubuntu 7.3.0-16ubuntu3)) 
Nov 01 09:13:58 Tigger kernel: Command line: BOOT_IMAGE=/boot/vmlinuz-4.15.0-38-generic root=UUID=63cde20a-e93c-4472-83ce-154c0e7047f
Nov 01 09:13:58 Tigger kernel: KERNEL supported cpus:
Nov 01 09:13:58 Tigger kernel:   Intel GenuineIntel
Nov 01 09:13:58 Tigger kernel:   AMD AuthenticAMD
Nov 01 09:13:58 Tigger kernel:   Centaur CentaurHauls
Nov 01 09:13:58 Tigger kernel: x86/fpu: Supporting XSAVE feature 0x001: 'x87 floating point registers'
Nov 01 09:13:58 Tigger kernel: x86/fpu: Supporting XSAVE feature 0x002: 'SSE registers'
Nov 01 09:13:58 Tigger kernel: x86/fpu: Supporting XSAVE feature 0x004: 'AVX registers'
Nov 01 09:13:58 Tigger kernel: x86/fpu: xstate_offset[2]:  576, xstate_sizes[2]:  256
Nov 01 09:13:58 Tigger kernel: x86/fpu: Enabled xstate features 0x7, context size is 832 bytes, using 'standard' format.
Nov 01 09:13:58 Tigger kernel: e820: BIOS-provided physical RAM map:
Nov 01 09:13:58 Tigger kernel: BIOS-e820: [mem 0x0000000000000000-0x000000000009d7ff] usable
Nov 01 09:13:58 Tigger kernel: BIOS-e820: [mem 0x000000000009d800-0x000000000009ffff] reserved
Nov 01 09:13:58 Tigger kernel: BIOS-e820: [mem 0x00000000000e0000-0x00000000000fffff] reserved
Nov 01 09:13:58 Tigger kernel: BIOS-e820: [mem 0x0000000000100000-0x00000000cf584fff] usable
Nov 01 09:13:58 Tigger kernel: BIOS-e820: [mem 0x00000000cf585000-0x00000000cf5d7fff] ACPI NVS
Nov 01 09:13:58 Tigger kernel: BIOS-e820: [mem 0x00000000cf5d8000-0x00000000cf5fcfff] reserved
Nov 01 09:13:58 Tigger kernel: BIOS-e820: [mem 0x00000000cf5fd000-0x00000000cf5fdfff] usable
Nov 01 09:13:58 Tigger kernel: BIOS-e820: [mem 0x00000000cf5fe000-0x00000000cf60dfff] reserved
Nov 01 09:13:58 Tigger kernel: BIOS-e820: [mem 0x00000000cf60e000-0x00000000cf615fff] ACPI NVS
Nov 01 09:13:58 Tigger kernel: BIOS-e820: [mem 0x00000000cf616000-0x00000000cf618fff] reserved
Nov 01 09:13:58 Tigger kernel: BIOS-e820: [mem 0x00000000cf619000-0x00000000cf61cfff] ACPI NVS
Nov 01 09:13:58 Tigger kernel: BIOS-e820: [mem 0x00000000cf61d000-0x00000000cf63cfff] reserved
Nov 01 09:13:58 Tigger kernel: BIOS-e820: [mem 0x00000000cf63d000-0x00000000cf67ffff] ACPI NVS
Nov 01 09:13:58 Tigger kernel: BIOS-e820: [mem 0x00000000cf680000-0x00000000cf7fffff] usable
Nov 01 09:13:58 Tigger kernel: BIOS-e820: [mem 0x00000000fed1c000-0x00000000fed1ffff] reserved
Nov 01 09:13:58 Tigger kernel: BIOS-e820: [mem 0x00000000ff000000-0x00000000ffffffff] reserved
Nov 01 09:13:58 Tigger kernel: BIOS-e820: [mem 0x0000000100000000-0x000000022f7fffff] usable
Nov 01 09:13:58 Tigger kernel: NX (Execute Disable) protection: active
Nov 01 09:13:58 Tigger kernel: SMBIOS 2.6 present.
Nov 01 09:13:58 Tigger kernel: DMI: Dell Inc. XPS 8300  /002RX9, BIOS A01 12/21/2010
Nov 01 09:13:58 Tigger kernel: e820: update [mem 0x00000000-0x00000fff] usable ==> reserved
Nov 01 09:13:58 Tigger kernel: e820: remove [mem 0x000a0000-0x000fffff] usable
Nov 01 09:13:58 Tigger kernel: e820: last_pfn = 0x22f800 max_arch_pfn = 0x400000000
Nov 01 09:13:58 Tigger kernel: MTRR default type: uncachable
Nov 01 09:13:58 Tigger kernel: MTRR fixed ranges enabled:
Nov 01 09:13:58 Tigger kernel:   00000-9FFFF write-back
Nov 01 09:13:58 Tigger kernel:   A0000-BFFFF uncachable
Nov 01 09:13:58 Tigger kernel:   C0000-CFFFF write-protect
Nov 01 09:13:58 Tigger kernel:   D0000-E7FFF uncachable
Nov 01 09:13:58 Tigger kernel:   E8000-FFFFF write-protect
Nov 01 09:13:58 Tigger kernel: MTRR variable ranges enabled:
Nov 01 09:13:58 Tigger kernel:   0 base 000000000 mask E00000000 write-back
Nov 01 09:13:58 Tigger kernel:   1 base 200000000 mask FC0000000 write-back
Nov 01 09:13:58 Tigger kernel:   2 base 0D0000000 mask FF0000000 uncachable
Nov 01 09:13:58 Tigger kernel:   3 base 0E0000000 mask FE0000000 uncachable
Nov 01 09:13:58 Tigger kernel:   4 base 22F800000 mask FFF800000 uncachable
Nov 01 09:13:58 Tigger kernel:   5 base 230000000 mask FF0000000 uncachable
```

I've also had problems (that I hadn't really noticed!) about when I try to boot my computer. Not every time, but about a once every five times. I hear four short, repeated beeps and a flashing on/off power button. The most recent that this happened, I've unplugged it, and held down the power button for 15 seconds (as suggested by a site I found online somewhere). This allowed it to start normally. 

Thanks!
Naomi

---

