---
title: "Error when attempting to boot Ubuntu"
date: 2014-06-11
forum: General Help
---

### Post by pizza4554 on 2014-06-11
I have an older computer that I use to toy around with Operating Systems and other programs I'm too afraid to use on my good computer. I tried to install Ubuntu onto it, but when I attempted to boot from a USB drive, the console boots it, then the loading screen with the picture of the keyboard comes up for a while, then the console returns printing the following message:

```

/bin/sh: error while loading shared libraries: /lib/i386-linux-gnu/libc.so.6:invalid ELF header
[    9.612230] Kernel panic - not syncing: Attempted to kill init! exitcode=0x00
007f00
[    9.612230]
[    9.612287] CPU: 0 PID: 1 Comm: init Not tainted 3.13.0-24-generic #46-Ubuntu
[    9.612334] Hardware name: Dell Computer Corporation Dimension 2400
     /0C2425, BIOS A03 09/19/2003
[    9.612385] 00000000 00000000 c5c5df1c c164b873 c192fe00 c5c5df3c c16469ac c
1826f5c
[    9.612699] c1aa5c80 c5c5df28 c192fe00 c5179200 c5c90000 c5c5df8c c105911f c
1827280
[    9.163011] 00007f00 00000004 b7761f08 00000001 00000020 00000000 00000000 c
5153008
[    9.163324] Call Trace:
[    9.613379]  [<c164b873>] dump_stack+0x41/0x52
[    9.613425]  [<c16469ac>] panic+0x87/0x181
[    9.613470]  [<c105911f>] do_exit+0x8ef/0x8f0
[    9.613514]  [<c1059194>] do_group_exit+0x34/0xa0
[    9.613558]  [<c1059216>] SyS_exit_group+0x16/0x20
[    9.613604]  [<c1652947>] syscall_call+0x7/0xb

```

The Scroll lock and caps lock key blink on and off. I'm not sure what all this means, so if anyone could tell me what the problem is, I'd appreciate it. Thanks!

---

### Post by QIII on 2014-06-11
*Moved to **General Support**.*

---

### Post by Bucky Ball on 2014-06-11
Welcome. Which release, thanks? If the specs are low on the old machine then maybe you'd be better off with a lighter flavour, e.g. Xubuntu or particularly Lubuntu. How much RAM do you have? What processor? 32bit or 64bit processor?

---

