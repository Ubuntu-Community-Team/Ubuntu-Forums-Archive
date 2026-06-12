---
title: "Ubuntu 16.04 ARMhf Core package corrupted files...?"
date: 2016-05-03
forum: General Help
---

### Post by James_Lewis on 2016-05-03
Hey guys. So, I wanted to run a full Linux distro on my rooted Android tablet )RCA Viking Pro 10.1"). So, after doing some googling I decided that booting a Linux distro in chroot inside Android would be the easiest solution. After trying a few different Linux installers I settled with Complete Linux Installer as the other two I tried always gave me errors... The problem with that installer though is that it hasnt been updated since 2014, and that means the only distros it comes with are super old, in fact the newest Ubuntu distro it has is 13.04/13.10 :O So, it works, but it isn't too useful...

So, I decided, "well, I guess I'll just build my own img file with the latest version on it and use that". On the LinuxOnAndroid wiki it tells you how to build a bootable img file using the Core package for the distro you want, then you can install any other applications you want once you are booted. So, going by the instructions, I went to the Ubuntu website, found a copy of the 16.04 ARMhf Core package, and downloaded it...

Unfortunately for me, after I extracted it, I found that some of the files- 67 to be precise- seem to be corrupt! Some really important ones too, including several shell commands, /bin/sh, /bin/rbash, dev/stdout, dev/stdin, ld-linux-armhf.so and more! At first I thought it didn't extract properly, but then I looked into the archive while it was still compressed, and low and behold, there were a lot of files in there that were 0 bytes in size! So it is most definitely the files themselves that are the problem.

So... until that gets fixed, does anyone have an Ext4-formatted ARMhf Ubuntu 16.04 or 16.10 img I can use?

Oh, by the way, here is the error log from the extracter I used:

