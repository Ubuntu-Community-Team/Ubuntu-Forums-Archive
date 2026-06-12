---
title: "dd copy error - partition not an even increment of bs size"
date: 2007-06-22
forum: General Help
---

### Post by B-Con on 2007-06-22
I'm trying to clone a partition to another partition (bit for bit) using the dd command. They're both the exact same size (I ensured by creating the partition table manually with fdisk).

My problem is that I'm trying to use bs=4096 to speed up the copy (since it's about 19GB) but the partition size isn't in an increment size of 4096 bytes. (I calculated this to be true.)

```
b-con@beacon:~$ sudo dd if=/dev/sda2 of=/dev/sda3 bs=4096 conv=sync,noerror
dd: writing `/dev/sda3': Input/output error
4588565+1 records in
4588565+0 records out
18794762240 bytes (19 GB) copied, 878.299 seconds, 21.4 MB/s
```
Now, obviously, both partitions are not of a perfect incremental 4096 size. The conv=noerror part keeps there from being an error thrown on the very last read (there would be an error because the very last read doesn't have 4096 bytes.) However, the error is getting thrown on the very last write, since there isn't enough space to hold the last 4096-sized write.

What options exist for dd that will allow me to copy all the way to the end of the partition, even if the last chunk isn't a perfect increment of the bs increment I specify? In other words, how can I make dd not whine because the output isn't the perfect incremental size of 4096?

---

