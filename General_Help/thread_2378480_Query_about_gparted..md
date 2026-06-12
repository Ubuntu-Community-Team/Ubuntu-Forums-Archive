---
title: "Query about gparted."
date: 2017-11-23
forum: General Help
---

### Post by deepakdeshp on 2017-11-23
Hello, I have partition sda7 which I need to grow.
I have free space before sda7 data,
I free space after  the next partion sda8.
What may be the method to grow sda7 , yet I sould not lose the capacity to boot from sda7 and the data should not be destroyed.

My partitions are

```
/dev/sda1       2048   1333247   1331200   650M Windows recovery 
/dev/sda2    1333248   1865727    532480   260M EFI System
/dev/sda3    1865728   2127871    262144   128M Microsoft reserve
/dev/sda4    2127872 230522879 228395008 108.9G Microsoft basic d
/dev/sda5  230522880 443516927 212994048 101.6G Linux filesystem
/dev/sda7  443516928 571676671 128159744  61.1G Linux filesystem
/dev/sda10 571676672 786716671 215040000 102.6G Linux filesystem
/dev/sda11 844060672 845084671   1024000   500M Linux filesystem
/dev/sda8  910200832 920653823  10452992     5G Linux swap
/dev/sda6  920653824 976762879  56109056  26.8G Microsoft basic d
```

---

### Post by VMC on 2017-11-23
Growing with gparted takes forever with existing data. Clone sda7 then delete it, create new partition with new size. Then you can restore cloned os. Use fsarchiver.

---

### Post by oldos2er on 2017-11-23
Thread moved to General Help.

---

