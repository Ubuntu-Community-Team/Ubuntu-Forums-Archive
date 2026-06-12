---
title: "Dapper - cannot compile new NIC module from source"
date: 2008-03-08
forum: General Help
---

### Post by Rich99 on 2008-03-08
I've just moved a dapper system on to new hardware & the nic isn't supported by the dapper kernel.  It's a broadcom BCM5722 & broadcom provide the source code for the driver.  I downloaded the driver file (linux-3.81c.zip), unzipped it to give 3 tarballs, untarred tg3-3.81c.tar.gz, went to the directory tg3-3.81c & typed 'make' as per the README.  I got the following error:

make -C  SUBDIRS=/home/rich/driver/Server/Linux/Driver/tg3-3.81c modules
make: *** SUBDIRS=/home/rich/driver/Server/Linux/Driver/tg3-3.81c: No such file or directory. Stop.
make: *** [default] Error 2

According to this thread here: [http://ubuntuforums.org/showthread.php?t=691776](http://ubuntuforums.org/showthread.php?t=691776) the first line should read:
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/michael/tmp/tg3/Server/Linux/Driver/ tg3-3.81c modules

If I go the /lib/modules/2.6.15-51-686/ directory, I have no 'build' folder, which I assume is what is causing the problems.  What package creates that folder?  I've installed build-essential, linux-kernel-headers, linux-kernel-source and linux-kernel-dev but still get the same error.  What am I missing?

---

### Post by Rich99 on 2008-03-08
Why is it you always find the answer after posting a question?  I'd installed the wrong kernel headers, all sorted now.

---