```
Cannot create symbolic link /storage/emulated/0/ZIPTMP/ubuntucore/bin/ypdomainname
&#8226; Function not implemented
... some similar messages are skipped
Cannot create symbolic link /storage/emulated/0/ZIPTMP/ubuntucore/bin/dnsdomainname
&#8226; Function not implemented
... some similar messages are skipped
Cannot create symbolic link /storage/emulated/0/ZIPTMP/ubuntucore/bin/sh
&#8226; Function not implemented
... some similar messages are skipped
Cannot create symbolic link /storage/emulated/0/ZIPTMP/ubuntucore/bin/sh.distrib
&#8226; Function not implemented
... some similar messages are skipped
Cannot create symbolic link /storage/emulated/0/ZIPTMP/ubuntucore/dev/stdout
&#8226; Try again
... some similar messages are skipped
Cannot create symbolic link /storage/emulated/0/ZIPTMP/ubuntucore/dev/stdin
&#8226; Function not implemented
... some similar messages are skipped
Cannot create symbolic link /storage/emulated/0/ZIPTMP/ubuntucore/etc/dpkg/origins/default
&#8226; Function not implemented
... some similar messages are skipped
Cannot create symbolic link /storage/emulated/0/ZIPTMP/ubuntucore/lib/arm-linux-gnueabihf/libpam.so.0
&#8226; Function not implemented
... some similar messages are skipped
Cannot create symbolic link /storage/emulated/0/ZIPTMP/ubuntucore/lib/arm-linux-gnueabihf/libresolv.so.2
&#8226; Function not implemented
... some similar messages are skipped
Cannot create symbolic link /storage/emulated/0/ZIPTMP/ubuntucore/lib/arm-linux-gnueabihf/libusb-0.1.so.4
&#8226; Function not implemented
... some similar messages are skipped
Cannot create symbolic link /storage/emulated/0/ZIPTMP/ubuntucore/lib/arm-linux-gnueabihf/libmount.so.1
&#8226; Function not implemented
... some similar messages are skipped
Cannot create symbolic link /storage/emulated/0/ZIPTMP/ubuntucore/lib/arm-linux-gnueabihf/libprocps.so.4
&#8226; Function not implemented
... some similar messages are skipped
Cannot create symbolic link /storage/emulated/0/ZIPTMP/ubuntucore/lib/arm-linux-gnueabihf/libnss_dns.so.2
&#8226; Function not implemented
... some similar messages are skipped
Cannot create symbolic link /storage/emulated/0/ZIPTMP/ubuntucore/lib/arm-linux-gnueabihf/libnss_compat.so.2
&#8226; Function not implemented
... some similar messages are skipped
Cannot create symbolic link /storage/emulated/0/ZIPTMP/ubuntucore/lib/arm-linux-gnueabihf/ld-linux-armhf.so.3
&#8226; Function not implemented
... some similar messages are skipped
Cannot create symbolic link /storage/emulated/0/ZIPTMP/ubuntucore/lib/arm-linux-gnueabihf/libgcrypt.so.20
&#8226; Function not implemented
... some similar messages are skipped
Cannot create symbolic link /storage/emulated/0/ZIPTMP/ubuntucore/lib/arm-linux-gnueabihf/libnss_nis.so.2
&#8226; Function not implemented
... some similar messages are skipped
Cannot create symbolic link /storage/emulated/0/ZIPTMP/ubuntucore/lib/arm-linux-gnueabihf/libkmod.so.2
&#8226; Function not implemented
... some similar messages are skipped
Cannot create symbolic link /storage/emulated/0/ZIPTMP/ubuntucore/lib/arm-linux-gnueabihf/libext2fs.so.2
&#8226; Function not implemented
... some similar messages are skipped
Cannot create symbolic link /storage/emulated/0/ZIPTMP/ubuntucore/lib/arm-linux-gnueabihf/libapparmor.so.1
&#8226; Function not implemented
... some similar messages are skipped
Cannot create symbolic link /storage/emulated/0/ZIPTMP/ubuntucore/lib/arm-linux-gnueabihf/libm.so.6
&#8226; Function not implemented
... some similar messages are skipped
Cannot create symbolic link /storage/emulated/0/ZIPTMP/ubuntucore/lib/arm-linux-gnueabihf/libpcre.so.3
&#8226; Function not implemented
... some similar messages are skipped
Cannot create symbolic link /storage/emulated/0/ZIPTMP/ubuntucore/lib/arm-linux-gnueabihf/libnss_nisplus.so.2
&#8226; Function not implemented
... some similar messages are skipped
Cannot create symbolic link /storage/emulated/0/ZIPTMP/ubuntucore/lib/arm-linux-gnueabihf/libss.so.2
&#8226; Function not implemented
... some similar messages are skipped
Cannot create symbolic link /storage/emulated/0/ZIPTMP/ubuntucore/lib/arm-linux-gnueabihf/libutil.so.1
&#8226; Function not implemented
... some similar messages are skipped
Cannot create symbolic link /storage/emulated/0/ZIPTMP/ubuntucore/lib/arm-linux-gnueabihf/libbz2.so.1
&#8226; Function not implemented
... some similar messages are skipped
Cannot create symbolic link /storage/emulated/0/ZIPTMP/ubuntucore/lib/arm-linux-gnueabihf/libtinfo.so.5
&#8226; Function not implemented
... some similar messages are skipped
Cannot create symbolic link /storage/emulated/0/ZIPTMP/ubuntucore/lib/arm-linux-gnueabihf/libanl.so.1
&#8226; Function not implemented
... some similar messages are skipped
Cannot create symbolic link /storage/emulated/0/ZIPTMP/ubuntucore/lib/arm-linux-gnueabihf/libuuid.so.1
&#8226; Function not implemented
... some similar messages are skipped
Cannot create symbolic link /storage/emulated/0/ZIPTMP/ubuntucore/lib/arm-linux-gnueabihf/libaudit.so.1
&#8226; Function not implemented
... some similar messages are skipped
Cannot create symbolic link /storage/emulated/0/ZIPTMP/ubuntucore/lib/arm-linux-gnueabihf/libdl.so.2
&#8226; Function not implemented
... some similar messages are skipped
Cannot create symbolic link /storage/emulated/0/ZIPTMP/ubuntucore/lib/arm-linux-gnueabihf/libcom_err.so.2
&#8226; Function not implemented
... some similar messages are skipped
Cannot create symbolic link /storage/emulated/0/ZIPTMP/ubuntucore/lib/arm-linux-gnueabihf/libncurses.so.5
&#8226; Function not implemented
... some similar messages are skipped
Cannot create symbolic link /storage/emulated/0/ZIPTMP/ubuntucore/lib/arm-linux-gnueabihf/libcrypt.so.1
```
Too many messages

---

### Post by James_Lewis on 2016-05-04
I probably shouldn't do this, but, bump?

Also, i just thought about something. Should I have posted this in the Installation and Upgrades board instead? If so, I wouldn't mind a mod moving it there.

---

