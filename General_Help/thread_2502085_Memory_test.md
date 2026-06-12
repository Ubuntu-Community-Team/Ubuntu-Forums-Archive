---
title: "Memory test?"
date: 2024-11-01
forum: General Help
---

### Post by corradoventu on 2024-11-01
In the GRUB menu I see 2 lines I don't understand:
> Memory test (memtest86+x64.efi)
Memory test (memtest86+x64.efi, serial console)
If at boot I select one of these lines nothing happen.
what are they for? what should they do?
Thanks.

---

### Post by 1fallen on 2024-11-01
The memory test is there so that you can test the memory in your machine.

This is not something I have ever done myself, it is only useful if you are having some problems with your computer and want to try to find the cause.

Memtest86 and Memtest86+ are not part of the Grub bootloader, they are separate hardware diagnostic tools. They are included in Ubuntu's default boot menus for convenience.

They cannot be run under Linux (or Windows); they must be booted into like an operating system so that they can access the entirety of a machine's physical memory for testing.

If you don't want them in Ubuntu, you can remove the memtest86+ package through the Apt package manager.

I wonder though if UEFI is in play with the tool, I remember a long while back it did not work well with UEFI systems.

EDIT:  to show what it does:
```
sudo memtester 1G 1
memtester version 4.6.0 (64-bit)
Copyright (C) 2001-2020 Charles Cazabon.
Licensed under the GNU General Public License version 2 (only).

pagesize is 4096
pagesizemask is 0xfffffffffffff000
want 1024MB (1073741824 bytes)
got  1024MB (1073741824 bytes), trying mlock ...locked.
Loop 1/1:
  Stuck Address       : ok         
  Random Value        : ok
  Compare XOR         : ok
  Compare SUB         : ok
  Compare MUL         : ok
  Compare DIV         : ok
  Compare OR          : ok
  Compare AND         : ok
  Sequential Increment: ok
  Solid Bits          : ok         
  Block Sequential    : ok         
  Checkerboard        : ok         
  Bit Spread          : ok         
  Bit Flip            : ok         
  Walking Ones        : ok         
  Walking Zeroes      : ok         
  8-bit Writes        : ok
  16-bit Writes       : ok

Done.


```
I  ran a very short run with only 1Gig checked with no stress

---

### Post by Doug S on 2024-11-01
I no longer have memtest86 as a boot option with Ubuntu. I now use a specific bootable memory stick with memtest installed.
Whenever I build a new computer, I will run memtest for at least a couple of days.

It has been a few years since I made the mem stick, but the label says "MEMTEST UEFI Bootable", so I assume it is fine with UEFI.

---

### Post by 1fallen on 2024-11-01
> **Doug S said:**
>  I made the mem stick, but the label says_** "MEMTEST UEFI Bootable"**_, so I assume it is fine with UEFI.

+1 Yep that's the one

---

