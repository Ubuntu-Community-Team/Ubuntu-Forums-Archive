---
title: "How to read the offset?"
date: 2012-12-31
forum: General Help
---

### Post by 00oddn4a on 2012-12-31
Hi to all!  Reading the manual of **lsof** i noted the *-o* flag which shows in place of the filesize , the offset. For example:
```

COMMAND     PID  USER   FD   TYPE             DEVICE     OFFSET      NODE NAME
chromium-  1212 sleax  DEL    REG               0,18               150973 /run/shm/.org.chromium.Chromium.3t7B5n
chromium-  1212 sleax    0r   CHR                1,3        0t0      1029 /dev/null
chromium-  1212 sleax    1w   CHR                1,3        0t0      1029 /dev/null
chromium-  1212 sleax    2w   REG               0,22    0t29496   3409205 /home/sleax/.xsession-errors
chromium-  1212 sleax    3u  0000                0,9        0t0      6821 anon_inode
chromium-  1212 sleax    4r   REG                8,6        0t0    919845 /usr/lib/chromium-browser/chrome.pak
chromium-  1212 sleax    5u  unix 0xffff880192258340        0t0    149930 socket
chromium-  1212 sleax    6u  sock                0,7        0t0    151740 can't identify protocol
chromium-  1212 sleax    7u  sock                0,7        0t0   1299162 can't identify protocol

```
How do i read these values? What do *0t0* and *0t29496* mean?
Thanks. :-)

---

### Post by spjackson on 2012-12-31
Does the [lsof FAQ]("ftp://lsof.itap.purdue.edu/pub/tools/unix/lsof/FAQ") help? 14.2 Why does the offset have ``0t' and ``0x'' prefixes?

0t means that the value is an offset in decimal.

---

### Post by rnerwein on 2012-12-31
> **sl34x said:**
> Hi to all!  Reading the manual of **lsof** i noted the *-o* flag which shows in place of the filesize , the offset. For example:
```

COMMAND     PID  USER   FD   TYPE             DEVICE     OFFSET      NODE NAME
chromium-  1212 sleax  DEL    REG               0,18               150973 /run/shm/.org.chromium.Chromium.3t7B5n
chromium-  1212 sleax    0r   CHR                1,3        0t0      1029 /dev/null
chromium-  1212 sleax    1w   CHR                1,3        0t0      1029 /dev/null
chromium-  1212 sleax    2w   REG               0,22    0t29496   3409205 /home/sleax/.xsession-errors
chromium-  1212 sleax    3u  0000                0,9        0t0      6821 anon_inode
chromium-  1212 sleax    4r   REG                8,6        0t0    919845 /usr/lib/chromium-browser/chrome.pak
chromium-  1212 sleax    5u  unix 0xffff880192258340        0t0    149930 socket
chromium-  1212 sleax    6u  sock                0,7        0t0    151740 can't identify protocol
chromium-  1212 sleax    7u  sock                0,7        0t0   1299162 can't identify protocol

```How do i read these values? What do *0t0* and *0t29496* mean?
Thanks. :-)
hi
yeah it's to offset where the process filetable points to.
try follwing and you will understand clearly:
ls -o -p PID_of_rsyslogd   ( has always /var/log/syslog ( and kern.log open)
then ls -l /var/log/sylog (and kern.log) you will see the offset here is the size of the files
(that's because rsyslogd writes sequential). 0 is the begining of the file or it's a stream socket - there you will mostely a zero.
cheers

---

