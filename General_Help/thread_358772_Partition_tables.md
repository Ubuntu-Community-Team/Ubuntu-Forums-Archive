---
title: "Partition tables"
date: 2007-02-11
forum: General Help
---

### Post by Kiwinote on 2007-02-11
I have been trying to install a server lately, but without much success. Tried dapper and edgy, both installed without errors, but haven't been able to boot it up yet. Once grub has loaded, it attempts to boot ubuntu, the pc restarts and gets into this everlasting loop. I can't run a liveCD on it because of the lack of memory, but I can boot with the rescue mode of the server install cd and get a command line in /dev/hda1. Sudo fdisk -l gives me "cannot open /proc/partitions" and fdisk -l /dev/hda1 tells me that it couldn't find a valid partition table. The fstab file looks fine. Anyone got any ideas how to solve this?
Kiwinote

---

### Post by Kiwinote on 2007-02-11
Any ideas?

---

### Post by llamakc on 2007-02-11
Not without more details. What are the system specs? What appears in the output of dmesg when you are able to get into the system?

---

### Post by charl.ie on 2007-02-11
What about booting to the install CD and re-formatting from there?

---

### Post by Kiwinote on 2007-02-11
@llamakc pentium mmx - 233 mhz, 48mb ram, 2gb hdd
                   Do you want the dmesg from the commandline in the server install cd? Can't get into the system itself...
@charl.ie The aim was to boot from the hdd rather than wiping it, this is allready install number somany.

---

### Post by llamakc on 2007-02-11
I misunderstood your OP.

What was your original partition layout when you did the install?

Hopefully somebody comes along who has experience installing Ubuntu in a low-memory environment as your machine. Sorry I can't help further.

---

### Post by Kiwinote on 2007-02-11
Layout of hdd is 1.7gb as / and 0.3gb as swap or something along those lines.

---

### Post by llamakc on 2007-02-11
To be clear, you are trying to install with the server ISO's, correct?

---

### Post by Kiwinote on 2007-02-11
Yes, ubuntu server 6.10. As far as I can see it seems to have installed all ok, but grub can't boot it because the partition table is messed up, I think...

---

### Post by Kiwinote on 2007-02-14
Ideas anyone? (Otherwise I'll try a different HDD when I next have time...)

---

