---
title: "VM86 Syscall Generated Signal 4"
date: 2007-05-06
forum: General Help
---

### Post by AndrewNi on 2007-05-06
I posted a topic yesterday about not being able to use multiple sessions. It seems like it's worse than that.

X is crashing when I log off, and it's also crashing when I try to end a session. But X starts up properly when I boot the machine.

Here is a segment from the X log for a successful start:

```
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(II) I810(0): VESA BIOS detected
(II) I810(0): VESA VBE Version 3.0
```
Here it is once I try to end the session:

```
(II) I810(0): initializing int10
(WW) I810(0): Bad V_BIOS checksum
(II) I810(0): Primary V_BIOS segment is: 0xc000
(EE) I810(0): vm86() syscall generated signal 4.
(II) I810(0): EAX=0x00004d05, EBX=0x00000000, ECX=0x00000000, EDX=0x00000000
(II) I810(0): ESP=0x00000ffa, EBP=0x00000000, ESI=0x00000000, EDI=0x00002000
(II) I810(0): CS=0xc000, SS=0x0100, DS=0x0040, ES=0x0000, FS=0x0000, GS=0x0000
(II) I810(0): EIP=0x0000078b, EFLAGS=0x00033202
(II) I810(0): code at 0x000c078b:
 0f 00 00 00 00 00 00 00 05 0f ff 00 00 2a 00 00
 6a 2a 2a 15 15 3f 15 15 3f 3f 3f 00 05 11 1c 08
(II) stack at 0x00001ffa:
 00 06 00 00 00 32
(II) I810(0): VESA BIOS not detected
(EE) I810(0): VBE initialization failed.
```
I could really use some help with fixing this. It used to work so that I could end the session and start a new X session normally.

Thanks.

---

