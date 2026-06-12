---
title: "command free shows swap free space is zero"
date: 2007-07-11
forum: General Help
---

### Post by bearyblue on 2007-07-11
user@host:~$ free
             total       used       free     shared    buffers     cached
Mem:       1035428     983124      52304          0     116740     573548
-/+ buffers/cache:     292836     742592
**Swap:**            0          0          **0**

Swap is in /dev/sda6. I allotted 1 GB for it. But free shows there is 0 free space on swap. Should I be concerned?

I recenty installed another Linux distro and set its swap to be /dev/sda6 also.

---

### Post by dannyboy79 on 2007-07-11
please show me the results of the following commands:

cat /etc/fstab | grep swap

cat /proc/swaps

and then I can help.

---

### Post by bearyblue on 2007-07-11
cat /etc/fstab | grep swap
# /dev/sda6
UUID=fb2e751a-6469-4b37-9548-3aae8ff7dc9d none            swap    sw              0       0

cat /proc/swaps doesn't return anything. only some column headers for what i think is a table.

---

### Post by dannyboy79 on 2007-07-11
try
sudo swapon -a
that should enable the swap that is designated by the fstab entry. Make sure that the fstab entry UUID matches what is in the /dev/disk/by-uuid/ folder. you can find out what the uuid for your /dev/sda6 partition by entering this command:

ls -la /dev/disk/by-uuid/ | grep sda6

then just copy and paste that long number from the output and paste it into your /etc/fstab line for your swap. OR just change your fstab so that it's 
/dev/sda6              none            swap    sw              0       0

BUT once in  a while the kernel ide driver get's changed and your dev id's for your hard drives may change from hda to sda and vis-versa so that's why I suggest first going with the UUID of the parititon. good luck

---

### Post by bearyblue on 2007-07-12
thanks! it's ok now. the uuid was somehow changed. how did that happen?

---

### Post by dannyboy79 on 2007-07-12
not sure but I am glad I could help.

---

### Post by bearyblue on 2007-07-12
thank you again! i learned something new.

---

