---
title: "dpkg error"
date: 2020-03-13
forum: General Help
---

### Post by pedro_rodriguez2 on 2020-03-13
Hi,
I've been getting this error since yesterday:

```
Preparing to unpack .../cpp-7_7.5.0-3ubuntu1~18.04_amd64.deb ...
Unpacking cpp-7 (7.5.0-3ubuntu1~18.04) over (7.4.0-1ubuntu1~18.04.1) ...
dpkg-deb (subprocess): decompressing archive member: lzma error: compressed data is corrupt
dpkg-deb: error: <decompress> subprocess returned error exit status 2
dpkg: error processing archive /var/cache/apt/archives/cpp-7_7.5.0-3ubuntu1~18.04_amd64.deb (--unpack):
 cannot copy extracted data for './usr/lib/gcc/x86_64-linux-gnu/7/cc1' to '/usr/lib/gcc/x86_64-linux-gnu/7/cc1.dpkg-new': unexpected end of file or stream
Errors were encountered while processing:
 /var/cache/apt/archives/cpp-7_7.5.0-3ubuntu1~18.04_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

What should I do??

---

### Post by Impavidus on 2020-03-13
The downloaded package file is damaged. Remove it and try again:```
sudo rm /var/cache/apt/archives/cpp-7*
sudo apt update
sudo apt upgrade
```
If this happens frequently, it's time to start worrying about your hard drive.

---

### Post by pedro_rodriguez2 on 2020-03-17
Thanks a lot, seems to have done the trick! This is the first time I ever had this problem.

This is an ssd drive I put in my old laptop to speed it up. Maybe it is too much for this old Samsung!

If it happens again, I'll junk the drive!

Thanks again!

---

