---
title: "system rescue cd /partimage help"
date: 2007-07-29
forum: General Help
---

### Post by dragonwings on 2007-07-29
i want to make image of my hard drive on dvd  using system resue cd  x86-0.3.7

please help with commands or any other ideas

so far i have followed insructions and had to make some mods to commands here and there to get things to work,i guess the instructions are for a n older version or somthing ??

anyway i have loaded partimage to ram

put in dvd+rw disc 

typed dvd+rw format -force=full /dev/sdb        but no go 

so i typed    dvd+rw format -force /dev/sdb 
which started formatting ,but stoped at 93% 
tryed a few more times but still same thing 93%

so i try next stage to see if it would work  making udf filesystem
by typing 
mkudffs --lvid="dvd-backup" --udfrev=0x0150 /dev/sdb

but it just says   trying to change filsystem thenwait for next command

which is mount disc and copy files 

mkdir -p /mnt/disk
mount -tudf -o rw,noatime /dev/hdb /mnt/disk         but no luck

---

### Post by dragonwings on 2007-07-29
hello?

---

