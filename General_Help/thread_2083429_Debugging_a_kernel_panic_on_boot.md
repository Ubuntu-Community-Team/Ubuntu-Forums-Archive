---
title: "Debugging a kernel panic on boot"
date: 2012-11-12
forum: General Help
---

### Post by Fortrek on 2012-11-12
Configuration: Alienware m17x with Kingston 120GB SSD as sda, Hitachi 500GB as sdb, nVidia GTX260M, Intel Core2 Quad.

Install: Most current updates of 12.04 including linux-3.2.0-19-generic x86_64. 

Problem: When booting any 12.04 kernel other than 3.2.0-17-generic (I believe it happened with 3.0.0-16; know it happens with 3.2.0-18 and -19) grub comes up and permits me to make my selection. Then, whether I select standard or recovery, the machine locks up after 2.5 seconds.

The numeric and caps lock leds begin blinking.

The 2.5 seconds is determined by watching the crash on the screen when booting a recovery configuration. Unfortunately the screen information shoots by very quickly and I haven't time to read anything before the crash stack dump. I can get the last few lines of that if it helps. 

The problem is that there is no writable device for logging so I cannot see the error on subsequent boots back in -17. How can I either: get the boot trace to print to the screen with a smaller font (or larger resolution) so I can see more to copy down? Or get it to log somewhere else (have thumbdrive in or something?).

Looking at the trace of a working boot, it appears to be the moment that the SSD is being queried is where the lockup occurs. The drive is formatted with ext4 and is one big partition with a swap partition. I configured it before I understood where the swap should go and haven't moved it since the second spindle still boots fine and I can get work done over there. I will backup and move swap once 12.04 boots reliably. 

I want to report on what is going wrong but I really don't know what tools to use to capture a boot log before the boot log is recorded.

Thank.

---

