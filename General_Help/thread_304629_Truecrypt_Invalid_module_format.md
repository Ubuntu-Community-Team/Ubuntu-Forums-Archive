---
title: "Truecrypt: Invalid module format"
date: 2006-11-22
forum: General Help
---

### Post by shizow on 2006-11-22
I am using Edgy with all updates.
I installed the deb file provided by truecrypt.org for edgy.
I made a truecrypt partition on my external disk(the whole disk).
This worked.

But when i try to start truecrypt:

```

sudo truecrypt --device-number 0 /dev/sda
Enter password for '/dev/sda':
insmod: error inserting '/usr/share/truecrypt/kernel/truecrypt-2.6.17.ko': -1 Invalid module format
FATAL: Module truecrypt not found.
truecrypt: Failed to load TrueCrypt kernel module

```

any suggestions?

---

### Post by kc109 on 2006-11-24
No help but I get the same after downloading and installing the Ubuntu 6.10 x86 .deb package from [www.truecrypt.org/downloads.php](www.truecrypt.org/downloads.php)

/usr/bin/truecrypt /media/hda10/test.tc ~/tc-test
Enter password for '/media/hda10/test.tc': 
insmod: error inserting '/usr/share/truecrypt/kernel/truecrypt-2.6.17.ko': -1 Invalid module format
FATAL: Module truecrypt not found.
truecrypt: Failed to load TrueCrypt kernel module

modinfo /usr/share/truecrypt/kernel/truecrypt-2.6.17.ko
filename:       /usr/share/truecrypt/kernel/truecrypt-2.6.17.ko
author:         TrueCrypt Foundation
description:    device-mapper target for encryption and decryption of TrueCrypt volumes
license:        GPL and additional rights
vermagic:       2.6.17.13-ubuntu1 SMP mod_unload 586 REGPARM gcc-4.1
depends:        dm-mod
srcversion:     DE03299AC42280F13545208
parm:           trace:Trace level (int)

uname -a
Linux ubuntu 2.6.17-10-386 #2 Fri Oct 13 18:41:40 UTC 2006 i686 GNU/Linux

Mmm... I know nothing about Linux systems but could it be something to do with the difference between the kernel version and the vermagic info?

---

### Post by shizow on 2006-11-25
i think one has to compile truecrypt from source
i am doing that now

---

### Post by manni on 2006-11-26
I had the same problem (same error message and same versions). 

After installing the kernel source I compiled truecrypt from source following 
[http://wiki.ubuntuusers.de/TrueCrypt]("http://wiki.ubuntuusers.de/TrueCrypt")

No more errors. It is working as expected.

---

### Post by mikelanc on 2006-11-27
I've followed the instructions at [http://wiki.ubuntuusers.de/TrueCrypt](http://wiki.ubuntuusers.de/TrueCrypt) (as best I could - can't read German)
I've done everything suggested on [http://www.ubuntuforums.org/showthread.php?t=269305](http://www.ubuntuforums.org/showthread.php?t=269305)

but still it doesn't work.
insmod: error inserting '/usr/share/truecrypt/kernel/truecrypt-2.6.17.ko': -1 Invalid module format
FATAL: Error inserting truecrypt (/lib/modules/2.6.17-10-386/extra/truecrypt.ko): Invalid module format
truecrypt: Failed to load TrueCrypt kernel module

kernel version is 2.6.17-10

How can I reset and start again?  Something must be configured wrong.  Is it a case of deleting the kernel source and headers and truecrypt, redownloading it?

---

### Post by kc109 on 2006-11-28
I am following the same instructions except changing the values to match my system
linux-source-2.6.17
gcc-4.1

when I sudo ./build.sh I get the following error

Checking build requirements...
Building internal kernel modules (may take a long time)... In file included from fs/nfs/inode.c:49:
fs/nfs/internal.h:24: error: static declaration of ‘nfs_do_refmount’ follows non-static declaration
include/linux/nfs_fs.h:320: error: previous declaration of ‘nfs_do_refmount’ was here
fs/nfs/internal.h:65: warning: ‘struct nfs4_fs_locations’ declared inside parameter list

[snip the long list of other error and warning messages to keep it brief]

I have found other references to the same list of errors but no solution
[http://ubuntuforums.org/showthread.php?p=1612788](http://ubuntuforums.org/showthread.php?p=1612788)
and
[http://linux-nfs.org/pipermail/nfsv4/2006-June/004505.html](http://linux-nfs.org/pipermail/nfsv4/2006-June/004505.html)

Anyone have any ideas on how to proceed.
TIA

---

### Post by Cone on 2006-12-21
Hey, having the same problem here and just wondering if anyone has figured out where these errors are stemming from.

Any help would be very appreciated.

Thanks.

---

### Post by Ted_Smith on 2006-12-23
Me too, on Dapper using the dpkg package from the Truecrpyt website : 

ted@mainunit:~/Downloads/truecrypt-4.2a$ truecrypt test ~/Temp
Enter password for '/home/ted/Downloads/truecrypt-4.2a/test':
FATAL: Module truecrypt not found.
truecrypt: Failed to load TrueCrypt kernel module

Mmmm...I have compiled it from source before (using a HOWTO on the Truecrypt discussion forum) but had hoped that the newer dpkg's would work OK.

---

### Post by Cone on 2006-12-23
It happened to me both when I compiled it from source and when I tried using the deb from the website.

And I made sure it was actually outputting the module when compiling by rm'ing the old file just to be absolutely certain. :/

Still haven't figured this one out.

---

### Post by clas on 2007-02-10
I had the same problem, even with a compiled truecrypt.

My solution was to delete the kernel-source-... under /usr/src/ and reinstall the kernel source.

When I afterwards launched build.sh in truecrypt, it asked me if I wanted to compile the kernel modules, which I agreed to.

After running install.sh I was again able to mount my truecrypt files.

---

### Post by korami on 2007-05-16
In case someone still has this problem, I managed to fix it by reinstalling truecrypt using the deb package from truecrypt's website: [http://www.truecrypt.org/downloads.php](http://www.truecrypt.org/downloads.php)

---

