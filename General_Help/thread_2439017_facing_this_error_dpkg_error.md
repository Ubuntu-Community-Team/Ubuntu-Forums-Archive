---
title: "facing this error dpkg error"
date: 2020-03-21
forum: General Help
---

### Post by stevepaul09 on 2020-03-21
I've been getting this error since yesterday: what is this[[COLOR=#000000].[/COLOR]]("https://www.alitechhub.com/textsheet-alternatives/")

```
Preparing to unpack .../cpp-7_7.5.0-3ubuntu1~18.04_amd64.deb ...Unpacking cpp-7 (7.5.0-3ubuntu1~18.04) over (7.4.0-1ubuntu1~18.04.1) ...
dpkg-deb (subprocess): decompressing archive member: lzma error: compressed data is corrupt
dpkg-deb: error: <decompress> subprocess returned error exit status 2
dpkg: error processing archive /var/cache/apt/archives/cpp-7_7.5.0-3ubuntu1~18.04_amd64.deb (--unpack):
 cannot copy extracted data for './usr/lib/gcc/x86_64-linux-gnu/7/cc1' to '/usr/lib/gcc/x86_64-linux-gnu/7/cc1.dpkg-new': unexpected end of file or stream
Errors were encountered while processing:
 /var/cache/apt/archives/cpp-7_7.5.0-3ubuntu1~18.04_amd64.deb
```

can you please help me to solve this.

---

### Post by Impavidus on 2020-03-21
A package file was downloaded and temporarily stored in a cache directory. Then it was unpacked and appeared to be corrupt. I suggest you delete it and try again:```
sudo rm /var/cache/apt/archives/cpp-7_7.5.0-3ubuntu1~18.04_amd64.deb
```Have you got backups of all your important files? Because random file corruption can happen to your documents too.

---

