---
title: "problems moving data between time-capsule"
date: 2014-12-05
forum: General Help
---

### Post by mevsthevoices2 on 2014-12-05
So, I managed to get my time-machine mounted through smb with
```
//10.0.0.2/Data /media/time-capsule cifs username=xxx,password=xxx,iocharset=utf8,sec=ntlm
```
under my fstab, but when I transfer files the kernel complains loudly about a repeating
```
CIFS VFS: bogus file nlink value 0
```
None of my searching has turned up much of anything, and I'm a bit of a loss of where I'd start. Is there anyone that could shed a little light on this? It seems to be transferring files back and forth fine, just, having a little issue with this popping up all the time.

---

### Post by mnk123 on 2014-12-14
I'm having the exact same problem with a time capsule, same kernel error log message. Would be great if someone knew how to fix this.

---

### Post by DaBzzz on 2015-09-12
This isn't limited to Apple-SMB. I have the very same error message when accessing a Novell CrapStorage via VPN, which my university work group uses at the campus data center. It pops up dozens of times on every folder change and even after some idle time, maybe for thumbnail generation and pulling meta data (as it is also present on empty folders, txt files only, etc.)

Additionally, those messages also appear when quickly surfing the folders, as if the horribly slow server falls behind and sends unwanted data for seconds...:

```

[726861.149268] CIFS VFS: bogus file nlink value 0
[726862.218387] CIFS VFS: bogus file nlink value 0
[726865.081066] CIFS VFS: No task to wake, unknown frame received! NumMids 3
[726865.081072] Received Data is: : dump of 37 bytes of data at 0xffff880106bb3340
[726865.081075]  23000000 424d53ff ff0002a4 800180ff . . . # \xffffffff S M B \xffffffa4 . . \xffffffff \xffffffff . . .
[726865.081077]  00000000 00000000 00000000 2e9713b1 . . . . . . . . . . . . \xffffffb1 . . .
[726865.081079]  198445b8 00000000 \xffffffb8 E . . .
[726865.081204] CIFS VFS: No task to wake, unknown frame received! NumMids 2
[726865.081206] Received Data is: : dump of 37 bytes of data at 0xffff88010a2bae00
[726865.081208]  23000000 424d53ff ff0002a4 800180ff . . . # \xffffffff S M B \xffffffa4 . . \xffffffff \xffffffff . . .
[726865.081210]  00000000 00000000 00000000 2e9713b1 . . . . . . . . . . . . \xffffffb1 . . .
[726865.081212]  198645b8 00000000 \xffffffb8 E . . .
[...]
[727586.935719] CIFS VFS: No task to wake, unknown frame received! NumMids 0
[727586.935726] Received Data is: : dump of 37 bytes of data at 0xffff88010a2bb500
[727586.935729]  23000000 424d53ff ff0002a4 800180ff . . . # \xffffffff S M B \xffffffa4 . . \xffffffff \xffffffff . . .
[727586.935732]  00000000 00000000 00000000 2f7413b1 . . . . . . . . . . . . \xffffffb1 . t /
[727586.935733]  208345b8 00000000 \xffffffb8 E .   .

```

Using 14.04 LTS, cifs-utils 2:6.0-1ubuntu2 and all the samba stuff is 2:4.1.6+dfsg-1ubuntu2.14.04.9

---

