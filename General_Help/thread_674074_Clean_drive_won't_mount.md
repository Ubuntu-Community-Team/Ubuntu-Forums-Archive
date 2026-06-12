---
title: "Clean drive won't mount"
date: 2008-01-21
forum: General Help
---

### Post by scottevan on 2008-01-21
I have a secondary internal hard drive (ext3) that I use for backup; however, it has mysteriously stopped mounting. Can anyone suggest a remedy?
```
scott@squid-desk:~$ sudo mount -a
[sudo] password for scott:
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

scott@squid-desk:~$ sudo fsck -y /dev/sdb1
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
/dev/sdb1: clean, 11/19546112 files, 628583/39062039 blocks
```

Here is my fstab:
```
/dev/sdb1        /media/conformist   ext3    defaults     0        2
```

I've had some other weird problems too. My main hard drive has required manual fsck multiple times in the last week and my machine is not performing very well. Not sure if there is a connection. I checked my RAM, power supply voltage and I ran a virus scan. Not sure why any of that would cause disk problems though.

Any advice would be appreciated! Thanks.

---

### Post by PmDematagoda on 2008-01-21
How old are both your hard drives?

Also, post the output of:-
```
sudo fdisk -l
```

---

### Post by geirha on 2008-01-21
Are you sure it's ext3 and not ext2 on that partition? Try ```
sudo mount -t ext2 /dev/sdb1 /media/conformist
```

---

### Post by scottevan on 2008-01-27
> **PmDematagoda said:**
> How old are both your hard drives?

Also, post the output of:-
```
sudo fdisk -l
```
Sorry about the slow response. I thought I had instant notifications turned on. The drive in question is not very old, but it was harvested from a failing system. There is, I guess, some possibility that it has problems. Is there a utility to test disks?

fdisk outputs:
```
scott@squid-desk:~$ sudo fdisk -l

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9865ffc3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       47884   384628198+  83  Linux
/dev/sda2           47885       48641     6080602+   5  Extended
/dev/sda5           47885       48641     6080571   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19452   156248158+  83  Linux
```

---

### Post by scottevan on 2008-01-27
> **geirha said:**
> Are you sure it's ext3 and not ext2 on that partition? Try ```
sudo mount -t ext2 /dev/sdb1 /media/conformist
```

Thanks for the suggestion! I tried that command and it may have worked... The drive doesn't appear on my desktop or under Computer; however, I now see it in /media. If I go to /media/conformist, the only file present is "lost + found" which I can't open. Can I retrieve stuff from this folder?

Very strange. I was 99% sure that my drive was ext3 and the fstab above worked for months!?

---

### Post by geirha on 2008-01-27
> **scottevan said:**
> Thanks for the suggestion! I tried that command and it may have worked... The drive doesn't appear on my desktop or under Computer; however, I now see it in /media. If I go to /media/conformist, the only file present is "lost + found" which I can't open. Can I retrieve stuff from this folder?

Very strange. I was 99% sure that my drive was ext3 and the fstab above worked for months!?

Sounds like it has been formatted with ext2. You haven't accidentally run "mkfs.ext2" instead of fsck.ext2 for example, on that partition?

What's the date stamp on the filesystem? ```
ls -ld /media/conformist
```

And look through the bash history and see what has been run on that partition: ```
grep 'sdb1' ~/.bash_history
```

---

### Post by scottevan on 2008-01-27
Thanks again for the speedy response, geirha! The date stamp is "drwxr-xr-x 3 root root 4096 2008-01-19 16:30 /media/conformist" - that would be about the time my problems started.

Looking at the bash history, I appear to have typed "mke2fs /dev/sdb1" instead of "mke2fs -n /dev/sdb1" while looking for a replacement superblock. I guess this is the cause of my changed file system? Can I recover my files? No big deal if I can't b/c it was mostly junk.

Wow. The terminal is dangerous in the wrong hands :)

---

### Post by geirha on 2008-01-28
I think it is likely that you can recover most the files, though I have no experience with such software. A quick search at google came up with this: [http://www.linuxforums.org/forum/servers/109903-recovering-some-files-rm-rf.html](http://www.linuxforums.org/forum/servers/109903-recovering-some-files-rm-rf.html)

And of course, don't write anything to the partition. Any write may overwrite some of your previous files. So keep it unmounted when you don't need it, and mount it readonly (ro option) if you need to mount it.

---

