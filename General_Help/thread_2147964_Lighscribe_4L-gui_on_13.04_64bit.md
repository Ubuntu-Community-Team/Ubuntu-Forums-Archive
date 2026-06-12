---
title: "Lighscribe 4L-gui on 13.04 64bit"
date: 2013-05-23
forum: General Help
---

### Post by shizeon on 2013-05-23
Hi everyone,
  I've been using the LaCie 4L-gui program for years now on my ubuntu 64 installs.  I recently updated to 13.04 Raring from 12.10  and it has stopped working.  The SimpleLabler still works.  However the 4L-gui comes up, but it fails to detect any drives.  I've removed and reinstalled everything (using [https://help.ubuntu.com/community/LightScribe](https://help.ubuntu.com/community/LightScribe) ) and a few other google hits.  I'm starting to wonder if 13.04 introduced something that causes this not to work anymore.  No errors are reported on the command line.  Everytime I hit the refresh button on the drives, the command line kicks out a "Using /etc/lightscribe.rc".  

Does anyone have 4L-gui writing to disks on their 13.04 64-bit install?

Thanks a million!

[IMG]https://dl.dropboxusercontent.com/u/180604/Share/Screenshot%20from%202013-05-23%2009%3A48%3A39.png[/IMG]

---

### Post by shizeon on 2013-05-23
Okay, so right after posting I started to investigate more possible libstdc++.so.5 issues.  I do have it installed, but it appears that in ubuntu 13.04 the default library search path is different than before (maybe).

> shizeon@asustower:/usr/4L$ sudo ldd 4L-cli 
	linux-gate.so.1 =>  (0xf7730000)
	liblightscribe.so.1 => /usr/lib/liblightscribe.so.1 (0xf7450000)
	libpthread.so.0 => /lib/i386-linux-gnu/libpthread.so.0 (0xf7435000)
	libstdc++.so.6 => /usr/lib/i386-linux-gnu/libstdc++.so.6 (0xf734b000)
	libm.so.6 => /lib/i386-linux-gnu/libm.so.6 (0xf7308000)
	libgcc_s.so.1 => /lib/i386-linux-gnu/libgcc_s.so.1 (0xf72eb000)
	libc.so.6 => /lib/i386-linux-gnu/libc.so.6 (0xf7138000)
	libstdc++.so.5 => **/usr/lib/i386-linux-gnu/libstdc++.so.5 **(0xf707e000)
	/lib/ld-linux.so.2 (0xf7731000)

So this is looking in i386-linux-gnu instead of the old behavior of looking in lib32. 

Quick relinking took care of it.

```
shizeon@asustower:/usr/lib/i386-linux-gnu$ ls -la | grep stdc
lrwxrwxrwx   1 root root       18 Jan 31 06:58 libstdc++.so.5 -> libstdc++.so.5.0.7
-rw-r--r--   1 root root   737596 Jan 31 06:59 libstdc++.so.5.0.7
lrwxrwxrwx   1 root root       19 Apr 15 05:03 libstdc++.so.6 -> libstdc++.so.6.0.17
-rw-r--r--   1 root root   922208 Apr 15 05:12 libstdc++.so.6.0.17

shizeon@asustower:/usr/lib/i386-linux-gnu$ sudo rm /usr/lib/i386-linux-gnu/libstdc++.so.5
shizeon@asustower:/usr/lib/i386-linux-gnu$ sudo ln -s /usr/lib/lightscribe/libstdc++.so.5.0.7  /usr/lib/i386-linux-gnu/libstdc++.so.5

shizeon@asustower:/usr/lib/i386-linux-gnu$ ls -la | grep stdc
lrwxrwxrwx   1 root root       39 May 23 10:24 libstdc++.so.5 -> /usr/lib/lightscribe/libstdc++.so.5.0.7
-rw-r--r--   1 root root   737596 Jan 31 06:59 libstdc++.so.5.0.7
lrwxrwxrwx   1 root root       19 Apr 15 05:03 libstdc++.so.6 -> libstdc++.so.6.0.17
-rw-r--r--   1 root root   922208 Apr 15 05:12 libstdc++.so.6.0.17



```

Not sure if there are long time consequences from using the lightscribe provided libstdc++.so.5 over the deb packaged one, but it appears to be working now.

---

### Post by Botruckle on 2013-06-15
Many thanks! This has had me in fits for quite some time. Your fix worked for me and the LaCie gui now sees the drive.

---

### Post by urticadioica on 2013-06-27
According to strace, '4L-gui' calls '4L-cli' to find suitable optical drives, but during/after enumeration the lightscribe driver (?) causes seg fault and core dump. Thus the enumeration call returns empty list.

```
# strace 4L-cli enumerate
...
open("/proc/sys/dev/cdrom/info", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xfffffffff774d000
read(3, "CD-ROM information, Id: cdrom.c "..., 8192) = 433
read(3, "", 7168)                       = 0
read(3, "", 8192)                       = 0
close(3)                                = 0
munmap(0xf774d000, 4096)                = 0
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
--- SIGSEGV (Segmentation fault) @ 0 (0) ---
+++ killed by SIGSEGV (core dumped) +++
Segmentation fault (core dumped)
```

Exactly the same seg fault happens when I try to write label using linux 64-bit native 'qlscribe'. The program itself outputs D-BUS timeout error. That is because its D-BUS daemon (lscribed) has core dumped and it is not answering. The daemon uses default libs.

```
ldd /usr/sbin/lscribed | grep libstdc
    libstdc++.so.6 => /usr/lib/i386-linux-gnu/libstdc++.so.6 (0xf72ee000)
    libstdc++.so.5 => /usr/lib/i386-linux-gnu/libstdc++.so.5 (0xf7020000)
```

It looks like there is a problem with standard 'libstdc.so.5' from the repos, because Lightscribe's own SimpleLabeler application finds the drive OK. It uses its own supplied libs.

```
# ldd /opt/lightscribeApplications/SimpleLabeler/SimpleLabeler | grep lightsc
    liblightscribe.so.1 => /usr/lib32/liblightscribe.so.1 (0xf74a1000)
    libQtXml.so.4 => /opt/lightscribeApplications/common/Qt/libQtXml.so.4 (0xf7456000)
    libQtGui.so.4 => /opt/lightscribeApplications/common/Qt/libQtGui.so.4 (0xf69ba000)
    libQtCore.so.4 => /opt/lightscribeApplications/common/Qt/libQtCore.so.4 (0xf6513000)
    **libstdc++.so.5 => /opt/lightscribeApplications/common/Qt/libstdc++.so.5 (0xf6416000)**
```


I replaced the original soft link with the lightscribe one and oh sweet success:

```
$ 4L-cli enumerate
Using /etc/lightscribe.rc
Drive path: /dev/sr0
Usable: 1
Full name: Optiarc DVD RW AD-7241S 1.03 196
Model: DVD RW AD-7241S 
Manufacturer: Optiarc 
Capabilities: monochrome 
Drive inner radius: 22500
Drive outer radius: 58700
```

Whenever I need to run 'ldconfig' the soft link gets "fixed" back to its original value.

---

### Post by jippolito0003 on 2013-10-10
I am using Linux Mint 15 and I am trying to run Laie on it and there just what happened to you Lacie does not see the drive but the simple labeler sees it. How can I go about to fix this? Thanks.

---

### Post by jippolito0003 on 2013-10-10
I am running 32 bit version of Linux Mint 15 KDE when I am running Lacie

---

### Post by domfe on 2014-02-15
Hi.
I've the same problem with libstdc++ on my new 64bit computer.
I followed your symlink advice and now 4L-cli and 4L-gui recognize my drive, but when I start writing the disk, the procedure stops with a console error "SG_IO ioctl error: Cannot allocate memory"

Have you experienced the same issue?

Thank you!

---

### Post by interknighterrant on 2014-02-17
Thanks all here for the help, I finally got my lightscribe drive to work on 64-bit 13.10 with some help from these posts and some other links.

---

### Post by domfe on 2014-02-18
Me too!
But I don't like to mess with system libraries.
Just put the correct library (libstdc++.so.5.0.7) in /usr/4L and make a file in /etc 

```

$ cat /etc/ld.so.conf.d/4L-cli.conf
/usr/4L
$
```

and then execute
```

$ sudo ldconfig

```

Thank you for your help!

---

