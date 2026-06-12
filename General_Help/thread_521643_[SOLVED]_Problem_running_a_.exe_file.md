---
title: "[SOLVED] Problem running a .exe file"
date: 2007-08-09
forum: General Help
---

### Post by pauleh on 2007-08-09
I have a Linux installer program that runs successfully in ubuntu running under VMware using ./<filename>, but if I try exactly the same thing on a machine that boots to ubuntu I get a "not found" error.

The file is present in the cwd and I've opened up all the permissions.

Help !!

Thanks Paul

---

### Post by apetresc on 2007-08-09
I think this is the third time in 24 hours we've had this problem... :)

The problem is almost certainly the fact that the binary and your processor are not built for each other; one is 32-bit and the other is 64-bit.

Is your system 32-bit or 64-bit? (cat /proc/cpuinfo to check if you're not sure)
Is the binary 32-bit or 64-bit? (file /path/to/file to check if you're not sure)

Chances are they are not the same, and the binary will not work :( (It probably works on the Virtual Machine because the VM is emulating a 32-bit arch)

---

### Post by pauleh on 2007-08-09
Hi Adrian,

With this .exe both 32 bit and 64 bit binaries are "installed" and when the actual application is started the correct binary is picked dependent on platform.

Paul

---

### Post by apetresc on 2007-08-09
> **pauleh said:**
> Hi Adrian,

With this .exe both 32 bit and 64 bit binaries are "installed" and when the actual application is started the correct binary is picked dependent on platform.

Paul

Hmm, then what does ```
file /path/to/file.exe
``` return?

---

### Post by pauleh on 2007-08-09
I don't have access to the particular machine until tomorrow to run the file command.

What should I expect to see

Paul

---

### Post by apetresc on 2007-08-09
> **pauleh said:**
> I don't have access to the particular machine until tomorrow to run the file command.

What should I expect to see

Paul

Hopefully something like ```
adrian@rootbeer:~$ file callback
callback: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.6.0, dynamically linked (uses shared libs), not stripped
```
I'm mostly interested whether it's "ELF 32-bit" or "ELF 64-bit". Or if it's "ELF" at all.

---

### Post by pauleh on 2007-08-10
The machine in question is 64 bit and needed the 32 bit libraries installing.  Problem solved.  Thanks for your help.

Paul

---

