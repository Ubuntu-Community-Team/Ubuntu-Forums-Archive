---
title: "Partitioning | Configuring format is taking forever"
date: 2018-12-02
forum: General Help
---

### Post by suhd550 on 2018-12-02
Ubuntu server installation configuring format is taking forever.


Computer specs:
Gigabyte AB350M-D3H Motherboard
Ryzen 3 2200G APU
Trancsend 512GB M.2 NVME SSD
8GB DDR4 RAM


Windows 10 is working fine on my computer.

**[Screenshot]("https://i.imgur.com/iEkIFcC.jpg")**

---

### Post by TheFu on 2018-12-03
If you use LVM, the format aspect will be nearly instant regardless of the storage amount.
BTW, that screen-shot doesn't work for me.

If you can post the output from **lsblk** it might be helpful.
Also, check the system log files.

In general, on a system like yours, installation of 18.04 should require about 10-15 minutes, total time.

But if you didn't free up storage BEFORE doing the installation, perhaps the installer is attempting to make space by reducing the amount of disk used by Windows?  Depending on the amount of data, that could take hours.

I never let partitioning happen automatically, especially on a dual-boot setup.  So many things can go wrong and I'd hate to have the other OS wiped, completely, gone.

---

