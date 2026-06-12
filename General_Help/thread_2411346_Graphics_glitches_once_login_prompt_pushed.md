---
title: "Graphics glitches once login prompt pushed"
date: 2019-01-29
forum: General Help
---

### Post by thamyd on 2019-01-29
I have an old machine I'm working on that uses 32bit EFI to boot, however i've managed to get ubuntu server 14.04 running on it. I know its running because I can blindly type commands and also ssh into it once the screen starts glitching, however the actual video output of the machine is just lots of garbled dots on the command line. This happens when I pass nomodeset at boot, without nomodeset the screen freezes just before login. Has anyone experienced this before? I very much appreciate any help given, thanks!

---

### Post by Autodave on 2019-01-29
Can you give us some specs on this machine please?

---

### Post by thamyd on 2019-01-29
Yep sorry, the machine is a XServe 1,1 with a Radeon X1300 graphics card. I actually had it displaying correctly the other night but after tinkering with some boot files in the boot/efi/ partition its reverted back to having display issues.

---

