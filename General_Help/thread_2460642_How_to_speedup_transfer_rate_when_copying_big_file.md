---
title: "How to speedup transfer rate when copying big files?"
date: 2021-04-15
forum: General Help
---

### Post by rikuitop on 2021-04-15
Hi, 

Below is an example when I copy 2 files of around 2GB using rsync on a 16GB USB key (msdos filesystem type). The first file has a transfer rate of 200MB/s, the second one only 12MB/s.
Kernel: 5.8.0-48-generic x86_64 bits: 64
Distro: Ubuntu 20.04.2 LTS
Memory: 15.50 GiB

Could you please tell me how to speedup transfer rate for the second file (in addition one has to wait 2 more minutes after the second file is transfered)?
```

randomguy@heaven1:~/backup$ rsync -avv --progress backup.20210402.tgz.a* /media/randomguy/KINGSTON/
sending incremental file list
delta-transmission disabled for local transfer or --whole-file
backup.20210402.tgz.aa  2,097,152,000 100%  200.50MB/s    0:00:09 (xfr#1, to-chk=1/2)
backup.20210402.tgz.ab  1,813,868,515 100%   12.16MB/s    0:02:22 (xfr#2, to-chk=0/2)

total: matches=0  hash_hits=0  false_alarms=0 data=3911020515

sent 3,911,975,510 bytes  received 121 bytes  11,872,460.19 bytes/sec
total size is 3,911,020,515  speedup is 1.00

```

Thank you for your help.

---

### Post by CelticWarrior on 2021-04-15
Welcome.

I'm sure you understand that such high speeds aren't "real". What is shown is the transference rate for the origin to RAM, not from origin to destiny directly. It's impossible for any USB flash memory currently available to achieve 200MB/s writing speed.

The system is working as expected, there's nothing to speed up.

---

### Post by dragonfly41 on 2021-04-15
Consider also USB 3.0 instead of USB 2.0 port.

[https://www.usr.com/education/usb3-peripherals/#:~:text=When%20comparing%202.0%20and%203.0,and%20USB%20ports%20and%20cables](https://www.usr.com/education/usb3-peripherals/#:~:text=When%20comparing%202.0%20and%203.0,and%20USB%20ports%20and%20cables).

I run Ubuntu on external SSD through USB 3.0 port.

---

### Post by rikuitop on 2021-04-15
Thank you CelticWarrior & dragonfly41! The given speed is indeed 100MB/s read, 15MB/s write. I use the USB 3.0 port.

---

### Post by HermanAB on 2021-04-15
You can speed it up by buying better quality flash memory devices.  SD cards come with speed ratings of 4, 6, 10 etc.  With USB sticks, you are kinda lost in a sea of sargassum though.

---

### Post by ActionParsnip on 2021-04-15
eSATA may help instead of USB

---

### Post by rikuitop on 2021-04-15
Good ideas:
SD card reader on USB-C port
eSATA external drive on USB-C port

---

