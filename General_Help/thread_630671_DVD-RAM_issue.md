---
title: "DVD-RAM issue"
date: 2007-12-03
forum: General Help
---

### Post by el_rico on 2007-12-03
Hello,

I am using Ubuntu 7.10 and I cannot use a DVD-RAM in r/w mode. I have tried to mount it as root as suggested in other posts but it still gets mounted read-only.

Here is what I do:

```
eric@brocoli:~$ sudo mount -t udf -o rw /dev/cdrom /media/cdrom0/
mount: block device /dev/scd0 is write-protected, mounting read-only
eric@brocoli:~$ mount
< other volumes info >
/dev/scd0 on /media/cdrom0 type udf (ro)
```

Any idea?

Thanks!

---

### Post by geraldm on 2007-12-04
You did not disclose your hardware.  See the manpage for mount, especiallly type udf
On some hardware it is a read-only filesystem.  On others, it makes no difference whether the user has permission to write, because some restricted systems only allow the root user to 
write.
It would be a problem if the root user could not write to the DVD-RAM.

Gerald

---

### Post by el_rico on 2007-12-06
My drive is a Samsung SH-S203. The problem is that even root is not able to mount it as RW, even though this option is passed to mount...

---

### Post by geraldm on 2007-12-06
Sorry, I do not have an answer for Samsung hardware.
Perhaps you could try writing some filesyatem with data to a blank DVD-RAM, then try to
mount that and read it to see if you got what you wrote. That would show whether the 
hardware works, even though it is not known how OR if it supports rw mode for DVD-RAM

Gerald

---

