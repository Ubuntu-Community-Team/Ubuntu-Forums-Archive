---
title: "[SOLVED] My Hard Drives Are Missing"
date: 2008-02-14
forum: General Help
---

### Post by Sabar on 2008-02-14
Ok, I don't know what is going on here. The last time I was on my computer I had two Hard drives sitting on my desktop. They have been listed there ever sence I installed 7.10. in fact they were there on 7.04.

For some reason I turned on my computer today and they are both missing. So I went looking for them. I found both my hard drives under

Places > File system > media > ( here listed are both sda1 sdb1 unfortunately they are both empty.

I went to my terminal after finding something in anouther post and did this

> alien@alien:~$ sudo fdisk -l
[sudo] password for alien:

Disk /dev/sda: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeedbeedb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10199    81923436    7  HPFS/NTFS
/dev/sda2           12729       20023    58597087+  83  Linux
/dev/sda3           12485       12728     1959930    5  Extended
/dev/sda5           12486       12728     1951897+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3d8d3d8c

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30400   244187968+   7  HPFS/NTFS


Not real sure what all this means but it looks like Ubuntu is seeing my hard drives. ( obviously. I am running the computer ) 

Can any one help me out with this?

Sabar

---

### Post by taurus on 2008-02-14
Did you shutdown your windows cleanly the last time you used it?  What happens when you try to mount them from a terminal such as

```
sudo mkdir /media/sda1 /media/sdb1
sudo mount -t ntfs /dev/sda1 /media/sda1
sudo mount -t ntfs /dev/sdb1 /media/sdb1
df -h
```

---

### Post by Sabar on 2008-02-15
No actually XP froze up on me and I just shut it down, then came back up on my Ubuntu. 

I am going to shut down go back into windows then and do a clean shut down. guessing its to late now for that. but might as well try.

Then go and try each line separately? What about the df -h Do I do that by its self too?

Sabar

---

### Post by Sabar on 2008-02-16
That was an easy fix. All I did was shut down and restart windows then shut windows back down the proper way. and restarted Ubuntu. 

Wish I knew why that would affect Ubuntu starting. 

Thank you very much taurus for answering my Question. 

Sabar

---

### Post by getitdone on 2008-02-16
Crazy, I signed up(to the forum) to figure out the same problem. I was trying all this mounting crap and all I had to do was described above.

---

