---
title: "&quot;Last modified&quot; timestamp corruption"
date: 2023-04-21
forum: General Help
---

### Post by sba923 on 2023-04-21
[COLOR=#232629][FONT=-apple-system]On my DIY NAS (Ubuntu 22.04.2 LTS, Samba Version 4.15.13-Ubuntu) working among other things as a file server for Windows clients I'm facing a rather weird issue.
[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]The "last modified" timestamp for some random files get set to [FONT=courier new]0x80000000[/FONT]:
[/FONT][/COLOR]
[FONT=courier new]pwsh> stat /data/P/Photos/2022/07/11/_MG_9662.jpg
File: /data/P/Photos/2022/07/11/_MG_9662.jpg
Size: 9409475         Blocks: 18384      IO Block: 4096   regular file
Device: 10300h/66304d   Inode: 233443606   Links: 1
Access: (0764/-rwxrw-r--)  Uid: ( 1000/     sto)   Gid: ( 1000/     sto)
Access: 2023-03-01 17:15:10.470901300 +0100
Modify: 1901-12-13 20:55:13.000000000 +0009
Change: 2023-03-01 17:39:59.215467666 +0100
Birth: 2022-07-17 21:00:34.495834896 +0200
pwsh> stat -c %Y /data/P/Photos/2022/07/11/_MG_9662.jpg
-2147483648
pwsh> "0x{0:X8}" -f -2147483648
0x80000000[/FONT]


[COLOR=#232629][FONT=-apple-system]How would you investigate that issue?
[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Filesystem bug?
[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Samba bug?
[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Windows bug?[/FONT][/COLOR]

---

### Post by TheFu on 2023-04-21
I wouldn't assume any bug at this stage. I'd assume I was misunderstanding what each field means and question which part of my entire software stack isn't supported.

I'd first start by reading the manpage for the 'stat' program and be certain I understand what it being output.  For example, some shells have their own version of stat, so that would be preventing the real 'stat' program from being used.  If that's the case for my shell, I'd read the manpage for it.  From the stat manpage on 21.1 Mint:
```
       NOTE: your shell may have its own version of stat,  which  usually  supersedes  the
       version  described  here.   Please  refer to your shell's documentation for details
       about the options it supports.
```
then I'd work up in the stack, reading the documentation for the exact file system, then samba, then Windows connections. I'm fairly certain that not all parts of the stack involved supports all the different timestamp fields available.  Remember reading something like that a few years ago.

The good news is that file system timestamps can be mostly ignored for images.  Use the exif data if you want to know anything about an image file.  **exiftool** can access/modify most EXIF data.

---

### Post by sba923 on 2023-04-21
Having worked as a software engineer with those systems for more than 30 years, I'm pretty aware of the fact Windows, both locally and remotely via the SMB/CIFS protocol, that Samba implements very precisely, supports all three (creation, access and modification) timestamps. So the files stored onto the NAS are supposed to have their timestamps preserved / identical whether you look at them from the Unix side or from the Windows side.

The issue is that, randomly, the stored "last modification" timestamp of some files is changed to that crazy [COLOR=#000000][FONT=&amp]1901-12-13 20:55:13 value which happens to correspond to an 32-bit internal representation (in seconds since 1970-01-01 00:00:00 UTC) of 0x80000000.

Looks like some bug to me, where the value stored is overwritten by something that could be the return (error) value of some operation...

[/FONT][/COLOR]

---

### Post by sba923 on 2023-06-26
I've tracked down the issue to the FFC tool from Uwe Sieber's excellent collection of free tools [https://www.uwe-sieber.de/filetools_e.html](https://www.uwe-sieber.de/filetools_e.html) that I use to compare files. I'll be working with Uwe to get a fix.

---

