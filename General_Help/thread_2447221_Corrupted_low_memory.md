---
title: "Corrupted low memory"
date: 2020-07-15
forum: General Help
---

### Post by oygle on 2020-07-15
I noticed the following this morning; it is still appearing 7 hours later

> 
Jul 15 16:34:05 oygle-Inspiron-3542 kernel: [29184.958928] check: Corrupted low memory at 00000000a3e5fdab (3a50 phys) = 10000067900000
Jul 15 16:34:05 oygle-Inspiron-3542 kernel: [29184.958945] check: Corrupted low memory at 000000003751a815 (3a58 phys) = 10000067a0000000
Jul 15 16:34:05 oygle-Inspiron-3542 kernel: [29184.958961] check: Corrupted low memory at 000000002e7d0ab2 (3a60 phys) = 67b000000000
Jul 15 16:34:05 oygle-Inspiron-3542 kernel: [29184.958977] check: Corrupted low memory at 0000000097a1cb75 (3a68 phys) = 67c00000000010
Jul 15 16:34:05 oygle-Inspiron-3542 kernel: [29184.958994] check: Corrupted low memory at 000000006dbca086 (3a70 phys) = 67d0000000001000
Jul 15 16:34:05 oygle-Inspiron-3542 kernel: [29184.959014] check: Corrupted low memory at 00000000b2f68d0e (3a78 phys) = e000000000100000
Jul 15 16:34:05 oygle-Inspiron-3542 kernel: [29184.959031] check: Corrupted low memory at 00000000c02c13b8 (3a80 phys) = 10000067
Jul 15 16:34:05 oygle-Inspiron-3542 kernel: [29184.959047] check: Corrupted low memory at 00000000da933a65 (3a88 phys) = 10000067f0
Jul 15 16:34:05 oygle-Inspiron-3542 kernel: [29184.959064] check: Corrupted low memory at 0000000043455d69 (3a90 phys) = 5046240454504224
Jul 15 16:34:05 oygle-Inspiron-3542 kernel: [29184.959078] check: Corrupted low memory at 00000000249cc09c (3a98 phys) = 49584d0008003053
Jul 15 16:34:05 oygle-Inspiron-3542 kernel: [29184.959098] check: Corrupted low memory at 000000009915bd5e (3aa0 phys) = 20552f4c35322043
Jul 15 16:34:05 oygle-Inspiron-3542 kernel: [29184.959116] check: Corrupted low memory at 0000000086956b66 (3aa8 phys) = 736569726553
Jul 15 16:34:05 oygle-Inspiron-3542 kernel: [29184.959133] check: Corrupted low memory at 000000005ca56388 (3ac8 phys) = 80000000

Kubuntu 19.10,  Laptop is Dell Inspiron 3542. I assume a memory test for starters or is this a bug ?

---

### Post by guiverc on 2020-07-15
The *linux* kernel doesn't use the first 1MB of RAM. 

For legacy reasons (*ie. old DOS computers & maintaining compatibility with the past*) the first  1MB of RAM is reserved. It's available for use by hardware (expansion cards etc; used mostly by hardware from the 1980s & early 90s) and/or the BIOS, and old fashioned DOS should you boot it for some reason  (*I still have a DOS machine under the house!*).

Yes I would check your memory (*sorry I'd have to assume memtest would check that first 1MB but I don't know*), it could also mean two devices on your box are malfunctioning and corrupting the memory IF they actually using it... That shouldn't impact your Ubuntu kernel, however if it's the result of malfunctioning hardware, it could be seen as a warning sign.

  Sorry I have limited experience with that message, so hopefully you'll get more advice from others.

---

### Post by CatKiller on 2020-07-15
> **oygle said:**
> Kubuntu 19.10
Be aware that 19.10 reaches End-of-Life this month. You'll want to upgrade to 20.04 sooner rather than later.

---

### Post by Impavidus on 2020-07-15
> **CatKiller said:**
> Be aware that 19.10 reaches End-of-Life this month. You'll want to upgrade to 20.04 sooner rather than later.

To be more precise, the day after tomorrow. I think it's safe to postpone upgrading until Saturday. It takes some time before the repositories are taken off the servers.
[https://lists.ubuntu.com/archives/ubuntu-announce/2020-July/000257.html](https://lists.ubuntu.com/archives/ubuntu-announce/2020-July/000257.html)

---

### Post by oygle on 2020-07-16
> **guiverc said:**
> The *linux* kernel doesn't use the first 1MB of RAM. .

Okay thanks for your reply and explanations. I have done a full test from BIOS and it is all okay, so I have to assume the messages are irrelevant. Some details:

Dell Inspiron 3542
BIOS version  A01
System memory    8192 MB  (DDR3L)
Extended memory  640  Kb
Memory speed  1600   Mhz

> **CatKiller said:**
> Be aware that 19.10 reaches End-of-Life this month. You'll want to upgrade to 20.04 sooner rather than later.

Thanks

> **Impavidus said:**
> To be more precise, the day after tomorrow. I think it's safe to postpone upgrading until Saturday. It takes some time before the repositories are taken off the servers.
[https://lists.ubuntu.com/archives/ubuntu-announce/2020-July/000257.html](https://lists.ubuntu.com/archives/ubuntu-announce/2020-July/000257.html)

Oh I didn't know they actually start removing repositories from the server. Best I update/upgrade at least for now, thanks.

---

### Post by ActionParsnip on 2020-07-16
Do you have the latest BIOS?
https://www.dell.com/support/home/en-uk/product-support/product/inspiron-15-3542-laptop/drivers

---

### Post by oygle on 2020-07-16
> **ActionParsnip said:**
> Do you have the latest BIOS?
[https://www.dell.com/support/home/en-uk/product-support/product/inspiron-15-3542-laptop/drivers](https://www.dell.com/support/home/en-uk/product-support/product/inspiron-15-3542-laptop/drivers)

I certainly don't have that BIOS update, and it looks like I'm about 4 updates behind. I only have Kubuntu on it, no windows at all so updating the BIOS was always going to be a pain. I think when I looked into it last there was a method to update the BIOS from a Linux based computer though ??

---

### Post by ActionParsnip on 2020-07-16
[https://www.dell.com/support/article/en-uk/sln171755/update-the-dell-bios-in-a-linux-or-ubuntu-environment?lang=en](https://www.dell.com/support/article/en-uk/sln171755/update-the-dell-bios-in-a-linux-or-ubuntu-environment?lang=en)

---

### Post by oygle on 2020-07-16
> **ActionParsnip said:**
> [https://www.dell.com/support/article/en-uk/sln171755/update-the-dell-bios-in-a-linux-or-ubuntu-environment?lang=en](https://www.dell.com/support/article/en-uk/sln171755/update-the-dell-bios-in-a-linux-or-ubuntu-environment?lang=en)

Great, thanks  :)

---

### Post by oygle on 2020-09-12
Given that updating the BIOS is needed, best to mark this as solved.

---

### Post by oygle on 2020-10-17
Updated the BIOS today, however those messages are still appearing ?

---

