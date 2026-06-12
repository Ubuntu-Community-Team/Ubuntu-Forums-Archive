---
title: "Which Windows partitions can I delete?"
date: 2021-02-17
forum: General Help
---

### Post by donsy on 2021-02-17
I would like to maintain my dual-boot but need more space. Can I safely delete partitions 4-6 and still login to Windows occasionally? What about 2?

```
Disk /dev/sda: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: ST1000LM035-1RK1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: CA8EB8DE-8E5D-4B3A-8E2C-2095D80A33F0


Device          Start        End   Sectors   Size Type
/dev/sda1        2048    1025484   1023437 499.7M EFI System
/dev/sda2     1026048    1288191    262144   128M Microsoft reserved
/dev/sda3     1288192  488151039 486862848 232.2G Microsoft basic data
/dev/sda4  1924886528 1925808127    921600   450M Windows recovery environment
/dev/sda5  1925808128 1951250431  25442304  12.1G Windows recovery environment
/dev/sda6  1951252480 1953523711   2271232   1.1G Windows recovery environment
/dev/sda7   488153088 1130473471 642320384 306.3G Linux filesystem
/dev/sda8  1130473472 1924886527 794413056 378.8G Linux filesystem


Partition table entries are not in disk order.



```

---

### Post by agvantibo on 2021-02-17
Nope nope nope. Don't do it. Windows will break. Just squish the MS Basic Data for another 50 GB and move everything after it to the left, then expand the Linux partition. This has been proven to work and be safe.

---

### Post by ajgreeny on 2021-02-17
> **agvantibo said:**
> Nope nope nope. Don't do it. Windows will break. Just squish the MS Basic Data for another 50 GB and move everything after it to the left, then expand the Linux partition. This has been proven to work and be safe.

That will never work as those partitions are not side by side, and unfortunately I know nothing about Windows partitions so can not give you any other help.

Just be very careful or you may completely kill you Windows OS, and ant actions you do undertake to their partitions [COLOR="#FF0000"]MUST BE DONE USING WINDOWS UTILITIES AND APPLICATIONS.[/COLOR]

---

### Post by Impavidus on 2021-02-17
I don't know about Windows partitions. This is an Ubuntu forum, after all. I do know that your partition 2, 4, 5 and 6 are together just 1.5% of your hard drive. That won't make a difference.

---

### Post by Hagar Delest on 2021-02-17
sda3 is just before sda7, thus, you can decrease the size of sda3 and increase by the same amount sda7 to the left.
If you almost never use Windows, you don't need those 230GiB. I've resized my Windows 10 partition to a mere 80GiB and it's only 50% full.

---

### Post by yancek on 2021-02-17
> I would like to maintain my dual-boot but need more space 

Need more space for what?  Your windows system partition is 232GB and your Ubuntu system partition is over 306GB plus a second Linux partition of over 370GB.  sda3 and sda7 are contiguous so you could expand either but it you expand sda7 to sda3 you will also need to move the data on that partition.  Windows generally has one Recovery partition so I'm not sure why you have 3.  In any case, which you can safely remove is something you should be asking at a windows forum.

---

### Post by donsy on 2021-02-17
Thanks to all for the informative replies, I've decided to do nothing. Thread marked as solved.

---

