---
title: "Entry still missing after Boot Repair"
date: 2014-01-06
forum: General Help
---

### Post by ibrahim.chhaya on 2014-01-06
Hello,

I have both Windows 7 and Ubuntu 13.04 in my computer.

I mistakenly formatted a partition that contained my bootloader, so I tried getting it back with Boot Repair running off an Ubuntu live USB. The program finds Windows 7 but it does not add it to the entry list.

The URL for the paste is: [http://paste.ubuntu.com/6679248/](http://paste.ubuntu.com/6679248/)

Please advise.

---

### Post by Bucky Ball on 2014-01-06
Well, at the moment grub is installed in the MBR of sdb, your second disk which contains one NTFS partition. If you can boot into Ubuntu, open a terminal and type:

```
sudo grub-install /dev/sda

```
... but I'm wondering why Boot Repair didn't do this. Do you do the 'Recommended' repair?

---

### Post by ibrahim.chhaya on 2014-01-06
Yes I did do Recommend repair.
I did what you said and Grub only shows Ubuntu

---

