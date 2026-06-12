---
title: "ubi extract problem ?!"
date: 2015-09-08
forum: General Help
---

### Post by fairbird on 2015-09-08
Hi guys ..

I am using ubuntu 12.04 and I have some problem with large rootfs.bin (ubi) 91.5MB files to extract it... I've got error message as code shown below ... 
```
root@fairbird:/home/raed# mkdir /mnt/ubi
root@fairbird:/home/raed# modprobe mtdblock
root@fairbird:/home/raed# modprobe ubi
root@fairbird:/home/raed# modprobe nandsim first_id_byte=0x20 second_id_byte=0xaa third_id_byte=0x00 fourth_id_byte=0x15
root@fairbird:/home/raed# cat /proc/mtd
dev:    size   erasesize  name
mtd0: 10000000 00020000 "NAND simulator partition 0"
root@fairbird:/home/raed# ls -la /dev/mtd*
crw------- 1 root root 90, 0 Sep  9 01:34 /dev/mtd0
crw------- 1 root root 90, 1 Sep  9 01:34 /dev/mtd0ro
brw-rw---- 1 root disk 31, 0 Sep  9 01:34 /dev/mtdblock0
root@fairbird:/home/raed# dd if=rootfs.bin of=/dev/mtdblock0 bs=2048
44544+0 records in
44544+0 records out
91226112 bytes (91 MB) copied, 2.41974 s, 37.7 MB/s
root@fairbird:/home/raed# ubiattach /dev/ubi_ctrl -m 0 -O 2048
ubiattach: error!: cannot attach mtd0
           error 22 (Invalid argument)
root@fairbird:/home/raed#
```
other file (80MB) extracted just fine without any problem ....
Please any idea ?!
Thank you advised

---

